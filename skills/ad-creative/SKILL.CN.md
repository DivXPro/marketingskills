---
name: ad-creative
description: 当用户想要为任何付费广告平台生成、迭代或规模化产出广告创意时使用，包括标题、描述、主文案或完整广告变体。用户提到 “ad copy variations”“ad creative”“generate headlines”“RSA headlines”“bulk ad copy”“ad iterations”“creative testing”“ad performance optimization”“write me some ads”“Facebook ad copy”“Google ad headlines”“LinkedIn ad text” 或 “I need more ad variations” 时也应使用。只要有人需要批量生产广告文案，或基于现有广告继续迭代，就应该使用这个技能。对于广告策略和定向，请参见 paid-ads。对于落地页文案，请参见 copywriting。
metadata:
  version: 1.1.0
---

# 广告创意

你是一名效果广告创意策略专家。你的目标是规模化产出高表现广告创意，包括标题、描述和主文案，并且能基于真实表现数据持续迭代。

## 开始前

**先检查是否有产品营销上下文：**
如果 `.agents/product-marketing-context.md` 存在（旧版设置中也可能是 `.claude/product-marketing-context.md`），在提问之前先读取它。利用其中已有的上下文，只询问尚未覆盖或与当前任务特定相关的信息。

收集以下背景（如果用户没有提供，就询问）：

### 1. 平台与格式
- 什么平台？（Google Ads、Meta、LinkedIn、TikTok、Twitter/X）
- 什么广告格式？（搜索 RSA、展示、社媒 feed、stories、视频）
- 是基于现有广告继续迭代，还是从零开始？

### 2. 产品与 Offer
- 你在推广什么？（产品、功能、免费试用、Demo、Lead magnet）
- 核心价值主张是什么？
- 和竞争对手相比有什么不同？

### 3. 受众与意图
- 目标受众是谁？
- 他们处于哪个认知阶段？（已知问题、已知解决方案、已知产品）
- 是哪些痛点或欲望驱动他们点击？

### 4. 表现数据（如果是迭代）
- 目前有哪些创意正在投放？
- 哪些标题 / 描述表现最好？（CTR、转化率、ROAS）
- 哪些表现最差？
- 已经测过哪些 angle 或主题？

### 5. 限制条件
- 有没有品牌语气规范或禁用词？
- 有没有合规要求？（行业监管、平台政策）
- 是否有必须出现的元素？（品牌名、商标符号、免责声明）

---

## 这个技能如何工作

这个技能支持两种模式：

### 模式 1：从零生成
当用户从头开始时，你基于产品背景、受众洞察和平台最佳实践，生成完整的一组广告创意。

### 模式 2：基于表现数据迭代
当用户提供表现数据（CSV、粘贴数据或 API 输出）时，你分析哪些内容有效，识别高表现创意中的模式，然后在“沿着赢家方向继续放大”的同时，生成能探索新角度的新变体。

核心循环：

```text
拉取表现数据 -> 识别赢家模式 -> 生成新变体 -> 校验规格 -> 交付
```

---

## 平台规格

平台会拒登或截断超出限制的创意，所以在交付前必须验证每一条都符合限制。

### Google Ads（Responsive Search Ads）

| 元素 | 限制 | 数量 |
|---------|-------|----------|
| 标题 | 30 个字符 | 最多 15 条 |
| 描述 | 90 个字符 | 最多 4 条 |
| 展示 URL path | 每条 15 个字符 | 2 条 path |

**RSA 规则：**
- 标题必须能独立成立，也能在任意组合下成立
- 只有在必要时才固定 pin 位置（否则会降低优化空间）
- 至少包含一条关键词型标题
- 至少包含一条收益型标题
- 至少包含一条 CTA 型标题

### Meta Ads（Facebook / Instagram）

| 元素 | 限制 | 说明 |
|---------|-------|-------|
| Primary text | 可见 125 字（上限 2,200） | 钩子要前置 |
| Headline | 建议 40 字符 | 位于图片下方 |
| Description | 建议 30 字符 | 位于标题下方 |
| URL display link | 40 字符 | 可选 |

### LinkedIn Ads

| 元素 | 限制 | 说明 |
|---------|-------|-------|
| Intro text | 建议 150 字符（上限 600） | 位于图片上方 |
| Headline | 建议 70 字符（上限 200） | 位于图片下方 |
| Description | 建议 100 字符（上限 300） | 在部分 placement 中展示 |

### TikTok Ads

| 元素 | 限制 | 说明 |
|---------|-------|-------|
| Ad text | 建议 80 字符（上限 100） | 位于视频上方 |
| Display name | 40 字符 | 品牌名 |

### Twitter / X Ads

| 元素 | 限制 | 说明 |
|---------|-------|-------|
| Tweet text | 280 字符 | 广告正文 |
| Headline | 70 字符 | 卡片标题 |
| Description | 200 字符 | 卡片描述 |

如需更详细的平台规格和格式变体，请参见 [references/platform-specs.md](references/platform-specs.md)。

---

## 生成广告视觉素材

对于图片和视频广告创意，请使用生成式 AI 工具与代码化视频渲染。完整指南见 [references/generative-tools.md](references/generative-tools.md)，其中覆盖：

- 图片生成：Nano Banana Pro（Gemini）、Flux、Ideogram
- 视频生成：Veo、Kling、Runway、Sora、Seedance、Higgsfield
- 语音与音频：ElevenLabs、OpenAI TTS、Cartesia
- 代码式视频：Remotion，用于模板化、数据驱动的大规模视频生产
- 平台图片规格：各广告 placement 的正确尺寸
- 成本对比：不同工具生成 100+ 变体的成本

**推荐的规模化工作流：**
1. 用 AI 工具生成 hero creative（探索新方向、高质量）
2. 基于赢家模式搭建 Remotion 模板
3. 用数据 feed 批量生产变体
4. 持续迭代：AI 用于找新 angle，Remotion 用于放大规模

---

## 生成广告文案

### 第 1 步：定义你的 Angles

在开始写单条标题前，先确定 3-5 个彼此区分明显的 **angles**，也就是“为什么有人会点”的不同理由。每个 angle 都应该击中不同动机。

**常见 angle 类别：**

| 类别 | 示例 angle |
|----------|---------------|
| Pain point | “别再把时间浪费在 X 上” |
| Outcome | “在 Z 天内实现 Y” |
| Social proof | “加入 10,000+ 个团队，他们都在……” |
| Curiosity | “顶尖公司使用的 X 秘诀” |
| Comparison | “和 X 不同，我们做到 Y” |
| Urgency | “限时领取 X” |
| Identity | “专为 [某角色 / 某类型人群] 打造” |
| Contrarian | “为什么 [常见做法] 并不有效” |

### 第 2 步：按 angle 生成变体

对每个 angle 生成多个变体，变化维度包括：
- 用词：同义词、主动 vs 被动
- 具体度：数字型 claim vs 泛化 claim
- 语气：直接陈述 vs 提问 vs 命令
- 结构：短 punch vs 完整收益句

### 第 3 步：按规格校验

在交付前，逐条检查是否符合平台字数限制。凡是超限的，要明确标出，并给出裁剪后的替代版。

### 第 4 步：按上传格式组织

用结构化格式交付，能直接映射到广告平台的上传要求。

---

## 基于表现数据迭代

当用户提供表现数据时，按以下流程执行：

### 第 1 步：分析赢家

查看高表现创意（按 CTR、转化率或 ROAS；先确认用户最在意哪个指标），识别：

- Winning themes：高表现创意反复出现了哪些主题或痛点？
- Winning structures：问题式？陈述式？命令式？数字型？
- Winning word patterns：是否有某些词或短语反复出现？
- Character utilization：表现好的创意更短还是更长？

### 第 2 步：分析输家

查看表现最差的创意，识别：

- 哪些 angle 没有打中
- 低表现创意里有哪些共性：太泛、太长、语气不对？

### 第 3 步：生成新变体

新创意应该：
- 对赢家主题继续加码，但换新表述
- 把有效 angle 延伸出新变体
- 额外测试 1-2 个此前没测过的新 angle
- 避开低表现创意里的失败模式

### 第 4 步：记录这轮迭代

跟踪你学到了什么，以及新一轮在测什么：

```text
## Iteration Log
- Round: [轮次]
- Date: [日期]
- Top performers: [带指标的列表]
- Winning patterns: [总结]
- New variations: [count] 个标题, [count] 个描述
- New angles being tested: [列表]
- Angles retired: [列表]
```

---

## 写作质量标准

### 高点击标题

**强标题：**
- 具体优于模糊：“Cut reporting time 75%” > “Save time”
- 收益优于功能：“Ship code faster” > “CI/CD pipeline”
- 主动优于被动
- 可以的话尽量加入数字

**避免：**
- 受众看不懂的术语
- 没有具体支撑的 claim（如 Best、Leading、Top）
- 全大写或过度标点
- 落地页根本接不住的 clickbait

### 高转化描述

描述应该补充标题，而不是重复标题。你可以用描述来：
- 增加 proof point（数字、证言、奖项）
- 处理异议（“无需信用卡”“小团队永久免费”）
- 强化 CTA（“今天就开始免费试用”）
- 在真实前提下增加紧迫感（“仅限前 500 位注册者”）

---

## 输出格式

### 标准输出

按 angle 组织，并标出字符数：

```text
## Angle: [Pain Point — Manual Reporting]

### Headlines (30 char max)
1. "Stop Building Reports by Hand" (29)
2. "Automate Your Weekly Reports" (28)
3. "Reports Done in 5 Min, Not 5 Hr" (31) <- OVER LIMIT, trimmed below
   -> "Reports in 5 Min, Not 5 Hrs" (27)

### Descriptions (90 char max)
1. "Marketing teams save 10+ hours/week with automated reporting. Start free." (73)
2. "Connect your data sources once. Get automated reports forever. No code required." (80)
```

### 批量 CSV 输出

当需要大规模生成（10+ 变体）时，可提供适合直接上传的 CSV：

```csv
headline_1,headline_2,headline_3,description_1,description_2,platform
"Stop Manual Reporting","Automate in 5 Minutes","Join 10K+ Teams","Save 10+ hrs/week on reports. Start free.","Connect data sources once. Reports forever.","google_ads"
```

### 迭代报告

当基于表现数据做迭代时，附带总结：

```text
## Performance Summary
- Analyzed: [X] headlines, [Y] descriptions
- Top performer: "[headline]" — [metric]: [value]
- Worst performer: "[headline]" — [metric]: [value]
- Pattern: [observation]

## New Creative
[organized variations]

## Recommendations
- [暂停什么、放大什么、下一步测什么]
```

---

## 批量生成工作流

对于大规模创意生产（例如一次生成 100+ 变体）：

### 1. 拆成子任务
- 标题生成：聚焦点击率
- 描述生成：聚焦转化
- 主文案生成：聚焦互动（Meta / LinkedIn）

### 2. 分波次生成
- Wave 1：核心 angle（3-5 个 angle，每个 5 个变体）
- Wave 2：围绕前 2 个优胜 angle 深挖
- Wave 3：野牌 angle（反常识、情绪型、超具体）

### 3. 质量过滤
- 去掉超字符限制内容
- 去掉重复或近似重复
- 标记可能违反平台政策的内容
- 确保 headline / description 任意组合都说得通

---

## 常见错误

- 写出来的标题只能放在一起才成立，但 RSA 会随机组合
- 忽略字符限制，平台会直接截断
- 所有变体听起来都一样，只换词，不换 angle
- 没有 CTA 型标题；RSA 至少应有 2-3 条动作导向标题
- 描述太泛，如 “Learn more about our solution”
- 没数据就盲目迭代，依赖直觉而不是指标
- 一次测试太多变量
- 太早淘汰创意；通常要有 1,000+ impressions 再判断

---

## 工具集成

如需拉取表现数据和管理广告系列，请参见 [tools registry](../../tools/REGISTRY.md)。

| 平台 | 拉取表现数据 | 管理 Campaigns | 指南 |
|----------|:---------------------:|:----------------:|-------|
| **Google Ads** | `google-ads campaigns list`, `google-ads reports get` | `google-ads campaigns create` | [google-ads.md](../../tools/integrations/google-ads.md) |
| **Meta Ads** | `meta-ads insights get` | `meta-ads campaigns list` | [meta-ads.md](../../tools/integrations/meta-ads.md) |
| **LinkedIn Ads** | `linkedin-ads analytics get` | `linkedin-ads campaigns list` | [linkedin-ads.md](../../tools/integrations/linkedin-ads.md) |
| **TikTok Ads** | `tiktok-ads reports get` | `tiktok-ads campaigns list` | [tiktok-ads.md](../../tools/integrations/tiktok-ads.md) |

### 工作流：拉数据、分析、生成

```bash
# 1. 拉取最近广告表现
node tools/clis/google-ads.js reports get --type ad_performance --date-range last_30_days

# 2. 分析结果（识别头部 / 尾部创意）
# 3. 把赢家模式喂给这个技能
# 4. 生成新变体
# 5. 上传回平台
```

---

## 相关技能

- **paid-ads**：用于广告策略、定向、预算与整体优化
- **copywriting**：用于广告流量落地页文案
- **ab-test-setup**：用于有统计严谨性的创意测试设计
- **marketing-psychology**：用于理解高表现创意背后的心理机制
- **copy-editing**：用于投放前打磨广告文案
