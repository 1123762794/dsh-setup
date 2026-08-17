# DSH Setup — 本机插件汇总

> 本机（Windows）DeepSeek Harness（`dsh`）正在使用与维护的插件清单。
> 记录每个插件的**名称 / 代码仓库 / 功能介绍 / 在本机的使用频率**。

## 更新约定（重要）

本仓库的维护遵循一条硬性规则：

> **任何更新（新增插件、修改描述、调整频率、删除条目）都必须先经过仓库所有者明确同意。**

- 更新提议以 Issue 或 Pull Request 形式提出，由所有者审批后才可合并/发布。
- 未经同意，不得直接推送变更。
- 本机实际启用的插件以 `~/.dsh/profiles/web/` 下 `package.json`（`dsh.profile.bundles`）与 `cordis.patch.yml` 为准；本清单是它的可读镜像。

## 插件总览

统计：共 **18** 项（官方核心 2 / 第三方插件 12 / 本地自研运行中 3 / 本机自研工程 2）。

### 官方核心（随 dsh 发行，每个 profile 必备）

| 插件名 | 仓库 | 介绍 | 本机使用频率 |
| --- | --- | --- | --- |
| `@deepseek-ai/dsh-base` | [deepseek-harness](https://github.com/deepseek-ai/deepseek-harness) | 共享 dsh 核心：作为每个 profile 的第一层 patch，在空 profile 根上插入基础插件行 | 每回合（核心运行时） |
| `@deepseek-ai/dsh-web-app` | [deepseek-harness](https://github.com/deepseek-ai/deepseek-harness) | dsh 浏览器面 bundle：dsh-base 之上的 web patch 层 + 运行时胶水插件（前端 dist 服务、web 面 prompt、bash 运行时变量、URL 行） | 每次打开 Web 界面（核心运行时） |

### 第三方插件（从社区/市场安装）

| 插件名 | 仓库 | 介绍 | 本机使用频率 |
| --- | --- | --- | --- |
| `dshmarket` | [dsh-market/dsh-market](https://github.com/dsh-market/dsh-market)（803★） | DSH 可视化插件市场：浏览、搜索、一键安装社区插件 | 按需（装插件时） |
| `@deepseek-ai/dsh-plugin-console` | [Noob-stupid/dsh-plugin-hub](https://github.com/Noob-stupid/dsh-plugin-hub)（37★） | 插件控制台：一键启用/停用插件，浏览并安装 GitHub dsh-plugin | 按需（管理插件时） |
| `dsh-context` | [bowenliang123/dsh-context](https://github.com/bowenliang123/dsh-context)（180★） | 上下文洞察面板：查看模型上下文窗口构成与演化（组成、历史、压缩、注入、模型切换） | 常用（观察上下文时） |
| `@omdsh-dev/dsh-genui` | [omdsh-dev/dsh-genui](https://github.com/omdsh-dev/dsh-genui)（180★） | GenUI：在助手回复内联渲染交互式 UI 组件（布局/图表/表单/测验/mermaid/3D/动作事件循环） | 高频（结构化回复自动触发） |
| `@dsh-external/dsh-visualize` | [Nagi-ovo/dsh-visualize](https://github.com/Nagi-ovo/dsh-visualize)（164★） | 内联可视化：visualize 工具让模型把交互式 HTML 渲染为沙箱卡片 | 常用（可视化展示时） |
| `dsh-better-sidebar` | [omdsh-dev/DSH-better-sidebar](https://github.com/omdsh-dev/DSH-better-sidebar)（1920★） | VSCode 风格右侧边栏（资源管理器/编辑器/终端/git/浏览器），暴露服务供其他插件注册标签 | 每次打开 Web 界面 |
| `@anionex/dsh-vision-toolkit` | [Anionex/dsh-vision-toolkit](https://github.com/Anionex/dsh-vision-toolkit)（609★） | agent-vision-toolkit 的 DSH 原生集成：图像问答、OCR、接地、UI 还原、像素对比、Artifacts | 按需（视觉任务时） |
| `@xmanrui/dsh-im` | [xmanrui/dsh-im](https://github.com/xmanrui/dsh-im)（33★） | 扫码/机器人凭据把 IM 机器人接入 DSH（飞书/微信/钉钉/企微/QQ/Telegram/Discord） | 底层（供各渠道接入） |
| `dsh-lark-channel` | [omdsh-dev/dsh-lark](https://github.com/omdsh-dev/dsh-lark)（30★） | 飞书 IM 机器人渠道：对话驱动 agent，回复与审批以消息/卡片返回 | 高频（当前会话即经此渠道） |
| `@liustack/modlens` | [liustack/modlens](https://github.com/liustack/modlens)（2743★） | 面向文本 LLM 的即插即用视觉桥：免费 Antigravity CLI 提供图像理解/OCR | 按需（读图/OCR 时） |
| `lan-gate` | [hchao3335-maker/dsh-lan-gate](https://github.com/hchao3335-maker/dsh-lan-gate)（11★） | 内网访问网关（第三方开源）：`0.0.0.0:3088 → 127.0.0.1:3080`，本机审批、设备令牌、限流、手机适配，单文件零依赖（本机有镜像 `1123762794/dsh-lan-gate`） | 常驻（移动端远程访问） |

### 本地自研（本机开发、正在运行）

| 插件名 | 仓库 | 介绍 | 本机使用频率 |
| --- | --- | --- | --- |
| `dsh-memory-evolve` | [csyangwen/dsh-memory-evolve](https://github.com/csyangwen/dsh-memory-evolve)（149★） | 五轨分层记忆（用户/全局/项目关键记忆/项目日志/每日日志，git 分支感知）+ 自我进化（技能自动创建+回合内审查）+ 技能/待办管理 + 无限画板 + COI 调度 + 会话广播 + 提示词管理器 + 记忆同步 + 书签/分支 + 本地搜索 + 临时便签，带 WebUI（记忆/技能/待办/设置 Tab）。发布账号 csyangwen，本地 link 开发 | 每回合（记忆持续写入） |
| `dsh-web-restart` | [1123762794/dsh-web-restart](https://github.com/1123762794/dsh-web-restart) | DSH Web 一键重启按钮：侧边栏底部单击即重启 dsh web 进程 | 常用（Web 需重启时） |
| `dsh-opencode-quota` | [1123762794/dsh-opencode-quota](https://github.com/1123762794/dsh-opencode-quota) | 输入框下方显示 OpenCode Go 订阅额度（5小时/周/月已用百分比） | 每次打开 Web 界面 |

### 本机自研工程（已在 D 盘、未在 web profile 运行）

| 插件名 | 仓库 | 介绍 | 本机使用频率 |
| --- | --- | --- | --- |
| `dsh-desktop` | [1123762794/dsh-desktop](https://github.com/1123762794/dsh-desktop) | DeepSeek Harness 极简桌面客户端：一键拉起 dsh web 并打开原生窗口（Electron） | 未在 web profile 运行 |
| `dsh-inline-images` | [3403473060/dsh-inline-images](https://github.com/3403473060/dsh-inline-images)（2★） | 对话内联图片：LLM 回复输出的本地图片路径直接渲染为图片（9 种格式、灯箱、可调尺寸） | 已安装（node_modules 中） |

## 数据文件

机器可读清单见 [`plugins.json`](./plugins.json)（与上方表格同源）。

## 生成方式

本清单由 DSH Agent 从本机 web profile 配置（`package.json` 的 `dsh.profile.bundles` + `cordis.patch.yml`）及本机 `D:/1` 自研工程扫描生成。保持更新需经所有者同意（见上）。