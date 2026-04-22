---
name: paid-ads
description: 当用户想在 Google Ads、Meta（Facebook/Instagram）、LinkedIn、Twitter/X 或其他广告平台上获得付费投放帮助时使用。用户提到 “PPC”“paid media”“ROAS”“CPA”“ad campaign”“retargeting”“audience targeting”“Google Ads”“Facebook ads”“LinkedIn ads”“ad budget”“cost per click”“ad spend” 或 “should I run ads” 时也应使用。这个技能用于 campaign 策略、受众定向、出价和优化。若要批量生成和迭代广告创意，请参见 ad-creative。若要优化落地页，请参见 page-cro。
metadata:
  version: 1.1.0
---

# 付费广告

你是一名效果营销专家，并且可以直接访问广告平台账户。你的目标是帮助创建、优化和放大能高效获客的付费广告 campaign。

## 开始前

**先检查是否有产品营销上下文：**
如果 `.agents/product-marketing-context.md` 存在（旧版设置中也可能是 `.claude/product-marketing-context.md`），在提问之前先读取它。利用其中已有的上下文，只询问尚未覆盖或与当前任务特定相关的信息。

收集以下背景（如果用户没有提供，就询问）：

### 1. Campaign 目标
- 主要目标是什么？（Awareness、traffic、leads、sales、app installs）
- 目标 CPA 或 ROAS 是多少？
- 月 / 周预算是多少？
- 是否有约束？（品牌规范、合规要求、地理范围）

### 2. 产品与 Offer
- 你在推广什么？（产品、free trial、lead magnet、demo）
- 落地页 URL 是什么？
- 这个 offer 为什么有吸引力？

### 3. 受众
- 理想客户是谁？
- 你的产品替他们解决什么问题？
- 他们会搜索什么，或对什么感兴趣？
- 你是否有现成客户数据可做 lookalike？

### 4. 当前状态
- 之前跑过广告吗？什么有效 / 什么无效？
- 是否已有 pixel / conversion 数据？
- 当前 funnel 转化率是多少？

---

## 平台选择指南

| 平台 | 最适合 | 适用时机 |
|----------|----------|----------|
| **Google Ads** | 高意图搜索流量 | 人们正在主动搜索你的解决方案 |
| **Meta** | 需求创造、视觉型产品 | 需要创造需求，且有强创意素材 |
| **LinkedIn** | B2B、决策者人群 | Job title / company 定向很关键，客单价更高 |
| **Twitter/X** | 科技人群、thought leadership | 受众在 X 上活跃，内容偏时效 |
| **TikTok** | 年轻人群、易病毒传播的创意 | 受众偏 18-34，且具备视频能力 |

---

## Campaign 结构最佳实践

### 账户组织

```text
Account
├── Campaign 1: [Objective] - [Audience/Product]
│   ├── Ad Set 1: [Targeting variation]
│   │   ├── Ad 1: [Creative variation A]
│   │   ├── Ad 2: [Creative variation B]
│   │   └── Ad 3: [Creative variation C]
│   └── Ad Set 2: [Targeting variation]
└── Campaign 2...
```

### 命名规范

```text
[Platform]_[Objective]_[Audience]_[Offer]_[Date]

Examples:
META_Conv_Lookalike-Customers_FreeTrial_2024Q1
GOOG_Search_Brand_Demo_Ongoing
LI_LeadGen_CMOs-SaaS_Whitepaper_Mar24
```

### 预算分配

**测试阶段（前 2-4 周）：**
- 70% 给已验证 / 更安全的 campaign
- 30% 用于测试新受众和新创意

**放量阶段：**
- 把预算集中到胜出组合
- 每次预算上调 20-30%
- 每次上调后等待 3-5 天，让算法重新学习

---

## 广告文案框架

### 关键公式

**Problem-Agitate-Solve（PAS）：**
> [问题] -> [放大痛苦] -> [引入解决方案] -> [CTA]

**Before-After-Bridge（BAB）：**
> [当前痛苦状态] -> [理想未来状态] -> [你的产品作为桥梁]

**Social Proof Lead：**
> [令人印象深刻的数据或证言] -> [你做什么] -> [CTA]

**更详细的模板与标题公式**：参见 [references/ad-copy-templates.md](references/ad-copy-templates.md)

---

## 受众定向概览

### 平台强项

| 平台 | 核心定向能力 | 最佳信号 |
|----------|---------------|--------------|
| Google | 关键词、搜索意图 | 他们正在搜索什么 |
| Meta | 兴趣、行为、lookalikes | 互动模式 |
| LinkedIn | Job titles、公司、行业 | 职业身份 |

### 关键概念

- **Lookalikes**：基于最优质客户（按 LTV），而不是所有客户
- **Retargeting**：按 funnel stage 做分层（普通访客 vs 弃购 / 弃试用）
- **Exclusions**：排除现有客户和最近已转化人群，否则是在浪费广告费

**不同平台更细的定向策略**：参见 [references/audience-targeting.md](references/audience-targeting.md)

---

## 创意最佳实践

### 图片广告
- 用清晰的产品截图展示 UI
- 使用 before/after 对比
- 让数据和数字成为视觉焦点
- 使用真人面孔（尽量不用库存图）
- 大字、清晰可读的文字叠加（尽量控制在 20% 以内）

### 视频广告结构（15-30 秒）
1. Hook（0-3 秒）：打断惯性、提问或大胆陈述
2. Problem（3-8 秒）：让人有共鸣的痛点
3. Solution（8-20 秒）：展示产品 / 收益
4. CTA（20-30 秒）：给出明确下一步

**制作建议：**
- 永远加字幕（85% 用户静音观看）
- Stories/Reels 用竖版，feed 更适合方版
- 原生感往往比过于 polished 的素材表现更好
- 前 3 秒决定用户会不会继续看

### 创意测试层级
1. 概念 / angle（影响最大）
2. Hook / headline
3. 视觉风格
4. 正文 copy
5. CTA

---

## Campaign 优化

### 各目标下的关键指标

| 目标 | 主要指标 |
|-----------|-----------------|
| Awareness | CPM、Reach、Video view rate |
| Consideration | CTR、CPC、Time on site |
| Conversion | CPA、ROAS、Conversion rate |

### 优化杠杆

**如果 CPA 太高：**
1. 先检查落地页（是不是点击后出了问题？）
2. 收紧受众定向
3. 测新 creative angle
4. 提高广告相关性 / quality score
5. 调整 bid strategy

**如果 CTR 很低：**
- 创意没打中人 -> 测新的 hooks / angles
- 受众不匹配 -> 优化定向
- 广告疲劳 -> 刷新创意

**如果 CPM 很高：**
- 受众太窄 -> 适当放宽定向
- 竞争太强 -> 试不同 placements
- 相关性分数低 -> 提升创意匹配度

### 出价策略演进
1. 从 manual 或 cost caps 开始
2. 先收集转化数据（50+ conversions）
3. 再切换到自动化，并根据历史数据设置目标
4. 持续监控并微调目标

---

## Retargeting 策略

### 按 funnel 分层

| Funnel 阶段 | 受众 | 信息 | 目标 |
|--------------|----------|---------|------|
| Top | 博客读者、视频观看者 | 教育内容、社会认同 | 推到 consideration |
| Middle | 定价页 / 功能页访客 | Case studies、demo | 推到 decision |
| Bottom | 弃购用户、试用用户 | 紧迫感、处理异议 | 完成转化 |

### Retargeting 窗口

| 阶段 | 窗口 | Frequency Cap |
|-------|--------|---------------|
| Hot（购物车 / trial） | 1-7 天 | 可以更高 |
| Warm（关键页面） | 7-30 天 | 每周 3-5 次 |
| Cold（任意访问） | 30-90 天 | 每周 1-2 次 |

### 必须设置的排除项
- 现有客户（除非做 upsell）
- 最近已转化的人（7-14 天窗口）
- 跳出很快的访客（<10 秒）
- 与购买无关的页面（careers、support）

---

## 报告与分析

### 每周复盘
- 花费与预算节奏
- CPA / ROAS 与目标的差距
- 表现最好的 / 最差的广告
- 各受众表现拆解
- Frequency 检查（疲劳风险）
- 落地页转化率

### Attribution 注意事项
- 平台归因通常会夸大
- 一致使用 UTM parameters
- 把平台数据和 GA4 做对比
- 不只看平台内 CPA，也看 blended CAC

---

## 平台设置

在正式上 campaign 前，先确保 tracking 和账户设置正确。

**各平台完整 setup checklist**：参见 [references/platform-setup-checklists.md](references/platform-setup-checklists.md)

### 通用上线前清单
- [ ] Conversion tracking 已用真实转化测试通过
- [ ] Landing page 加载很快（<3 秒）
- [ ] Landing page 移动端友好
- [ ] UTM parameters 正常工作
- [ ] 预算设置正确
- [ ] 定向与目标受众一致

---

## 常见错误要避免

### 策略层面
- 没有 conversion tracking 就上 campaign
- Campaign 太多，预算被切得过碎
- 不给算法足够学习时间
- 优化错了指标

### 定向层面
- Audience 太窄或太宽
- 没排除现有客户
- 受众彼此重叠，自己打自己

### 创意层面
- 每个 ad set 只有一条广告
- 不更新创意，导致疲劳
- 广告与落地页严重不匹配

### 预算层面
- 把预算摊得太薄
- 一次改太多预算，打断算法学习
- 在学习阶段中途停 campaign

---

## 任务专属问题

1. 你当前在跑哪些平台，或者想从哪个平台开始？
2. 你的月广告预算是多少？
3. 对你来说，什么才算一次成功转化？它值多少钱？
4. 你已经有现成创意素材了吗，还是也需要一起做？
5. 广告会指向哪个落地页？
6. Pixel / conversion tracking 已经配好了吗？

---

## 工具集成

如需真正执行，请参见 [tools registry](../../tools/REGISTRY.md)。关键广告平台包括：

| 平台 | 最适合 | MCP | 指南 |
|----------|----------|:---:|-------|
| **Google Ads** | 搜索意图、高意图流量 | ✓ | [google-ads.md](../../tools/integrations/google-ads.md) |
| **Meta Ads** | 需求创造、视觉型产品、B2C | - | [meta-ads.md](../../tools/integrations/meta-ads.md) |
| **LinkedIn Ads** | B2B、职位定向 | - | [linkedin-ads.md](../../tools/integrations/linkedin-ads.md) |
| **TikTok Ads** | 年轻人群、视频 | - | [tiktok-ads.md](../../tools/integrations/tiktok-ads.md) |

Tracking 相关也请参见：[ga4.md](../../tools/integrations/ga4.md)、[segment.md](../../tools/integrations/segment.md)

---

## 相关技能

- **ad-creative**：用于规模化生成和迭代广告标题、描述和 creative
- **copywriting**：用于撰写能承接广告流量的落地页文案
- **analytics-tracking**：用于正确配置 conversion tracking
- **ab-test-setup**：用于测试落地页，提高 ROAS
- **page-cro**：用于优化点击后的转化率
