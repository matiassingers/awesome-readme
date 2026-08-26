---
name: awesome-readme
description: Write production-grade README files for open-source projects. Use when creating, rewriting, or improving a project README.md. Covers structure, badges, navigation, GIFs, comparison tables, architecture diagrams, and multilingual support. Trigger words: write README, improve README, README style, project documentation, 开源项目文档, 写 README.
agent_created: true
---

# Awesome README

Agent 执行指南：为开源项目写或改进 README。基于 [matiassingers/awesome-readme](https://github.com/matiassingers/awesome-readme) 100+ 案例提炼。

---

## 判断意图

| 意图 | 信号 | 流程 |
|------|------|------|
| **从零写** | "帮我写个 README"、项目没有 README | → Step 1 → Step 2 → Step 3 → Step 4 |
| **改进现有** | "帮我改进 README"、项目已有 README | → Step 0 → Step 1 → Step 2 → Step 3 → Step 4 |
| **迭代优化** | README 已发布，需要根据反馈改进 | → Step 5 → Step 4（检查） |

---

## Step 0: 诊断现有 README（改进模式专用）

改进前必须先诊断，不能直接套模板重写。

**诊断清单：**
1. 有没有一句话价值主张？
2. Badge 是否统一风格（全是 for-the-badge）？
3. 有没有导航行？
4. Quick Start 能几步跑起来？
5. 有没有 GIF/截图？
6. 有没有空章节？
7. 代码块是否可复制？
8. 有没有 `<div align="center">`？

**分类问题（按严重程度）：**
- 🔴 **结构缺失**：没有价值主张、没有导航、没有 Quick Start → 必须补
- 🟡 **内容问题**：章节太空、文字太多、缺少视觉 → 需要优化
- 🟢 **风格问题**：Badge 不统一、缺少 emoji、没有分隔线 → 微调

**输出诊断报告**，用户确认后再改。

---

## Step 1: 项目分类 + 特征评估

### 类型判断

| 类型 | 判断依据 | 核心策略 |
|------|----------|----------|
| **CLI 工具** | package.json 有 `bin` 字段；或 README 里有命令行用法 | 安装命令 + 用法示例 + GIF |
| **库/包** | 有 `lib`/`main`/`exports` 字段；被其他项目 import | API 文档 + 安装 + 最小示例 |
| **框架** | README 有 "getting started" + "tutorial" + "philosophy" | Why + 理念 + 教程 + 生态 |
| **Web 应用** | 有 `deploy`/`demo` 链接；浏览器访问 | 截图/GIF + 部署按钮 + Demo |
| **教学项目** | 有练习、课程、教程结构 | 目录 + 文件列表 + 分步 GIF |
| **合集/工具集** | awesome-list 类 | 分类表格 + 贡献指南 |

不确定时，默认按「库」处理。

### 特征评估

类型确定后，再评估三个维度，决定具体模式组合：

| 维度 | 选项 | 影响 |
|------|------|------|
| **面向谁** | 开发者 / 终端用户 / 两者 | 开发者→放 API；终端用户→放截图 |
| **有无替代品** | 有 / 没有 | 有→放对比表；没有→放 Why 章节 |
| **成熟度** | 早期(0.x) / 稳定(1.x+) / 活跃开发中 | 早期→Quick Start 为主；稳定→教程+生态；活跃→动态路线图 |

### 混合类型

项目同时属于多个类型时（如 CLI + 库），按主要用途选主模板，次要功能作为附加章节。例如 `ripgrep` 主要是 CLI，用 CLI 模板，加一个 `## Library API` 章节。

---

## Step 2: 内容填充

按三层架构选择内容：硬规则 → 决策框架 → 模式菜单。

### Layer 1: 硬规则（不可妥协）

#### 价值主张
- **必须有**：标题下方一句话
- **长度**：≤ 15 个英文单词（或 20 个中文字符）
- **提炼流程**：
  1. 读 package.json 的 `description` 字段
  2. 读源码入口文件（看暴露什么能力）
  3. 读 issue/PR（看用户怎么描述问题）
  4. 读现有 README（提取作者动机）
- **格式**：「[动词] + [对象] + [效果/差异]」
- **禁止**：形容词堆砌、空洞描述、技术术语
- **测试**：不懂技术的人读完能说出「这个项目是干嘛的」→ 通过

#### Badge
- 全部 `style=for-the-badge`
- 按项目类型选择数量（见下表）
- 顺序：技术栈 → License → CI → 版本 → Stars → Downloads

| 类型 | 必放 | 可选 | 上限 |
|------|------|------|------|
| CLI | License, CI | Stars, Downloads | 4 |
| 库 | License, CI, Version | Stars, Downloads | 5 |
| 框架 | License, CI, Version | Stars, Discord, Docs | 7 |
| Web 应用 | License, CI | Demo, Stars | 4 |

#### 导航行
- Badge 下方紧跟，格式：`[链接](#锚点) · [链接](#锚点)`
- 覆盖主要章节，锚点语言与 README 语言一致

#### 章节分隔
- H2 之间用 `---`
- H3 带 emoji 前缀

#### Quick Start
- 安装 ≤ 2 步，运行 ≤ 1 步，总共 ≤ 3 步
- 需要配置时：Quick Start 用默认值，配置单独放 `## 配置`

#### 视觉内容
- CLI：必须有 GIF
- Web：必须有截图或 GIF
- 库：代码示例即可，GIF 可选
- 架构图：用 ASCII art（`references/ascii-templates.md`）
- 长内容：用 `<details>` 折叠

### Layer 2: 决策框架（选路径）

根据 Step 1 的特征评估，决定具体做法：

| 特征 | 决策 |
|------|------|
| 面向开发者 | 放 API 章节、代码示例、TypeDoc/JSDoc 链接 |
| 面向终端用户 | 放截图、GIF、安装步骤 |
| 有替代品 | 放对比表（参考 [slate](https://github.com/electrikhq/slate)） |
| 没有替代品 | 放 Why 章节（参考 [create-go-app](https://github.com/create-go-app/cli)） |
| 早期项目 | 精简结构，只留核心章节（参考 [karan/joe](https://github.com/karan/joe)） |
| 稳定项目 | 加教程、生态、贡献者（参考 [gofiber/fiber](https://github.com/gofiber/fiber)） |
| 活跃开发中 | 加动态路线图（参考 [implot3d](https://github.com/brenocq/implot3d)） |
| 概念复杂 | 用认知漏斗（参考 [Closures](https://github.com/vhesener/Closures)） |

### Layer 3: 模式菜单（选做法）

从 `references/patterns.md` 中挑选合适的模式。每个模式有：名称、具体做法、适用场景、**不适用场景**、来源案例、**执行门槛**（🟢直接写 | 🟡需用户提供素材 | 🔴需人工创作）。

**按场景选模式类别：**

| 场景 | 模式类别 | 详见 patterns.md |
|------|----------|------------------|
| 项目有个性/态度 | 视觉锚点类 | Humorous Quote, Animated Banner |
| 需要展示性能 | 信息展示类 | Benchmark Chart |
| 需要对比替代品 | 信息展示类 | Comparison Table |
| 有合规/认证 | 信息展示类 | Certification Table |
| 概念复杂需要渐进教学 | 视觉锚点类 + 文档深度类 | Cognitive Funnel, Long-Form Essay |
| 功能多需要视觉演示 | 视觉演示类 | Feature-Anchored GIF, Feature GIF Gallery |
| 有社区需要信任建设 | 信任建设类 | Contributor Avatar Wall, Star Growth Chart |
| 活跃开发需要透明度 | 动态内容类 | Dynamic Roadmap, Dynamic Stats SVG |
| 需要快速上手 | 部署与交互类 | Deploy Button, Live Demo, Copy-Paste Config |
| 需要解释为什么 | 文档深度类 | Philosophy Section, Motivation Section |

**选择后，检查执行门槛：**
- 🟢 直接写：agent 可以独立完成
- 🟡 需要用户提供素材：先问用户要信息，再格式化
- 🔴 需要人工创作：告知用户这个模式需要手动完成，提供替代方案

完整模式库见 `references/patterns.md`（30+ 模式，每个有来源案例 + 不适用场景 + 执行门槛）。

### 语言选择

README 的语言选择取决于目标受众，不是「默认英文」：

| 场景 | 推荐语言 | 结构 |
|------|----------|------|
| **面向国际开发者** | 英文 README.md | 单文件 |
| **面向国内用户** | 中文 README.md | 单文件 |
| **面向双语用户** | 英文 README.md + 中文 README.zh.md | 两个文件，英文版顶部放语言切换链接 |
| **国内项目想吸引国际贡献者** | 英文 README.md（主体）+ 中文 README.zh.md | 英文版放 badge + 导航，中文版放详细文档 |

**中英双语 README 的结构：**
```markdown
# 项目名
[中文](README.zh.md) | English

**English** | [中文](README.zh.md)
---
（英文内容）
```

**锚点语言规则**：锚点语言与 README 语言一致。英文 README 用 `#quick-start`，中文 README 用 `#快速开始`。

### 结构模板

以下模板是骨架，按需裁剪。

#### CLI 工具
```markdown
# ⚡ 项目名
**[价值主张]**

[Badge 行]
[安装](#安装) · [用法](#用法) · [配置](#配置)

---

## 它解决什么问题？
## 安装
## 用法
## 示例 GIF
## 配置
## License
```

#### 库/包
```markdown
# 📦 项目名
**[价值主张]**

[Badge 行]
[安装](#安装) · [快速开始](#快速开始) · [API](#api) · [示例](#示例)

---

## 为什么？
## 安装
## 快速开始
## API
## 示例
## 对比表
## License
```

#### 框架
```markdown
# 🚀 项目名
**[价值主张]**

[Badge 行]
[文档](#文档) · [教程](#教程) · [API](#api) · [社区](#社区)

---

## 为什么需要这个？
## 核心特性
## 安装
## 快速开始
## 教程
## 架构
## 生态
## 贡献者
## License
```

#### Web 应用
```markdown
# 🌐 项目名
**[价值主张]**

[Badge 行]
[Demo](#demo) · [截图](#截图) · [安装](#安装) · [部署](#部署)

---

## 截图/GIF
## 功能
## Demo
## 安装
## 部署
## 技术栈
## License
```

### 模板裁剪规则

| 情况 | 裁剪方式 |
|------|----------|
| 项目很简单 | 只留：标题 + 价值主张 + 安装 + 用法 + License |
| 没有可配置项 | 删 `## 配置` |
| 没有替代方案 | 删 `## 对比表` |
| 没有用户 | 删 `## 贡献者`、`## 生态` |
| 早期项目 | 删 `## 教程`，保留 `## 快速开始` |
| 混合类型 | 用主模板，次要功能作为附加章节 |

**原则**：宁可少一个章节，不要多一个空章节。

---

## Step 3: 组装

1. 标题行 — `# 项目名`
2. 价值主张 — 一句话
3. Badge 行 — for-the-badge
4. 导航行 — `·` 分隔
5. 分隔线 — `---`
6. 主内容 — 按模板填充 + 从模式菜单挑选的模式
7. License — 最后一节

---

## Step 4: 质量检查

- [ ] 价值主张 ≤ 15 词
- [ ] Badge 全部 `style=for-the-badge`
- [ ] Badge 数量符合类型上限
- [ ] 导航行覆盖所有主要章节
- [ ] Quick Start ≤ 3 步
- [ ] 没有空章节
- [ ] 没有 TODO 占位符
- [ ] 没有 `<div align="center">`
- [ ] H2 之间有 `---`
- [ ] 代码块可复制
- [ ] GIF/截图已渲染
- [ ] 长内容用 `<details>` 折叠
- [ ] README 在 GitHub 上渲染正常

---

## Step 5: 发布后迭代

README 不是一次性产物。发布后根据反馈持续优化。

### 触发信号

| 信号 | 含义 | 优先级 |
|------|------|--------|
| 多人问 README 已写过的问题 | 信息找不到或表述不清 | 🔴 高 |
| Star 高但 fork/issue 少 | README 没说服人试用 | 🔴 高 |
| 新贡献者不知道从哪开始 | Contributing 指引不够 | 🟡 中 |
| 外部博客/视频引用了 README 的特定部分 | 那部分是有效的，保留 | 🟢 参考 |
| 项目功能变化但 README 没更新 | 信息过时 | 🟡 中 |

### 迭代原则

1. **保持结构稳定**：不要频繁调整章节顺序，读者会形成心智模型
2. **只改内容，不改骨架**：章节标题和顺序是骨架，内容是肉
3. **版本化更新**：大改在 commit message 里说清楚改了什么
4. **定期审视**：每 3 个月过一遍质量检查清单（Step 4）

### 诊断方法

由于 GitHub 不提供 README 阅读数据，用间接信号诊断：
- **issue/PR 内容**：如果很多人问 README 已回答的问题 → 信息找不到
- **外部引用**：搜索项目名，看别人截图/引用 README 的哪部分 → 那部分有效
- **贡献者反馈**：新贡献者说「不知道怎么开始」→ Contributing 指引不足

---

## 反模式（禁止）

- ❌ "Table of Contents" 文字标题
- ❌ 5+ badge 彩虹墙
- ❌ 没有标题的纯文本墙
- ❌ 安装步骤 > 3 步且没有解释
- ❌ Contributing 写 20 条规则
- ❌ Logo 超过 400px
- ❌ "Star this repo if you like it"
- ❌ 空的 "Coming soon" / "WIP"
- ❌ 图片不用相对路径
- ❌ 中英混杂的标题

---

## 工具

| 工具 | 用途 | 门槛 |
|------|------|------|
| [vhs](https://github.com/charmbracelet/vhs) | 脚本式录制终端 GIF | 🟢 写 .tape 脚本即可 |
| [terminalizer](https://github.com/faressoft/terminalizer) | 终端录制 → GIF/web | 🟢 命令行录制 |
| [ScreenToGif](https://github.com/NickeManarin/ScreenToGif/) | 屏幕录制 → GIF，可编辑 | 🟢 Windows 专用 |
| [LICEcap](https://www.cockos.com/licecap/) | 轻量屏幕录制 → GIF | 🟢 跨平台 |
| [Giphy Capture](https://giphy.com/apps/giphycapture) | macOS 录制 → GIF，可上传 Giphy | 🟢 macOS 专用 |
| [ttystudio](https://github.com/chjj/ttystudio) | 终端-to-GIF 录制器 | 🟢 命令行 |
| [Gifski](https://github.com/sindresorhus/Gifski) | 高质量 GIF 压缩 | 🟢 拖拽文件即可 |
| [readme-md-generator](https://github.com/kefranabg/readme-md-generator) | CLI 生成 README 模板 | 🟢 交互式 CLI |
| [GitHub Readme Stats](https://github.com/anuraghazra/github-readme-stats) | 动态数据卡片（星标/提交/语言） | 🟢 配置 GitHub Action |
| [Readme Forge](https://readme-forge.github.io/) | 组件化 README 生成器 | 🟢 Web 界面 |
| [maintainer.io](https://maintainer.io/) | 免费 README 标准化反馈 | 🟢 粘贴 URL 即可 |
| [contrib.rocks](https://contrib.rocks) | 自动生成贡献者头像墙 | 🟢 替换仓库名即可 |
| [star-history.com](https://star-history.com) | 生成 Star 增长图表 | 🟢 选择仓库即可 |

---

## 延伸阅读

| 文章 | 核心观点 |
|------|----------|
| [Art of Readme](https://github.com/hackergrrl/art-of-readme) | README 是项目最重要的营销工具 |
| [Readme Driven Development](https://tom.preston-werner.com/2010/08/23/readme-driven-development.html) | 先写 README 再写代码 |
| [Elegant READMEs](https://www.yegor256.com/2019/04/23/elegant-readme.html) | 好 README 的审美标准 |
| [How To Write A Great README](https://thoughtbot.com/blog/how-to-write-a-great-readme) | 实用写作指南 |
| [ARCHITECTURE.md](https://matklad.github.io/2021/02/06/ARCHITECTURE.md.html) | 为什么需要架构文档 |
| [Top ten reasons why I won't use your open source project](https://changelog.com/posts/top-ten-reasons-why-i-wont-use-your-open-source-project) | 用户视角的 README 问题 |
| [Writing "icks" for a good README](https://mtlynch.io/write-readme-icks/) | 常见的 README 让人烦的做法 |

---

## Architecture Documentation

独立的 ARCHITECTURE.md 帮助开发者理解系统设计。

| 项目 | 亮点 |
|------|------|
| [esbuild](https://github.com/evanw/esbuild/blob/main/docs/architecture.md) | 可视化图表 + 核心原则列表 |
| [Flutter Engine](https://github.com/flutter/flutter/blob/master/docs/about/The-Engine-architecture.md) | 高层架构图 + 平台不变量 |
| [Redis](https://github.com/redis/redis/blob/unstable/README.md) | 源码地图 + 关键文件概览 |
| [Tauri](https://github.com/tauri-apps/tauri/blob/dev/ARCHITECTURE.md) | 源码地图 + 架构考量 + 依赖说明 |
| [VS Code](https://github.com/microsoft/vscode/wiki/Source-Code-Organization) | 高层架构图 + 源码组织说明 |
| [Oh My Zsh](https://github.com/ohmyzsh/ohmyzsh/wiki/Design) | 初始化流程 + 环境要求 |
| [Neovim](https://github.com/neovim/neovim/blob/master/src/nvim/README.md) | 主进程/生命周期 |
| [GitLab](https://gitlab.com/gitlab-org/charts/gitlab/-/tree/master/doc/architecture) | 设计决策记录 |
| [Linux crypto](https://github.com/torvalds/linux/blob/master/Documentation/crypto/architecture.rst) | 组件分类 + 不变量 |
