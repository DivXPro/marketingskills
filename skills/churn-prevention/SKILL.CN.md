---
name: churn-prevention
description: 当用户想要降低流失、设计取消流程、设置 save offers、恢复失败支付或实施留存策略时使用。用户提到 “churn”“cancel flow”“offboarding”“save offer”“dunning”“failed payment recovery”“win-back”“retention”“exit survey”“pause subscription”“involuntary churn”“people keep canceling”“churn rate is too high”“how do I keep users” 或 “customers are leaving” 时也应使用。只要有人正在流失订阅用户，或想建立系统来减少流失，就应该使用这个技能。对于取消后的 win-back 邮件序列，请参见 email-sequence。对于应用内升级页，请参见 paywall-upgrade-cro。
metadata:
  version: 1.1.0
---

# 流失预防

你是一名 SaaS 留存与流失预防专家。你的目标是通过设计良好的取消流程、动态 save offer、主动留存和 dunning 策略，降低主动流失（用户主动取消）和被动流失（支付失败）。

## 开始前

**先检查是否有产品营销上下文：**
如果 `.agents/product-marketing-context.md` 存在（旧版设置中也可能是 `.claude/product-marketing-context.md`），在提问之前先读取它。利用其中已有的上下文，只询问尚未覆盖或与当前任务特定相关的信息。

收集以下背景（如果用户没有提供，就询问）：

### 1. 当前流失情况
- 当前月流失率是多少？（如果知道，区分主动 / 被动流失）
- 当前有多少活跃订阅用户？
- 单个客户平均 MRR 是多少？
- 现在有没有 cancel flow，还是点取消就直接结束？

### 2. 账单与平台
- 使用什么 billing provider？（Stripe、Chargebee、Paddle、Recurly、Braintree）
- 同时支持月付和年付吗？
- 是否支持 pause 或 downgrade？
- 是否已有 retention 工具？（Churnkey、ProsperStack、Raaft）

### 3. 产品与使用数据
- 是否能跟踪用户级 feature usage？
- 能识别 engagement drop-off 吗？
- 有没有历史取消原因数据？
- 激活指标是什么？（留存用户会做什么，而流失用户不会做什么）

### 4. 限制条件
- B2B 还是 B2C？（会影响 flow 设计）
- 法规是否要求 self-serve cancel？
- Offboarding 的品牌语气是什么？（empathetic、direct、playful）

---

## 这个技能如何工作

流失分为两类，需要不同策略：

| 类型 | 原因 | 解决方式 |
|------|-------|----------|
| **Voluntary** | 客户主动决定取消 | Cancel flow、save offer、exit survey |
| **Involuntary** | 支付失败 | Dunning emails、智能重试、card updater |

主动流失通常占总流失的 50-70%。被动流失占 30-50%，但往往更容易修复。

这个技能支持三种模式：

1. **构建 cancel flow** - 从零设计 survey、save offers 和确认流程
2. **优化已有 flow** - 分析取消数据并提升 save rate
3. **搭建 dunning** - 用于失败支付恢复的重试与邮件序列

---

## Cancel Flow 设计

### Cancel Flow 结构

每个 cancel flow 都遵循这个顺序：

```text
Trigger -> Survey -> Dynamic Offer -> Confirmation -> Post-Cancel
```

**Step 1: Trigger**  
用户在账户设置中点击 “Cancel subscription”。

**Step 2: Exit Survey**  
询问他们为什么取消，这决定了应该展示哪种 save offer。

**Step 3: Dynamic Save Offer**  
基于原因展示有针对性的 offer（折扣、暂停、降级等）。

**Step 4: Confirmation**  
如果他们仍然想取消，要清楚确认，并说明是到计费周期结束后生效。

**Step 5: Post-Cancel**  
设定后续预期、提供清晰的 reactivation 路径，并触发 win-back sequence。

### Exit Survey 设计

Exit survey 是整个流程的基础。好的原因分类包括：

| 原因 | 它告诉你的信息 |
|--------|-------------------|
| 太贵了 | 对价格敏感，可能适合折扣或 downgrade |
| 用得不够多 | Engagement 低，可能适合 pause 或 onboarding 帮助 |
| 缺少我需要的功能 | 产品 gap，可展示 roadmap 或 workaround |
| 准备切到竞品 | 存在竞争压力，需要知道对方提供了什么 |
| 技术问题 / Bug | 产品质量问题，应升级到支持团队 |
| 暂时 / 季节性需求 | 使用模式问题，可提供 pause |
| 业务关闭 / 变化 | 往往不可挽回，应优雅放行 |
| 其他 | 兜底选项，附带自由文本 |

**Survey 最佳实践：**
- 1 个问题，单选，允许补充自由文本
- 原因选项控制在 5-8 个
- 把最常见原因排前面（每季度复查一次）
- 不要让用户觉得被 guilt-trip
- “Help us improve” 的 framing 往往比 “Why are you leaving?” 更好

### 动态 Save Offers

关键洞察是：**offer 必须和取消原因匹配。**  
对一个不用产品的人，打折并不会真正挽回他；对一个付不起的人，功能 roadmap 也没有用。

**原因 -> offer 映射：**

| 取消原因 | 主 offer | 备用 offer |
|---------------|---------------|----------------|
| 太贵了 | 折扣（20-30%，持续 2-3 个月） | 降级到更低套餐 |
| 用得不够多 | Pause（1-3 个月） | 免费 onboarding session |
| 缺少功能 | 展示 roadmap + 时间线 | Workaround 指南 |
| 切换到竞品 | Competitive comparison + 折扣 | Feedback session |
| 技术问题 | 立即升级到支持团队 | Credit + 优先修复 |
| 暂时 / 季节性需求 | Pause subscription | 临时 downgrade |
| 业务关闭 | 跳过 offer，尊重现实 | — |

### Save Offer 类型

**折扣**
- 20-30% 持续 2-3 个月通常是甜区
- 避免 50%+ 深折扣（会训练用户“先取消再拿折扣”）
- 给出时效限制
- 尽量展示实际省下多少钱，而不是只说百分比

**暂停订阅**
- 最多 1-3 个月（超过这个长度的 pause 很少能重新激活）
- 60-80% 的 pausers 最终会重新激活
- 自动恢复前要提前邮件提醒
- 保留他们的数据和设置

**套餐降级**
- 给出更低套餐，而不是直接放弃
- 说明他们保留什么、会失去什么
- 用 “right-size your plan” 的 framing，而不是 “downgrade”
- 同时保留随时升回去的路径

**功能解锁 / 延期**
- 解锁他们还没试过的高级功能
- 延长高套餐试用期
- 对 “还没获得足够价值” 这类原因尤其有效

**人工跟进**
- 针对高价值账户（按 MRR 排名前 10-20%）
- 路由给 customer success 安排通话
- 对较小公司可由创始人亲自发邮件

### Cancel Flow UI 模式

```text
┌─────────────────────────────────────┐
│  We're sorry to see you go          │
│                                     │
│  What's the main reason you're      │
│  cancelling?                        │
│                                     │
│  ○ Too expensive                    │
│  ○ Not using it enough              │
│  ○ Missing a feature I need         │
│  ○ Switching to another tool        │
│  ○ Technical issues                 │
│  ○ Temporary / don't need right now │
│  ○ Other: [____________]            │
│                                     │
│  [Continue]                         │
│  [Never mind, keep my subscription] │
└─────────────────────────────────────┘
         ↓ (selects "Too expensive")
┌─────────────────────────────────────┐
│  What if we could help?             │
│                                     │
│  We'd love to keep you. Here's a    │
│  special offer:                     │
│                                     │
│  ┌───────────────────────────────┐  │
│  │  25% off for the next 3 months│  │
│  │  Save $XX/month               │  │
│  │                               │  │
│  │  [Accept Offer]               │  │
│  └───────────────────────────────┘  │
│                                     │
│  Or switch to [Basic Plan] at       │
│  $X/month →                         │
│                                     │
│  [No thanks, continue cancelling]   │
└─────────────────────────────────────┘
```

**UI 原则：**
- `continue cancelling` 必须清晰可见（不要用 dark patterns）
- 一个主 offer + 一个 fallback 即可，不要堆满选项墙
- 展示具体金额 savings，不只写抽象比例
- 如果可以，使用用户姓名和账户数据做个性化
- 保证移动端友好（很多取消行为发生在手机上）

按行业和 billing provider 划分的更详细模式：参见 [references/cancel-flow-patterns.md](references/cancel-flow-patterns.md)。

---

## 流失预测与主动留存

最好的挽回，发生在用户还没点击 “Cancel” 之前。

### 风险信号

跟踪这些 churn leading indicators：

| 信号 | 风险级别 | 时间窗口 |
|--------|-----------|-----------|
| 登录频率下降 50%+ | 高 | 取消前 2-4 周 |
| 关键功能停止使用 | 高 | 取消前 1-3 周 |
| 支持工单先激增后沉寂 | 高 | 取消前 1-2 周 |
| 邮件打开率下滑 | 中 | 取消前 2-6 周 |
| 账单页访问增多 | 高 | 取消前几天 |
| 团队 seat 被移除 | 高 | 取消前 1-2 周 |
| 发起数据导出 | 极高 | 取消前几天 |
| NPS 低于 6 | 中 | 取消前 1-3 个月 |

### Health Score 模型

可以基于加权信号构建一个简单的 health score（0-100）：

```text
Health Score = (
  Login frequency score × 0.30 +
  Feature usage score   × 0.25 +
  Support sentiment     × 0.15 +
  Billing health        × 0.15 +
  Engagement score      × 0.15
)
```

| 分数 | 状态 | 动作 |
|-------|--------|--------|
| 80-100 | 健康 | Upsell 机会 |
| 60-79 | 需要关注 | 主动 check-in |
| 40-59 | 有风险 | 干预 campaign |
| 0-39 | 危急 | 人工介入 |

### 主动干预

**在他们考虑取消之前：**

| 触发条件 | 干预动作 |
|---------|-------------|
| 两周内使用量下降 >50% | 发邮件：“我们注意到你最近没在用 [feature]，需要帮助吗？” |
| 接近套餐上限 | 升级提示（不是硬墙；paywall-upgrade-cro 处理这一块） |
| 14 天未登录 | 发 re-engagement 邮件，带上最近产品更新 |
| NPS detractor（0-6） | 24 小时内进行人工 follow-up |
| 支持工单 48h+ 未解决 | 升级处理并主动同步状态 |
| 年付续费还剩 30 天 | 发价值回顾 + 续费确认邮件 |

---

## 被动流失：支付恢复

支付失败导致 30-50% 的总流失，但也是最容易挽回的一部分。

### Dunning 技术栈

```text
Pre-dunning -> Smart retry -> Dunning emails -> Grace period -> Hard cancel
```

### Pre-Dunning（提前预防）

- **卡过期提醒**：在卡到期前 30、15、7 天发邮件
- **备用支付方式**：在注册时鼓励绑定第二支付方式
- **Card updater 服务**：Visa / Mastercard 自动更新计划（可减少 30-50% 的硬性拒付）
- **预扣费提醒**：针对年付，在扣款前 3-5 天提醒

### 智能重试逻辑

不是所有支付失败都一样。不同失败类型的重试策略不同：

| 拒付类型 | 例子 | 重试策略 |
|-------------|----------|----------------|
| Soft decline（临时） | 余额不足、processor timeout | 在 7-10 天内重试 3-5 次 |
| Hard decline（永久） | 卡被盗、账户关闭 | 不要重试，直接要求更新卡 |
| 需要认证 | 3D Secure、SCA | 引导用户更新支付或完成认证 |

**重试时间建议：**
- 第 1 次：失败后 24 小时
- 第 2 次：失败后 3 天
- 第 3 次：失败后 5 天
- 第 4 次：失败后 7 天（同时升级 dunning 邮件）
- 超过 4 次后：Hard cancel，但保留 reactivation 路径

**Smart retry 小技巧：** 如果用户原本每月 1 号付款成功，就尽量在月初同样日期重试。Stripe Smart Retries 会自动做这件事。

### Dunning 邮件序列

| 邮件 | 时间 | 语气 | 内容 |
|-------|--------|------|---------|
| 1 | Day 0（失败当天） | 友好提醒 | “你的付款没有成功，请更新卡信息。” |
| 2 | Day 3 | 帮助型提醒 | “快速提醒：更新付款方式以保持访问权限。” |
| 3 | Day 7 | 增强紧迫感 | “还有 3 天账户将被暂停，请立即更新。” |
| 4 | Day 10 | 最后警告 | “最后一次机会，保留你的账户。” |

**Dunning 邮件最佳实践：**
- 直接链接到支付更新页（尽量做到无需登录）
- 说明他们会失去什么（数据、团队访问权限）
- 不要责怪用户
- 提供支持联系方式
- 在 dunning 场景里，纯文本邮件往往比设计精美的邮件更有效

### 恢复 Benchmark

| 指标 | 差 | 平均 | 好 |
|--------|------|---------|------|
| Soft decline 恢复率 | <40% | 50-60% | 70%+ |
| Hard decline 恢复率 | <10% | 20-30% | 40%+ |
| 整体支付恢复率 | <30% | 40-50% | 60%+ |
| Pre-dunning 预防效果 | 无 | 10-15% | 20-30% |

完整 dunning playbook 及按 provider 的配置方式：参见 [references/dunning-playbook.md](references/dunning-playbook.md)。

---

## 指标与衡量

### 关键流失指标

| 指标 | 公式 | 目标 |
|--------|---------|--------|
| Monthly churn rate | 流失客户 / 月初客户数 | B2C <5%，B2B <2% |
| Revenue churn（净） | (流失 MRR - 扩张 MRR) / 月初 MRR | 最好为负（净扩张） |
| Cancel flow save rate | Saved / Total cancel sessions | 25-35% |
| Offer acceptance rate | Accepted offers / Shown offers | 15-25% |
| Pause reactivation rate | Reactivated / Total paused | 60-80% |
| Dunning recovery rate | Recovered / Total failed payments | 50-60% |
| Time to cancel | 从首个风险信号到取消的天数 | 持续跟踪趋势 |

### Cohort 分析

按以下维度拆解 churn：
- **获客渠道** - 哪些渠道带来的客户更能留？
- **套餐类型** - 哪些 plan 最容易 churn？
- **使用时长** - 大多数取消发生在第 30、60、90 天哪一档？
- **取消原因** - 哪类原因在增长？
- **Save offer 类型** - 哪类 offer 对哪些 segment 最有效？

### Cancel Flow A/B 测试

一次只测一个变量：

| 测试项 | 假设 | 指标 |
|------|-----------|--------|
| 折扣比例（20% vs 30%） | 更高折扣能提升 save rate | Save rate、LTV 影响 |
| Pause 时长（1 vs 3 个月） | 更长 pause 能提升回流率 | Reactivation rate |
| Survey 位置（offer 前 vs 后） | 先 survey 能提升个性化效果 | Save rate |
| Offer 展示方式（modal vs full page） | Full page 更容易引发注意 | Save rate |
| 文案语气（empathetic vs direct） | 更共情能减少摩擦 | Save rate |

**如何做 cancel flow 实验：** 使用 **ab-test-setup** 技能设计更严谨的测试。PostHog 很适合 cancel flow 实验，它的 feature flags 能把用户分到不同 flow，中间每一步（survey -> offer -> 接受 / 拒绝 -> 确认）都能放进 funnel 里分析。具体可看 [PostHog integration guide](../../tools/integrations/posthog.md)。

---

## 常见错误

- **完全没有 cancel flow** - 直接 instant cancel 会白白丢钱。即便只是 survey + 一个 offer，也常常能挽回 10-15%
- **故意把取消入口藏起来** - 会制造怨气、差评，很多地区也要求 easy cancellation
- **所有人都给同一个 offer** - blanket discount 不能解决 “缺功能” 或 “用得不够多”
- **折扣太深** - 50%+ 的折扣会训练用户“先取消再回来拿优惠”
- **忽视被动流失** - 它往往占 30-50%，也是最容易修复的一部分
- **没有 dunning 邮件** - 让失败支付静默导致账户取消
- **使用 guilt-trip 文案** - 会伤害品牌信任
- **不跟踪 save offer 的长期 LTV** - 30 天后又流失的 “挽回用户” 其实没真正被救回来
- **Pause 太长** - 超过 3 个月的 pause 很少能重新激活
- **取消后没有回流路径** - 一定要让 reactivation 简单，并触发 win-back 邮件

---

## 工具集成

如需真正落地，请参见 [tools registry](../../tools/REGISTRY.md)。

### 留存平台

| 工具 | 最适合 | 核心特性 |
|------|----------|-------------|
| **Churnkey** | 完整 cancel flow + dunning | AI 自适应 offer，平均 34% save rate |
| **ProsperStack** | 带分析能力的 cancel flow | 高级规则引擎，支持 Stripe / Chargebee |
| **Raaft** | 简单的 cancel flow 构建器 | 易上手，适合早期团队 |
| **Chargebee Retention** | Chargebee 用户 | 原生集成，前身为 Brightback |

### Billing Providers（Dunning）

| Provider | Smart Retries | Dunning Emails | Card Updater |
|----------|:------------:|:--------------:|:------------:|
| **Stripe** | 内置 | 内置 | 自动 |
| **Chargebee** | 内置 | 内置 | 通过 gateway |
| **Paddle** | 内置 | 内置 | 托管 |
| **Recurly** | 内置 | 内置 | 内置 |
| **Braintree** | 手动配置 | 手动 | 通过 gateway |

### 相关 CLI 工具

| 工具 | 用途 |
|------|---------|
| `stripe` | 订阅管理、dunning 配置、支付重试 |
| `customer-io` | Dunning 邮件序列、留存 campaign |
| `posthog` | 用 feature flags 测试 cancel flow、看 funnel |
| `mixpanel` / `ga4` | 使用行为跟踪、churn signal 分析 |
| `segment` | 把事件路由到 health scoring 系统 |

---

## 相关技能

- **email-sequence**：用于取消后的 win-back 邮件序列
- **paywall-upgrade-cro**：用于 in-app 升级时刻和 trial 到期场景
- **pricing-strategy**：用于套餐结构和年付折扣策略
- **onboarding-cro**：用于提升激活，减少早期流失
- **analytics-tracking**：用于设置 churn signal 事件
- **ab-test-setup**：用于以统计严谨的方式测试 cancel flow 变体
