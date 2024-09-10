---
title: 使用命令行全新安装Windows操作系统（附文件备份教程）
date: 2022-06-15 21:30:30
categories:
- [运维, 装机]
tags: 
- 技术
- Ops
- Windows
- Command Line 
- OS Install
- Backup
---

**关键词：** 运维、命令行、装机、备份

**授权协议：** [CC BY-NC-SA 3.0](https://creativecommons.org/licenses/by-nc-sa/3.0/)，转载请标注来源

---
## 前言

操作系统安装是每个专业计算机使用者应该学会的必备技能。

某些特殊情况下，我们可能无法使用图形化界面在新的驱动器上部署Windows操作系统，这时候使用命令行则成为了可选的方式。本文是笔者为整理在虚拟驱动器上部署Windows操作系统所写，其的步骤和方式在裸机上同样可用。

**注意：如果需要进行文件备份，可以先看补充部分再看步骤部分。**

---

## 步骤

### 第零阶段：预先准备

首先，请准备好 Windows 安装镜像（通常为 ISO 格式的光盘镜像文件），你可以在微软官网上下载 Media Creation Tool 制作或在官网上直接下载镜像文件。

下面是官方的镜像和工具的下载页面：

* [Windows 10](https://www.microsoft.com/en-us/software-download/windows10)
* [Windows 11](https://www.microsoft.com/en-us/software-download/windows11)

笔者不推荐使用来自于其他网站的非官方镜像版本（除非来源经过了适当的审查以确保安全）。

使用例如 Rufus 一类的驱动磁盘制作软件在其他计算机上制作好所需的启动U盘，并提前查询需要维护的计算机所需的启动项选择快捷键就可以开始进行裸机安装程序了。

* 下载 [Rufus](https://rufus.ie/)

如果手工制作启动U盘请注意使用 FAT32 格式作为文件系统格式。

如遇到 FAT32 最大文件限制可使用 DISM 工具将镜像分块：
```
Dism /Split-Image /ImageFile:D:\sources\install.wim /SWMFile:D:\sources\install.swm /FileSize:4096
```
> 路径中的分卷号请按照实际情况予以更换。

关闭需要维护的计算机，并断开不需要操作的其他驱动器的硬件接口（可选步骤）。并连接上准备好的U盘。

多次尝试，直到能进入 Windows RE 恢复环境

在使用正确方式启动后，你应该可以看到 Windows RE 环境，这是微软为部署和维护 Windows 操作系统设计的最小化启动环境。然后在高级设置中选择使用使用命令行工具进行维护。

如果步骤正确，你将看到 CMD 工具的字符窗口。

接下来我们将正式进入到裸机安装步骤。

请被操作的设备内重要的资料文件已经得到妥善的备份，该操作将彻底彻底设备上的一切文件和信息。

---

### 第一阶段：使用 Diskpart 工具对磁盘进行适当的处置

首先，我们需要使用 Diskpart 工具对磁盘进行适当的处置，以保证我们可以在后续的步骤中正确的安装操作系统。

其全部命令如下（可以拷贝作为脚本）：

```
diskpart
list disk
select disk 0
convert gpt
create partition efi size=260
format quick fs=fat32 label="System"
assign letter="S"
create partition msr size=16
create partition primary
shrink minimum=1260
gpt attributes=0x0000000000000000
format quick fs=ntfs label="Windows OS"
assign letter="W"
create partition primary size=1260
set id=DE94BBA4-06D1-4D40-A16A-BFD50179D6AC
gpt attributes=0x8000000000000001
format quick fs=ntfs label="Recovery"
assign letter="R"
rescan
exit
```

下面我们进行每一步骤的解释说明：

1. 启用 Diskpart 工具：
```
diskpart
```
2. 列出设备上的全部驱动器：
```
list disk
```
3. 选择需要操作的驱动器：
```
select disk 0
```
> 注意：请根据列出的驱动器来选择需要处理的驱动器，可通过名称、容量来确定所应该操作的驱动器。
4. 将被选择的驱动器引导方式转换为 GPT 方式：
```
convert gpt
```
> 在大多数现代（2013年后生产）计算机上，已默认使用UEFI+GPT形式的组合来作为引导机制。
5. 创建用于 UEFI 引导的 EFI 分区：
```
create partition efi size=260
```
6. 转换该分区文件系统格式为 FAT32 ，并添加卷标“System”：
```
format quick fs=fat32 label="System"
```
7. 注册该分区的分区号为S：
```
assign letter="S"
```
8. 创建 MSR 分区：
```
create partition msr size=16
```
> 该 MSR 分区是用于操作系统后期执行例如 Bitlocker 等可能变更分区所需要的操作预留的。
9. 使用剩下的全部磁盘空间创建一个分区：
```
create partition primary
```
10. 收缩之前的分区，为回复分区创建预留空间：
```
shrink minimum=1260
```
> 按照微软的解释，恢复分区需要至少650MB以上的空间，但为了之后的升级扩展，本文设定为1260MB。
11. 设定该分区为可读写的GPT分区：
```
gpt attributes=0x0000000000000000
```
12. 转换该分区文件系统格式为NTFS，并添加卷标“Windows OS”：
```
format quick fs=ntfs label="Windows OS"
```
13. 注册该分区的分区号为W：
```
assign letter="W"
```
14. 创建 Windows RE 分区：
```
create partition primary size=1260
```
15. 设定恢复分区所需的ID：
```
set id=DE94BBA4-06D1-4D40-A16A-BFD50179D6AC
```
> 微软文档指出：恢复分区必须使用“DE94BBA4-06D1-4D40-A16A-BFD50179D6AC”作为ID。
16. 设定改分区为受保护分区（防止误操作损坏恢复工具）：
```
gpt attributes=0x8000000000000001
```
17. 转换该分区文件系统格式为 NTFS ，并添加卷标“Recovery”：
```
format quick fs=ntfs label="Recovery"
```
18. 注册该分区的分区号为R：
```
assign letter="R"
```
19. 验证该驱动器分配操作是否存在问题：
```
rescan
```
20. 退出Diskpart工具：
```
exit
```
至此，驱动器分区的工作全部完成。

---

### 第二阶段：使用Dism工具将操作系统从镜像部署到所需分区上

首先，请通过以下命令确认你的操作系统镜像所在位置和镜像信息。

镜像位置一般位于你接入的可移动驱动器上，将下文命令内的盘符D替换成你可移动驱动器的盘符。
```
dism /get-imageinfo /imagefile:D:\sources\install.wim
```
> 注意：如果你的镜像格式为esd/swm格式，请将命令中的wim替换为esd/swm即可。

然后，根据提示的信息，确定你所需的操作系统镜像序号，并填写到下面的指令内（本案例为序号4）。

```
dism /apply-image /imagefile:D:\sources\install.esd /index:4 /applydir:W:
```
> 注意：applydir参数为系统安装的释放路径。

最后，在之前步骤完成后，通过bcdboot命令设定操作系统的启动配置参数。
```
bcdboot W:\windows /l zh-cn
```
> 注意：l参数为操作系统语言，请按照你的镜像上的语言进行填写。

至此，操作系统已经部署完毕了。

---
### 第三阶段：部署和注册操作系统恢复工具（Windows RE Tools）

微软为了保证在操作系统因为故障而无法启动时，用户能通过备份或其他方式恢复自己的数据所以在设备内一般会装在 Windows RE 分区，我们现在需要人工为该设备装载 Windows RE 设施并注册。

首先，我们创建对应的目录：
```
mkdir R:\Recovery\WindowsRE
```
随后，使用 xcopy 工具将 Windows RE 所需的文件复制到刚刚创建的目录：
```
xcopy /h W:\Windows\System32\Recovery\Winre.wim R:\Recovery\WindowsRE
```
最后在操作系统上注册 Windows RE 启动路径：
```
W:\Windows\System32\Reagentc /setreimage /path R:\Recovery\WindowsRE /target W:\Windows
```
这样，操作系统安装的全部工作就大功告成了。

---

## 外篇：如何备份原有系统上的文件

有些时候，我们可能需要对驱动器内原有的文件进行备份，以防止用户可能并不知道自己的文件并未完成备份。

这同样可以使用 DISM 命令来完成。

**请在开始前确认可移动驱动器是否有足够的存储空间。**

```
Dism /Capture-Image /ImageFile:D:\Backup\Windows.wim /CaptureDir:W:\ /Name:MyBackup 
```
>命令参数解释：  
/Capture-Image - 捕获镜像  
/ImageFile - 指定生成的映像文件释放的路径。  
/CaptureDir - 指定捕获路径。  
/Name - 指定镜像名称（不能省略）。 

备份过程需要一定时间，其耗时取决于用户文件数量和设备性能。

等待镜像创建完成后，创建的镜像可使用例如 [NanaZIP](https://apps.microsoft.com/store/detail/9N8G7TSCL18R) 这一类的文件归档工具进行查看和导出。

---

## 参考

- [DISM Overview | Microsoft Docs](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/what-is-dism)

- [Bare metal reset/recovery: enable your users to create recovery media | Microsoft Docs](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/bare-metal-resetrecovery-enable-your-users-to-create-media-and-to-recover-hard-drive-space/)

- [Deploy Windows RE | Microsoft Docs](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/deploy-windows-re/)

**本文以[CC BY-NC-SA 3.0](https://creativecommons.org/licenses/by-nc-sa/3.0/)协议发布，转载请标注来源。**
