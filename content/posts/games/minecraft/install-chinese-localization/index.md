---
title: "我的世界地图和整合包汉化安装教程"
date: 2025-11-27T00:30:00+08:00
lastmod: 2025-11-27T00:30:00+08:00
# avatar: /img/author.jpg
# authorlink: https://author.site
cover: cover.png
# covercaption: a description of the cover image
# images:
#   - cover.webp
categories:
  - 我的世界
tags:
  - 我的世界
  - 汉化
  - 教程
# nolastmod: true
---

<!--more-->

本文演示如何为**地图**和**整合包**安装汉化，分别使用 [PCL](https://afdian.com/p/0164034c016c11ebafcb52540025c377)、[Modrinth App](https://modrinth.com/app) 和 [HMCL](https://hmcl.huangyuhui.net/download/) 启动器进行演示

---

# 一、开始前的常识与准备

在正式操作前，建议先了解一些基础概念，并调整好启动器设置

## 1. 版本隔离

默认情况下，所有版本会共用同一个 `mods` 等文件夹，也就是说，只要是带 Mod 加载器的版本，都会加载这些 Mod

如果你同时有：

- 一个 Forge 版本
- 一个 NeoForge 版本
- 一个 Fabric 版本

而某个 Mod 只支持其中一种 Mod 加载器，那么你每次切换版本时，就需要手动禁用另外两个版本的 Mod，非常麻烦

**开启版本隔离，就能很好地解决这个问题**

### 1.1 PCL

#### 文字步骤

1. 打开 PCL
2. 单击上方「`设置`」
3. 单击左侧「`启动`」
4. 在「`启动选项`」下单击「`默认版本隔离`」展开，选择「`隔离可安装 Mod 的版本与非正式版`」

#### 图文步骤

<details>
<summary>点击展开</summary>
<img src="images/pcl/1-step-1.png">
<img src="images/pcl/1-step-2.png">
</details>

### 1.2 Modrinth App

Modrinth App 默认就是按实例隔离的，无需额外设置

### 1.3 HMCL

#### 文字步骤

1. 打开 HMCL
2. 单击左侧「`通用`」下的「`设置`」
3. 单击左侧「`全局游戏设置`」
4. 展开「`版本隔离`」，选择「`各实例独立`」

#### 图文步骤

<details>
<summary>点击展开</summary>
<img src="images/hmcl/1-step-1.png">
<img src="images/hmcl/1-step-2.png">
</details>

---

## 2. 什么是「版本文件夹」

在后续教程中会多次提到**版本文件夹**，不同启动器的打开方式略有区别

### 2.1 PCL

#### 文字步骤

1. 打开 PCL
2. 单击**左下方**区域的「`版本选择`」
3. 选择需要安装汉化的版本
4. 再单击**左下方**区域的「`版本设置`」
5. 在「`快捷方式`」中单击「`版本文件夹`」，系统打开的文件夹即为**版本文件夹**

#### 图文步骤

<details>
<summary>点击展开</summary>
<img src="images/pcl/2-step-1.png">
<img src="images/pcl/2-step-2.png">
<img src="images/pcl/2-step-3.png">
<img src="images/pcl/2-step-4.png">
</details>

### 2.2 Modrinth App

#### 文字步骤

1. 打开 Modrinth App
2. 单击左侧「`Library`」
3. 单击需要安装汉化的实例
4. 单击右侧「`More`」
5. 单击「`Open folder`」，系统打开的文件夹即为**版本文件夹**

#### 图文步骤

<details>
<summary>点击展开</summary>
<img src="images/modrinth/2-step-1.png">
<img src="images/modrinth/2-step-2.png">
</details>

### 2.3 HMCL

#### 文字步骤

1. 打开 HMCL
2. 单击左侧「`实例列表`」
3. 单击需要安装汉化的实例
4. 返回主界面
5. 单击左侧「`实例管理`」
6. 在**左下方**区域单击「`浏览`」，再单击「`实例运行文件夹`」，系统打开的文件夹即为**版本文件夹**

#### 图文步骤

<details>
<summary>点击展开</summary>
<img src="images/hmcl/2-step-1.png">
<img src="images/hmcl/2-step-2.png">
<img src="images/hmcl/2-step-3.png">
<img src="images/hmcl/2-step-4.png">
</details>

---

## 3. 地图 / 材质包 / Mod 文件夹

下面三个文件夹都位于**版本文件夹**内，如不存在请**手动创建**

### 3.1 地图文件夹

地图文件夹为版本文件夹中的 **`saves`** 文件夹

![](images/saves-folder.png)

### 3.2 材质包文件夹

材质包文件夹为版本文件夹中的 **`resourcepacks`** 文件夹

![](images/resourcepacks-folder.png)

### 3.3 Mod 文件夹

Mod 文件夹为版本文件夹中的 **`mods`** 文件夹

![](images/mods-folder.png)

---

# 二、地图与整合包的汉化思路

地图和整合包的汉化方式不同：

- **地图汉化**：通常是通过材质包汉化，也有少数直接修改地图本体
- **整合包汉化**：一般通过「汉化补丁 + I18nUpdateMod +（可能的额外 Mod）」实现

下面分别说明

---

# 三、地图汉化

地图汉化主要分为两步：

1. 安装地图
2. 安装（并应用）汉化用的材质包（如果有）

## 3.1 安装地图

一个文件夹中如果包含 `level.dat` 文件，那么这个文件夹就是一张地图

![](images/level-dat.png)

> [!WARNING]
> 请确认地图支持的游戏版本，一般会在下载页面写明。版本不兼容时，**非常容易**出现各种问题（如崩溃、卡住、方块报错等）

将**地图文件夹**放入**地图文件夹**（`saves`）中，即可在游戏的「单人游戏」里看到这张地图

![](images/copy-to-saves.png)
![](images/world-in-game.png)

## 3.2 安装材质包

高版本的材质包一般是一个压缩包，内部包含 `pack.mcmeta` 文件：

![](images/pack-mcmeta.png)

如果你下载的汉化内容里包含一个「材质包」，说明这张地图需要这个材质包才能实现完整汉化

> [!WARNING]
> **材质包通常不需要解压！**  
> 只有当你把材质包放入材质包文件夹后，游戏内不显示（多见于低版本）时，才需要尝试解压

将**材质包压缩包**放入**材质包文件夹**（`resourcepacks`），即可在游戏中「选项 → 资源包 → 可用」里看到

## 3.3 应用材质包

1. 进入游戏，打开「**选项 → 资源包**」
2. 在左侧「可用」列表中，将鼠标放在材质包图标上
3. 单击右箭头，将材质包移动到右侧的「已选」区域
4. 单击「完成」，游戏加载完毕后即应用成功

![](images/choose-resourcepacks.png)
![](images/apply-resourcepacks.png)

至此，**地图汉化**安装完成，可以进世界体验了

---

# 四、整合包汉化

整合包汉化一般会包含：

- 一个或多个汉化补丁压缩包
- [I18nUpdateMod](https://www.curseforge.com/minecraft/mc-mods/i18nupdatemod)
- 有些整合包还会要求安装额外的 Mod

下面以 [VM 汉化组](https://vmct-cn.top/) 的 [FTB StoneBlock 4](https://vmct-cn.top/modpacks/sb4) 为例

从 [VM 汉化组 - FTB StoneBlock 4 汉化](https://vmct-cn.top/modpacks/sb4) 下载后，可以看到类似下面的两个文件：

![](images/ftb-stoneblock-4-chinese-files.png)

## 4.1 安装汉化补丁

汉化补丁一般是压缩包，需要先解压

1. 解压汉化补丁压缩包
2. 打开解压后的文件夹，**全选里面的所有内容**
3. 将这些内容复制到对应整合包的**版本文件夹**中

![](images/copy-to-versions.png)

> [!NOTE]
> 这个步骤**通常会出现「是否覆盖」提示**，请选择**覆盖**  
> 如果没有同名文件需要覆盖，**很可能你复制错了位置**，建议重新确认

## 4.2 安装 I18nUpdateMod

安装完汉化补丁后，还需要安装 I18nUpdateMod：

1. 将下载好的 `I18nUpdateMod` 文件（`.jar`）复制或移动到该整合包的 **`mods` 文件夹** 中

![](images/install-i18n-mod.png)

部分整合包还会说明需要额外安装一些 Mod，按照同样方式放入 `mods` 文件夹即可

## 4.3 应用汉化材质包

很多整合包汉化还会附带一个或多个材质包，需要在游戏内启用：

1. 启动游戏，进入「**选项 → 资源包**」
2. 找到与汉化相关的材质包，将鼠标放在图标上，单击右箭头，将其移动到右侧「已选」区域
3. 单击「完成」，等待游戏加载

> [!NOTE]
> 如果你不确定哪个是汉化用材质包，可以把名字里带有「`中文`」或「`汉化`」的材质包都应用上

![](images/choose-resourcepacks-for-modpacks.png)
![](images/apply-resourcepacks-for-modpacks.png)

至此，**整合包汉化**就安装完成了，进入游戏享受吧