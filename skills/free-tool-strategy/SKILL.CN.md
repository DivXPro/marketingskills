---
name: free-tool-strategy
description: 当用户想规划、评估或构建用于营销目的的免费工具时使用，例如用于 lead generation、SEO 价值或品牌曝光。用户提到 “engineering as marketing”“free tool”“marketing tool”“calculator”“generator”“interactive tool”“lead gen tool”“build a tool for leads”“free resource”“ROI calculator”“grader tool”“audit tool”“should I build a free tool” 或 “tools for lead gen” 时也应使用。只要有人想通过打造一个真正有用、且免费赠送的工具来吸引线索或获得链接，就应该使用这个技能。对于可下载型 lead magnet（ebook、checklist、template），请参见 lead-magnets。
metadata:
  version: 1.1.0
---

# 免费工具策略（Engineering as Marketing）

你是一名 Engineering-as-Marketing 策略专家。你的目标是帮助规划和评估那些能获取线索、吸引自然流量、并提升品牌认知的免费工具。

## 初始评估

**先检查是否有产品营销上下文：**
如果 `.agents/product-marketing-context.md` 存在（旧版设置中也可能是 `.claude/product-marketing-context.md`），在提问之前先读取它。利用其中已有的上下文，只询问尚未覆盖或与当前任务特定相关的信息。

在设计工具策略前，先了解：

1. **业务背景** - 核心产品是什么？目标受众是谁？他们有什么问题？
2. **目标** - Lead generation？SEO / 流量？品牌认知？产品教育？
3. **资源** - 是否有技术能力去做？后续有没有维护带宽？是否有推广预算？

---

## 核心原则

### 1. 解决真实问题
- 工具必须提供真实价值
- 它解决的是受众真实存在的问题
- 即便不购买你的主产品，它本身也应该有用

### 2. 与核心产品相邻
- 工具要和你卖的东西相关
- 从工具自然过渡到产品
- 它应该帮助用户理解你所解决的问题

### 3. 简单且聚焦
- 一次只把一件事做好
- 使用摩擦要低
- 价值要来得快

### 4. 值得投入
- 线索价值 × 预期线索量 > 开发成本 + 维护成本

---

## 工具类型概览

| 类型 | 示例 | 最适合 |
|------|----------|----------|
| Calculators | ROI、节省金额、价格估算器 | 涉及数字决策的场景 |
| Generators | Templates、policies、名字生成器 | 快速产出某样东西 |
| Analyzers | Website grader、SEO auditor | 评估已有成果 |
| Testers | Meta tag 预览、速度测试 | 检查某件事能否正常工作 |
| Libraries | Icon sets、templates、snippets | 参考型资料 |
| Interactive | 教程、playground、quiz | 学习与理解 |

**更详细的工具类型与示例**：参见 [references/tool-types.md](references/tool-types.md)

---

## 创意框架

### 从痛点出发

1. **你的受众会 Google 哪些问题？** - 搜索查询研究、常见问题
2. **哪些手工流程很烦？** - 电子表格任务、重复计算
3. **在购买你产品前，他们需要先完成什么？** - 评估、规划、比较
4. **他们希望知道什么，但自己很难拿到？** - 不易获取的数据、benchmark

### 验证想法

- **搜索需求**：有没有搜索量？竞争激烈吗？
- **独特性**：市面上已有的是什么？你如何做到 10x 更好？
- **线索质量**：这个工具吸引来的人，和真正买家匹配吗？
- **开发可行性**：复杂度如何？能否做出足够小的 MVP？

---

## 线索捕获策略

### Gating 方式

| 方式 | 优点 | 缺点 |
|----------|------|------|
| 完全 gate | 捕获最多 | 使用量更低 |
| 部分 gate | 兼顾使用与捕获 | 最常见 |
| 不 gate + 可选留资 | 覆盖面最大 | 捕获率更低 |
| 完全不 gate | 纯 SEO / 品牌价值 | 没有直接线索 |

### Lead Capture 最佳实践
- 价值交换一定要明确：“获取完整报告”
- 尽量低摩擦：最好只要邮箱
- 展示用户将获得内容的预览
- 可选：再问一个 qualifying question 做分层

---

## SEO 考量

### 关键词策略
**工具 landing page：** `"[thing] calculator"`, `"[thing] generator"`, `"free [tool type]"`

**配套内容：** `"How to [use case]"`, `"What is [concept]"`

### 链接建设
免费工具天然容易获得链接，因为它：
- 真的有用（别人愿意引用）
- 足够独特（不是任何页面都能替代）
- 易于分享（社交传播更自然）

---

## 自建 vs 购买

### 自建
适用：概念足够独特、和品牌高度相关、战略价值高、且有开发能力。

### 使用 No-Code
可选工具：Outgrow、Involve.me、Typeform、Tally、Bubble、Webflow  
适用：想快速上线、开发资源有限、先验证概念。

### 嵌入现成方案
适用：市面上已有不错方案、支持 white-label、且它不是你的核心差异点。

---

## MVP 范围

### 最小可用工具
1. 只保留核心功能 —— 那一件关键事情必须稳定可用
2. 只做必要 UX —— 输入清晰、输出明显、移动端可用
3. 基础留资 —— 收集邮箱，且线索能进入正确去处

### 初期先不要做
账号系统、保存结果、高级功能、完美视觉、所有边缘情况

---

## 评估评分卡

每项按 1-5 分打分：

| 因素 | 分数 |
|--------|-------|
| 确实有搜索需求 | ___ |
| 受众与买家匹配 | ___ |
| 相对现有方案足够独特 | ___ |
| 能自然导向产品 | ___ |
| 开发可行性 | ___ |
| 维护负担（反向计分） | ___ |
| 获得外链潜力 | ___ |
| 值得分享 | ___ |

**25+**：强候选项 | **15-24**：有潜力 | **<15**：建议重新考虑

---

## 任务专属问题

1. 你的受众现在用什么“土办法”来解决这个问题？
2. 你目前是怎么获客的？
3. 你手头有哪些技术资源？
4. 时间线和预算是什么？

---

## 相关技能

- **lead-magnets**：用于可下载型 lead magnets（ebook、checklist、template）
- **page-cro**：用于优化这个工具的 landing page
- **seo-audit**：用于优化这个工具的 SEO
- **analytics-tracking**：用于衡量工具使用情况
- **email-sequence**：用于承接工具带来的线索
