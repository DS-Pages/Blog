---
title: 家里云和家庭网络配置说明
date: 2025-02-16T16:41:58+08:00
lastmod: 2025-02-17T05:50:50+08:00
author: DongShaoNB
# avatar: avatar.jpg
# authorlink: https://author.site
cover: proxmox_logo.png
# images:
#   - proxmox_logo.png
categories:
  - 教程
tags:
  - PVE
  - OpenWrt
# nolastmod: true
---
 
本文简述博主的家里云和家庭网络配置
 
<!--more-->

# 服务器配置

## 硬件配置

| 配件  |        型号         |
| :---: | :-----------------: |
|  CPU  | i5-12600KF (10c16t) |
| 内存  |    64G (32G * 2)    |
| 固态  |         1TB         |
| 机械  |    8TB (4TB * 2)    |

## 软件配置

基于 PVE 虚拟化平台（固态硬盘用于安装系统及虚拟机），PVE 上安装 OpenWrt 和 TrueNAS，OpenWrt 为主路由，TrueNAS 将两块 4T 机械硬盘组建为 ZFS 镜像模式，在确保单盘故障时数据安全的前提下提供 4T 可用存储空间。

虚拟机的系统安装在固态硬盘上，在 TrueNAS 的存储池中为每一个虚拟机分别创建一个专用的数据集，并将这些数据集共享给对应的虚拟机用于数据存储，Windows 通过 SMB 映射为磁盘，Linux 通过 NFS 映射为磁盘，这样就算固态硬盘出现故障也能保护数据。

# 网络配置

## OpenWrt
  
> [!WARNING]
> **“旁路由”是一种错误的使用方式**  
> [关于“旁路由”的一些吐槽](https://github.com/Aethersailor/Custom_OpenClash_Rules/wiki/%E5%85%B3%E4%BA%8E%E2%80%9C%E6%97%81%E8%B7%AF%E7%94%B1%E2%80%9D%E7%9A%84%E4%B8%80%E4%BA%9B%E5%90%90%E6%A7%BD)
  
OpenWrt 安装 OpenClash 插件翻墙，按照 [此教程](https://github.com/Aethersailor/Custom_OpenClash_Rules)进行配置

## 无线网络

服务器的 LAN 口接到交换机，交换机再接到原硬路由作 AP 使用，将硬路由设置为中继模式

## 网段

博主按照不同类型的设备区分了网段

> [!IMPORTANT]
> 如果你也像博主一样区分开网段，请将 OpenWrt 的 LAN 口设置 IPv4 子网掩码为 255.255.0.0，否则无法访问不同网段的设备
  
|       设备类型       |    网段     |
| :------------------: | :---------: |
| 有线连接(包含虚拟机) | 192.168.1.X |
|       无线连接       | 192.168.2.X |
|   家电(米家设备等)   | 192.168.3.X |