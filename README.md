# Awesome DSH Plugins

[![Awesome](https://awesome.re/badge-flat2.svg)](https://awesome.re)
[![Topic](https://img.shields.io/badge/topic-dsh--plugin-4D6BFE)](https://github.com/topics/dsh-plugin)
[![Curated](https://img.shields.io/badge/curated-50-16a34a)](#精选插件)
[![License: MIT](https://img.shields.io/badge/license-MIT-f59e0b)](LICENSE)

**中文** · [English](README.en.md)

> 精选 50 个 [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness) 插件。
> 我们通读了 GitHub [`dsh-plugin`](https://github.com/topics/dsh-plugin) 主题下的全部公开仓库，只留下真正值得装的那一批。

DeepSeek Harness（`dsh`）的设计是 **Everything is a Plugin**：模型、工具、沙箱、会话、调度、UI 都可以替换。社区仓库很多，这份列表不做全量索引，只回答一件事：**如果只装 50 个，装哪几个？**

## 目录

- [快速开始](#快速开始)
- [挑选标准](#挑选标准)
- [精选插件](#精选插件)
  - [视觉与多模态](#视觉与多模态)
  - [Web UI 与创作](#web-ui-与创作)
  - [终端、桌面与发行版](#终端桌面与发行版)
  - [Agent 编排、记忆与工作流](#agent-编排记忆与工作流)
  - [浏览器与电脑控制](#浏览器与电脑控制)
  - [搜索、内容与数据](#搜索内容与数据)
  - [生态基建与开发](#生态基建与开发)
  - [集成与迁移](#集成与迁移)
  - [皮肤与分享](#皮肤与分享)
- [安全提示](#安全提示)
- [欢迎补充](#欢迎补充)

## 快速开始

先安装官方运行时：

```sh
npx @deepseek-ai/dsh web
```

再按各仓库说明安装插件。当前主流方式是把声明了 `dsh.bundle` 的包挂到 `web` profile：

```sh
dsh plugin --profile web add "github:owner/repo"
```

装完后重启 `dsh --profile web` 并刷新页面。没有 `dsh.bundle` 声明的包可能只作为普通依赖安装，不会激活任何层。

## 挑选标准

我们逐条阅读了主题下的仓库描述，并对高区分度候选精读了 README、安装方式和能力边界。入选需要同时满足：

1. **真的给 DSH 加能力**——可安装的 bundle / 发行版，而不是只贴了 `dsh-plugin` 标签的独立产品。
2. **解决明确痛点**——视觉、侧栏、TUI、记忆、浏览器、搜索、迁移等。
3. **文档完整、仍在维护**——能看懂装什么、解决什么、边界在哪。
4. **同类只留代表作**——同一能力有多个实现时，优先选 DSH 原生、文档更好的那一个。

## 精选插件
- [dhicoc/dsh-reverse-skill](https://github.com/dhicoc/dsh-reverse-skill) — 完整 reverse-skill（85 个 SKILL.md）的 DeepSeek Harness 插件：逆向工程、授权渗透测试与安全研究的技能路由包。
- [dhicoc/dsh-reverse-skill](https://github.com/dhicoc/dsh-reverse-skill) - Complete reverse-skill pack (85 SKILL.md) as a DeepSeek Harness Cordis plugin: reverse engineering, authorized pentesting and security-research skill router.

### 视觉与多模态

DeepSeek 文本模型本身不能看图。下面两个插件把「看」做成可调用的工具，而不是换一个多模态模型。

- [modlens](https://github.com/liustack/modlens) — **DSH 第一个视觉插件**。图片直接粘贴进对话即可阅读：OCR、阅读顺序版面、实体与关系，输出可引用的结构化证据。也可复用本机 Claude Code / Codex / OpenCode / Pi 已有的视觉通道。
- [dsh-vision-toolkit](https://github.com/Anionex/dsh-vision-toolkit) — 把上游 agent-vision-toolkit 做成 DSH 原生 Profile Bundle。带意图的看图问答、长截图 OCR、UI 还原、像素级定位与对比、可预览 Artifacts；十个独立工具按需暴露，避免把整套视觉 schema 一次性塞进上下文。

### Web UI 与创作

- [dsh-web-ui](https://github.com/zhu1090093659/dsh-web-ui) — 目前最完整的 Web UI 插件与皮肤集合：任务看板（含 cron）、Git 图谱、右侧文件/预览/SCM、移动端扫码遥控、SSH 远程运维、鲸鱼娘宠物、实时 TPS / token 统计。可单独装，也可一次装齐。
- [DSH-better-sidebar](https://github.com/omdsh-dev/DSH-better-sidebar) — 一个插件变成完整工作台：资源管理器、CodeMirror 编辑、Office/PDF/HTML 预览、沙箱内嵌浏览器、真实终端、Git 面板、后台任务树。第三方插件可通过 `ctx.betterSidebar` 注册新 Tab。
- [dsh-visualize](https://github.com/Nagi-ovo/dsh-visualize) — 对话内生成式 UI：模型把交互式 HTML 卡片画进会话流，带沙箱渲染、流式预览和鲸鱼蓝主题跟随。
- [dsh-genui](https://github.com/omdsh-dev/dsh-genui) — 用 `dsh-ui` fence 在回复里渲染布局、图表、表单、测验、Mermaid、3D 场景，用户操作再回传给模型。
- [dsh-at-file](https://github.com/omdsh-dev/dsh-at-file) — Codex 风格的 `@file`：在输入框搜索工作区文件，把内容附到提示词上。
- [dsh-annotation](https://github.com/omdsh-dev/dsh-annotation) — 选中文字 → 批注 → 回车随消息发送；回复按 Annotation 逐条对照，适合审稿和精确反馈。
- [dsh-openpencil](https://github.com/ZSeven-W/dsh-openpencil) — 让 Agent 操作真实 OpenPencil 设计画布：预览、检查、编辑多页 `.op` 文档，而不是只吐一张效果图。
- [dsh-web-review](https://github.com/CanglongCl/dsh-web-review) — 内置浏览器里点选页面元素、写修改意见、临时改颜色字号间距；确认后 Agent 按批注改工作区源码。

### 终端、桌面与发行版

官方目前以 Web UI 为主。下面几项补上终端党和「双击即用」的缺口。

- [dsh-TUI](https://github.com/ccch1mneyyy/dsh-TUI) — Claude Code 风格全屏终端：像素鲸鱼顶栏、实时工作状态行、思考流式展开、双击 Esc 回滚、上下文进度条与 TPS 仪表。已被官方公众号作为内测精选插件介绍。
- [dsh-tianshu-tui](https://github.com/huiliyi37/dsh-tianshu-tui) — 另一套交互式终端 UI，渲染层来自天枢 TUI；额外做了 TDD 工作流、证据门、视觉桥接和代码智能检索等 harness 层改造。
- [oh-dsh](https://github.com/hust-open-atom-club/oh-dsh) — 华科开源俱乐部的社区发行版：把固定版本 DSH runtime、Node、Electron 和本地能力打成可安装桌面工作台，TUI / 桌面 / Web 三种形态统一体验。
- [dsh-launcher](https://github.com/Ruler4396/dsh-launcher) — Windows 轻量启动器：MSI 或便携包、开机自启、独立 WebView2 小窗口，自动用 `npx` 拉起官方服务，不用先敲命令。

### Agent 编排、记忆与工作流

- [dsh-agent-teams](https://github.com/NanmiCoder/dsh-agent-teams) — 把 Claude Code AgentTeams 语义搬进 DSH：一句话拉起队长 + 可续聊成员、任务依赖、成员间直达邮箱；Web 右上角有团队活动面板。
- [dsh_workflow](https://github.com/icetomoyo/dsh_workflow) — 把一次性多 Agent 调度升级成可生成、可保存、可治理、可观察、可恢复的 Workflow 层（对标 KodaX）。原生 `workflow` 工具负责「这一次并行跑完」；它负责流程资产本身。
- [dsh-memory-evolve](https://github.com/csyangwen/dsh-memory-evolve) — 跨会话五轨长期记忆、git 分支感知、技能自我进化、四轨待办、COI 调度、会话广播。默认大量能力关闭，避免撑爆工具清单。
- [dsh-mnemon](https://github.com/omdsh-dev/dsh-mnemon) — Mnemon 与 DSH 的深度集成：运行时热记忆、可阅读的项目档案、按需召回的长期记忆体，三层都受监督、可检索。
- [dsh-sidechain](https://github.com/Buyi-wsgzg/dsh-sidechain) — `/side` 持续性侧会话（Codex 风格）与 `/btw` 一次性侧问（Claude 风格），在临时 fork 里跑，不写入主会话历史。
- [dsh-turn-rewind](https://github.com/Anionex/dsh-turn-rewind) — 以消息为锚点回退对话和工程文件。底层 Change Ledger 先做恢复点，再预览路径级漂移，最后在对话框里确认全量或选择性还原。
- [allinluna](https://github.com/zenx0x/allinluna) — 资源感知的多 Agent 编排：一个大目标拆成可并行的顶层任务，任务内再递归调用子代理 / 工具 / MCP，避免整仓塞进同一段对话。
- [distill](https://github.com/LoserFox/distill) — 后台 subagent 反省当前对话，自动 create / update 技能，把一次性经验沉淀成可复用能力。
- [dsh-automation](https://github.com/titanwings/dsh-automation) — 定时或一次性编码任务在**全新 Agent Session** 里跑，带明确工作区与权限边界；Web 或 Agent 都可管理，历史可审计。
- [dsh-deep-research](https://github.com/omdsh-dev/dsh-deep-research) — 基于官方 workflow 引擎的自适应深研：先定义答案空间和验收标准，再按边际信息增益决定要不要继续搜，可选对抗性审查压幻觉。
- [dsh-sentinel](https://github.com/fuhefei/dsh-sentinel) — 条件唤醒：监视文件 / 命令 / HTTP / 进程 / Webhook，条件成立就叫醒休眠会话。订阅能活过进程重启，输入框上方有值班面板。
- [dsh-message-edit](https://github.com/Moeblack/dsh-message-edit) — 基于事件日志的消息编辑、reroll、retry 和版本时间线，改一句旧提示不必整段重来。

### 浏览器与电脑控制

- [dsh-browser](https://github.com/Lum1104/dsh-browser) — Chrome 侧栏扩展，让 DSH 操作你**已经打开、已经登录**的标签页。页面变成带编号的结构化文本，模型按编号点击 / 填表 / 滚动；截图不进模型上下文。
- [browser-bridge](https://github.com/hanelalo/browser-bridge) — 浏览器扩展当「手」、本地 WebSocket 当枢纽，不依赖 CDP。可用 Rust CLI 或 MCP 把真实窗口交给 Agent。
- [dsh-computer-use](https://github.com/Anionex/dsh-computer-use) — macOS Accessibility 优先的电脑控制：新鲜观测、过期状态拒绝、按应用授权。默认不抢系统光标，键盘输入前才必要时把目标窗口前置。
- [dsh-record-replay](https://github.com/humblebanana/dsh-record-replay) — 把本机演示过的 macOS 工作流录下来，校验证据后打成 Agent 可复用的 skill（`orr_*` 工具）。

### 搜索、内容与数据

- [modsearch](https://github.com/liustack/modsearch) — DSH 的网页插件：问 Web 或 X，拿回结构化结果；和 ModLens 同一作者，补的是「读网」而不是「读图」。
- [argo](https://github.com/taxueseek/argo) — 专门给 Agent 用的多语言搜索与证据核验，覆盖中英、学术、代码、购物、金融、新闻、百科，强调可引用而不是一段摘要。
- [dsh-openbiliclaw](https://github.com/whiteguo233/dsh-openbiliclaw) — OpenBiliClaw 的 DSH 客户端：右侧第四栏做推荐 / 内容库 / 画像，并注册 22 个工具，让 Agent 边干活边从 B 站、小红书、抖音、YouTube、X、知乎等平台找内容。
- [dsh-data-agent](https://github.com/omdsh-dev/dsh-data-agent) — 专用 Data Agent 预设：连上 MySQL / PostgreSQL / SQLite / Oracle / Hive / Impala，用 `sqlcmd` 进入「写 SQL → 看结果 → 改 SQL」的闭环；密码只留内存。
- [dsh-plugin-mineru](https://github.com/HuanLinOTO/dsh-plugin-mineru) — 向模型暴露 MinerU：PDF / 图片 / DOCX / PPTX / XLSX 转结构化 Markdown 或 JSON。

### 生态基建与开发

- [plugin-registry](https://github.com/vlln/plugin-registry) — 薄控制台：在浏览器里看 profile 的 bundle 层栈、insert 行和启停；附带 `make-dsh-plugin` 引导，按官方格式写插件。
- [dsh-find-plugins](https://github.com/Nagi-ovo/dsh-find-plugins) — 直接问 DSH「有没有做 X 的插件」：搜索 `dsh-plugin` 主题、解释匹配项、等你点头后再安装并验收。
- [dsh-plugin-check](https://github.com/omdsh-dev/dsh-plugin-check) — 只读体检：清单协议、patch 格式、构建陷阱（cordis 双副本、tsconfig、产物残留 `.ts`）、hub 收录状态，给报告不改仓库。
- [dsh-toolkit](https://github.com/omdsh-dev/dsh-toolkit) — 十个零依赖确定性工具一次装齐：time / encoding / json / calculator / csv / regex / markdown / diff / stat / schema，子包也可单独启用。
- [dsh-custom-tool](https://github.com/omdsh-dev/dsh-custom-tool) — 在 Monaco 编辑器里写沙箱 JavaScript 工具，由模型驱动工具的创建、更新和生命周期。
- [dsh-security-audit](https://github.com/omdsh-dev/dsh-security-audit) — 本机只读安全审计：配置、凭据元数据、插件来源、路径权限、会话文件、网络暴露面。脱敏报告，不自动修复，不把「没读到」当成「安全」。
- [dsh-handbook](https://github.com/Electricitysheep/dsh-handbook) — 从 0 到 1 的中英白皮书：安装、插件开发、性能调优、实测案例、同模型多 Agent 对比；有[在线版](https://electricitysheep.github.io/dsh-handbook/)和 PDF。

### 集成与迁移

- [dsh-open-in-vscode](https://github.com/omdsh-dev/dsh-open-in-vscode) — Web GUI 里一键用 VS Code 打开当前工作区目录。
- [dsh-notification](https://github.com/omdsh-dev/dsh-notification) — 回合完成桌面通知：按成功 / 失败 / 等待等结果分别开关，并可用关键词包含或排除。
- [dsh-interconnect](https://github.com/Chinesezjc/dsh-interconnect) — 跨 DSH 实例的消息与事件交接：一台机器上的会话可以把上下文递给另一台。
- [dsh-chat-import](https://github.com/Nwflower/dsh-chat-import) — 13 源全保真导入（Claude Code/Codex/ChatGPT/Cursor/Gemini/Reasonix/opencode/ZCode/Grok Build/OpenClaw/Pi/Hermes/Kimi）历史会话为可续聊 DSH 会话，并支持反向导出/同步回 Claude Code。
- [dsh-worktree](https://github.com/FlashingChen/dsh-worktree) — Codex 风格的永久 git worktree：一次创建、跨会话复用，主工作区不被打乱；提供 `worktree_create/list/remove` 和 `/worktree` 命令。

### 皮肤与分享

- [dsh-deep-whale](https://github.com/Small-tailqwq/dsh-deep-whale) — 社区里完成度最高的鲸鱼娘皮肤系列（深海女仆工坊）。亮暗双主题，CC BY-NC-SA 4.0。
- [whale-girl](https://github.com/vlln/whale-girl) — DSH Web GUI 桌面宠物（QQ 宠物形态）：右下角可拖拽、投喂、玩耍，按任务和陪伴时长积累等级。
- [dsh-share](https://github.com/hellodigua/dsh-share) — 把一轮问答导出成 PNG：保留 Markdown、代码块、表格和工具摘要，可隐藏思考过程，复制到剪贴板或下载。

## 安全提示

第三方插件可能读取 API Key、会话日志、工作区文件，或在本机开端口。建议：

1. 优先选声明了 `dsh.bundle`、README 写清权限边界的仓库。
2. 先看最近提交和 `cordis.patch.yml` / 工具列表，再决定装不装。
3. 用 [dsh-plugin-check](https://github.com/omdsh-dev/dsh-plugin-check) 和 [dsh-security-audit](https://github.com/omdsh-dev/dsh-security-audit) 做结构与暴露面检查。
4. 本列表只做发现与整理，**不是** DeepSeek 官方背书，也不保证兼容当前 rc。

## 欢迎补充

发现更值得收录的插件、描述过时或分类不准，请开 Issue 或 Pull Request。请说明：它解决什么问题、为什么比现有条目更有代表性、如何安装。

## License

本列表采用 [MIT License](LICENSE)。被收录项目遵循各自的许可证。