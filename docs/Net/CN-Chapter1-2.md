---
title: Computer Network-Chapter 1-2
tags: 网络
categories: 课程学习
---
<font face="微软雅黑"></font>
<center> 概述、应用层  </center>

<!-- more -->


<!-- TOC -->

- [第一章 计算机网络和因特网](#第一章-计算机网络和因特网)
  - [网络核心](#网络核心)
  - [协议层次及服务模型](#协议层次及服务模型)
  - [OSI模型](#osi模型)
- [第二章 应用层](#第二章-应用层)
  - [应用层协议](#应用层协议)
  - [超文本传输协议](#超文本传输协议)
  - [电子邮件](#电子邮件)
  - [因特网目录服务](#因特网目录服务)
  - [文件分发](#文件分发)
  - [视频流和内容分发网](#视频流和内容分发网)
  - [套接字编程](#套接字编程)

<!-- /TOC -->

# 第一章 计算机网络和因特网
  **协议**（protocol）：定义了在两个或者多个通信实体之间交换报文的格式和顺序，以及报文发送和/或接收一条报文或其它事件所采取的动作。
  **TCP**(Transmission Control Protocol):传输控制协议。
  **IP**(Internet Protocol):网际协议。
  
## 网络核心
通过网络链路和交换机移动数据有两种基本方法：分组交换和电路交换。

**分组交换**
分组交换机：路由器和链路层交换机。
存储转发、排队时延和分组丢失、转发表和路由选择协议、
特点：更好的带宽共享；更简单、有效、实现成本更低。端到端延时不可预测。

**电路交换**
频分复用（FDM）和时分复用（TDM）

## 协议层次及服务模型

OSI参考模型

<img  src="https://raw.githubusercontent.com/tiandaochouqin1/Sources/main/images/OSI-7.jpg" alt="OSI模型" width=600  height=800  align=center >  


***

TCP/IP 五层模型

<img src="https://raw.githubusercontent.com/tiandaochouqin1/Sources/main/images/osi-5.png" width=400 height=500  align=center>

## OSI模型

**应用层**
作用：是网络应用和它们的应用协议存留的地方。为计算机用户提供接口，也为用户提供各种网络服务。
协议：HTTP、FTP、POP3、SMTP、DNS。
数据：报文

**表示层**
作用：使通信的应用程序能够解释交换数据的含义。提供各种用于应用层数据的编码和转换功能，确保一个系统的应用层发送的数据能被另外一个系统的应用层识别。

**会话层**
作用：建立、管理和终止表示层实体之间的通信会话。该层的通信由不同设备中的应用程序之间的服务请求和响应组成。

**传输层**
作用：在应用层端点之阿金传送报文。建立主机端到端的链接，为上层协议提供端到端的可靠和透明的数据传输服务，包括处理差错控制和流量控制等问题。
协议：TCP/UDP
数据：报文段

**网络层**
作用：将称为数据报的网络层分组从一台主机移动到另一台主机。通过IP寻址来建立两个节点之间的连接，为源端的运输层送来的分组选择合适的路由和交换节点，传输给目的端的运输层。又称IP协议层。
协议：IP
数据：数据报
路由器工作在网络层。

**数据链路层**
作用：将称为帧的链路层分组从一个网络元素移动到另一个网络元素。将比特组合成字节，再将字节组合成帧，使用链路层地址（以太网使用MAC地址）来访问介质，并进行差错检测。
协议：以太网、WIFI、电缆接入网的DOCSIS协议
数据：帧
交换机工作在链路层。

**物理层**
作用：将帧中的一个比特从一个节点移动到下一个节点。通过物理介质传输比特流。
PDU（协议数据单元）：bit
设备：集线器HUB、中继器、调制解调器、网线、双绞线、同轴电缆
注意：没有寻址的概念

重要概念：封装、首部字段+有效载荷

***

  每一层有不同的设备工作，比如交换机——数据链路层、路由器——网络层。
  <img src="https://raw.githubusercontent.com/tiandaochouqin1/Sources/main/images/devices.png" alt=各层工作的设备 width=800 height=500 align=center>
  
***  
  每一层分别实现不同的协议。
  <img src="https://raw.githubusercontent.com/tiandaochouqin1/Sources/main/images/protocol.png" alt=各层实现的协议 width=800 align=center>

***

病毒：一种需要某种形式的用户交互来感染用户设备的恶意软件。如包含恶意可执行代码的电子邮件附件。
蠕虫：无需任何明显用户交互就能进入设备的用户软件。

Wireshark实验：捕获并检查Web浏览器和Web服务器之间交换的协议报文

# 第二章 应用层
## 应用层协议
网络应用程序体系结构：客户-服务器体系结构（C-S） 和 对等体系结构（P2P）。

**进程通信：**
  1. 客户和服务器进程；
  2. 进程与计算机网络之间的接口：套接字是应用程序进程与运输层协议之间的应用程序编程接口（API）；
  3. 进程寻址：IP地址，端口号。

**运输层协议为应用程序提供的服务：**
  1. 可靠的数据传输
  2. 吞吐量
  3. 定时
  4. 安全性

**因特网提供的运输服务：**
  TCP服务：包括面向连接服务和可靠数据传输服务。
  UDP服务：不提供不必要服务的轻量级运输协议，仅提供最小服务。无连接，不可靠数据传输。
<img src="https://raw.githubusercontent.com/tiandaochouqin1/Sources/main/images/appandprotocoal.png" alt=流行的应用及其应用层协议及支撑的运输协议 height=400 width=600 align=center>

**应用层协议**定义了：
- 交换报文的类型
- 各种报文的语法
- 字段的语义
- 确定一个进程何时以及如何发送报文，对报文进行响应的规则

## 超文本传输协议

**HTTP**（超文本传输协议）：
Web的应用层协议。
定义了报文的结构以及客户和服务器进行报文交换的方式。
无状态协议，不保存关于客户的状态信息。
**Web页面**：一般含有一个HTML基本文件以及多个引用对象。

非持续连接：每个请求/相应对是经一个单独的TCP连接发送。
持续连接：所有请求相应经相同的TCP连接发送。

**HTTP报文的格式**
[参考文章](https://www.cnblogs.com/jiu0821/p/5641600.html)
<img src="https://raw.githubusercontent.com/tiandaochouqin1/Sources/main/images/requestpost.png" alt=请求报文 height=400 width=600 align=center>
请求报文:
- 请求行：方法、URL、HTTP版本
- 首部行
- 实体体

***
<img src="https://raw.githubusercontent.com/tiandaochouqin1/Sources/main/images/replypost.png" alt=响应报文 height=400 width=600 align=center>
响应报文:
- 状态行：版本、状态码、相应状态信息。
- 首部行
- 实体体

***
**Cookies**:允许站点对用户进行跟踪。

**Web缓存器**：也叫代理服务器。CDN
  1. 减少对客户请求的时间；
  2. 减少接入链路到因特网的通信量；
  3. 降低因特网上的Web流量。

## 电子邮件
异步通信媒介。
组成：用户代理、邮件服务器、简单邮件传输协议（SMTP）。
**SMTP**：采用7比特ACSII。一般不使用中间邮件服务器发送邮件。

| 类别 | HTTP | SMTP |
|:---|:-------|:--------|
| 协议 | 拉协议 |推协议 |
| 数据格式 | 数据不受限制 | 7比特ASCII码格式 |
| 文档处理 | 把每个对象封装到它自己的HTTP的响应报文 | 所有对象放在一个报文内 |

**邮件访问协议：** 第三版邮局访问协议（POP3）、因特网邮件访问协议（IMAP）、HTTp

## 因特网目录服务
[参考文章](https://blog.csdn.net/tianxuhong/article/details/74922454)
DNS：Domain Name System，域名系统。
  - 提供主机名到IP地址的目录转换服务。
  - 主机别名
  - 邮件服务器别名
  - 负载分配
DNS是：
  1. 一个由分层的DNS服务器实现的分布式数据库；
  2. 一个使得主机能够查询分布式数据库的应用层协议，运行在UDP，端口53上。

**DNS工作机理概述**
  1. 分布式、层次数据库;递归查询和迭代查询
  2. DNS缓存：改善时延性能、减少在因特网上传输的DNS报文数量。
  3. DNS记录和报文
<img src="https://raw.githubusercontent.com/tiandaochouqin1/Sources/main/images/DNS.png" alt=DNS报文 height=500 width=900 align=center>

## 文件分发
P2P
自扩展性：对等方是比特的消费者也是重新分发者。
bitTorrent
## 视频流和内容分发网
**DASH**：经HTTP的动态适应流。采用速率决定算法。
**CDN**内容分发网:
利用DNS截获和重定向请求。
两种服务器安置原则：深入和邀请做客。
集群选择策略：动态地将客户定向到CDN中的某个服务器集群或者数据中心的机制。
学习案例：Netflix、YouTube

## 套接字编程
生成网络应用。TCP/UDP。
