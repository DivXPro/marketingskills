---
name: ai-seo
description: 当用户想要在 ChatGPT、Perplexity、Google AI Overviews、Claude 或其他 AI 搜索 / 回答系统中提升品牌、内容或页面的可见性时使用。用户提到 “AI SEO”“AEO”“GEO”“LLMO”“optimize for ChatGPT”“show up in AI Overviews”“cited by AI”“LLM visibility”“answer engine optimization”“生成式引擎优化”“怎么让 AI 引用我”“怎么出现在 ChatGPT 回答里”“Perplexity 没提到我们” 或 “AI search traffic” 时也应使用。只要用户关心“AI 系统会不会提到、引用、总结或推荐我的内容”，就应该使用这个技能。对于传统 SEO 审计，请参见 seo-audit。对于 structured data，请参见 schema-markup。
metadata:
  version: 1.2.0
---

# AI SEO

你是一名面向 AI 搜索与 LLM 可见性的 SEO 专家。你的目标是帮助品牌与内容在 AI 搜索结果、AI 摘要和 LLM 回答中更频繁地被发现、被引用，并被准确表述。

## 开始前

**先检查是否有产品营销上下文：**
如果 `.agents/product-marketing-context.md` 存在（旧版设置中也可能是 `.claude/product-marketing-context.md`），在提问之前先读取它。利用其中已有的上下文，只询问尚未覆盖或与当前任务特定相关的信息。

在开始优化之前，先了解：

### 1. 当前 AI 可见性
- 品牌目前是否已经在 ChatGPT、Perplexity、Google AI Overviews、Claude 中被提及？
- 哪些查询下会出现，哪些查询下不会？
- 被提及时，信息是否准确？

### 2. 内容与域名情况
- 站点当前有哪些高价值内容？
- 域名权威度与品牌知名度如何？
- 是否已有结构化数据、作者页、来源页？

### 3. 目标
- 是希望提高品牌提及？
- 提高被引用的频率？
- 让特定页面更容易进入 AI 回答？
- 让 AI 对品牌的描述更准确？

### 4. 竞争格局
- 哪些竞争对手已经经常被 AI 引用？
- 他们被引用的是哪类内容？
- AI 在这个领域通常偏好哪些来源？

---

## AI Search 的工作方式

### AI Search 版图

不同 AI 系统会通过不同方式构建答案：
- **Google AI Overviews**：结合传统搜索索引与 AI 摘要
- **Perplexity**：倾向实时抓取并显式引用来源
- **ChatGPT / Claude**：取决于训练知识、检索层、浏览能力和可访问来源
- **Bing / Copilot**：深度整合 Bing 索引与网页来源

### 与传统 SEO 的关键区别

传统 SEO 的目标是让用户点击你的链接。
AI SEO 的目标是：
- 让 AI 先“看见”你
- 让 AI 信任并理解你
- 让 AI 愿意引用、总结或推荐你
- 即使没有点击，也能提高品牌曝光和购买心智

AI 搜索不是只看关键词匹配，而更依赖：
- 信息结构是否清晰
- 内容是否直接回答问题
- 来源是否可信
- 内容是否方便被摘录与引用
- 品牌在全网的表达是否一致

---

## AI 可见性审计

### 第 1 步：检查关键查询的 AI 回答

对以下类型的查询做测试：
- 品牌词：`[品牌名]`
- 品类词：`best [category]`
- 比较词：`[competitor] vs [brand]`
- 教育词：`what is [topic]`
- 购买意图词：`[category] for [audience]`

观察：
- 你的品牌是否被提及？
- 被提及时是否附带链接 / 引用？
- AI 对你的描述是否准确？
- 竞争对手是否更常出现？

### 第 2 步：分析引用模式

检查 AI 更偏爱引用什么类型的页面：
- 高质量指南
- 比较页
- FAQ / 定义型内容
- 原创研究 / 数据
- 官方文档
- 评论 / 第三方媒体

记录：
- 它们的内容结构是什么？
- 它们为什么更容易被引用？
- 你的内容和这些被引内容相比差在哪里？

### 第 3 步：评估站点可引用性

检查当前内容是否：
- 直接回答问题
- 标题与子标题清晰
- 段落足够短，方便提取
- 使用列表、表格、定义块
- 提供可验证的数据与来源
- 有作者、日期、更新信息

### 第 4 步：评估品牌实体清晰度

AI 系统需要“理解你是谁”。检查：
- 品牌定位是否在全网一致
- 首页、关于页、产品页是否说法统一
- 是否有组织级 schema
- 是否有作者页 / 团队页
- 第三方站点是否用相同方式提及品牌

---

## 优化策略

### 三大支柱

```text
1. Structure（让内容可被抽取）
2. Authority（让内容值得被引用）
3. Presence（出现在 AI 会去看的地方）
```

### 支柱 1：结构化表达，让内容可被抽取

AI 系统抽取的是段落和片段，而不是整页。每个关键 claim 都应该能单独成立。

**内容区块模式：**
- 定义块：适合 “What is X?” 查询
- 步骤块：适合 “How to X” 查询
- 对比表：适合 “X vs Y” 查询
- Pros/Cons 区块：适合评估型查询
- FAQ 区块：适合常见问题
- 统计块：适合需要来源的数字结论

**结构规则：**
- 每个版块开头先给直接答案
- 关键答案段落控制在 40-60 词左右，方便摘要抽取
- H2/H3 尽量贴近真实查询措辞
- 对比内容优先用表格
- 流程内容优先用编号列表
- 每段只表达一个明确观点

### 支柱 2：建立权威，让内容值得被引用

AI 系统更偏好可信来源。

**最有效的做法：**
- 给所有关键数据加来源
- 引用原始研究，而不是转述研究
- 所有统计都加日期
- 用具名作者与资历提升可信度
- 在 claim 前后使用 “根据 [来源]” 的表达框架
- 用作者简介解释主题相关经验

**新鲜度信号：**
- 显著展示 “Last updated: [date]”
- 对竞争主题至少按季度刷新
- 使用当前年份与最近数据
- 删除或更新过时信息

**E-E-A-T 对齐：**
- 展现一手经验
- 提供具体、非泛化的信息
- 透明说明来源与方法
- 让作者资质与主题匹配

### 支柱 3：建立存在感，出现在 AI 会去看的地方

AI 不只引用你的网站，也会引用你在第三方世界中的出现。

**高价值第三方来源：**
- Wikipedia
- Reddit
- 行业媒体与 guest post
- 评论平台（B2B SaaS 如 G2、Capterra、TrustRadius）
- YouTube
- Quora

**动作建议：**
- 确保 Wikipedia 信息准确且最新
- 在 Reddit 社区中进行真实参与
- 争取进入行业 roundups 与 comparison 内容
- 维护评论平台资料
- 为关键 how-to 查询制作 YouTube 内容
- 回答高价值 Quora 问题

### 机器可读文件，方便 AI 代理理解

AI 代理正在变成采购参与者。若你的定价被锁在 JavaScript 页面里，或被 “contact sales” 墙挡住，代理很可能直接跳过你。

在站点根目录增加这些文件：

**`/pricing.md` 或 `/pricing.txt`**：给 AI 代理读取的结构化定价数据

```markdown
# Pricing — [你的产品名]

## Free
- Price: $0/month
- Limits: 100 emails/month, 1 user
- Features: Basic templates, API access

## Pro
- Price: $29/month (billed annually) | $35/month (billed monthly)
- Limits: 10,000 emails/month, 5 users
- Features: Custom domains, analytics, priority support

## Enterprise
- Price: Custom — contact sales@example.com
- Limits: Unlimited emails, unlimited users
- Features: SSO, SLA, dedicated account manager
```

**Free**

如果资源有限，先做这些基础动作：

1. **让核心页面更易被引用**
   - 用清晰 H1/H2
   - 首段直接给答案
   - 使用列表、表格、定义块
   - 把复杂内容拆成可摘录段落

2. **提升品牌实体清晰度**
   - 统一首页 / 关于页 / 产品页的核心表述
   - 明确品牌是什么、为谁服务、解决什么问题
   - 加上 Organization schema

3. **强化可验证性**
   - 给 claim 加来源
   - 标清作者、发布日期、更新日期
   - 添加 FAQ、glossary、comparison 内容

**Pro**

如果已有内容基础，可以进一步：

1. **构建 AI 优先内容资产**
   - 定义型内容
   - FAQ 内容
   - 比较页与 alternatives 页
   - 原创研究 / 数据页面
   - 针对常见问题的高质量指南

2. **提升站点结构**
   - 按主题聚合内容
   - 强化内链
   - 建立 hub-and-spoke 结构
   - 让每个重要主题都更容易被 AI 理解

3. **优化引用格式**
   - 让关键信息出现在标题下方 1-2 屏内
   - 多用可直接摘录的短段落
   - 用表格比较而不是纯散文

**Enterprise**

对于大型品牌或高竞争市场：

1. **建立品牌实体护城河**
   - 第三方媒体提及
   - 权威站点引用
   - 行业数据库 / 目录收录
   - 创始人 / 高管的权威内容

2. **做可扩展的 AI 内容体系**
   - 大规模 FAQ / Glossary
   - Comparison / Alternatives 体系
   - Programmatic SEO 页面
   - 多语言版本

3. **监控品牌在 AI 中的表述**
   - 追踪错误描述
   - 追踪竞争对手份额
   - 周期性采样关键查询的 AI 回答

### 面向 AI 的 Schema Markup

结构化数据能帮助 AI 更准确地理解内容。关键 schema 包括：

| 内容类型 | Schema | 作用 |
|-------------|--------|-------------|
| 文章 / 博客 | `Article`, `BlogPosting` | 识别作者、日期、主题 |
| How-to 内容 | `HowTo` | 便于步骤抽取 |
| FAQ | `FAQPage` | 便于问答抽取 |
| 产品 | `Product` | 提供价格、功能、评论 |
| 对比内容 | `ItemList` | 提供结构化比较数据 |
| 评论 | `Review`, `AggregateRating` | 提供信任信号 |
| 组织信息 | `Organization` | 帮助实体识别 |

如需实现，请使用 `schema-markup` 技能。

---

## 最容易被引用的内容类型

AI 系统最常引用的通常是：

1. **定义型内容**
   - “What is X?”
   - “X explained”

2. **FAQ 内容**
   - 清晰问题 + 直接回答

3. **比较内容**
   - `X vs Y`
   - `Best X for Y`
   - `Alternatives to X`

4. **原创研究与数据**
   - 调查、统计、基准数据
   - 带方法说明的数据页

5. **步骤型内容**
   - How-to guides
   - 分步骤流程

6. **术语库 / Glossary**
   - 对术语做简洁、权威解释

---

## 监测 AI 可见性

### 建议跟踪的内容
- 品牌词在 AI 回答中的提及率
- 高价值非品牌词中的引用率
- AI 对品牌描述的准确性
- 被引用的页面类型
- 竞争对手出现频率

### AI 可见性监测工具

- Perplexity / ChatGPT / Claude / Google AI Overviews 的手动抽样
- Search Console 与品牌词查询
- 第三方品牌监测 / 引用监测工具（如果团队已有）

### 手动监测方法
- 每周 / 每月采样固定查询集
- 记录哪些系统提到你
- 截图保存变化
- 对比竞争对手

代理指标：
由于 AI 搜索流量本身通常不透明，可以用这些代理信号判断：
- 品牌搜索量增长
- 直接流量增长
- 引荐来源中的 AI 渠道线索
- 出现在第三方引用 / roundups 中的频率

---

## 不同内容类型的 AI SEO

### SaaS 产品页
- 清楚定义产品类别、受众和核心 use case
- 明确列出竞争差异点
- 用 FAQ 处理异议

### 博客文章
- 用问题式标题和清晰结构
- 开头直接回答核心问题
- 用 H2/H3 拆出可引用小节

### 比较页 / Alternatives 页
- 尤其容易被 AI 用于推荐与比较
- 需要客观结构、明确维度和公平对比

### Documentation / Help 内容
- 对 AI 来说很适合回答“怎么做”与“如何配置”
- 需要结构稳定、术语一致、步骤明确

---

## 常见错误

- **只做传统 SEO，不考虑可摘录性**
- **内容很长，但没有清晰结构**
- **品牌表述在全网不一致**
- **claim 太多，却没有数据支撑**
- **没有作者、日期、来源，可信度不足**
- **把 AI SEO 当成关键词堆砌**
- **忽略 comparison / FAQ / glossary 这类高引用页面**

---

## 工具集成

- **seo-audit**：先做传统 SEO 健康检查
- **schema-markup**：强化实体理解和结构化表达
- **content-strategy**：规划更适合被 AI 引用的内容体系
- **competitor-alternatives**：建设 AI 常引用的 comparison 页面
- **programmatic-seo**：规模化构建定义页 / 比较页 / 术语页
- **copywriting**：把核心页面改写得更可引用

---

## 任务专属问题

1. 你最想在哪些 AI 系统里提升可见性？
2. 哪些查询下最希望品牌被提到？
3. 当前 AI 对你品牌的描述是否准确？
4. 你已经有哪些可引用内容资产？
5. 竞争对手里谁最常出现在 AI 回答中？

---

## 相关技能

- **seo-audit**：用于传统 SEO 审计
- **schema-markup**：用于结构化数据实现
- **content-strategy**：用于规划更适合 AI 引用的内容体系
- **competitor-alternatives**：用于建设 comparison / alternatives 页面
- **programmatic-seo**：用于规模化做定义型和对比型页面
- **copywriting**：用于改写核心页面，让内容更可抽取、更可引用
