---
title: "解决翼龙面板安装 Fabric 服务端卡住或失败"
date: 2026-05-22T22:38:00+08:00
# lastmod: 2026-04-17T18:00:00+08:00
# avatar: avatar.jpg
# authorlink: https://author.site
cover: cover.png
# images:
#   - cover.webp
categories:
  - 教程
tags:
  - 我的世界
  - 翼龙面板
  - Fabric
# nolastmod: true
---

解决使用翼龙面板部署我的世界 Fabric 服务端预设时，遇到的控制台“卡安装”或最终提示“安装失败”的问题

<!--more-->

_封面使用 ChatGPT Images 2.0 生成_

## 问题现象

在翼龙面板新建 Fabric 服务端并进入控制台时，状态一直显示“正在安装”，但控制台没有任何日志输出。等待许久后，可能会直接提示“安装失败”

## 根本原因

翼龙面板在部署 Fabric 服务端时，会通过**安装脚本**来自动下载服务端核心等必要文件

这个安装脚本并非在宿主机直接运行，而是运行在一个临时的 Docker 容器中。截止发文时，Fabric 预设默认使用的脚本容器镜像是 `eclipse-temurin:21-jdk-jammy`

而问题就出在**拉取镜像**这一步

- Docker 在后台拉取**脚本容器镜像**的进度**不会**实时同步到控制台中，导致控制台没输出，出现"卡安装"
- 如果你的节点服务器拉取 Docker 镜像的速度较慢，很容易因为拉取时间过长导致超时，最终安装失败

## 解决方法

既然找到了病因，解决起来就非常简单了：我们只需要手动在节点服务器上把镜像拉取下来即可

### 操作步骤

连接到对应节点服务器，通过以下命令手动拉取镜像即可，速度慢请自行配置加速源

```bash
docker pull eclipse-temurin:21-jdk-jammy
```
