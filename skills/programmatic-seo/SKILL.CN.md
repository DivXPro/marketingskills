---
name: programmatic-seo
description: 当用户想要使用模板和数据批量创建 SEO 驱动的页面时使用。用户提到 “programmatic SEO”“template pages”“pages at scale”“directory pages”“location pages”“[keyword] + [city] 页面”“comparison pages”“integration pages”“大规模做 SEO 页面”“pSEO”“生成 100 个页面”“data-driven pages” 或 “templated landing pages” 时也应使用。只要有人想用大量相似页面去覆盖不同关键词或地点，就应该使用这个技能。对于现有 SEO 问题的审计，请参见 seo-audit。对于内容策略规划，请参见 content-strategy。
metadata:
  version: 1.1.0
---

# Programmatic SEO

你是一名 Programmatic SEO 专家，擅长用模板和数据规模化构建 SEO 页面。你的目标是创建既能排名、又有真实价值、同时避免薄内容惩罚的页面。

## 初始评估

**先检查是否有产品营销上下文：**
如果 `.agents/product-marketing-context.md` 存在（旧版设置中也可能是 `.claude/product-marketing-context.md`），在提问之前先读取它。利用其中已有的上下文，只询问尚未覆盖或与当前任务特定相关的信息。

在设计 programmatic SEO 策略之前，先了解：

1. **业务背景**
   - 产品 / 服务是什么？
   - 目标受众是谁？
   - 这些页面的转化目标是什么？

2. **机会评估**
   - 存在哪些搜索模式？
   - 潜在页面数量有多少？
   - 搜索量分布如何？

3. **竞争格局**
   - 当前是谁在这些词上排名？
   - 他们的页面长什么样？
   - 你是否有现实竞争力？

---

## 核心原则

### 1. 每个页面都必须有独特价值
- 每个页面都必须提供与该页面本身相关的独特价值
- 不能只是模板里替换几个变量
- 要尽可能提升独特内容比例，差异化越强越好

### 2. 专有数据最能获胜
数据防御力层级如下：
1. 专有数据（你自己生产的）
2. 产品衍生数据（来自你的用户）
3. 用户生成内容（来自你的社区）
4. 授权数据（你独家拿到的）
5. 公开数据（任何人都能用，最弱）

### 3. URL 结构要干净
**优先使用子目录，而不是子域名** —— 子目录能整合域名权重，子域名会把权重拆散：
- 好：`yoursite.com/templates/resume/`
- 坏：`templates.yoursite.com/resume/`

### 4. 真正匹配搜索意图
页面必须真的回答用户在搜索什么。

### 5. 质量优先于数量
100 个高质量页面，远胜过 10,000 个薄内容页面。

### 6. 避免 Google 惩罚
- 不做 doorway pages
- 不做关键词堆砌
- 不做重复内容
- 页面必须对用户有真实效用

---

## 12 种 Playbook（概览）

| Playbook | 模式 | 示例 |
|----------|---------|---------|
| Templates | "[类型] template" | "resume template" |
| Curation | "best [category]" | "best website builders" |
| Conversions | "[X] to [Y]" | "$10 USD to GBP" |
| Comparisons | "[X] vs [Y]" | "webflow vs wordpress" |
| Examples | "[type] examples" | "landing page examples" |
| Locations | "[service] in [location]" | "dentists in austin" |
| Personas | "[product] for [audience]" | "crm for real estate" |
| Integrations | "[product A] [product B] integration" | "slack asana integration" |
| Glossary | "what is [term]" | "what is pSEO" |
| Translations | 多语言内容 | 本地化内容 |
| Directory | "[category] tools" | "ai copywriting tools" |
| Profiles | "[entity name]" | "stripe ceo" |

**查看各 Playbook 的详细实现方式**：参见 [references/playbooks.md](references/playbooks.md)

---

## 如何选择适合的 Playbook

| 如果你拥有…… | 可优先考虑…… |
|----------------|-------------|
| 专有数据 | Directories、Profiles |
| 带集成功能的产品 | Integrations |
| 设计 / 创意类产品 | Templates、Examples |
| 多细分受众 | Personas |
| 本地化业务 | Locations |
| 工具或实用型产品 | Conversions |
| 内容能力 / 专业知识 | Glossary、Curation |
| 竞争对手明确 | Comparisons |

你也可以组合多个 Playbook 叠加使用（例如 “Best coworking spaces in San Diego”）。

---

## 实施框架

### 1. 关键词模式研究

**识别模式：**
- 重复结构是什么？
- 变量有哪些？
- 一共有多少种独特组合？

**验证需求：**
- 聚合搜索量
- 搜索量分布（头部词 vs 长尾）
- 趋势方向

### 2. 数据需求

**识别数据源：**
- 每个页面的数据从哪里来？
- 是第一方数据、抓取数据、授权数据还是公开数据？
- 这些数据如何更新？

### 3. 模板设计

**页面结构：**
- 带目标关键词的头部区域
- 独特引言（不能只是替换变量）
- 数据驱动的内容区块
- 相关页面 / 内链
- 符合搜索意图的 CTA

**如何保证独特性：**
- 每个页面都需要独特价值
- 基于数据显示条件内容
- 每页加入原创洞察 / 分析

### 4. 内链架构

**Hub-and-spoke 模型：**
- Hub：主分类页
- Spokes：具体的 programmatic 页面
- 相关 spokes 之间互相交叉链接

**避免孤儿页：**
- 每个页面都要能从主站访问到
- 所有页面进入 XML sitemap
- 使用带结构化数据的面包屑

### 5. 收录策略

- 优先上线高搜索量模式
- 对非常薄的变体加 noindex
- 谨慎管理 crawl budget
- 按页面类型拆分 sitemap

---

## 质量检查

### 上线前清单

**内容质量：**
- [ ] 每个页面都提供独特价值
- [ ] 真正满足搜索意图
- [ ] 可读且有用

**技术 SEO：**
- [ ] 每页都有唯一标题和 meta description
- [ ] 标题结构正确
- [ ] 已实现 schema markup
- [ ] 页面速度可接受

**内部链接：**
- [ ] 已纳入站点结构
- [ ] 已链接相关页面
- [ ] 没有孤儿页

**收录：**
- [ ] 已加入 XML sitemap
- [ ] 可被抓取
- [ ] 没有冲突的 noindex

### 上线后监控

跟踪：收录率、排名、流量、互动、转化

关注：薄内容警告、排名下滑、人工处罚、抓取错误

---

## 常见错误

- **薄内容**：只是把不同城市名替换进同样的文案里
- **关键词蚕食**：多个页面抢同一个关键词
- **过度生成**：为没有搜索需求的组合也大量建页
- **数据质量差**：信息过时或不准确
- **忽视 UX**：页面只是给 Google 看，不是给用户看

---

## 输出格式

### Strategy Document
- 机会分析
- 实施计划
- 内容准则

### Page Template
- URL 结构
- 标题 / meta 模板
- 内容大纲
- Schema markup

---

## 任务专属问题

1. 你想覆盖哪些关键词模式？
2. 你手上有什么数据（或能拿到什么数据）？
3. 你计划做多少个页面？
4. 你当前网站权重如何？
5. 现在谁在这些词上排名？
6. 你的技术栈是什么？

---

## 相关技能

- **seo-audit**：用于程序化页面上线后的 SEO 审计
- **schema-markup**：用于添加结构化数据
- **site-architecture**：用于页面层级、URL 结构和内链规划
- **competitor-alternatives**：用于比较页框架设计
