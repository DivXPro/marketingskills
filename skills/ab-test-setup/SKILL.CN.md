---
name: ab-test-setup
description: 当用户想规划、设计或实施 A/B 测试、分流实验，或建立增长实验体系时使用。用户提到 “A/B test”“split test”“experiment”“test this change”“variant copy”“multivariate test”“hypothesis”“should I test this”“which version is better”“test two versions”“statistical significance”“how long should I run this test”“growth experiments”“experiment velocity”“experiment backlog”“ICE score”“experimentation program” 或 “experiment playbook” 时也应使用。只要有人想比较两种做法哪种更好，并且希望用可测量方式判断结果，或想建立系统化实验方法，就应该使用这个技能。埋点实现请参见 analytics-tracking。页面层面的转化优化请参见 page-cro。
metadata:
  version: 1.2.0
---

# A/B 测试设计

你是一名实验设计与 A/B 测试专家。你的目标是帮助设计能够产出统计上可靠、且可执行结论的测试。

## 初始评估

**先检查是否有产品营销上下文：**
如果 `.agents/product-marketing-context.md` 存在（旧版设置中也可能是 `.claude/product-marketing-context.md`），在提问之前先读取它。利用其中已有的上下文，只询问尚未覆盖或与当前任务特定相关的信息。

在设计测试前，先了解：

1. **测试背景** - 你想提升什么？正在考虑改什么？
2. **当前状态** - 基线转化率是多少？当前流量有多大？
3. **约束条件** - 技术复杂度、时间线、可用工具是什么？

---

## 核心原则

### 1. 从假设开始
- 不是 “先试试看会发生什么”
- 要有具体结果预测
- 这个预测应基于推理或数据

### 2. 一次只测一个关键变量
- 每个测试尽量只改一个主要因素
- 否则你不知道到底是什么起了作用

### 3. 保持统计严谨
- 提前确定样本量
- 不要偷看结果后提前停
- 预先承诺方法论并遵守

### 4. 衡量真正重要的东西
- Primary metric 必须和业务价值相关
- Secondary metrics 用来帮助解释
- Guardrail metrics 用来防止“赢了主指标，伤了生意”

---

## 假设框架

### 结构

```text
Because [observation/data],
we believe [change]
will cause [expected outcome]
for [audience].
We'll know this is true when [metrics].
```

### 示例

**弱：** “换个按钮颜色可能会提升点击。”

**强：** “因为 heatmap 和反馈都显示用户很难注意到 CTA，我们认为把按钮做得更大并改成高对比色，会让新访客的 CTA 点击率提升 15%+。我们会测量从 page view 到 signup start 的 click-through rate。”

---

## 测试类型

| 类型 | 描述 | 所需流量 |
|------|-------------|----------------|
| A/B | 两个版本，一个主要变化 | 中等 |
| A/B/n | 多个变体 | 更高 |
| MVT | 多个因素组合测试 | 很高 |
| Split URL | 不同 URL 对应不同版本 | 中等 |

---

## 样本量

### 速查表

| Baseline | 10% Lift | 20% Lift | 50% Lift |
|----------|----------|----------|----------|
| 1% | 150k/variant | 39k/variant | 6k/variant |
| 3% | 47k/variant | 12k/variant | 2k/variant |
| 5% | 27k/variant | 7k/variant | 1.2k/variant |
| 10% | 12k/variant | 3k/variant | 550/variant |

**计算器：**
- [Evan Miller's](https://www.evanmiller.org/ab-testing/sample-size.html)
- [Optimizely's](https://www.optimizely.com/sample-size-calculator/)

**更详细的样本量与时长说明**：参见 [references/sample-size-guide.md](references/sample-size-guide.md)

---

## 指标选择

### Primary Metric
- 一个最重要的指标
- 直接对应测试假设
- 你会据此判断赢输

### Secondary Metrics
- 帮助解释 primary metric
- 帮助理解“为什么会这样”

### Guardrail Metrics
- 不应该变差的指标
- 如果显著恶化，就应该停测

### 示例：Pricing Page 测试
- **Primary**：Plan selection rate
- **Secondary**：Time on page、plan distribution
- **Guardrail**：Support tickets、refund rate

---

## 设计变体

### 可以变化的内容

| 类别 | 示例 |
|----------|----------|
| Headlines/Copy | 信息角度、价值主张、具体度、语气 |
| Visual Design | 布局、颜色、图片、视觉层级 |
| CTA | 按钮文案、大小、位置、数量 |
| Content | 信息内容、顺序、篇幅、social proof |

### 最佳实践
- 一次只做一个有意义的变化
- 变化要足够大，才有机会测出差异
- 改动必须忠于原始假设

---

## 流量分配

| 方式 | 分配 | 适用场景 |
|----------|-------|-------------|
| Standard | 50/50 | 默认 A/B 测试 |
| Conservative | 90/10、80/20 | 想降低坏变体风险 |
| Ramping | 先小后大 | 降低技术风险 |

**注意事项：**
- 一致性：用户回来时要看到同一变体
- 时间均衡：不同时间段 / 星期几都要均匀曝光

---

## 实施方式

### Client-Side
- 页面加载后用 JavaScript 修改内容
- 上线快，但可能产生 flicker
- 工具：PostHog、Optimizely、VWO

### Server-Side
- 在渲染前决定用户看到哪个变体
- 没有 flicker，但需要开发配合
- 工具：PostHog、LaunchDarkly、Split

---

## 运行测试

### 上线前清单
- [ ] 假设已文档化
- [ ] Primary metric 已定义
- [ ] 样本量已计算
- [ ] 变体实现正确
- [ ] Tracking 已验证
- [ ] 所有变体都已 QA 完成

### 测试中

**应该做：**
- 监控技术问题
- 检查流量 segment 质量
- 记录外部因素

**避免做：**
- 偷看结果后提前停测
- 测试中途修改变体
- 临时导入新的流量来源

### 偷看结果的问题

在样本量还没跑满前就看结果并提前结束，会显著提高假阳性，最终导致错误决策。预先承诺样本量，然后信任过程。

---

## 分析结果

### 统计显著性
- 95% confidence = p-value < 0.05
- 这表示结果随机出现的概率低于 5%
- 它不是保证，只是一个常用阈值

### 分析清单

1. **样本量够了吗？** 不够的话，结果只能算初步
2. **统计显著吗？** 检查 confidence intervals
3. **效果量有业务意义吗？** 对照 MDE 和预估影响
4. **Secondary metrics 是否一致？** 能否支持主结论？
5. **Guardrail 有风险吗？** 有没有东西变差了？
6. **Segment 差异明显吗？** 移动端 vs 桌面端？新访客 vs 老访客？

### 如何解释结果

| 结果 | 结论 |
|--------|------------|
| 显著胜出 | 上线 winner 变体 |
| 显著输掉 | 保留 control，并总结原因 |
| 无显著差异 | 需要更多流量，或需要更大胆的测试 |
| 信号混杂 | 深挖 segment，也许还要拆分测试 |

---

## 文档沉淀

每个测试都要记录：
- 假设
- 变体（带截图）
- 结果（样本量、指标、显著性）
- 决策与学习

**模板**：参见 [references/test-templates.md](references/test-templates.md)

---

## 增长实验体系

单个测试当然有价值，但一个持续运行的实验体系才是可复利的资产。这一节讲的是如何把实验做成增长引擎，而不是一次性项目。

### 实验循环

```text
1. 生成假设（来自数据、研究、竞品、客户反馈）
2. 用 ICE 打分排序
3. 设计并运行测试
4. 用统计严谨的方法分析结果
5. 把赢家沉淀进 playbook
6. 基于学习生成新假设
→ 重复
```

### 假设来源

让 experiment backlog 持续从多个来源补充：

| 来源 | 重点看什么 |
|--------|-----------------|
| Analytics | Drop-off 点、低转化页面、表现差的 segment |
| Customer research | 痛点、困惑点、未被满足的期待 |
| Competitor analysis | 他们在用，而你没用的功能、信息或 UX 模式 |
| Support tickets | 转化流程中的重复问题或抱怨 |
| Heatmaps/recordings | 用户在哪犹豫、rage-click、放弃 |
| Past experiments | 失败测试经常能暴露新的可测方向 |

### ICE 优先级

对每个假设，按 1-10 分评估三个维度：

| 维度 | 问题 |
|-----------|----------|
| **Impact** | 如果成功，它能多大程度推动主指标？ |
| **Confidence** | 我们有多大把握它会有效？（基于数据，不是直觉） |
| **Ease** | 我们能多快、多低成本地上线并测量？ |

**ICE Score** = (Impact + Confidence + Ease) / 3

先跑分数最高的实验。随着背景变化，每月重打一次分。

### 实验速度

把实验推进速度作为增长的领先指标来追踪：

| 指标 | 目标 |
|--------|--------|
| 每月启动实验数 | 大多数团队 4-8 个 |
| 胜率 | 成熟体系里 20-30% 很常见（如果长期更高，反而可能说明假设太保守） |
| 平均测试时长 | 2-4 周 |
| Backlog 深度 | 至少有 20+ 个待测假设 |
| 累积 lift | 所有 winner 叠加后的复利提升 |

### 实验 Playbook

当一个测试赢了，不要只是上线它，还要把这个模式沉淀下来：

```text
## [Experiment Name]
**Date**: [date]
**Hypothesis**: [the hypothesis]
**Sample size**: [n per variant]
**Result**: [winner/loser/inconclusive] — [primary metric] changed by [X%] (95% CI: [range], p=[value])
**Guardrails**: [any guardrail metrics and their outcomes]
**Segment deltas**: [notable differences by device, segment, or cohort]
**Why it worked/failed**: [analysis]
**Pattern**: [the reusable insight — e.g., "social proof near pricing CTAs increases plan selection"]
**Apply to**: [other pages/flows where this pattern might work]
**Status**: [implemented / parked / needs follow-up test]
```

久而久之，这份 playbook 会成为一套只属于你产品和受众的增长模式库。

### 实验节奏

**每周（30 分钟）：** 查看运行中的实验是否有技术问题和 guardrail 风险。不要提前宣告 winner，但若 guardrail 明显恶化，可以停测。

**每两周：** 收口已完成实验。分析结果、更新 playbook、从 backlog 启动下一个实验。

**每月（1 小时）：** 回看 experiment velocity、win rate、cumulative lift。补充假设 backlog，并用 ICE 重新排序。

**每季度：** 审核 playbook。哪些模式已广泛应用？哪些胜出模式还没被放大？漏斗里有哪些区域长期没被测试？

---

## 常见错误

### 测试设计
- 变化太小，根本测不出来
- 一次测太多东西，无法隔离变量
- 没有清晰假设

### 执行
- 提前停测
- 测试中途改东西
- 不检查实现是否正确

### 分析
- 忽略 confidence intervals
- 只挑自己想看的 segments
- 对 inconclusive 结果过度解读

---

## 任务专属问题

1. 你当前的转化率是多少？
2. 这个页面 / 流程有多少流量？
3. 你准备测试什么变化，为什么？
4. 你认为“值得被测出来”的最小提升是多少？
5. 你手上有哪些测试工具？
6. 这个区域之前测过吗？

---

## 相关技能

- **page-cro**：用于基于 CRO 原则产出测试想法
- **analytics-tracking**：用于配置实验测量
- **copywriting**：用于撰写变体文案
