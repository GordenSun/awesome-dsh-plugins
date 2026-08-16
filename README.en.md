# Awesome DSH Plugins

[![Awesome](https://awesome.re/badge-flat2.svg)](https://awesome.re)
[![Topic](https://img.shields.io/badge/topic-dsh--plugin-4D6BFE)](https://github.com/topics/dsh-plugin)
[![Curated](https://img.shields.io/badge/curated-50-16a34a)](#curated-plugins)
[![License: MIT](https://img.shields.io/badge/license-MIT-f59e0b)](LICENSE)

[中文](README.md) · **English**

> Fifty curated [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness) plugins.
> We read every public repository under the GitHub [`dsh-plugin`](https://github.com/topics/dsh-plugin) topic and kept only the ones worth installing.

DeepSeek Harness (`dsh`) is built on **Everything is a Plugin**: models, tools, sandboxes, sessions, scheduling, and UI are all swappable. This list is not a full index. It answers one question: **if you only install fifty, which fifty?**

## Contents

- [Quick start](#quick-start)
- [Selection criteria](#selection-criteria)
- [Curated plugins](#curated-plugins)
  - [Vision and multimodal](#vision-and-multimodal)
  - [Web UI and creation](#web-ui-and-creation)
  - [Terminal, desktop, and distros](#terminal-desktop-and-distros)
  - [Orchestration, memory, and workflow](#orchestration-memory-and-workflow)
  - [Browser and computer use](#browser-and-computer-use)
  - [Search, content, and data](#search-content-and-data)
  - [Ecosystem infrastructure](#ecosystem-infrastructure)
  - [Integrations and migration](#integrations-and-migration)
  - [Skins and sharing](#skins-and-sharing)
- [Safety](#safety)
- [Contributing](#contributing)

## Quick start

Install the official runtime:

```sh
npx @deepseek-ai/dsh web
```

Then follow each repo's install notes. The usual path is to mount a package that declares `dsh.bundle` on the `web` profile:

```sh
dsh plugin --profile web add "github:owner/repo"
```

Restart `dsh --profile web` and refresh the page. Packages without a `dsh.bundle` declaration may install as plain dependencies and never become an active layer.

## Selection criteria

We read every topic description, then closely read READMEs, install paths, and capability boundaries for high-differentiation candidates. A repo had to:

1. **Actually extend DSH** — an installable bundle or distro, not an independent product that only added the topic tag.
2. **Fix a real gap** — vision, sidebar, TUI, memory, browser, search, migration.
3. **Ship usable docs and still be maintained** — what it installs, what it solves, and where it stops.
4. **Keep one representative per niche** — when several repos do the same job, we kept the DSH-native, better-documented one.

## Curated plugins

### Vision and multimodal

DeepSeek text models cannot see. These two plugins turn “looking” into callable tools instead of swapping in a multimodal model.

- [modlens](https://github.com/liustack/modlens) — **The first vision plugin for DSH.** Paste an image into chat: OCR, reading-order layout, entities and relations, quoted structured evidence. Can reuse vision channels you already have in Claude Code, Codex, OpenCode, or Pi.
- [dsh-vision-toolkit](https://github.com/Anionex/dsh-vision-toolkit) — The DSH-native Profile Bundle for upstream agent-vision-toolkit. Intent-aware VQA, long-screenshot OCR, UI restoration, pixel grounding and diffs, previewable Artifacts. Ten tools are disclosed only when the task needs them.

### Web UI and creation

- [dsh-web-ui](https://github.com/zhu1090093659/dsh-web-ui) — The most complete Web UI plugin and skin collection: cron task board, git graph, right-side files/preview/SCM, QR mobile remote, SSH ops, whale pet, live TPS and token stats. Install pieces or the whole suite.
- [DSH-better-sidebar](https://github.com/omdsh-dev/DSH-better-sidebar) — One plugin, a full workbench: file tree, CodeMirror, Office/PDF/HTML preview, sandboxed embedded browser, real terminal, git panel, background task tree. Other plugins can register tabs via `ctx.betterSidebar`.
- [dsh-visualize](https://github.com/Nagi-ovo/dsh-visualize) — In-conversation generative UI: the model paints interactive HTML cards into the stream, with sandbox rendering, streaming preview, and the whale-blue theme.
- [dsh-genui](https://github.com/omdsh-dev/dsh-genui) — Render layouts, charts, forms, quizzes, Mermaid, and 3D scenes from a `dsh-ui` fence; user actions loop back to the model.
- [dsh-at-file](https://github.com/omdsh-dev/dsh-at-file) — Codex-style `@file` mentions: search the workspace in the composer and attach file contents to the prompt.
- [dsh-annotation](https://github.com/omdsh-dev/dsh-annotation) — Select text → annotate → send with the message. Replies map back to each annotation — useful for review and precise feedback.
- [dsh-openpencil](https://github.com/ZSeven-W/dsh-openpencil) — Let the agent operate a real OpenPencil canvas: preview, inspect, and edit multi-page `.op` documents instead of returning a single mock image.
- [dsh-web-review](https://github.com/CanglongCl/dsh-web-review) — Pick elements in the built-in browser, write notes, tweak color/type/spacing, then have the agent patch workspace source from those annotations.
- [bowenliang123/dsh-context](https://github.com/bowenliang123/dsh-context) - Context insight panel: see what the model's context window is made of and how it evolves — composition vs. window size, per-request history, compression/injection events, and per-message token stats.

### Terminal, desktop, and distros

The official surface is still mostly Web UI. These fill the terminal-native and “double-click to run” gaps.

- [dsh-TUI](https://github.com/ccch1mneyyy/dsh-TUI) — Claude Code-style fullscreen terminal: pixel-whale header, live working line, streaming thoughts, double-Esc rewind, context bar and TPS gauge. Featured by the official DeepSeek Harness WeChat account.
- [dsh-tianshu-tui](https://github.com/huiliyi37/dsh-tianshu-tui) — Another interactive TUI, rendered from Tianshu TUI, plus harness-level extras: TDD workflow, evidence gates, a vision bridge, and code-aware retrieval.
- [oh-dsh](https://github.com/hust-open-atom-club/oh-dsh) — Community distro from HUST Open Atom Club: a pinned DSH runtime, Node, Electron, and local capabilities in one installable desktop workbench (TUI / desktop / Web).
- [dsh-launcher](https://github.com/Ruler4396/dsh-launcher) — Lightweight Windows launcher: MSI or portable zip, logon autostart, a small WebView2 window, and `npx` to start the official server — no CLI required.

### Orchestration, memory, and workflow

- [dsh-agent-teams](https://github.com/NanmiCoder/dsh-agent-teams) — Claude Code AgentTeams semantics on DSH: one sentence spins up a captain plus resumable members, task dependencies, and direct member mailboxes, with a live team panel in the Web GUI.
- [dsh_workflow](https://github.com/icetomoyo/dsh_workflow) — Turns one-shot multi-agent dispatch into a generatable, savable, governable, observable, resumable workflow layer (KodaX-inspired). Built-in `workflow` still means “run this in parallel once”; this plugin owns the process asset.
- [dsh-memory-evolve](https://github.com/csyangwen/dsh-memory-evolve) — Five-track long-term memory, git-branch awareness, skill self-evolution, four-track todos, COI scheduling, session broadcast. Most capabilities stay off by default so the tool list does not explode.
- [dsh-mnemon](https://github.com/omdsh-dev/dsh-mnemon) — Deep Mnemon integration: supervised, searchable runtime memory, readable project documents, and on-demand long-term memory spaces.
- [dsh-sidechain](https://github.com/Buyi-wsgzg/dsh-sidechain) — `/side` persistent side sessions (Codex-style) and `/btw` one-shot side questions (Claude-style), run in a temporary fork without writing to the main history.
- [dsh-turn-rewind](https://github.com/Anionex/dsh-turn-rewind) — Message-anchored rewind for conversation and project files. Change Ledger creates a restore point, previews path-level drift, then confirms a full or selective restore.
- [allinluna](https://github.com/zenx0x/allinluna) — Resource-aware multi-agent orchestration: one large goal becomes parallel top-level tasks; each task can recurse into subagents, tools, or MCP instead of stuffing the whole repo into one chat.
- [distill](https://github.com/LoserFox/distill) — A background subagent reflects on the conversation and creates or updates skills, turning one-off experience into reusable capability.
- [dsh-automation](https://github.com/titanwings/dsh-automation) — Recurring or one-shot coding jobs in a **fresh Agent session**, with an explicit workspace and permission boundary. Manage from Web or the agent; history is auditable.
- [dsh-deep-research](https://github.com/omdsh-dev/dsh-deep-research) — Adaptive deep research on the official workflow engine: define the answer space and acceptance criteria first, stop when expected information gain hits zero, optionally run an adversarial review against hallucinations.
- [dsh-sentinel](https://github.com/fuhefei/dsh-sentinel) — Condition-driven wakeup: watch files, commands, HTTP, processes, or webhooks and resume a dormant session when they fire. Subscriptions survive process restarts; a dock card shows what is on duty.
- [dsh-message-edit](https://github.com/Moeblack/dsh-message-edit) — Event-log message editing, reroll, retry, and a version timeline — change an old prompt without replaying the whole thread.

### Browser and computer use

- [dsh-browser](https://github.com/Lum1104/dsh-browser) — A Chrome sidebar extension so DSH can drive the tab you already have open and signed in. Pages become numbered structured text; the model clicks, types, and scrolls by index. Screenshots never enter the model context.
- [browser-bridge](https://github.com/hanelalo/browser-bridge) — Browser extension as the “hands,” local WebSocket hub, no CDP required. Drive a real window from a Rust CLI or MCP.
- [dsh-computer-use](https://github.com/Anionex/dsh-computer-use) — Accessibility-first macOS computer use: fresh observations, stale-state rejection, per-app grants. The default route does not warp the system cursor; the target window is raised only when typing needs it.
- [dsh-record-replay](https://github.com/humblebanana/dsh-record-replay) — Record a demonstrated macOS workflow, validate the evidence, and package it as a reusable agent skill (`orr_*` tools).

### Search, content, and data

- [modsearch](https://github.com/liustack/modsearch) — The web plugin for DSH: ask the web or X and get structured results. Same author as ModLens; this one reads the network, not images.
- [argo](https://github.com/taxueseek/argo) — Agent-first multilingual search and evidence checking across Chinese/English, academic, code, shopping, finance, news, and encyclopedias — citations over blurbs.
- [dsh-openbiliclaw](https://github.com/whiteguo233/dsh-openbiliclaw) — DSH client for OpenBiliClaw: a fourth pane for recommendations, library, and profile, plus 22 tools so the agent can pull personalized content from Bilibili, Xiaohongshu, Douyin, YouTube, X, Zhihu, and more while you work.
- [dsh-data-agent](https://github.com/omdsh-dev/dsh-data-agent) — A dedicated Data Agent preset: connect MySQL / PostgreSQL / SQLite / Oracle / Hive / Impala and close the loop with `sqlcmd` (write SQL → see results → fix SQL). Passwords stay in memory.
- [dsh-plugin-mineru](https://github.com/HuanLinOTO/dsh-plugin-mineru) — Exposes MinerU so the model can turn PDF, images, DOCX, PPTX, and XLSX into structured Markdown or JSON.

### Ecosystem infrastructure

- [plugin-registry](https://github.com/vlln/plugin-registry) — A thin console for the profile bundle stack, insert rows, and enable/disable, plus a `make-dsh-plugin` guide for the official format.
- [dsh-find-plugins](https://github.com/Nagi-ovo/dsh-find-plugins) — Ask DSH “is there a plugin for X?” It searches the `dsh-plugin` topic, explains matches, waits for your pick, then installs and verifies.
- [dsh-plugin-check](https://github.com/omdsh-dev/dsh-plugin-check) — Read-only health check: manifest protocol, patch shape, build traps (duplicate cordis, tsconfig, leftover `.ts` in artifacts), hub listing status. Reports only; never mutates the repo.
- [dsh-toolkit](https://github.com/omdsh-dev/dsh-toolkit) — Ten zero-dependency deterministic tools in one install: time, encoding, json, calculator, csv, regex, markdown, diff, stat, schema. Subpackages can be enabled on their own.
- [dsh-custom-tool](https://github.com/omdsh-dev/dsh-custom-tool) — Author sandboxed JavaScript tools in a Monaco editor, with a model-driven create/update lifecycle.
- [dsh-security-audit](https://github.com/omdsh-dev/dsh-security-audit) — Local read-only security audit: config, credential metadata, plugin provenance, path permissions, session files, network exposure. Redacted reports, no auto-fix, and “could not read” is never treated as “safe.”
- [dsh-handbook](https://github.com/Electricitysheep/dsh-handbook) — A bilingual 0-to-1 handbook: install, plugin development, performance, measured cases, same-model multi-agent comparisons. [Read online](https://electricitysheep.github.io/dsh-handbook/) or grab the PDF.

### Integrations and migration

- [dsh-open-in-vscode](https://github.com/omdsh-dev/dsh-open-in-vscode) — Open the current workspace folder in VS Code from the Web GUI.
- [dsh-notification](https://github.com/omdsh-dev/dsh-notification) — Desktop notifications when a turn finishes, with per-outcome toggles and include/exclude keyword rules.
- [dsh-interconnect](https://github.com/Chinesezjc/dsh-interconnect) — Cross-instance message and event handoff so one DSH session can pass context to another.
- [dsh-chat-import](https://github.com/Nwflower/dsh-chat-import) — Read-only import of Claude Code, Codex, ChatGPT, Cursor, Gemini, Reasonix, and OpenCode histories (tool calls and thinking blocks included) so you can resume inside DSH.
- [dsh-worktree](https://github.com/FlashingChen/dsh-worktree) — Codex-style permanent git worktrees: create once, reuse across sessions, leave the main tree alone. Ships `worktree_create/list/remove` and a `/worktree` command.

### Skins and sharing

- [dsh-deep-whale](https://github.com/Small-tailqwq/dsh-deep-whale) — The most complete whale-girl skin series (Deep-Sea Maid Atelier). Light and dark themes, CC BY-NC-SA 4.0.
- [whale-girl](https://github.com/vlln/whale-girl) — A QQ-pet-style companion in the DSH Web GUI: drag, feed, and play in the corner; levels accumulate from tasks and time spent together.
- [dsh-share](https://github.com/hellodigua/dsh-share) — Export one Q&A turn as a PNG: Markdown, code, tables, and tool summaries, with an option to hide the thinking trace. Copy to clipboard or download.

## Safety

Third-party plugins may read API keys, session logs, workspace files, or open ports on your machine. Prefer repos that declare `dsh.bundle` and document their permission boundary. Inspect recent commits and the tool list before installing. Use [dsh-plugin-check](https://github.com/omdsh-dev/dsh-plugin-check) and [dsh-security-audit](https://github.com/omdsh-dev/dsh-security-audit) for structural and exposure checks.

This list is discovery only. It is **not** an official DeepSeek endorsement and does not guarantee compatibility with the current rc.

## Contributing

If a plugin belongs here, a description is stale, or a category is wrong, open an Issue or Pull Request. Say what problem it solves, why it is more representative than what is already listed, and how to install it.

## License

This list is released under the [MIT License](LICENSE). Listed projects keep their own licenses.
