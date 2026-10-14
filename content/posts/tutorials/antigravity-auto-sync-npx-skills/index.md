---
title: "让 Antigravity 自动识别全局 Skills：配置 skills.json 实现 npx skills 自动同步"
date: 2026-10-14T12:37:00+08:00
cover: cover.png
categories:
  - 教程
tags:
  - Antigravity
  - AI
  - Skills
---

解决用 npx skills 安装全局技能后 Antigravity 无法识别的问题，通过添加 skills.json 配置文件实现自动同步，无需手动重复添加

<!--more-->

_封面使用 GPT Image 2.5 生成_

## 问题背景

使用 `npx skills` 安装 Agent 技能时，例如添加中文润色技能 `humanizer-zh`：

```bash
npx skills add op7418/Humanizer-zh
```

工具默认会将技能存放在用户目录下的 `~/.agents/skills/` 中

但打开 Google Antigravity 后，它默认识别不到这些技能，输入 `/<skill-name>` 也没有任何提示，如果想用，通常得手动在 Antigravity 目录下再拷一份，后续更新了技能又得重新同步

## 为什么默认读不到？

根本原因在于两者约定的全局目录不同：

- **`npx skills`**：默认将用户主目录下的 `~/.agents/skills` 作为全局存放位置
- **Antigravity**：自身的全局配置目录是 `~/.gemini/config/`，而把 `.agents/skills` 当作项目工作区级别的目录，只有打开具体代码工程时才会去读取

因此，存放在用户主目录下的技能不会被 Antigravity 自动识别

## 解决方法：添加 skills.json

不需要手动复制文件，Antigravity 原生支持在全局配置中通过 `skills.json` 挂载外部目录

在 Antigravity 全局配置目录下新建或编辑 `skills.json`：

- **Windows**：`C:\Users\<你的用户名>\.gemini\config\skills.json`
- **macOS / Linux**：`~/.gemini/config/skills.json`

写入以下配置：

```json
{
  "entries": [
    {
      "path": "~/.agents/skills"
    }
  ]
}
```

保存后，Antigravity 启动时就会自动扫描 `~/.agents/skills` 下的所有子目录，并把它们注册为全局技能

后续无论是用 `npx skills add` 安装新技能，还是更新现有技能，Antigravity 都能自动同步识别

## 验证生效

1. **重启客户端**：Antigravity 的技能索引在服务启动时加载，配置完成后完全退出并重启一次客户端
2. **测试调用**：在聊天输入框中输入斜杠 `/`，即可看到刚安装的技能出现在快捷指令列表中（如 `/humanizer-zh`），直接选中即可调用
