---
title: Hyper-V虚拟机虚拟磁盘文件越用越大怎么办？
date: 2022-7-6 21:30:22
categories:
- [运维，优化]
tags:
- 技术
- Hyper-V
- Optimalize
- VHD
---

**关键词：** Hyper-V、Optimalize、VHD

**授权协议：** [CC BY-NC-SA 3.0](http://creativecommons.org/licenses/by-nc-sa/3.0/)，转载请标注来源

----

## 起因

众所周知，QQ和微信这种国民级小可爱总是偷偷扫描电脑上的数据，且喜欢在各种目录下倾泻废物。 

而且因为工作的原因你还不能选择不用。

于是本人使用了虚拟机来运行这些小可爱。

但是在日常使用中虚拟机的虚拟磁盘会动态扩充体积，即使在虚拟机内进行了文件删除，空间也不能得到自动释放，这很快就会变成一个令人头疼的问题。

---

## 思路

网上不少人给出的方案是在Hyper-V管理器中使用磁盘压缩，但这个方法并没有用处。

还有些人建议通过磁盘管理软件拷贝文件后手动整理，但本人麻烦且费事，而且不小心会把虚拟磁盘里的文件搞坏。

于是去微软的文档中查看有没有官方提供的解决方法，然后找到了微软做的一个命令工具 **Optimize-VHD** 。

微软的文档说明如下：

> **Optimize-VHD** 优化了一个或多个虚拟硬盘文件的空间分配。
>
>这个操作可以回收未使用的块，以及重新排列块，使其更有效地打包，从而减少虚拟硬盘文件的大小。

经过测试,改工具效果很好，所以将使用方法记录下来供不时之需。

---

## 方法

1. 首先将你的的虚拟磁盘在宿主机的 **磁盘管理实用程序** 内用 **只读** 模式挂载（非必须）；

2. 打开PowerShell或CMD输入以下命令处理需要整理的虚拟磁盘：

**注意⚠：请自行替换例子内的路径成为你的虚拟磁盘所在路径。**

### 例子：以快速模式处理需要优化的卷
~~~
Optimize-VHD -Path C:\Demo\Demo.vhdx -Mode Quick
~~~
>快速回收未使用的块，仅在虚拟磁盘以只读模式挂在时可用。

### 例子：在带有空格的路径中以重新裁剪（Retrim）处理需要优化的卷
~~~
Optimize-VHD -Path "D:\Have Space Path\Demo.vhdx" -Mode Retrim
~~~
>向磁盘发送重新裁剪而不扫描零块或回收未使用的块，仅在虚拟磁盘以只读模式挂在时可用。

### 例子：在后台作业中以完整模式处理需要优化的卷
~~~
Optimize-VHD -Path E:\Background-Job\Demo.vhdx -Mode Full -AsJob
~~~
>以完整模式进行扫描和处理（扫描零块并回收未使用的块），仅在虚拟磁盘以只读模式挂在时可用。

3. 享受节省的空间吧！

---

## 参考

- [Optimize-VHD (Hyper-V) | Microsoft Docs](https://docs.microsoft.com/en-us/powershell/module/hyper-v/optimize-vhd)


**本文以[CC BY-NC-SA 3.0](https://creativecommons.org/licenses/by-nc-sa/3.0/)协议发布，转载请标注来源。**