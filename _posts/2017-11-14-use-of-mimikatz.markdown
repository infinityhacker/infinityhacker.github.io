---
layout: post
category: "android"
title:  "mimikatz[神器]"
tags: [mimikataz的用法]
---
### 0x01--简介
  mimikataz是以为法国人Benjamin Delpy发布的一款基于c的开源渗透神器，可以做的事情有很多，主要是从内存中提取密码，哈希值，PIN码，并且可以做伪证，进行哈希绕过，凭据绕过或者直接建立金手指凭据（通俗说法）
  除此之外，mimikatz基本通杀所有windows系统，从wind-xp到win-10，是渗透测试中不可缺少的一款利器，本文主要讲解mimikatz的主要功能以及作适当的拓展
 
### 0x02--使用场景
 进入windows主机并获得管理员权限之后

### 0x03--模块介绍
  mimikatz的模块很多，打开mimikatz后输入```::```就可以获得全部的模块介绍，最简单也是最主要的就是```previlege```模块里面的```debug```命令，主要用于第一步的提权操作，没有这个操作的话，下面的命令将 没有足够的权限运行。

  ### privilege模块
**命令:**
```
  mimikatz# privilege::debug
```
  如果结果返回的是
```
  privilege '20' OK
```
  则说明提权成功。
  如果返回的是
 ```
  ERROR kuhl_m_privilege_simple ; RtlAdjustPrivilege (20) c0000061
 ```
 就说明权限不够，测试的时候可以使用管理员身份运行。
 
 当然，privilege模块还有很多功能来获取其他各种各样的权限，比如获取```驱动权限```，```安全权限```，```tcb权限```等，具体可以通过```privilege::```获得详细信息
 
   ### sekurlsa模块
 这个模块最常用的命令莫过于```logonPasswords```了，使用
 ```
 mimikatz# sekurlsa::logonPasswords
 ```
 本电脑所有的用户以及密码，而且还是明文的喔！下面是实例
 ![image](/images/sekurlsa-test)
