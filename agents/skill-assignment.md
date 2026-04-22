# Agent Skill 分配总表

## 第一梯队 skill 范围

本次第一梯队 skill 包括：

- `product-marketing-context` / 产品营销上下文
- `social-content` / 社交内容
- `copywriting` / 营销文案写作
- `copy-editing` / 文案编辑
- `customer-research` / 客户研究
- `paid-ads` / 付费广告
- `ad-creative` / 广告创意
- `analytics-tracking` / 分析与埋点追踪
- `ab-test-setup` / A/B 测试设计
- `pricing-strategy` / 定价策略
- `marketing-ideas` / 营销创意
- `marketing-psychology` / 营销心理学

## 第二梯队 skill 范围

本次第二梯队 skill 包括：

- `launch-strategy` / 发布策略
- `community-marketing` / 社区营销
- `referral-program` / 推荐裂变计划
- `email-sequence` / 邮件序列设计
- `page-cro` / 页面转化率优化（CRO）
- `churn-prevention` / 流失预防

## Skill 中文对照

- `product-marketing-context`：产品营销上下文
- `social-content`：社交内容
- `copywriting`：营销文案写作
- `copy-editing`：文案编辑
- `customer-research`：客户研究
- `paid-ads`：付费广告
- `ad-creative`：广告创意
- `analytics-tracking`：分析与埋点追踪
- `ab-test-setup`：A/B 测试设计
- `pricing-strategy`：定价策略
- `marketing-ideas`：营销创意
- `marketing-psychology`：营销心理学
- `launch-strategy`：发布策略
- `community-marketing`：社区营销
- `referral-program`：推荐裂变计划
- `email-sequence`：邮件序列设计
- `page-cro`：页面转化率优化（CRO）
- `churn-prevention`：流失预防

## 分配原则

- `product-marketing-context` 作为基础上下文共享 skill，不设单一 owner
- 每个 skill 尽量只有 1 个核心 owner，其他角色只做协作引用
- 协作引用必须有明确理由，不能因为“好像也能用”就扩散到所有 agent
- 第二梯队只做增量补充，不推翻第一梯队已定 owner
- `community-marketing` 当前不设唯一 owner，避免在策略和内容之间过早强绑
- `orchestrator` 只负责路由与停机判断，不拥有任何梯队的 owner skill
- “未分配”是显式状态，不是遗漏；它用于记录当前能力空白

## 按 Agent 分配

### 账号主理 / 内容策略官

- 核心 owner：
  - `marketing-ideas` / 营销创意
  - `marketing-psychology` / 营销心理学
  - `launch-strategy` / 发布策略
- 协作引用：
  - `product-marketing-context` / 产品营销上下文
  - `customer-research` / 客户研究
  - `pricing-strategy` / 定价策略
  - `community-marketing` / 社区营销
- 分配理由：
  - 负责目标、主推方向、内容支柱、发布节奏和活动编排，最适合承接策略、创意、心理驱动与发布型 skill

### 内容制作官

- 核心 owner：
  - `social-content` / 社交内容
  - `copywriting` / 营销文案写作
  - `copy-editing` / 文案编辑
  - `email-sequence` / 邮件序列设计
- 协作引用：
  - `customer-research` / 客户研究
  - `marketing-psychology` / 营销心理学
  - `product-marketing-context` / 产品营销上下文
  - `community-marketing` / 社区营销
- 分配理由：
  - 负责把策略和卖点变成内容成品，同时也适合承接多触点、多阶段的邮件内容表达

### 店铺运营官

- 核心 owner：
  - `pricing-strategy` / 定价策略
  - `page-cro` / 页面转化率优化（CRO）
- 协作引用：
  - `copywriting` / 营销文案写作
  - `copy-editing` / 文案编辑
  - `product-marketing-context` / 产品营销上下文
  - `customer-research` / 客户研究
- 分配理由：
  - 负责价格结构、利益点承接和成交表达；在当前场景下，`page-cro` 迁移到商品详情页、活动页、店铺首页与直播承接页

### 选品与供给官

- 核心 owner：
  - 暂不设
- 协作引用：
  - `customer-research` / 客户研究
  - `pricing-strategy` / 定价策略
  - `marketing-ideas` / 营销创意
  - `product-marketing-context` / 产品营销上下文
  - `analytics-tracking` / 分析与埋点追踪
  - `page-cro` / 页面转化率优化（CRO）
  - `churn-prevention` / 流失预防
- 分配理由：
  - 当前两梯队里仍没有专门面向选品、货盘、供给和履约判断的专属 skill，只能通过协作引用补足

### 投放与增长官

- 核心 owner：
  - `paid-ads` / 付费广告
  - `ad-creative` / 广告创意
  - `analytics-tracking` / 分析与埋点追踪
  - `ab-test-setup` / A/B 测试设计
  - `referral-program` / 推荐裂变计划
- 协作引用：
  - `social-content` / 社交内容
  - `product-marketing-context` / 产品营销上下文
  - `copywriting` / 营销文案写作
  - `copy-editing` / 文案编辑
  - `launch-strategy` / 发布策略
- 分配理由：
  - 负责放量、素材、测量、实验设计和增长机制放大，最适合承接推荐裂变和增长回路相关 skill

### 数据复盘与客服体验官

- 核心 owner：
  - `customer-research` / 客户研究
  - `churn-prevention` / 流失预防
- 协作引用：
  - `analytics-tracking` / 分析与埋点追踪
  - `ab-test-setup` / A/B 测试设计
  - `product-marketing-context` / 产品营销上下文
  - `copy-editing` / 文案编辑
  - `marketing-psychology` / 营销心理学
- 分配理由：
  - 负责反馈收集、归因分析、问题回流、退款与流失诊断，最适合承接研究和留存挽回类 skill

### Orchestrator / 轻量调度器

- 核心 owner：
  - 不设
- 协作引用：
  - `product-marketing-context` / 产品营销上下文
  - `analytics-tracking` / 分析与埋点追踪
  - `ab-test-setup` / A/B 测试设计
  - `launch-strategy` / 发布策略
  - `page-cro` / 页面转化率优化（CRO）
  - `churn-prevention` / 流失预防
- 分配理由：
  - 仅用于判断是否缺上下文、缺测量、是否进入发布编排、承接优化或流失诊断，不直接产出专业结论

## 按 Skill 反查

### 共享基础 skill

- `product-marketing-context` / 产品营销上下文
  - 核心 owner：无
  - 协作引用：`账号主理`、`内容制作官`、`店铺运营官`、`选品与供给官`、`投放与增长官`、`数据复盘与客服体验官`、`orchestrator`
  - 说明：全体角色可共享的前置上下文 skill

### 策略与创意

- `marketing-ideas` / 营销创意
  - 核心 owner：`账号主理`
  - 协作引用：`选品与供给官`
- `marketing-psychology` / 营销心理学
  - 核心 owner：`账号主理`
  - 协作引用：`内容制作官`、`数据复盘与客服体验官`
- `launch-strategy` / 发布策略
  - 核心 owner：`账号主理`
  - 协作引用：`投放与增长官`、`orchestrator`
- `community-marketing` / 社区营销
  - 核心 owner：无
  - 协作引用：`账号主理`、`内容制作官`
  - 说明：当前不设唯一 owner，作为策略与内容的双协作 skill

### 内容与文案

- `social-content` / 社交内容
  - 核心 owner：`内容制作官`
  - 协作引用：`投放与增长官`
- `copywriting` / 营销文案写作
  - 核心 owner：`内容制作官`
  - 协作引用：`店铺运营官`、`投放与增长官`
- `copy-editing` / 文案编辑
  - 核心 owner：`内容制作官`
  - 协作引用：`店铺运营官`、`投放与增长官`、`数据复盘与客服体验官`
- `email-sequence` / 邮件序列设计
  - 核心 owner：`内容制作官`
  - 协作引用：无

### 研究、测量、留存与实验

- `customer-research` / 客户研究
  - 核心 owner：`数据复盘与客服体验官`
  - 协作引用：`账号主理`、`内容制作官`、`店铺运营官`、`选品与供给官`
- `analytics-tracking` / 分析与埋点追踪
  - 核心 owner：`投放与增长官`
  - 协作引用：`选品与供给官`、`数据复盘与客服体验官`、`orchestrator`
- `ab-test-setup` / A/B 测试设计
  - 核心 owner：`投放与增长官`
  - 协作引用：`数据复盘与客服体验官`、`orchestrator`
- `churn-prevention` / 流失预防
  - 核心 owner：`数据复盘与客服体验官`
  - 协作引用：`选品与供给官`、`orchestrator`

### 定价、承接与增长执行

- `pricing-strategy` / 定价策略
  - 核心 owner：`店铺运营官`
  - 协作引用：`账号主理`、`选品与供给官`
- `page-cro` / 页面转化率优化（CRO）
  - 核心 owner：`店铺运营官`
  - 协作引用：`选品与供给官`、`orchestrator`
  - 说明：在当前场景下指商品详情页、活动页、店铺首页和直播承接页的承接优化
- `paid-ads` / 付费广告
  - 核心 owner：`投放与增长官`
  - 协作引用：无
- `ad-creative` / 广告创意
  - 核心 owner：`投放与增长官`
  - 协作引用：无
- `referral-program` / 推荐裂变计划
  - 核心 owner：`投放与增长官`
  - 协作引用：无

## 未分配与暂不设 owner

### 无单一 owner，但被共享引用

- `product-marketing-context` / 产品营销上下文
  - 原因：它是通用前置上下文，不适合收归某一个职能 agent 独占
- `community-marketing` / 社区营销
  - 原因：当前同时影响账号主理的长期主题与内容制作官的互动表达，暂不设唯一 owner

### 当前明确不设专属 owner

- `选品与供给官`
  - 原因：两梯队里都没有直接面向选品、货盘、供给和履约判断的专属 skill
  - 当前状态：通过 `customer-research`（客户研究）、`pricing-strategy`（定价策略）、`marketing-ideas`（营销创意）、`page-cro`（页面转化率优化）和 `churn-prevention`（流失预防）等 skill 做协作补足

## 重叠度分析

### 重叠度口径

- `低重叠`：1 个核心 owner，0-1 个协作引用 agent
- `中重叠`：1 个核心 owner，2-3 个协作引用 agent
- `高重叠`：4 个及以上 agent 引用，或无 owner 但被广泛共享

### 按 Skill 分析

| Skill | 核心 owner | 协作引用 Agent | 重叠度 | 说明 |
|---|---|---|---|---|
| `product-marketing-context` / 产品营销上下文 | 无 | 全体 agent + `orchestrator` | 高重叠 | 基础上下文共享 |
| `marketing-ideas` / 营销创意 | `账号主理` | `选品与供给官` | 低重叠 | 上游策略与货盘思路共享 |
| `marketing-psychology` / 营销心理学 | `账号主理` | `内容制作官`、`数据复盘与客服体验官` | 中重叠 | 策略、表达与动机分析共享 |
| `launch-strategy` / 发布策略 | `账号主理` | `投放与增长官`、`orchestrator` | 中重叠 | 发布编排与放量节奏共享 |
| `community-marketing` / 社区营销 | 无 | `账号主理`、`内容制作官` | 中重叠 | 暂不设 owner，避免过早固化边界 |
| `social-content` / 社交内容 | `内容制作官` | `投放与增长官` | 低重叠 | 内容生产与投流素材衔接 |
| `copywriting` / 营销文案写作 | `内容制作官` | `店铺运营官`、`投放与增长官` | 中重叠 | 内容表达与承接表达共享 |
| `copy-editing` / 文案编辑 | `内容制作官` | `店铺运营官`、`投放与增长官`、`数据复盘与客服体验官` | 中重叠 | 文案精修跨执行与复盘共享 |
| `email-sequence` / 邮件序列设计 | `内容制作官` | 无 | 低重叠 | 多阶段触达内容专属 |
| `customer-research` / 客户研究 | `数据复盘与客服体验官` | `账号主理`、`内容制作官`、`店铺运营官`、`选品与供给官` | 高重叠 | 用户声音贯穿策略、内容、承接和货盘 |
| `analytics-tracking` / 分析与埋点追踪 | `投放与增长官` | `选品与供给官`、`数据复盘与客服体验官`、`orchestrator` | 中重叠 | 测量前提被增长、复盘和路由共享 |
| `ab-test-setup` / A/B 测试设计 | `投放与增长官` | `数据复盘与客服体验官`、`orchestrator` | 中重叠 | 实验设计由增长主导，复盘与调度协作引用 |
| `churn-prevention` / 流失预防 | `数据复盘与客服体验官` | `选品与供给官`、`orchestrator` | 中重叠 | 流失诊断与挽回判断共享 |
| `pricing-strategy` / 定价策略 | `店铺运营官` | `账号主理`、`选品与供给官` | 中重叠 | 定价、套餐和利益点跨策略与承接共享 |
| `page-cro` / 页面转化率优化（CRO） | `店铺运营官` | `选品与供给官`、`orchestrator` | 中重叠 | 平台电商承接页迁移用法 |
| `paid-ads` / 付费广告 | `投放与增长官` | 无 | 低重叠 | 增长执行专属 |
| `ad-creative` / 广告创意 | `投放与增长官` | 无 | 低重叠 | 广告素材专属 |
| `referral-program` / 推荐裂变计划 | `投放与增长官` | 无 | 低重叠 | 增长机制专属 |

### 按 Agent 分析

| Agent | 核心 owner 数 | 协作引用数 | 重叠水平 | 说明 |
|---|---:|---:|---|---|
| `账号主理` | 3 | 4 | 中重叠 | 增补发布策略后仍以策略 owner 为主 |
| `内容制作官` | 4 | 4 | 中重叠 | 内容表达中心，新增邮件序列 owner |
| `店铺运营官` | 2 | 4 | 中重叠 | 新增 `page-cro` 后承接能力更完整 |
| `选品与供给官` | 0 | 7 | 高重叠 | 仍无专属 owner，说明能力空白仍存在 |
| `投放与增长官` | 5 | 5 | 中重叠 | owner 最集中，是增长执行与放大主力位 |
| `数据复盘与客服体验官` | 2 | 5 | 高重叠 | 新增流失预防后，复盘与留存诊断更完整 |
| `orchestrator` | 0 | 6 | 中重叠 | 仍为路由角色，但识别阶段更多 |

## 后续建议

- 优先为 `选品与供给官` 补专属 skill，例如 `social-commerce-merchandising`
- 如果后面要强化私域/CRM 触达，可继续把 `email-sequence` 与 `community-marketing` 做更细边界拆分
- 如果后面要做直播场景，可考虑新增 `livestream-commerce-ops` 类 skill
- 当某个 skill 的重叠持续扩大时，优先收敛 owner 和协作边界，而不是继续扩散
