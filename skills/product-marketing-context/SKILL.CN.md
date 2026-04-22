---
name: product-marketing-context
description: 当用户想创建或更新产品营销上下文文档时使用。用户提到 “product context”“marketing context”“set up context”“positioning”“who is my target audience”“describe my product”“ICP”“ideal customer profile” 或者想避免在多个营销任务里重复讲述基础信息时，也应使用。这个技能应该在任何新项目开始时优先使用，它会创建 `.agents/product-marketing-context.md`，供其他营销技能读取产品、受众和定位上下文。
metadata:
  version: 1.1.0
---

# 产品营销上下文

你帮助用户创建和维护一份产品营销上下文文档。它会沉淀基础定位和信息框架，供其他营销技能直接引用，让用户不用反复从头讲一遍。

该文档保存在 `.agents/product-marketing-context.md`。

## 工作流

### 步骤 1：检查现有上下文

首先检查 `.agents/product-marketing-context.md` 是否已经存在。也要同时检查旧版路径 `.claude/product-marketing-context.md`；如果旧路径存在而 `.agents/` 下没有，就询问用户是否要迁移。

**如果已存在：**
- 读取并总结已经记录了什么
- 询问用户想更新哪些部分
- 只针对这些部分补充信息

**如果不存在，提供两个选项：**

1. **从代码库自动起草**（推荐）：你先研究仓库内容，如 README、landing pages、marketing copy、package.json 等，然后起草一个 V1 的上下文文档，再让用户审核、修正并补缺。这通常比从零开始更快。

2. **从零开始**：用对话方式逐节收集信息，一次只处理一个部分。

大多数用户会更喜欢第 1 种。展示初稿后，问一句：`“哪里需要修正？哪里还缺？”`

### 步骤 2：收集信息

**如果采用自动起草：**
1. 读取代码库：README、landing pages、marketing copy、about pages、meta descriptions、package.json、已有文档
2. 根据找到的信息起草所有章节
3. 展示草稿，并询问哪里需要修正或补充
4. 循环迭代，直到用户满意

**如果从零开始：**
按下面的章节顺序，用对话方式逐个收集，不要一次性抛出所有问题。

对每个章节：
1. 简短解释这一部分在记录什么
2. 提出相关问题
3. 确认表述准确
4. 再进入下一部分

要尽量追问用户的原始客户语言。客户原话通常比润色后的描述更有价值，因为它更接近客户真实思维和表达，也更能支撑后续文案。

---

## 需要记录的章节

### 1. 产品概览
- 一句话描述
- 它做什么（2-3 句话）
- 产品品类（客户会把你放在哪个 “货架” 上搜索）
- 产品类型（SaaS、marketplace、电商、服务等）
- 商业模式和定价

### 2. 目标受众
- 目标公司类型（行业、规模、阶段）
- 目标决策者（角色、部门）
- 主要 use case（你解决的核心问题）
- Jobs to be done（客户“雇佣”你做的 2-3 件事）
- 更具体的 use cases 或场景

### 3. Personas（仅 B2B）
如果购买过程中涉及多个 stakeholder，则为每类角色记录：
- User、Champion、Decision Maker、Financial Buyer、Technical Influencer
- 他们各自关心什么、面临什么挑战、你承诺给他们什么价值

### 4. 问题与痛点
- 客户在找到你之前面对的核心挑战
- 为什么现有方案不够好
- 这些问题给他们带来的代价（时间、金钱、机会）
- 情绪张力（压力、担忧、怀疑）

### 5. 竞争格局
- **直接竞品**：同样的解决方案、同样的问题（例如 Calendly vs SavvyCal）
- **次级竞品**：不同的解决方案、同样的问题（例如 Calendly vs Superhuman scheduling）
- **间接竞品**：对立的做法（例如 Calendly vs personal assistant）
- 每一类方案为什么会让客户失望

### 6. 差异化
- 关键差异点（替代方案没有的能力）
- 你是怎么以不同方式解决问题的
- 为什么这种方式更好（收益）
- 为什么客户最终选你而不是别的选择

### 7. 异议与反向画像
- 销售中最常听到的 3 个异议，以及应对方式
- 哪些人**不适合**你（anti-persona）

### 8. 切换动力学
用 JTBD 的 Four Forces 结构来记录：
- **Push**：是什么不满把他们从当前方案推开
- **Pull**：是什么在把他们吸引到你这边
- **Habit**：是什么习惯把他们困在原有做法里
- **Anxiety**：他们对切换最大的担忧是什么

### 9. 客户语言
- 客户如何描述问题（verbatim）
- 客户如何描述你的解决方案（verbatim）
- 建议使用的词和短语
- 需要避免的词和短语
- 与产品相关的术语表

### 10. 品牌语气
- Tone（professional、casual、playful 等）
- Communication style（direct、conversational、technical）
- Brand personality（3-5 个形容词）

### 11. 证据点
- 可引用的关键指标或结果
- 重要客户 / logo
- Testimonial 片段
- 主要价值主题及其支撑证据

### 12. 目标
- 主要业务目标
- 关键转化动作（你希望用户做什么）
- 当前指标（如果知道）

---

## 步骤 3：创建文档

信息收集完成后，按以下结构创建 `.agents/product-marketing-context.md`：

```markdown
# Product Marketing Context

*Last updated: [date]*

## Product Overview
**One-liner:**
**What it does:**
**Product category:**
**Product type:**
**Business model:**

## Target Audience
**Target companies:**
**Decision-makers:**
**Primary use case:**
**Jobs to be done:**
-
**Use cases:**
-

## Personas
| Persona | Cares about | Challenge | Value we promise |
|---------|-------------|-----------|------------------|
| | | | |

## Problems & Pain Points
**Core problem:**
**Why alternatives fall short:**
-
**What it costs them:**
**Emotional tension:**

## Competitive Landscape
**Direct:** [Competitor] — falls short because...
**Secondary:** [Approach] — falls short because...
**Indirect:** [Alternative] — falls short because...

## Differentiation
**Key differentiators:**
-
**How we do it differently:**
**Why that's better:**
**Why customers choose us:**

## Objections
| Objection | Response |
|-----------|----------|
| | |

**Anti-persona:**

## Switching Dynamics
**Push:**
**Pull:**
**Habit:**
**Anxiety:**

## Customer Language
**How they describe the problem:**
- "[verbatim]"
**How they describe us:**
- "[verbatim]"
**Words to use:**
**Words to avoid:**
**Glossary:**
| Term | Meaning |
|------|---------|
| | |

## Brand Voice
**Tone:**
**Style:**
**Personality:**

## Proof Points
**Metrics:**
**Customers:**
**Testimonials:**
> "[quote]" — [who]
**Value themes:**
| Theme | Proof |
|-------|-------|
| | |

## Goals
**Business goal:**
**Conversion action:**
**Current metrics:**
```

---

## 步骤 4：确认并保存

- 展示完整文档
- 询问是否还有需要调整的地方
- 保存到 `.agents/product-marketing-context.md`
- 告诉用户：`“其他营销技能之后会自动使用这份上下文。以后任何时候都可以运行 /product-marketing-context 来更新它。”`

---

## 小提示

- **尽量具体**：问 “把他们带到你这里的头号挫败感是什么？” 比 “他们解决什么问题？” 更好
- **记录原话**：客户语言通常胜过打磨后的描述
- **追问例子**：`“能给我举个例子吗？”` 往往能换来更好的回答
- **边走边确认**：每完成一节，就先总结并确认，再继续
- **跳过不适用部分**：不是每个产品都需要所有章节（例如 B2C 不一定要 Personas）
