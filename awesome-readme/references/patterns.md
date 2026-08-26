# 模式库（Patterns）

从 [matiassingers/awesome-readme](https://github.com/matiassingers/awesome-readme) 100+ 案例中提取的可复用设计模式。

每个模式包含：名称、具体做法、适用场景、**不适用场景**、来源案例、**执行门槛**。

- **适用场景**：什么时候该用
- **不适用场景**：什么时候不该用（反例）
- **执行门槛**：AI agent 能否直接执行（🟢 直接写代码/文本 | 🟡 需要用户提供素材 | 🔴 需要人工创作）

---

## 视觉锚点类

### Humorous Quote（幽默引言）
- **做法**：标题下方放一句有趣/有态度的话，替代干巴巴的描述
- **适用**：个人项目、创意工具、有个性的开源项目
- **不适用**：❌ 企业级项目、❌ 严肃工具（安全/金融/合规）、❌ 团队项目（幽默感因人而异）
- **来源**：[doomemacs/doomemacs](https://github.com/doomemacs/doomemacs) — "Well-written introduction with a humorous quote that perfectly describes the project, plus a little demon that says 'Yay Evil!' to complete the aesthetic"
- **可抄**：找一句能概括项目精神的引言，放在标题下方
- **执行门槛**：🟡 需要用户提供项目气质/调性，agent 建议候选引言

### Comic Demo（漫画演示）
- **做法**：用漫画/插图解释核心概念，替代文字描述
- **适用**：概念抽象的库、创意项目
- **不适用**：❌ 需要精确技术描述的项目、❌ 企业级项目
- **来源**：[sultan99/react-on-lambda](https://github.com/sultan99/react-on-lambda) — "comics to present the main idea"
- **可抄**：画 2-3 帧简笔画，说清楚"输入什么 → 得到什么"
- **执行门槛**：🔴 需要手绘/设计能力，agent 无法生成漫画
- **替代方案（agent 可执行）**：用「概念流程」文字模板：
  ```
  ### 核心概念

  **传统方式：**
  ```
  // 10 行复杂代码才能实现 X
  ```

  **本项目：**
  ```
  // 1 行搞定
  ```
  > 💡 关键区别：传统方式需要手动管理 A、B、C，本项目自动处理。
  ```

### Cognitive Funnel（认知漏斗）
- **做法**：从最简单的例子开始，逐步增加复杂度，让读者自然理解
- **适用**：概念复杂的库（函数式编程、状态管理等）
- **不适用**：❌ 简单工具（杀鸡用牛刀）、❌ API 参考文档（应该按功能分组）
- **来源**：[vhesener/Closures](https://github.com/vhesener/Closures) — "cognitive funnel, animated examples. Color-coordinated"
- **可抄**：第 1 个例子 3 行代码，第 2 个 10 行，第 3 个 20 行，逐步引入概念
- **执行门槛**：🟢 agent 可以根据项目复杂度设计递进示例

### Animated Banner（动态横幅）
- **做法**：用动画 GIF 或 SVG 作为项目 banner，不是静态图片
- **适用**：有视觉冲击力的项目
- **不适用**：❌ 性能敏感的 CLI 工具（读者可能在终端看 README）、❌ 网络受限环境
- **来源**：[Grigorij-Dudnik/Clean-Coder-AI](https://github.com/Grigorij-Dudnik/Clean-Coder-AI) — "Crazy project trailer video. Beautiful logo, explanatory motion gifs"
- **可抄**：录一段 5 秒的终端/界面动画作为 banner
- **执行门槛**：🔴 需要录制/剪辑能力，agent 无法生成动画
- **替代方案（agent 可执行）**：用静态 logo + typing SVG 动画文字：
  ```markdown
  <p align="center">
    <img src="logo.png" width="200" alt="Logo">
  </p>

  <h3 align="center">
    <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&pause=1000&color=37A3E4&center=true&vCenter=true&width=435&lines=项目的一句话描述;功能1+功能2+功能3;开源+免费" alt="Typing SVG" />
  </h3>
  ```
  工具：[readme-typing-svg](https://github.com/DenverCoder1/readme-typing-svg)

### Visual Hierarchy with SVG Icons（SVG 图标层级）
- **做法**：用自定义 SVG 图标做章节标题，而不是纯文字 emoji
- **适用**：追求视觉品质的项目
- **不适用**：❌ 快速迭代的项目（维护成本高）、❌ 纯文本 README（终端兼容性）
- **来源**：[dmunish/reach](https://github.com/dmunish/reach) — "Makes extensive use of HTML and custom SVG icons"
- **可抄**：为每个主要章节设计一个小图标
- **执行门槛**：🔴 需要设计能力，agent 无法生成 SVG 图标
- **替代方案（agent 可执行）**：用 emoji + 统一映射表：
  ```
  📡 网络/通信    🔐 安全/认证    ⚡ 性能/速度
  📦 打包/发布    🧪 测试/质量    🚀 部署/上线
  📊 数据/统计    🔧 配置/工具    📖 文档/教程
  🤝 社区/贡献    🎨 UI/设计     🏗️ 架构/设计
  ```
  保持全项目 emoji 映射一致即可达到类似层级效果。

---

## 信息展示类

### Benchmark Chart（性能基准图）
- **做法**：用图表展示性能数据，替代"比 XX 快 N 倍"的文字描述
- **适用**：性能敏感的库（解析器、运行时、数据库）
- **不适用**：❌ 性能不是卖点的项目（暴露短板）、❌ 没有 benchmark 数据的项目（不要编造数据）
- **来源**：[gofiber/fiber](https://github.com/gofiber/fiber) — "benchmark charts"
- **可抄**：用 benchmark 工具跑出数据，生成柱状图/折线图
- **执行门槛**：🟢 agent 可以用 Markdown 表格展示 benchmark 数据（简单的柱状图），复杂图表需要用户生成图片

### Certification Table（认证/合规表）
- **做法**：用表格展示合规信息、认证状态、安全审计结果
- **适用**：企业级项目、安全类项目、金融类项目
- **不适用**：❌ 个人项目（没有认证信息）、❌ 早期项目（还没做审计）
- **来源**：[Abblix/Oidc.Server](https://github.com/Abblix/Oidc.Server) — "certification details with informative tables"
- **可抄**：列出 `| 标准 | 状态 | 说明 |` 的表格
- **执行门槛**：🟡 需要用户提供认证/合规信息，agent 只负责格式化

### Feature GIF Gallery（功能 GIF 画廊）
- **做法**：每个主要功能配一段独立 GIF，而不是只放一个总演示
- **适用**：功能多的 Web 应用、桌面应用
- **不适用**：❌ 功能单一的工具（一个 GIF 够了）、❌ 纯 CLI 工具（用文字描述更清晰）
- **来源**：[brenocq/implot3d](https://github.com/brenocq/implot3d) — "Project banner with GIFs"
- **可抄**：每个功能截图/GIF 一行，左图右文
- **执行门槛**：🔴 需要录制/截图，agent 无法生成 GIF
- **替代方案（agent 可执行）**：用「功能卡片」表格 + 代码示例：
  ```markdown
  ## 功能

  | 功能 | 描述 | 示例 |
  |------|------|------|
  | 🔍 搜索 | 模糊搜索，支持拼音 | `search("hello")` → 结果 |
  | 📊 统计 | 实时数据看板 | `stats()` → 图表 |
  | 🔔 通知 | 多渠道推送 | `notify("msg")` → 发送 |
  ```

### Comparison Table（对比表）
- **做法**：和替代方案的特性对比表格，帮用户做选择
- **适用**：有竞争替代品的库/工具
- **不适用**：❌ 没有替代品的创新项目（放对比表反而暴露局限）、❌ 替代品太多（表格变成 20 行，读者看不完）
- **来源**：[electrikhq/slate](https://github.com/electrikhq/slate) — "a short why-this-readme comparison table"
- **可抄**：`| 特性 | 本项目 | 替代方案 A | 替代方案 B |` 格式
- **执行门槛**：🟡 需要用户提供对比维度和数据，agent 负责格式化

### Version Callout（版本说明）
- **做法**：明确区分当前版本和旧版本，避免用户混淆
- **适用**：有重大版本升级的项目
- **不适用**：❌ 还没有 1.0 的项目（版本号本身就不稳定）、❌ 小版本更新（不需要特别说明）
- **来源**：[gui-cs/Terminal.Gui](https://github.com/gui-cs/Terminal.Gui) — "Versioning callout distinguishing the current v2 from the v1 maintenance line"
- **可抄**：在 README 顶部加 `> ⚠️ v2 已发布，v1 仅维护安全更新`
- **执行门槛**：🟢 agent 可以直接写

### TL;DR Usage（极简用法）
- **做法**：在详细文档前放一个 3 行以内的最小用法
- **适用**：API 复杂但有常见用法的库
- **不适用**：❌ API 简单的工具（直接写完整用法即可）、❌ 没有"常见用法"的项目
- **来源**：[Rebilly/redoc](https://github.com/Redocly/redoc) — "TL;DR usage"
- **可抄**：`## 快速使用` 下面只放代码，不解释
- **执行门槛**：🟢 agent 可以从源码中提取最小用法

---

## 导航与结构类

### Section Links（章节链接导航）
- **做法**：标题下方放一行锚点链接，用 `·` 分隔，替代传统 TOC
- **适用**：所有项目
- **不适用**：❌ 内容很少的项目（3 个章节不需要导航）
- **来源**：[doomemacs/doomemacs](https://github.com/doomemacs/doomemacs) — "Centered title with section links"
- **可抄**：`[安装](#安装) · [用法](#用法) · [配置](#配置)`
- **执行门槛**：🟢 agent 可以直接写

### Collapsible TOC（可折叠目录）
- **做法**：用 `<details>` 包裹 TOC，点击展开
- **适用**：内容多的 README（框架、长文档）
- **不适用**：❌ 内容少的项目（折叠后反而多一步操作）
- **来源**：[release-it/release-it](https://github.com/release-it/release-it) — "Expandable TOC"
- **可抄**：`<details><summary>目录</summary>...</details>`
- **执行门槛**：🟢 agent 可以直接写

### Back-to-Top Link（回顶部链接）
- **做法**：页脚放一个"回到顶部"链接
- **适用**：长 README（超过 200 行）
- **不适用**：❌ 短 README（用不到）
- **来源**：[aregtech/areg-sdk](https://github.com/aregtech/areg-sdk) — "'Back to top' links for easy navigation"
- **可抄**：`[↑ 返回顶部](#项目名)`
- **执行门槛**：🟢 agent 可以直接写

### Topic Hide/Show Menu（话题折叠菜单）
- **做法**：用 emoji + 折叠块组织多个话题，按需展开
- **适用**：内容多且分主题的项目
- **不适用**：❌ 内容少的项目、❌ 线性文档（教程不适合折叠）
- **来源**：[aregtech/areg-sdk](https://github.com/aregtech/areg-sdk) — "Topic hide/show menu"
- **可抄**：每个话题一个 `<details>` 块，emoji 标识
- **执行门槛**：🟢 agent 可以直接写

### Complete File List（完整文件列表）
- **做法**：列出仓库所有文件及其用途
- **适用**：教学项目、教程仓库
- **不适用**：❌ 大型项目（文件太多，列表变成噪音）、❌ 普通开源项目（用文档结构代替）
- **来源**：[priyavrat-misra/xrays-and-gradcam](https://github.com/priyavrat-misra/xrays-and-gradcam) — "Complete list of all files in the repo and what their function is"
- **可抄**：`| 文件 | 用途 |` 表格
- **执行门槛**：🟢 agent 可以从代码结构中提取

---

## 视觉演示类

### Feature-Anchored GIF（功能锚定 GIF）
- **做法**：每个功能章节开头放 GIF，章节内容围绕 GIF 展开
- **适用**：功能多的工具、有交互界面的项目
- **不适用**：❌ 纯 CLI 工具（用代码示例更清晰）、❌ 简单工具（一个 GIF 够了）
- **来源**：[haesleinhuepf/bia-bob](https://github.com/haesleinhuepf/bia-bob) — "sections are anchored by a GIF or screenshot of the feature in action"
- **可抄**：`### 功能名` → GIF → 说明文字 → 代码示例
- **执行门槛**：🔴 需要录制/截图，agent 无法生成 GIF
- **替代方案（agent 可执行）**：用「输入 → 输出」代码块锚定：
  ```markdown
  ### 自动格式化

  代码写完后自动整理格式：

  ```python
  # 写入（乱的）
  def   foo(  x,y):return x+y

  # 自动格式化后
  def foo(x, y):
      return x + y
  ```

  > 📝 支持 Python、JavaScript、Go 等 20+ 语言。
  ```

### GIF Step-by-Step（GIF 分步演示）
- **做法**：安装/配置过程用多段 GIF 逐步展示
- **适用**：安装过程复杂的 CLI 工具
- **不适用**：❌ 安装简单的工具（一行命令搞定）、❌ 没有 GUI 的纯 CLI 工具（文字更清晰）
- **来源**：[supunlakmal/thismypc](https://github.com/supunlakmal/thismypc) — "GIF step-by-step instructions for installation"
- **可抄**：每步一个 GIF，配一行说明
- **执行门槛**：🔴 需要录制/截图，agent 无法生成 GIF

### Tutorial GIF Sequence（教程 GIF 序列）
- **做法**：教程中每个关键步骤配 GIF，形成视觉叙事
- **适用**：教程类 README、分步指南
- **不适用**：❌ API 参考文档（应该用代码示例）、❌ 快速开始（太重了）
- **来源**：[skydio/revup](https://github.com/Skydio/revup) — "Animated GIF demo + GIFs for major stages of the step-by-step tutorial"
- **可抄**：教程每个 H3 下面紧跟 GIF
- **执行门槛**：🔴 需要录制/截图，agent 无法生成 GIF

### Screenshot Gallery（截图画廊）
- **做法**：多张截图并排展示，形成视觉画廊
- **适用**：有多个界面/主题的项目
- **不适用**：❌ 没有 GUI 的 CLI 工具、❌ 功能单一的工具
- **来源**：[electrikhq/slate](https://github.com/electrikhq/slate) — "Screenshot gallery of the docs site"
- **可抄**：用表格或 HTML 并排 2-3 张截图
- **执行门槛**：🔴 需要截图，agent 无法生成图片

### Usage Artwork（用法艺术图）
- **做法**：把代码输出/使用效果做成艺术化的展示
- **适用**：有视觉输出的工具（字体、主题、终端美化）
- **不适用**：❌ 纯逻辑/计算类工具（没有视觉输出）
- **来源**：[NSRare/NSGIF](https://github.com/NSRare/NSGIF) — "Usage artwork"
- **可抄**：用工具输出的截图拼成艺术化的展示图
- **执行门槛**：🔴 需要设计能力，agent 无法生成艺术图
- **替代方案（agent 可执行）**：用终端模拟 code block：
  ````
  ```bash
  $ 你的工具 --flag input.txt

  ╭──────────────────────────╮
  │   输出结果 1             │
  │   输出结果 2             │
  │   输出结果 3             │
  ╰──────────────────────────╯
  ```
  ````
  用 Unicode box-drawing 字符模拟终端 UI 效果。

---

## 信任建设类

### Contributor Avatar Wall（贡献者头像墙）
- **做法**：展示所有贡献者的头像和用户名
- **适用**：有社区贡献的项目
- **不适用**：❌ 单人项目（只有自己，没有墙）、❌ 早期项目（贡献者太少）
- **来源**：[PostHog/posthog](https://github.com/PostHog/posthog) — "profile images for contributors"
- **可抄**：用 [contrib.rocks](https://contrib.rocks) 生成头像墙
- **执行门槛**：🟢 agent 可以生成 HTML 代码，用户粘贴即可

### Star Growth Chart（Star 增长图）
- **做法**：展示 Star 数量随时间的增长趋势
- **适用**：增长中的项目
- **不适用**：❌ Star 数很少的项目（图表不好看）、❌ 下降趋势的项目（暴露问题）
- **来源**：[gofiber/fiber](https://github.com/gofiber/fiber) — "star growth statistics"
- **可抄**：用 [star-history.com](https://star-history.com) 生成图表
- **执行门槛**：🟢 agent 可以生成嵌入链接，用户粘贴即可

### Hall of Fame（荣誉榜）
- **做法**：展示活跃贡献者、特别贡献者
- **适用**：社区活跃的项目
- **不适用**：❌ 贡献者很少的项目（只有 1-2 人不值得做榜）、❌ 企业内部项目
- **来源**：[treeverse/dvc](https://github.com/treeverse/dvc) — "nice contribution section with the hall-of-fame"
- **可抄**：分 Top Contributors / New Contributors / Code Reviewers
- **执行门槛**：🟢 agent 可以从 GitHub API 获取数据生成

### Social Links with Badges（社交链接徽章）
- **做法**：用 badge 格式展示 Discord/微信/邮件等联系方式
- **适用**：有社区的项目
- **不适用**：❌ 没有社区渠道的项目、❌ 企业内部工具
- **来源**：[aregtech/areg-sdk](https://github.com/aregtech/areg-sdk) — "Links with badges to contact and share on social networks"
- **可抄**：`[![Discord](https://img.shields.io/badge/Discord-join?style=for-the-badge)](https://discord.gg/xxx)`
- **执行门槛**：🟢 agent 可以直接写

---

## 动态内容类

### Dynamic Roadmap（动态路线图）
- **做法**：用 GitHub Actions 自动更新路线图 SVG
- **适用**：活跃开发中的项目
- **不适用**：❌ 已停止维护的项目、❌ 稳定版不需要 roadmap 的项目
- **来源**：[brenocq/implot3d](https://github.com/brenocq/implot3d) — "Dynamic roadmap with auto-updating SVGs that reflect feature discussions in real-time, powered by GitHub Actions"
- **可抄**：从 GitHub Discussions 抓取 feature request，生成 SVG 看板
- **执行门槛**：🟡 需要用户提供项目结构和 GitHub Actions 配置，agent 写脚本

### Auto-Generated README（自动生成 README）
- **做法**：从结构化元数据自动生成 README
- **适用**：合集类项目、awesome-list
- **不适用**：❌ 需要个性化表达的项目（生成的 README 缺乏灵魂）
- **来源**：[yeaight7/awesome-ai-devtools](https://github.com/yeaight7/awesome-ai-devtools) — "Auto-Generated README built from structured metadata"
- **可抄**：用 JSON/YAML 存储条目信息，脚本生成 markdown
- **执行门槛**：🟢 agent 可以直接写脚本

### Dynamic Stats SVG（动态统计 SVG）
- **做法**：用 GitHub Actions 生成实时统计数据的 SVG 图片
- **适用**：个人 profile、项目统计页
- **不适用**：❌ 不需要动态数据的项目、❌ GitHub Actions 不可用的环境
- **来源**：[github-licenses-stats](https://github.com/lheintzmann1/github-licenses-stats) — "generates a dynamic SVG that shows the top licenses"
- **可抄**：GitHub Action + shields.io 动态 badge
- **执行门槛**：🟡 需要用户提供项目结构，agent 写 GitHub Actions 配置

---

## 文档深度类

### Long-Form Essay（长文论述）
- **做法**：把 README 写成一篇完整的文章，解释理念、用法、生态
- **适用**：有哲学/理念需要传达的框架
- **不适用**：❌ 简单工具（长文让人烦）、❌ API 参考文档（应该结构化）、❌ 快速开始类项目（读者想马上用）
- **来源**：[Day8/re-frame](https://github.com/Day8/re-frame) — "Stands out by being a giant, well-written essay about the tech, how to use it, the philosophy behind it, and how it fits into the greater ecosystem"
- **可抄**：不是写文档，是写文章——有论点、有论据、有结论
- **执行门槛**：🟡 需要用户提供项目理念和设计决策，agent 写文章

### Philosophy Section（哲学/理念章节）
- **做法**：解释"为什么存在"、"为什么不用现有方案"
- **适用**：框架、有独特设计理念的库
- **不适用**：❌ 没有独特理念的项目（硬写会变成空话）、❌ 纯功能型工具
- **来源**：[gofiber/fiber](https://github.com/gofiber/fiber) — "project philosophy notes ('the why of project')"
- **可抄**：`## 理念` 下面写 2-3 段，说清楚你的设计决策
- **执行门槛**：🟡 需要用户提供设计理念，agent 写文章

### Motivation Section（动机章节）
- **做法**：解释创建这个项目的动机，比理念更个人化
- **适用**：个人项目、side project
- **不适用**：❌ 企业级项目（动机是商业决策，不适合公开）、❌ fork 项目（动机是改进，不是原创）
- **来源**：[gowebly/gowebly](https://github.com/gowebly/gowebly) — "project philosophy notes ('motivation to create')"
- **可抄**：`## 为什么做这个` 下面写你的故事
- **执行门槛**：🟡 需要用户提供动机故事，agent 写文章

### FAQ Section（常见问题）
- **做法**：收集用户最常问的问题，用 Q&A 格式回答
- **适用**：有重复问题的项目
- **不适用**：❌ 没有用户反馈的新项目（不知道什么会被问）、❌ 文档已经很完善（不需要 FAQ）
- **来源**：[choojs/choo](https://github.com/choojs/choo) — "An FAQ inside of it for the main questions"
- **可抄**：**Q:** 问题 → **A:** 回答，每个 2-3 行
- **执行门槛**：🟡 需要用户提供常见问题，agent 负责格式化

---

## 部署与交互类

### Deploy Button（一键部署）
- **做法**：放一个按钮，点击直接部署到 Vercel/Railway/Heroku
- **适用**：Web 应用、模板项目
- **不适用**：❌ 部署复杂的项目（点了也部署不了）、❌ 需要付费账号才能部署的项目（误导用户）
- **来源**：[PostHog/posthog](https://github.com/PostHog/posthog) — "deploy button"
- **可抄**：`[![Deploy](https://vercel.com/button)](https://vercel.com/new/clone?repo=xxx)`
- **执行门槛**：🟢 agent 可以直接写

### Live Demo Link（在线演示）
- **做法**：放一个可以直接体验的在线演示链接
- **适用**：有前端界面的项目
- **不适用**：❌ 没有在线版本的项目、❌ 需要本地安装才能运行的工具
- **来源**：[IgorAntun/node-chat](https://github.com/IgorAntun/node-chat) — "Live demo"
- **可抄**：`[![Demo](https://img.shields.io/badge/Try-Demo-blue?style=for-the-badge)](https://demo.example.com)`
- **执行门槛**：🟢 agent 可以直接写

### Playground Link（在线沙盒）
- **做法**：放 CodeSandbox/StackBlitz 链接，浏览器内直接体验
- **适用**：前端库、组件库
- **不适用**：❌ 后端库（浏览器跑不了）、❌ 需要系统权限的工具
- **来源**：[dowjones/react-dropdown-tree-select](https://github.com/dowjones/react-dropdown-tree-select) — "online playground, storybook"
- **可抄**：`[![Playground](https://codesandbox.io/static/img/play-codesandbox.svg)](https://codesandbox.io/s/xxx)`
- **执行门槛**：🟢 agent 可以直接写

### Copy-Paste Ready Config（复制粘贴即用配置）
- **做法**：提供可直接复制粘贴的配置代码，不需要修改
- **适用**：需要配置的工具
- **不适用**：❌ 配置项太多（复制粘贴后改不完）、❌ 配置依赖环境变量（不能直接用）
- **来源**：[haesleinhuepf/bia-bob](https://github.com/haesleinhuepf/bia-bob) — "copy-paste-ready configurations"
- **可抄**：代码块里直接写好完整配置，用户复制就能用
- **执行门槛**：🟢 agent 可以直接写

---

## 信息密度类

### Selected Badges Only（精选 Badge）
- **做法**：只放真正有用的信息 badge，不凑数
- **适用**：所有项目
- **不适用**：❌ 无（这是通用规则）
- **来源**：[feberts/python-game-server](https://github.com/feberts/python-game-server) — "Selected badges that only show relevant information"
- **可抄**：问自己"这个 badge 对用户做决策有帮助吗？"——没有就不放
- **执行门槛**：🟢 agent 可以直接判断

### Concise One-Liner Description（一句话描述）
- **做法**：标题下方一行话说清楚项目是什么
- **适用**：所有项目
- **不适用**：❌ 无（这是通用规则）
- **来源**：[GyulyVGC/sniffnet](https://github.com/GyulyVGC/sniffnet) — "concise one-line description"
- **可抄**：不超过 15 个英文单词
- **执行门槛**：🟢 agent 可以直接写

### App Store Logos（应用商店图标）
- **做法**：展示 App Store / Google Play 下载按钮
- **适用**：移动端应用
- **不适用**：❌ 桌面/CLI 工具（没有应用商店）、❌ Web 应用
- **来源**：[gitpoint/git-point](https://github.com/gitpoint/git-point) — "App Store logos"
- **可抄**：用各商店官方 badge
- **执行门槛**：🟢 agent 可以直接写

### Tabular Download Section（表格下载区）
- **做法**：用表格列出所有平台的下载链接
- **适用**：跨平台工具
- **不适用**：❌ 单平台工具（直接放一个下载链接即可）
- **来源**：[GyulyVGC/sniffnet](https://github.com/GyulyVGC/sniffnet) — "tabular download section with links"
- **可抄**：`| 平台 | 下载 |` 表格
- **执行门槛**：🟢 agent 可以直接写

---

## 代码与文档类

### Mermaid Diagram（Mermaid 架构图）
- **做法**：用 Mermaid 语法画流程图/架构图/序列图，GitHub 原生渲染
- **适用**：需要展示系统架构、数据流、状态机的项目
- **不适用**：❌ 简单工具（一个 ASCII 图够了）、❌ 需要精确比例的工程图
- **来源**：[dutrevis/spark-resources-metrics-plugin](https://github.com/dutrevis/spark-resources-metrics-plugin) — "interactive Mermaid diagram in the Developer section"
- **可抄**：用 ```mermaid 代码块画图，GitHub 直接渲染
- **执行门槛**：🟢 agent 可以直接写 Mermaid 语法

### Multi-Language Docs（多语言文档结构）
- **做法**：为每个支持的编程语言提供独立的代码示例和安装说明
- **适用**：跨语言工具/库
- **不适用**：❌ 单语言项目（没必要）、❌ 语言太多（超过 5 种会变成噪音）
- **来源**：[sebyddd/SDVersion](https://github.com/sebyddd/SDVersion) — "Documentation structuring for multiple programming languages"
- **可抄**：用 Tab 或折叠块组织不同语言的示例
- **执行门槛**：🟢 agent 可以直接写

### Flowchart Overview（流程图概览）
- **做法**：用流程图展示项目的工作原理，替代纯文字描述
- **适用**：有明确处理流程的工具
- **不适用**：❌ 没有流程的静态工具（硬画会牵强）
- **来源**：[themerdev/themer](https://github.com/themerdev/themer) — "Visual description (flowchart) of what the project does"
- **可抄**：用 Mermaid flowchart 或 ASCII 画输入→处理→输出
- **执行门槛**：🟢 agent 可以直接写

### Dogfood in README（README 自身即演示）
- **做法**：README 本身就是项目的输出示例——项目生成 README，README 展示项目能力
- **适用**：文档生成器、模板引擎、代码生成工具
- **不适用**：❌ 非生成类项目（硬做会变成循环引用）
- **来源**：[Hexworks/Zircon](https://github.com/Hexworks/zircon) — "Dogfood in readme"
- **可抄**：在 README 开头注明「本 README 由项目自身生成」
- **执行门槛**：🟡 需要项目本身支持生成 README，agent 只负责格式化

---

## 信任与社区类

### Citation Box（引用框）
- **做法**：在 README 中提供学术引用格式，方便研究者引用
- **适用**：学术项目、有论文的开源工具
- **不适用**：❌ 非学术项目（没有论文可引用）
- **来源**：[Martinsos/edlib](https://github.com/Martinsos/edlib) — "Informative badges (build, version, publication)"
- **可抄**：提供 BibTeX 格式的引用块
- **执行门槛**：🟡 需要用户提供论文信息，agent 负责格式化

### Video Demo（视频演示）
- **做法**：嵌入 YouTube/Bilibili 视频作为项目演示
- **适用**：操作复杂的工具、需要展示完整工作流的项目
- **不适用**：❌ 简单工具（截图够了）、❌ 没有视频的项目
- **来源**：[php-censor/php-censor](https://github.com/php-censor/php-censor) — "video demo"；[PlexRipper/PlexRipper](https://github.com/PlexRipper/PlexRipper) — "demonstration video"
- **可抄**：`[![Demo](https://img.youtube.com/vi/VIDEO_ID/0.jpg)](https://youtu.be/VIDEO_ID)`
- **执行门槛**：🔴 需要录制视频，agent 无法生成。替代方案：用 GIF + 文字步骤

### Changelog Section（更新日志章节）
- **做法**：在 README 中嵌入或链接最近的更新日志
- **适用**：活跃开发的项目、有重大版本更新的项目
- **不适用**：❌ 已停止维护的项目、❌ 稳定无变化的项目
- **来源**：[ryanoasis/nerd-fonts](https://github.com/ryanoasis/nerd-fonts) — "detailed release changelog"；[xnbox/DeepfakeHTTP](https://github.com/xnbox/DeepfakeHTTP) — "Appendices"
- **可抄**：链接到 CHANGELOG.md 或放最近 3 个版本的摘要
- **执行门槛**：🟢 agent 可以从 CHANGELOG.md 提取摘要

### Table Layout Gallery（表格布局画廊）
- **做法**：用 Markdown 表格并排展示多个 GIF/截图，形成画廊效果
- **适用**：功能多的项目、需要展示多个界面的项目
- **不适用**：❌ 功能单一的项目（一张图够了）、❌ 纯 CLI 工具
- **来源**：[yvann-ba/ft_transcendence](https://github.com/yvann-ba/ft_transcendence) — "clear GIF gallery in table layout"
- **可抄**：`| 截图 1 | 截图 2 |` + `| 说明 1 | 说明 2 |`
- **执行门槛**：🟢 agent 可以直接写表格结构，用户替换图片

---

## 模式组合推荐

按项目类型，推荐常用模式组合：

### CLI 工具
- **必须**：Concise One-Liner + Section Links + GIF Demo
- **推荐**：GIF Step-by-Step（安装复杂时）+ FAQ（常见问题多时）
- **可选**：Version Callout（有大版本升级时）
- **避免**：Long-Form Essay、Philosophy Section（CLI 用户想快速上手，不想看长文）

### 库/包
- **必须**：Concise One-Liner + Comparison Table（有替代品时）
- **推荐**：Cognitive Funnel（概念复杂时）+ TL;DR Usage
- **可选**：Certification Table（企业级时）+ FAQ
- **避免**：Feature GIF Gallery（库没有 GUI，GIF 没意义）

### 框架
- **必须**：Philosophy Section + Contributor Avatar Wall
- **推荐**：Long-Form Essay（理念重要时）+ Star Growth Chart
- **可选**：Dynamic Roadmap（活跃开发时）+ Social Links
- **避免**：Benchmark Chart（框架的价值不是速度）

### Web 应用
- **必须**：Screenshot Gallery + Deploy Button + Live Demo Link
- **推荐**：Feature GIF Gallery + Tabular Download Section
- **可选**：Auto-Generated README（合集类时）
- **避免**：Long-Form Essay（Web 应用用户想看截图，不想看文章）

### 教学项目
- **必须**：Complete File List + Tutorial GIF Sequence
- **推荐**：Cognitive Funnel + FAQ
- **可选**：Copy-Paste Ready Config
- **避免**：Benchmark Chart、Certification Table（教学项目不关心这些）
