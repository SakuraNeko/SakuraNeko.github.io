---
title: 如何取得UnityHub内旧版本Unity下载链接
date: 2020-3-1 00:00:00
categories:
- [猫都能看懂的游戏开发教程]
tags:
- 技术
- Unity Engine
- UnityHub
---

**关键词：** 游戏开发、Unity、小技巧

**授权协议：** [CC BY-NC-SA 3.0](http://creativecommons.org/licenses/by-nc-sa/3.0/)，转载请标注来源

**本文为解决单一问题而准备，不具有技术和普适性。**

**也可能因为引擎开发商政策修改导致方法失效。**

**目前最新非测试版本为Unity 2020.1.8（2020/11/4）。**

----

![题图](banner.png)

## 前言

在之前工作的时候同事曾经遇到过一个 **“小”** 问题：

如果要下载安装一个打开特定工程版本的Unity编辑器且通过Unity Hub进行安装，但当你在Unity决定安装一个新版本引擎的时候，往往会遇到这样的窘境……

![大革命集线器（Unity Hub）](unityhub-scn.png)

没错， **只有当前最新版本的引擎能在列表中找到，而且当你下载后还会有特殊的事情发生！**

在你黑人问号自己在寻找什么东西时，你会发现此行的第一个**陷阱**：

![ ](add-unity.png)

然后稀里糊涂的跳转到中文官网上，下载了**特供**的EXE安装包……

之后再将引擎导入到Hub中，喝着被子里速溶咖啡装作什么事情都没发生。（其实在偷偷摸鱼）


**有没有更为节约时间的方法呢？**

“比如说我要同时下载几个引擎版本的时候……”

![1……2……3！](1……2……3!.png)

**当然有！来直接借助Unity Hub快速安装链接安装吧！**

下面是链接的地址：
[Unity - download archive](https://unity3d.com/get-unity/download/archive)

轻击一下，“世界”我有！

![唤醒集线器做奴隶](U-D-A.png)

但细心的你很快就会发现，这个网址的访问时好时坏，有时候甚至会空白一片完全加载不出来……

除非，你掌握**某些科学的方式**才能缓解窘境。

-------------

## 解法

而**本文**的意义，在于让暂时无法缓解窘境的朋友们能**弯道超车**！

顺带还能**避免**下载到中国特供版……

这个超车方式异常简单，请看下面！

### 步骤

#### 1、请在下表中找到你需要的引擎版本，然后复制它；

##### Unity 2020.2（Beta）：
```
unityhub://2020.2.0b9/ef2968fa77ae
```
##### Unity 2020.1：
```
unityhub://2020.1.11f1/698c1113cef0
unityhub://2020.1.10f1/974a9d56f159
unityhub://2020.1.9f1/145f5172610f
unityhub://2020.1.8f1/22e8c0b0c3ec
unityhub://2020.1.7f1/064ffcdb64ad
unityhub://2020.1.6f1/fc477ca6df10
unityhub://2020.1.5f1/e025938fdedc
unityhub://2020.1.4f1/fa717bb873ec
unityhub://2020.1.3f1/cf5c4788e1d8
unityhub://2020.1.2f1/7b32bc54ba47
unityhub://2020.1.1f1/2285c3239188
unityhub://2020.1.0f1/2ab9c4179772
```
##### Unity 2019.4（LTS）：
```
unityhub://2019.4.13f1/518737b1de84
unityhub://2019.4.12f1/225e826a680e
unityhub://2019.4.11f1/2d9804dddde7
unityhub://2019.4.10f1/5311b3af6f69
unityhub://2019.4.9f1/50fe8a171dd9
unityhub://2019.4.8f1/60781d942082
unityhub://2019.4.7f1/e992b1a16e65
unityhub://2019.4.6f1/a7aea80e3716
unityhub://2019.4.5f1/81610f64359c
unityhub://2019.4.4f1/1f1dac67805b
unityhub://2019.4.3f1/f880dceab6fe
unityhub://2019.4.2f1/20b4642a3455
unityhub://2019.4.1f1/e6c045e14e4e
unityhub://2019.4.0f1/0af376155913
```
##### Unity 2019.3：
```
unityhub://2019.3.15f1/59ff3e03856d
unityhub://2019.3.14f1/2b330bf6d2d8
unityhub://2019.3.13f1/d4ddf0d95db9
unityhub://2019.3.12f1/84b23722532d
unityhub://2019.3.11f1/ceef2d848e70

unityhub://2019.3.10f1/5968d7f82152
unityhub://2019.3.9f1/e6e740a1c473
unityhub://2019.3.8f1/4ba98e9386ed
unityhub://2019.3.8f1/4ba98e9386ed
unityhub://2019.3.7f1/6437fd74d35d
unityhub://2019.3.6f1/5c3fb0a11183
unityhub://2019.3.5f1/d691e07d38ef
unityhub://2019.3.4f1/4f139db2fdbd
unityhub://2019.3.3f1/7ceaae5f7503
unityhub://2019.3.2f1/c46a3a38511e
unityhub://2019.3.1f1/89d6087839c2
unityhub://2019.3.0f6/27ab2135bccf
```
##### Unity 2019.2：
```
unityhub://2019.2.21f1/9d528d026557
unityhub://2019.2.20f1/c67d00285037

unityhub://2019.2.19f1/929ab4d01772
unityhub://2019.2.18f1/bbf64de26e34
unityhub://2019.2.17f1/8e603399ca02
unityhub://2019.2.16f1/b9898e2d04a4
unityhub://2019.2.15f1/dcb72c2e9334
unityhub://2019.2.14f1/49dd4e9fa428
unityhub://2019.2.13f1/e20f6c7e5017
unityhub://2019.2.12f1/b1a7e1fb4fa5
unityhub://2019.2.11f1/5f859a4cfee5
unityhub://2019.2.10f1/923acd2d43aa

unityhub://2019.2.9f1/ebce4d76e6e8
unityhub://2019.2.8f1/ff5b465c8d13
unityhub://2019.2.7f2/c96f78eb5904
unityhub://2019.2.6f1/fe82a0e88406
unityhub://2019.2.5f1/9dace1eed4cc
unityhub://2019.2.4f1/c63b2af89a85
unityhub://2019.2.3f1/8e55c27a4621
unityhub://2019.2.2f1/ab112815d860
unityhub://2019.2.1f1/ca4d5af0be6f
unityhub://2019.2.0f1/20c1667945cf
```
##### Unity 2019.1：
```
unityhub://2019.1.14f1/148b5891095a
unityhub://2019.1.13f1/b5956c0a61e7
unityhub://2019.1.12f1/f04f5427219e
unityhub://2019.1.11f1/9b001d489a54
unityhub://2019.1.10f1/f007ed779b7a

unityhub://2019.1.9f1/d5f1b37da199
unityhub://2019.1.8f1/7938dd008a75
unityhub://2019.1.7f1/f3c4928e5742
unityhub://2019.1.6f1/f2970305fe1c
unityhub://2019.1.5f1/0ca0f5646614
unityhub://2019.1.4f1/ffa3a7a2dd7d
unityhub://2019.1.3f1/dc414eb9ed43
unityhub://2019.1.2f1/3e18427e571f
unityhub://2019.1.1f1/fef62e97e63b
unityhub://2019.1.0f2/292b93d75a2c
```
##### Unity 2018.4 (LTS) ：
```
unityhub://2018.4.28f1/a2d4f71491a4
unityhub://2018.4.27f1/4e283b7d3f88
unityhub://2018.4.26f1/a7ac1c6396db
unityhub://2018.4.25f1/b07bfa0a8827
unityhub://2018.4.24f1/3071911a89e9
unityhub://2018.4.23f1/c9cf1a90e812
unityhub://2018.4.22f1/3362ffbb7aa1
unityhub://2018.4.21f1/fd3915227633
unityhub://2018.4.20f1/008688490035

unityhub://2018.4.19f1/459f70f82ea4
unityhub://2018.4.18f1/61fce66342ad
unityhub://2018.4.17f1/b830f56f42f0
unityhub://2018.4.16f1/e6e9ca02b32a
unityhub://2018.4.15f1/13f5a1bf9ca1
unityhub://2018.4.14f1/05119b33d0b7
unityhub://2018.4.13f1/497f083a43af
unityhub://2018.4.12f1/59ddc4c59b4f
unityhub://2018.4.11f1/7098af2f11ea
unityhub://2018.4.10f1/a0470569e97b

unityhub://2018.4.9f1/ca372476eaba
unityhub://2018.4.8f1/9bc9d983d803
unityhub://2018.4.7f1/b9a993fd1334
unityhub://2018.4.6f1/cde1bbcc9f0d
unityhub://2018.4.5f1/7b38f8ac282e
unityhub://2018.4.4f1/5440768ff61c
unityhub://2018.4.3f1/8a9509a5aff9
unityhub://2018.4.2f1/d6fb3630ea75
unityhub://2018.4.1f1/b7c424a951c0
unityhub://2018.4.0f1/b6ffa8986c8d
```
##### Unity 2018.3：
```
unityhub://2018.3.14f1/d0e9f15437b1
unityhub://2018.3.13f1/06548a9e9582
unityhub://2018.3.12f1/8afd630d1f5b
unityhub://2018.3.11f1/5063218e4ab8
unityhub://2018.3.10f1/f88de2c96e63

unityhub://2018.3.9f1/947e1ea5aa8d
unityhub://2018.3.8f1/fc0fe30d6d91
unityhub://2018.3.7f1/9e14d22a41bb
unityhub://2018.3.6f1/a220877bc173
unityhub://2018.3.5f1/76b3e37670a4
unityhub://2018.3.4f1/1d952368ca3a
unityhub://2018.3.3f1/393bae82dbb8
unityhub://2018.3.2f1/b3c100a4b73a
unityhub://2018.3.1f1/bb579dc42f1d
unityhub://2018.3.0f2/6e9a27477296
```
##### Unity 2018.2：
```
unityhub://2018.2.21f1/a122f5dc316d
unityhub://2018.2.20f1/cef3e6c0c622

unityhub://2018.2.19f1/06990f28ba00
unityhub://2018.2.18f1/4550892b6062
unityhub://2018.2.17f1/88933597c842
unityhub://2018.2.16f1/39a4ac3d51f6
unityhub://2018.2.15f1/65e0713a5949
unityhub://2018.2.14f1/3262fb3b0716
unityhub://2018.2.13f1/83fbdcd35118
unityhub://2018.2.12f1/0a46ddfcfad4
unityhub://2018.2.11f1/38bd7dec5000
unityhub://2018.2.10f1/674aa5a67ed5

unityhub://2018.2.9f1/2207421190e9
unityhub://2018.2.8f1/ae1180820377
unityhub://2018.2.7f1/4ebd28dd9664
unityhub://2018.2.6f1/c591d9a97a0b
unityhub://2018.2.5f1/3071d1717b71
unityhub://2018.2.4f1/cb262d9ddeaf
unityhub://2018.2.3f1/1431a7d2ced7
unityhub://2018.2.2f1/c18cef34cbcd
unityhub://2018.2.1f1/1a9968d9f99c
unityhub://2018.2.0f2/787658998520
```
##### Unity 2018.1：
```
unityhub://2018.1.9f2/a6cc294b73ee
unityhub://2018.1.8f1/26051d4de9e9
unityhub://2018.1.7f1/4cb482063d12
unityhub://2018.1.6f1/57cc34175ccf
unityhub://2018.1.5f1/732dbf75922d
unityhub://2018.1.4f1/1a308f4ebef1
unityhub://2018.1.3f1/a53ad04f7c7f
unityhub://2018.1.2f1/a46d718d282d
unityhub://2018.1.1f1/b8cbb5de9840
unityhub://2018.1.0f2/d4d99f31acba
```
##### Unity 2017.4 (LTS) ：
```
unityhub://2017.4.40f1/6e14067f8a9a
unityhub://2017.4.39f1/947131c5be7e
unityhub://2017.4.38f1/82ac2fb100ce
unityhub://2017.4.37f1/78b69503ebc4
unityhub://2017.4.36f1/c663def8414c
unityhub://2017.4.35f1/e57a7bcbbf0b
unityhub://2017.4.34f1/121f18246307
unityhub://2017.4.33f1/a8557a619e24
unityhub://2017.4.32f1/4da3ed968770
unityhub://2017.4.31f1/9c8dbc3421cb
unityhub://2017.4.30f1/c6fa43736cae

unityhub://2017.4.29f1/06508aa14ca1
unityhub://2017.4.28f1/e3a0f7dd2097
unityhub://2017.4.27f1/0c4b856e4c6e
unityhub://2017.4.26f1/3b349d10f010
unityhub://2017.4.25f1/9cba1c3a94f1
unityhub://2017.4.24f1/786769fc3439
unityhub://2017.4.23f1/f80c8a98b1b5
unityhub://2017.4.22f1/eb4bc6fa7f1d
unityhub://2017.4.21f1/de35fe252486
unityhub://2017.4.20f2/413dbd19b6dc

unityhub://2017.4.19f1/47cd37c28be8
unityhub://2017.4.18f1/a9236f402e28
unityhub://2017.4.17f1/05307cddbb71
unityhub://2017.4.16f1/7f7bdd1ef02b
unityhub://2017.4.15f1/5d485b4897a7
unityhub://2017.4.14f1/b28150134d55
unityhub://2017.4.13f1/6902ad48015d
unityhub://2017.4.12f1/b582b87345b1
unityhub://2017.4.11f1/8c6b8ef6d111
unityhub://2017.4.10f1/f2cce2a5991f

unityhub://2017.4.9f1/6d84dfc57ccf
unityhub://2017.4.8f1/5ab7f4878ef1
unityhub://2017.4.7f1/de9eb5ca33c5
unityhub://2017.4.6f1/c24f30193bac
unityhub://2017.4.5f1/89d1db9cb682
unityhub://2017.4.4f1/645c9050ba4d
unityhub://2017.4.3f1/21ae32b5a9cb
unityhub://2017.4.2f2/52d9cb89b362
unityhub://2017.4.1f1/9231f953d9d3
```
##### Unity 2017.3：
```
unityhub://2017.3.1f1/fc1d3344e6ea
unityhub://2017.3.0f3/a9f86dcd79df
```
##### Unity 2017.2：
```
unityhub://2017.2.5f1/588dc79c95ed
unityhub://2017.2.4f1/f1557d1f61fd
unityhub://2017.2.3f1/372229934efd
unityhub://2017.2.2f1/1f4e0f9b6a50
unityhub://2017.2.1f1/94bf3f9e6b5e
unityhub://2017.2.0f3/46dda1414e51
```
##### Unity 2017.1：
```
unityhub://2017.1.5f1/9758a36cfaa6
unityhub://2017.1.4f1/9fd71167a288
unityhub://2017.1.3f1/574eeb502d14
unityhub://2017.1.2f1/cc85bf6a8a04
unityhub://2017.1.1f1/5d30cf096e79
unityhub://2017.1.0f3/472613c02cf7
```
##### Unity 5：
```
unityhub://5.6.7f1/e80cc3114ac1
unityhub://5.6.6f2/6bac21139588
unityhub://5.6.5f1/2cac56bf7bb6
unityhub://5.6.4f1/ac7086b8d112
unityhub://5.6.3f1/d3101c3b8468
unityhub://5.6.2f1/a2913c821e27
unityhub://5.6.1f1/2860b30f0b54
unityhub://5.6.0f3/497a0f351392
```
>Unity5.6以下版本不支持从Unity Hub中部署，故无法提供链接。

#### 2、将复制好的内容填到浏览器地址栏并按下回车（任何浏览器都行）；
>*在Windows下也可以在运行（Win键+R）菜单中填入

![“运行”](run.png)

如果有弹出窗口，请直接**确认**！

![该站点试图打开UnityHub](open-unityhub.png)

#### 3、等待UnityHub被唤醒，然后选择需要的模块安装即可！

![大功告成！](great-succeed.png)

> 因为网络条件差异，有时候会慢一点……

-----

## 其他

**什么？你还没有用Unity Hub？**

**那赶紧点击下面链接下载吧！**

[Unity Hub - Unity 3D](https://public-cdn.cloud.unity3d.com/hub/prod/UnityHubSetup.exe)

​
*下载的时候是否使用科学方式将决定你下载的客户端是全球版还是特供版。

>虽然即使下载了全球版也会被升级成特供客户端的<br/>（拒绝更新特供版即可绕开）……

---

![赤魔導士 新AF（By：ももこ） | Pixiv 73939373](赤魔導士-新AF.png)

> 赤魔導士 新AF（By：ももこ） | Pixiv 73939373

**本文以[CC BY-NC-SA 3.0](http://creativecommons.org/licenses/by-nc-sa/3.0/)协议发布，转载请标注来源。**