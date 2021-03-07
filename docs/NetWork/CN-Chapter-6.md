---
title: Computer Network-Chapter 6
tags: 网络
categories: 课程学习
---
<font face="微软雅黑"> </font>
<center>链路层 </center>

<!-- more -->


# 第六章 链路层和局域网
## 链路层概述
**链路层提供的服务**
- 成帧
- 链路介入：媒体访问控制（MAC）
- 可靠交付
- 差错检测和纠正
链路层的主体部分是在**网络适配器**中实现的，网络适配器又称为网络接口卡（NIC）。位于网络适配器核心的是链路层控制器，该控制器是一个实现许多链路层服务的专用芯片。
链路层是硬件与软件的结合体。

## 差错检测和纠正技术
差错检测和纠正比特（EDC）
1. 奇偶校验
2. 检验和方法：运输层
3. 循环冗余检测：链路层

## 多路访问链路和协议
**广播链路**：多个发送和接收节点连接到相同的、单一的、共享的广播信道上。当任何一个节点传输一个帧，信道广播该帧，每个其他节点都收到一个副本。以太网和无线局域网是广播链路层技术的例子。

**信道划分协议**：时分多路复用（TDM）、频分多路复用（FDM）、码分多址（CDMA）
**随机接入协议：**重发该帧之前等待一个随机时延。时隙ALOHA、ALOHA、载波侦听多路访问（CSMA）、带碰撞检测的载波侦听多路访问（CDMS/CD）
**轮流协议：**轮询协议、令牌传递协议

用于电缆因特网接入的链路层协议：DOCSIS

## 交换局域网
**链路层寻址和ARP**
MAC地址：又称LAN地址、物理地址。6字节。网络适配器具有的链路层地址。
ARP：地址解析协议，网络层地址和链路层地址之间的转换。ARP表。

**以太网**
以太网帧结构
 <img  src="https://raw.githubusercontent.com/tiandaochouqin1/Sources/main/images/Ethernet.png" alt=以太网帧结构 width=700   align=center >
以太网技术向网络层提供无连接、不可靠服务。
**交换机**
流量隔离：路由器、交换机
即插即用：集线器、交换机
优化路由：路由器

## 链路虚拟化
多协议标签交换（MPLS）:一种在开放的通信网上利用标签引导数据高速、高效传输的新技术。多协议的含义是指MPLS不但可以支持多种网络层层面上的协议，还可以兼容第二层的多种数据链路层技术。

 <img  src="https://raw.githubusercontent.com/tiandaochouqin1/Sources/main/images/MPLS.jpg" alt=MPLS width=500   align=center >

基于标签执行交换、流量管理能力、执行MPLS转发路径的快速恢复、虚拟专用网（VPN）

## 数据中心网络
 <img  src="https://raw.githubusercontent.com/tiandaochouqin1/Sources/main/images/DataCenter.png" alt=数据中心网络 width=600    align=center >

## 回顾-页面请求的历程
待补充


