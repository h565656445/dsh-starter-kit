# dsh-starter-kit

<!-- DeepSeek Harness 衍生声明 -->
> **DeepSeek Harness 个人适配声明（Personal Adaptation Notice）**
>
> 本项目是 [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness) 的**个人适配产物（personal adaptation）**，**并非 DeepSeek Harness 官方文件（not an official DeepSeek Harness file）**。随附功能、使用说明与个人产物，可与 DeepSeek Harness 搭配使用，也可独立使用。
>
> This project is a **personal adaptation** for DeepSeek Harness, and is **NOT an official DeepSeek Harness file**. It is bundled with features, documentation, and personal artifacts, and can be used alongside DeepSeek Harness or standalone.

**作者 / Author**: [h565656445](https://github.com/h565656445)

**合作 / Collaboration**: 如有项目可以一起合作，欢迎联系。微信：\`wohaishihenshuaide\`。If you have projects, let's collaborate. WeChat: \`wohaishihenshuaide\`.


---

## 用途 / What this is for

快速上手套件：Hermes Harness 是什么、三步安装、preset/skill 用法与示例场景，帮助新手快速上手。

Starter kit: what Hermes Harness is, three-step install, preset/skill usage and example scenarios.

---
## Hermes Harness DSH Starter Kit / Hermes Harness DSH 快速上手

本仓库是 **Hermes Harness** 及其 DeepSeek Harness（DSH）衍生的双语快速上手套件：Hermes Harness 是什么、如何安装 DSH 衍生 preset/skill、如何在工作流中使用，并附三个可直接照做的示例场景与 example/ 示例文件。

This repository is the **bilingual starter kit** for Hermes Harness and its DeepSeek Harness (DSH) derivatives: what Hermes Harness is, how to install DSH derivative presets/skills, how to use them in your workflow, plus three ready-to-follow example scenarios and example files under example/.

## Hermes Harness 是什么 / What Is Hermes Harness

Hermes Harness 是一套面向 LLM Agent 的控制平面与工程化框架（作者 h565656445）：以 PowerShell 模块承载任务契约、质量门禁、可观测性与升级治理，围绕 Agent OS 内核（运行时、规划、调度、worker 协议、可观测性）组织多 Agent 编排，并沉淀为 JSON Schema 驱动的契约体系。其可复用产物已按 A–H 八组拆分为 31 个 DSH 衍生开源项目（完整索引见 dsh-integration）。

Hermes Harness is a control-plane and engineering framework for LLM agents (author h565656445): PowerShell modules implement task contracts, quality gates, observability, and upgrade governance; an Agent OS kernel (runtime, planning, scheduling, worker protocol, observability) organizes multi-agent orchestration; and a JSON-Schema-driven contract system keeps everything consistent. Its reusable artifacts are split into 42 DSH derivative open-source projects across groups A–H (full index in dsh-integration).

## Features / 功能

- 三步上手：安装 DSH 衍生 → 选择 preset → 加载 skill / Three steps: install DSH derivatives → pick a preset → load a skill
- 覆盖 preset 与 skill 两种接入方式 / Covers both preset and skill integration paths
- 三个示例场景（含命令与预期结果）/ Three example scenarios (with commands and expected outcomes)
- example/ 提供示例 preset.yml 与示例 SKILL.md / example/ ships a sample preset.yml and a sample SKILL.md
- 全中文/English 双语说明 / Fully bilingual (zh/en) instructions

## What's inside / 目录结构

    dsh-starter-kit/
    ├── README.md           # 快速上手（双语）
    ├── LICENSE             # MIT
    ├── example/
    │   ├── preset.yml      # 示例 preset.yml（元数据）
    │   └── SKILL.md        # 示例 SKILL.md（技能）
    └── .dsh/
        ├── preset.yml
        ├── agent.cordis.yml
        ├── README.md
        └── skills/dsh-starter-kit/SKILL.md

## Quick start / 快速开始

### 第一步：安装 DSH 衍生

方式 A：一键安装全部预设（来自 dsh-integration）：

    git clone https://github.com/h565656445/dsh-integration
    cd dsh-integration
    .\install-presets.ps1

方式 B：手动安装单个 preset（PowerShell 7）：

    $dst = Join-Path $env:DSH_HOME '.agent-presets\dsh-integration'
    Copy-Item -Recurse -Force '.\dsh' $dst

方式 C：仅安装技能：

    $dst = Join-Path $env:DSH_HOME 'skills\dsh-starter-kit'
    New-Item -ItemType Directory -Force -Path $dst | Out-Null
    Copy-Item '.\dsh\skills\dsh-starter-kit\SKILL.md' $dst -Force

### 第二步：使用 preset

重启 DeepSeek Harness，新建会话时在预设列表选择对应预设（例如 Hermes DSH 总集成），会话即获得定制 persona 与完整工具组装。

### 第三步：使用 skill

在会话中告知模型使用对应技能（技能 id = 仓库名），模型会加载技能说明并按其工作流执行；也可直接在 $DSH_HOME/skills/ 目录查阅。

## Example Scenarios / 示例场景

### 场景一：快速定位任意衍生项目

目标：在 31 个项目中找到「小说规格」相关仓库。

步骤：
1. 安装 dsh-integration 预设（见上）。
2. 在会话中提问：在 CATALOG.md 中查找小说相关项目。
3. 预期结果：返回 dsh-novel-specs 及其一句话简介、来源映射。

### 场景二：用示例 preset 创建自己的预设

目标：参考 example/preset.yml 新建个人预设。

步骤：
1. 打开 example/preset.yml，复制到 $DSH_HOME/.agent-presets/my-preset/。
2. 修改 name/description/order，并从某项目复制 agent.cordis.yml 定制 persona。
3. 重启 DeepSeek Harness，在预设列表选择 my-preset。

### 场景三：用示例 SKILL.md 沉淀团队技能

目标：把常用检查流程固化为技能。

步骤：
1. 打开 example/SKILL.md，仿照 front-matter 与正文结构改写。
2. 保存到 $DSH_HOME/skills/<skill-id>/SKILL.md。
3. 会话中按技能 id 调用，模型按 Workflow 执行。

## DeepSeek Harness 衍生 / DSH Derivative

本项目附带 DeepSeek Harness 衍生包，位于 .dsh/ 目录：

- preset.yml — Agent 预设元数据
- agent.cordis.yml — Cordis 组装（基于 standard 预设，persona 已定制）
- skills/dsh-starter-kit/SKILL.md — 项目专属技能（skill）

安装与接入方式见 [.dsh/README.md](.dsh/README.md)（双语）。

## License / 许可证

[MIT](LICENSE)

---

---

## 相关项目 / Related Projects

> 这是 DeepSeek Harness 个人适配系列（共 31 个仓库）的完整导航。 / This is the complete navigation for the DeepSeek Harness personal-adaptation series (31 repos).

### Agent OS 内核 / Kernel

[`dsh-agent-os-runtime`](https://github.com/h565656445/dsh-agent-os-runtime) · [`dsh-agent-os-planning`](https://github.com/h565656445/dsh-agent-os-planning) · [`dsh-agent-os-scheduler`](https://github.com/h565656445/dsh-agent-os-scheduler) · [`dsh-agent-os-worker-protocol`](https://github.com/h565656445/dsh-agent-os-worker-protocol) · [`dsh-agent-os-observability`](https://github.com/h565656445/dsh-agent-os-observability) · [`dsh-agent-os-specs`](https://github.com/h565656445/dsh-agent-os-specs)

### Harness 基础设施 / Infrastructure

[`dsh-harness-core`](https://github.com/h565656445/dsh-harness-core) · [`dsh-graph-entry`](https://github.com/h565656445/dsh-graph-entry) · [`dsh-async-job`](https://github.com/h565656445/dsh-async-job) · [`dsh-file-identity`](https://github.com/h565656445/dsh-file-identity) · [`dsh-json-projection`](https://github.com/h565656445/dsh-json-projection) · [`dsh-manual-approval`](https://github.com/h565656445/dsh-manual-approval) · [`dsh-observation-writer`](https://github.com/h565656445/dsh-observation-writer) · [`dsh-provider-control`](https://github.com/h565656445/dsh-provider-control) · [`dsh-schema-negotiator`](https://github.com/h565656445/dsh-schema-negotiator) · [`dsh-upgrade-governance`](https://github.com/h565656445/dsh-upgrade-governance)

### 规格与文档 / Specs & Docs

[`dsh-harness-specs`](https://github.com/h565656445/dsh-harness-specs) · [`dsh-novel-specs`](https://github.com/h565656445/dsh-novel-specs) · [`dsh-architecture-guide`](https://github.com/h565656445/dsh-architecture-guide) · [`dsh-powershell-patterns`](https://github.com/h565656445/dsh-powershell-patterns) · [`dsh-json-schema-driven-dev`](https://github.com/h565656445/dsh-json-schema-driven-dev) · [`dsh-llm-agent-harness-guide`](https://github.com/h565656445/dsh-llm-agent-harness-guide)

### 适配器 / Adapters

[`dsh-short-story-engine`](https://github.com/h565656445/dsh-short-story-engine) · [`dsh-tutorial-video-state-machine`](https://github.com/h565656445/dsh-tutorial-video-state-machine) · [`dsh-governance-kernel`](https://github.com/h565656445/dsh-governance-kernel) · [`dsh-sports-pipeline`](https://github.com/h565656445/dsh-sports-pipeline) · [`dsh-motion-grammar`](https://github.com/h565656445/dsh-motion-grammar)

### DSH 总集成 / Integration

[`dsh-integration`](https://github.com/h565656445/dsh-integration) · [`dsh-presets-pack`](https://github.com/h565656445/dsh-presets-pack) · [`dsh-skills-pack`](https://github.com/h565656445/dsh-skills-pack) · **`dsh-starter-kit`（本仓库 / this repo）**

