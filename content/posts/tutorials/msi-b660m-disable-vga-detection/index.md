---
title: "微星 (MSI) B660M 主板关闭 VGA Detection 详细教程"
date: 2026-08-10T09:55:00+08:00
# lastmod: 2026-04-17T18:00:00+08:00
# avatar: avatar.jpg
# authorlink: https://author.site
cover: cover.png
# images:
#   - cover.webp
categories:
  - 教程
tags:
  - 主板
# nolastmod: true
---

解决微星 B660M 主板在没有核显和独显的情况下无法进入系统，主板的 VGA 灯常亮白灯的情况

<!--more-->

_封面使用 ChatGPT Images 2.0 生成_

## 问题现象

在 CPU 没有核显，主板也没有插独显的时候，微星 B660M 默认 BIOS 配置下无法进入系统，查看主板的 Debug 灯，发现标签为 VGA 的灯常亮白色

## 根本原因

电脑主板在每次开机时，都会执行一个叫做 POST（Power-On Self-Test，开机自检）的程序。它会依次检查 CPU、内存、显卡（VGA）和启动盘。如果缺少任何一个核心部件，系统就会判定硬件故障，停止引导，并亮起对应的 Debug 灯。像 B660M 这种为家用电脑设计的主板，没有显卡输出属于硬件异常

## 解决方法

首先需要有一张“亮机卡”。所谓亮机卡，就是任意能正常使用的，性能极弱、价格极便宜的显卡，仅仅用于显示画面。博主家刚好有一个十几年前的 GT 710

将亮机卡插到主板的 PCIe 口，连接显示器，开机后狂按 Delete 键，进入 BIOS

**在 BIOS 界面中，按 F7 切换到高级模式，然后依次点击进入**

**Settings -> Advanced -> Integrated Peripherals**

**在列表中找到 VGA Detection 选项，将其修改为 Ignore**

按下 F10 键，选择 “Yes” 保存设置并退出。电脑会自动重启，此时长按机箱电源键将其强制关机

断开电源，拔掉刚才安装的亮机卡。再次开机，此时应可以正常进入系统
