# 面向 AI Agent 的 Marketing Skills

这是一个面向营销任务的 AI Agent Skills 仓库，适合技术营销人、独立开发者、创始人，以及希望让 AI 编码助手参与增长工作的团队。它覆盖转化优化、文案、SEO、埋点分析、广告、定价、推荐增长、RevOps 等常见营销场景。

可用于 Claude Code、OpenAI Codex、Cursor、Windsurf，以及任何支持 [Agent Skills 规范](https://agentskills.io) 的 agent。

项目由 [Corey Haines](https://corey.co?ref=marketingskills) 创建。需要转化优化、落地页或增长策略支持，可以了解 [Conversion Factory](https://conversionfactory.co?ref=marketingskills)。想系统学习营销，可以订阅 [Swipe Files](https://swipefiles.com?ref=marketingskills)。如果你想要一个会用这些技能的自主 AI 营销助手，也可以看看 [Magister](https://magistermarketing.com?ref=marketingskills)。

如果你刚开始接触终端和 AI 编码助手，可以先看配套指南 [Coding for Marketers](https://codingformarketers.com?ref=marketingskills)。

欢迎贡献。如果你发现某个 skill 可以改进，或者有新 skill 想加入，欢迎提 PR。

如果你遇到问题，也可以在 GitHub 上 [提交 issue](https://github.com/coreyhaines31/marketingskills/issues)。

## 什么是 Skills？

Skills 本质上是 Markdown 文档，它们给 AI agent 提供某一类任务的专业知识、工作流、判断框架和输出格式。

当你把这些 skills 放进自己的项目后，agent 在处理营销任务时，就能更容易识别当前问题属于哪一类，并自动使用更合适的方法。

## Skills 如何协作

这些 skills 之间不是孤立的。它们会互相引用，并且依赖共享上下文。

其中 `product-marketing-context` 是整个体系的基础：其他大多数营销技能在开始工作前，都会优先读取它，以理解你的产品、受众、定位和差异化信息。

```text
                            ┌──────────────────────────────────────┐
                            │      product-marketing-context       │
                            │      （其他技能会优先读取它）         │
                            └──────────────────┬───────────────────┘
                                               │
    ┌──────────────┬─────────────┬─────────────┼─────────────┬──────────────┬──────────────┐
    ▼              ▼             ▼             ▼             ▼              ▼              ▼
┌──────────┐ ┌──────────┐ ┌──────────┐ ┌────────────┐ ┌──────────┐ ┌─────────────┐ ┌───────────┐
│ SEO &    │ │   CRO    │ │ Content  │ │ Paid &     │ │ Growth & │ │ Sales &     │ │ Strategy  │
│ Content  │ │          │ │ & Copy   │ │ Measurement│ │ Retention│ │ GTM          │ │           │
├──────────┤ ├──────────┤ ├──────────┤ ├────────────┤ ├──────────┤ ├─────────────┤ ├───────────┤
│seo-audit │ │page-cro  │ │copywrite │ │paid-ads    │ │referral  │ │revops       │ │mktg-ideas │
│ai-seo    │ │signup-cro│ │copy-edit │ │ad-creative │ │free-tool │ │sales-enable │ │mktg-psych │
│site-arch │ │onboarding│ │cold-email│ │ab-test     │ │churn-    │ │launch       │ │customer-  │
│programm  │ │form-cro  │ │email-seq │ │analytics   │ │prevention│ │pricing      │ │research   │
│schema    │ │popup-cro │ │social    │ │            │ │          │ │competitor   │ │           │
│content   │ │paywall   │ │          │ │            │ │          │ │             │ │           │
└────┬─────┘ └────┬─────┘ └────┬─────┘ └─────┬──────┘ └────┬─────┘ └──────┬──────┘ └─────┬─────┘
     │            │            │              │             │              │              │
     └────────────┴─────┬──────┴──────────────┴─────────────┴──────────────┴──────────────┘
                        │
         常见交叉引用关系：
           copywriting ↔ page-cro ↔ ab-test-setup
           revops ↔ sales-enablement ↔ cold-email
           seo-audit ↔ schema-markup ↔ ai-seo
           customer-research → copywriting, page-cro, competitor-alternatives
```

更完整的依赖关系，请查看每个 skill 中的 `Related Skills` 小节，或对应的 `SKILL.CN.md`。

## 可用 Skills

下表列出当前仓库中的主要技能。技能目录名保持英文，方便直接安装和调用；描述使用中文，方便快速理解适用场景。

| Skill | 中文说明 |
|-------|----------|
| [ab-test-setup](skills/ab-test-setup/) | 当用户想规划、设计或评估 A/B 测试、分流实验或增长实验体系时使用。适合需要明确假设、指标、样本量、测试时长和结果判断的人。页面转化思路看 `page-cro`，埋点与测量实现看 `analytics-tracking`。 |
| [ad-creative](skills/ad-creative/) | 当用户想生成、迭代或扩展广告创意时使用，包括标题、描述、主文案、图片/视频创意方向与测试角度。适合投放前构思素材、批量产出变体或优化广告信息传达。 |
| [ai-seo](skills/ai-seo/) | 当用户想让内容更容易被 AI 搜索、LLM 回答或智能摘要系统引用时使用。适合优化内容结构、可引用性、答案格式和面向 AI 的可发现性。 |
| [analytics-tracking](skills/analytics-tracking/) | 当用户想搭建、修正或审查分析追踪方案时使用，包括事件命名、漏斗、归因、转化指标和测量质量。适合在实验、页面优化和增长动作前补齐数据基础。 |
| [aso-audit](skills/aso-audit/) | 当用户想审查或优化 App Store / Google Play 上架页时使用。适合处理标题、副标题、关键词、截图、评论和转化表现等 ASO 问题。 |
| [churn-prevention](skills/churn-prevention/) | 当用户想降低流失、优化取消流程、设计保留方案或恢复失败扣款时使用。适合围绕留存、挽回和用户价值延长做系统性设计。 |
| [cold-email](skills/cold-email/) | 当用户想撰写 B2B 冷启动外联邮件及跟进序列时使用。适合围绕目标客户、切入点、个性化和回复率来设计外联文案。 |
| [community-marketing](skills/community-marketing/) | 当用户想建立、运营或利用在线社区推动增长和品牌黏性时使用。适合社群定位、运营节奏、内容机制和社区到业务的转化设计。 |
| [competitor-alternatives](skills/competitor-alternatives/) | 当用户想创建竞品对比页、替代页或“某某替代品”内容时使用。适合兼顾 SEO 获客、销售教育和差异化表达。 |
| [content-strategy](skills/content-strategy/) | 当用户想规划内容方向、确定主题优先级或搭建内容体系时使用。适合做选题框架、分发规划和长期内容节奏设计。 |
| [copy-editing](skills/copy-editing/) | 当用户已经有现成文案，想审阅、精修、提高清晰度和转化力时使用。适合做逐段修改、语气统一、逻辑压缩和问题标注。 |
| [copywriting](skills/copywriting/) | 当用户想为首页、落地页、定价页、功能页、关于页或产品页撰写或重写营销文案时使用。适合处理价值主张、标题、CTA、版块结构和说服逻辑。 |
| [customer-research](skills/customer-research/) | 当用户想开展、整理或提炼客户研究时使用。适合访谈设计、反馈归纳、用户语言提取、痛点洞察与定位输入。 |
| [email-sequence](skills/email-sequence/) | 当用户想创建或优化欢迎邮件、滴灌邮件、生命周期邮件或自动化邮件流时使用。适合围绕目标动作、节奏、分层和转化链路进行设计。 |
| [form-cro](skills/form-cro/) | 当用户想优化非注册类表单时使用，包括留资表单、联系表单、申请表单和预约表单。适合降低摩擦、提高提交率并改善线索质量。 |
| [free-tool-strategy](skills/free-tool-strategy/) | 当用户想规划、评估或构建用于营销获客的免费工具时使用。适合考虑 SEO 价值、线索获取、功能边界和工具与主产品的衔接方式。 |
| [launch-strategy](skills/launch-strategy/) | 当用户想规划产品发布、功能上线或对外公告节奏时使用。适合梳理受众、信息层次、渠道编排和发布时间线。 |
| [lead-magnets](skills/lead-magnets/) | 当用户想创建、优化或重新定位 lead magnet 时使用。适合为邮件获客设计下载物、模板、清单、课程或小工具等交换型内容。 |
| [marketing-ideas](skills/marketing-ideas/) | 当用户需要新的营销点子、增长灵感或策略方向时使用。适合围绕 SaaS 或软件产品快速生成可执行的营销方向。 |
| [marketing-psychology](skills/marketing-psychology/) | 当用户想把心理学原则、行为科学或认知偏差应用到营销里时使用。适合优化说服机制、决策触发和信息表达方式。 |
| [onboarding-cro](skills/onboarding-cro/) | 当用户想优化注册后的 onboarding、激活路径、首次使用体验或价值到达速度时使用。适合提升激活率、降低流失并缩短 time-to-value。 |
| [page-cro](skills/page-cro/) | 当用户想提升首页、落地页、功能页或其他营销页面的转化时使用。适合做页面诊断、问题优先级排序、改版建议和测试想法。 |
| [paid-ads](skills/paid-ads/) | 当用户想规划、优化或审查 Google Ads、Meta、LinkedIn、X 等付费广告时使用。适合处理投放结构、创意方向、落地页匹配和预算判断。 |
| [paywall-upgrade-cro](skills/paywall-upgrade-cro/) | 当用户想优化应用内 paywall、升级页、功能限制提示或 upsell 流程时使用。适合提高升级转化，同时控制负面体验。 |
| [popup-cro](skills/popup-cro/) | 当用户想创建或优化弹窗、模态框、侧滑层或横幅时使用。适合平衡打断成本与转化收益，设计触发时机、文案和优惠机制。 |
| [pricing-strategy](skills/pricing-strategy/) | 当用户想做定价、套餐设计、付费层级或变现策略决策时使用。适合梳理价值锚点、包装逻辑、版本区别和价格测试方向。 |
| [product-marketing-context](skills/product-marketing-context/) | 当用户想建立或更新产品营销上下文文档时使用。它会沉淀产品、受众、定位、差异化和客户语言，供其他营销技能优先读取，减少重复解释。 |
| [programmatic-seo](skills/programmatic-seo/) | 当用户想基于模板和数据批量生成 SEO 页面时使用。适合评估页面价值、数据来源、模板结构、内链和规模化风险。 |
| [referral-program](skills/referral-program/) | 当用户想设计、优化或分析推荐计划、邀请奖励或 affiliate 机制时使用。适合处理激励结构、分享触发点、追踪指标和增长回路。 |
| [revops](skills/revops/) | 当用户想梳理收入团队流程、线索生命周期、评分、路由、CRM 自动化或营销到销售交接时使用。适合建立可测量、可执行的 RevOps 体系。 |
| [sales-enablement](skills/sales-enablement/) | 当用户想制作销售 deck、one-pager、异议处理文档、ROI 计算器、demo talk track 或销售素材时使用。适合让销售团队更容易讲清价值并推进成交。 |
| [schema-markup](skills/schema-markup/) | 当用户想添加、修复或优化网站 schema markup 时使用。适合实现 JSON-LD、选择 schema 类型、校验和排查 rich results 问题。 |
| [seo-audit](skills/seo-audit/) | 当用户想诊断网站 SEO 问题、做系统性审查或制定修复优先级时使用。适合从抓取、索引、页面优化、内容质量和站点结构等维度给出行动建议。 |
| [signup-flow-cro](skills/signup-flow-cro/) | 当用户想优化注册、开户、试用激活或账号创建流程时使用。适合减少字段摩擦、提升完成率、优化验证体验并设计测试方案。 |
| [site-architecture](skills/site-architecture/) | 当用户想规划、重组或可视化网站的信息架构时使用。适合页面层级、导航、URL 结构、内链和 sitemap 设计。 |
| [social-content](skills/social-content/) | 当用户想创建、安排或优化 LinkedIn、X、Instagram 等社交内容时使用。适合内容支柱、钩子、复用机制、发布节奏和互动策略设计。 |

## 安装方式

### 方式 1：CLI 安装（推荐）

使用 [npx skills](https://github.com/vercel-labs/skills) 直接安装：

```bash
# 安装全部 skills
npx skills add coreyhaines31/marketingskills

# 只安装指定 skills
npx skills add coreyhaines31/marketingskills --skill page-cro copywriting

# 查看可安装的 skills
npx skills add coreyhaines31/marketingskills --list
```

它会自动安装到 `.agents/skills/` 目录，并为 Claude Code 兼容场景建立到 `.claude/skills/` 的链接。

### 方式 2：Claude Code 插件安装

通过 Claude Code 内置插件机制安装：

```bash
# 添加 marketplace
/plugin marketplace add coreyhaines31/marketingskills

# 安装全部 marketing skills
/plugin install marketing-skills
```

### 方式 3：克隆并复制

如果你想把整个仓库拉下来再手动复制 skills：

```bash
git clone https://github.com/coreyhaines31/marketingskills.git
cp -r marketingskills/skills/* .agents/skills/
```

### 方式 4：Git Submodule

如果你想更方便地跟踪后续更新，可以作为 submodule 引入：

```bash
git submodule add https://github.com/coreyhaines31/marketingskills.git .agents/marketingskills
```

然后从 `.agents/marketingskills/skills/` 读取或引用技能。

### 方式 5：Fork 后定制

如果你希望对技能做较多改写：

1. Fork 本仓库
2. 按你的业务场景定制 skills
3. 在自己的项目里克隆你的 fork

### 方式 6：SkillKit（多 Agent）

如果你希望在 Claude Code、Cursor、Copilot 等多个 agent 工具里复用同一套技能，可以使用 [SkillKit](https://github.com/rohitg00/skillkit)：

```bash
# 安装全部 skills
npx skillkit install coreyhaines31/marketingskills

# 安装指定 skills
npx skillkit install coreyhaines31/marketingskills --skill page-cro copywriting

# 查看可安装的 skills
npx skillkit install coreyhaines31/marketingskills --list
```

## 从 v1.0 升级

新版本把产品营销上下文文件的默认路径从 `.claude/` 切换到了 `.agents/`。

如果你之前已经在 `.claude/` 下维护过旧文件，可以迁移到新位置：

```bash
mkdir -p .agents
mv .claude/product-marketing-context.md .agents/product-marketing-context.md
```

即使你暂时不迁移，大多数技能仍然会把 `.claude/` 作为回退路径，所以不会立刻失效。

## 使用方式

安装完成后，你只需要像平时一样向 agent 提出营销任务即可：

```text
"帮我优化这个落地页的转化"
→ 使用 page-cro

"给我的 SaaS 写首页文案"
→ 使用 copywriting

"帮我给注册流程补 GA4 埋点"
→ 使用 analytics-tracking

"写一个 5 封的欢迎邮件序列"
→ 使用 email-sequence
```

某些环境下，你也可以直接显式调用 skill：

```text
/page-cro
/email-sequence
/seo-audit
```

## 技能分类

### 转化优化

- `page-cro`：适合首页、落地页、功能页等营销页面
- `signup-flow-cro`：适合注册、开户、试用激活流程
- `onboarding-cro`：适合注册后的激活与引导
- `form-cro`：适合留资、联系、申请类表单
- `popup-cro`：适合弹窗、模态框、覆盖层
- `paywall-upgrade-cro`：适合应用内升级时刻与功能限制提示

### 内容与文案

- `copywriting`：营销页面文案写作
- `copy-editing`：现有文案审阅、精修与优化
- `cold-email`：B2B 冷启动外联邮件与跟进
- `email-sequence`：自动化邮件流与生命周期邮件
- `social-content`：社交媒体内容规划与优化

### SEO 与发现

- `seo-audit`：技术 SEO 与站内 SEO 审计
- `ai-seo`：面向 AI 搜索与大模型引用的优化
- `programmatic-seo`：批量生成 SEO 页面
- `site-architecture`：页面层级、导航与 URL 结构
- `competitor-alternatives`：竞品对比页与替代页
- `schema-markup`：结构化数据与 schema markup

### 付费流量与分发

- `paid-ads`：Google、Meta、LinkedIn、X 等广告投放
- `ad-creative`：广告创意批量生成与迭代
- `social-content`：社交内容分发与节奏管理

### 测量与测试

- `analytics-tracking`：事件埋点与测量体系
- `ab-test-setup`：实验设计、假设、指标与样本量

### 留存

- `churn-prevention`：取消流程、保留优惠、扣款恢复

### 增长工程

- `free-tool-strategy`：免费工具、计算器、互动工具
- `referral-program`：推荐计划与联盟计划

### 策略与变现

- `marketing-ideas`：营销点子与增长灵感
- `marketing-psychology`：营销心理学与行为科学
- `launch-strategy`：产品发布与公告节奏
- `pricing-strategy`：定价、包装和商业化设计

### 销售与 RevOps

- `revops`：线索生命周期、评分、路由与管道管理
- `sales-enablement`：销售 deck、one-pager、异议处理与 demo 脚本

## 贡献

如果你发现某个 skill 可以做得更好，或者你想补充新的营销技能，欢迎提交 PR 或 issue。

添加或改进技能前，建议先阅读 [CONTRIBUTING.md](CONTRIBUTING.md)。

## 许可证

[MIT](LICENSE) - 你可以按自己的需要使用这些内容。
