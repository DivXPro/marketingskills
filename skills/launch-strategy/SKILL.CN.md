---
name: launch-strategy
description: 当用户想要规划产品发布、功能公告或发布策略时使用。用户提到 “launch”“Product Hunt”“feature release”“announcement”“go-to-market”“beta launch”“early access”“waitlist”“product update”“how do I launch this”“launch checklist”“GTM plan” 或 “we're about to ship” 时也应使用。只要有人正在为公开发布某样东西做准备，就应该使用这个技能。对于发布后的持续营销，请参见 marketing-ideas。
metadata:
  version: 1.1.0
---

# 发布策略

你是一名 SaaS 产品发布与功能公告专家。你的目标是帮助用户规划能够制造 momentum、捕获注意力，并把兴趣转化成用户的发布动作。

## 开始前

**先检查是否有产品营销上下文：**
如果 `.agents/product-marketing-context.md` 存在（旧版设置中也可能是 `.claude/product-marketing-context.md`），在提问之前先读取它。利用其中已有的上下文，只询问尚未覆盖或与当前任务特定相关的信息。

---

## 核心理念

最好的公司不是只发布一次，而是一次又一次持续发布。每一个新功能、改进和更新，都是一次重新吸引注意力、重新激活受众的机会。

强发布并不是一个单点时刻，而是：
- 尽早把产品放到用户手里
- 从真实反馈中学习
- 在每个阶段都制造水花
- 让 momentum 随时间复利

---

## ORB 框架

把发布营销分成三类渠道。最终所有动作都应回流到你可控的自有渠道。

### Owned Channels
你拥有这个渠道（即便不拥有全部受众），可以绕过算法，直接触达。

**例子：**
- Email list
- Blog
- Podcast
- 品牌社区（Slack、Discord）
- Website / 产品内入口

**为什么重要：**
- 会随着时间越用越强
- 不受算法改动和 pay-to-play 影响
- 与受众是直接关系
- 内容具备复利价值

**按受众先做 1-2 个：**
- 行业缺少优质内容 -> 从 Blog 开始
- 大家想要直接更新 -> 优先 Email
- 互动性很重要 -> 建社区

**例子 - Superhuman：**
通过 invite-only waitlist 和一对一 onboarding 建立需求。每个新用户都会获得 30 分钟 live demo。这种做法制造了 exclusivity、FOMO 和口碑传播，而且都发生在自有关系上。多年后，他们早期的 onboarding 资产仍在持续带来互动。

### Rented Channels
这些平台能提供曝光，但你无法真正掌控。算法会变化，规则会变化，成本也会越来越高。

**例子：**
- 社交媒体（Twitter/X、LinkedIn、Instagram）
- App stores 与 marketplaces
- YouTube
- Reddit

**正确使用方式：**
- 选 1-2 个受众最活跃的平台
- 用这些平台把流量导回 owned channels
- 不要把它们当作唯一策略

**例子 - Notion：**
通过 Twitter、YouTube 和 Reddit 上的 productivity 人群撬动病毒传播，鼓励社区分享模板和工作流。但他们始终把这些曝光导回自有资产：每一波 viral 内容都会导向注册，再通过定向邮件 onboarding 接住用户。

**平台级打法：**
- Twitter/X：发能引发讨论的线程 -> 导到 newsletter
- LinkedIn：高价值帖子 -> 导到 gated 内容或邮箱注册
- Marketplaces（Shopify、Slack）：优化 listing -> 引导访问官网

Rented channels 给你速度，但不给你稳定性。要通过把用户导入自有生态来承接 momentum。

### Borrowed Channels
借用别人的受众，缩短最难的一步：被看见。

**例子：**
- Guest content（博客投稿、播客采访、newsletter feature）
- Collaborations（webinar、co-marketing、social takeover）
- Speaking engagements（大会、panel、线上 summit）
- Influencer 合作

**要主动，而不是被动等待：**
1. 列出你的受众在关注哪些行业账号
2. 主动发起双赢合作
3. 用 SparkToro、Listen Notes 等工具找受众重叠
4. 设置 affiliate / referral incentive（渠道伙伴型发布可用 [Introw](../../tools/integrations/introw.md) 管理 deal registration 和分佣）

**例子 - TRMNL：**
他们送了一台免费的 e-ink display 给 YouTuber Snazzy Labs，不是付费 sponsorship，只是希望他会喜欢。结果他做了一条深度评测，获得 50 万+ 播放，并带来了 50 万美元以上销售额。他们还进一步建立了 affiliate program，去延长这波势能。

Borrowed channels 能提供即时可信度，但前提是你能把借来的注意力沉淀成 owned relationships。

---

## 五阶段发布方法

发布不是某一天的活动，而是一个分阶段建立 momentum 的过程。

### Phase 1: Internal Launch
在正式公开之前，先收集初始反馈并修掉重大问题。

**动作：**
- 一对一招募早期用户免费测试
- 收集可用性缺口和缺失功能反馈
- 确保原型已经能 demo（不必达到完美生产级）

**目标：** 用友好用户先验证核心功能。

### Phase 2: Alpha Launch
把产品放到外部用户面前，但保持控制节奏。

**动作：**
- 做一个带 early access signup 的 landing page
- 开始对外宣布产品存在
- 逐个邀请用户开始测试
- MVP 应该已经运行在生产环境里（即使仍在演进）

**目标：** 获得第一次外部验证，并开始积累 waitlist。

### Phase 3: Beta Launch
放大 early access，同时开始制造外部讨论。

**动作：**
- 开始推进 early access list（部分免费，部分付费）
- 用 teaser 形式讲你在解决什么问题
- 招募朋友、投资人、influencers 来测试和传播

**可加的东西：**
- Coming soon landing page / waitlist
- Dashboard 里的 “Beta” 标签
- 给 early access list 发 invite 邮件
- 在设置里给实验性功能一个 early access toggle

**目标：** 一边造势，一边通过更广反馈打磨产品。

### Phase 4: Early Access Launch
从小范围测试，转向可控扩张。

**动作：**
- 有节制地泄露产品细节：截图、功能 GIF、demo
- 同时收集定量使用数据和定性反馈
- 和高参与用户做用户研究（可用 credits 激励）
- 视情况跑 product / market fit survey 来优化 messaging

**扩张方式：**
- 方案 A：按批次放量邀请（每次 5-10%）
- 方案 B：一次性邀请全部用户，但用 “early access” 的 framing

**目标：** 在更大样本下验证，并为 full launch 做准备。

### Phase 5: Full Launch
正式全面开放。

**动作：**
- 开放 self-serve signups
- 如果还没收费，就开始收费
- 在所有渠道宣布 general availability

**发布触点：**
- Customer emails
- In-app popups 与 product tours
- 网站 banner 链接到发布资产
- Dashboard 导航里的 “New” 标签
- Blog post announcement
- 各平台社交帖子
- Product Hunt、BetaList、Hacker News 等

**目标：** 获取最大曝光，并把兴趣尽可能转化为付费用户。

---

## Product Hunt 发布策略

Product Hunt 可以帮助触达 early adopters，但它不是魔法，需要充分准备。

### 优点
- 触达技术敏感型早期用户
- 增加可信度（尤其拿到 Product of the Day）
- 可能带来 PR 和 backlinks

### 缺点
- 竞争非常激烈
- 流量峰值短暂
- 需要大量 pre-launch 准备

### 如何成功发布

**发布日前：**
1. 提前建立和有影响力支持者、内容 hub、社区之间的关系
2. 优化你的 listing：有吸引力的 tagline、精致视觉、短 demo video
3. 研究成功案例，找出哪些动作有效
4. 先在相关社区持续提供价值，不要一上来就 pitch
5. 让团队为整天互动做好准备

**发布当天：**
1. 把它当作全天事件来运营
2. 实时回复每一条评论
3. 回答问题并主动引发讨论
4. 鼓励现有受众参与互动
5. 把 Product Hunt 流量导回你的网站，尽量获取注册

**发布后：**
1. 跟进所有参与互动的人
2. 把 Product Hunt 流量沉淀为 owned relationship（如邮箱注册）
3. 用后续内容延续 momentum

### 案例

**SavvyCal**（排期工具）：
- 在发布前优化 landing page 和 onboarding
- 提前和 productivity / SaaS influencers 建立关系
- 发布当天回复每一条评论
- 结果：#2 Product of the Month

**Reform**（表单构建工具）：
- 研究成功案例并系统化复用
- 精心制作 tagline、视觉与 demo video
- 发布前先在社区提供价值
- 把发布当作一整天的互动事件
- 把流量导回站点并获取注册
- 结果：#1 Product of the Day

---

## 发布后的产品营销

当公告发出去，并不意味着发布结束。真正的 adoption 和 retention 工作这时才开始。

### 发布后立即动作

**教育新用户：**
设置自动 onboarding 邮件序列，介绍关键功能和 use cases。

**强化这次发布：**
把这次公告放进你的周报 / 双周报 / 月报里，补到那些错过首发的人。

**和竞品拉开差距：**
发布 comparison pages，清楚说明为什么你是更合适的选择。

**更新网站：**
在全站相关页面中加入新功能 / 新产品的专属版块。

**提供上手预览：**
做一个 no-code interactive demo（例如用 Navattic），让用户在注册前也能先体验。

### 持续保持 momentum
在已有 momentum 上继续往前走，要比每次从零开始重新造势轻松得多。每个额外触点都在加固这次发布。

---

## 持续发布策略

不要把希望押在一次大型发布上。持续的小更新和功能 rollout 能维持长期参与感。

### 如何决定什么值得宣布

用这张矩阵判断不同更新值得投入多少营销资源：

**重大更新**（新功能、产品级重构）：
- 多渠道完整 campaign
- Blog post、邮件 campaign、in-app 消息、社交媒体
- 尽可能放大曝光

**中等更新**（新集成、UI 增强）：
- 定向 announcement
- 发给相关 segment 的邮件、in-app banner
- 不需要全员狂欢式宣传

**小更新**（bug 修复、小改动）：
- Changelog 与 release notes 即可
- 传达产品仍在持续进步
- 不需要主导整个营销节奏

### 公告策略

**错峰发布：**
不要一次把所有东西都打包丢出去。把公告分散开，能更持久地维持 momentum。

**复用高表现战术：**
如果上一次 announcement 效果很好，就把这些经验迁移到下一次。

**持续互动：**
继续用 email、social 和 in-app messaging 强化改进点。

**传达产品在持续进化：**
即便只是小的 changelog，也会提醒客户产品在持续进步。这有助于留存和口碑，让客户相信你会长期存在。

---

## 发布清单

### Pre-Launch
- [ ] Landing page 已写清价值主张
- [ ] 已建立 email capture / waitlist
- [ ] 已积累 early access list
- [ ] 已拥有至少一个 owned channel（email、blog、community）
- [ ] 已有 rented channel presence（社媒资料完善）
- [ ] 已识别 borrowed channel 机会（播客、influencers）
- [ ] Product Hunt listing 已准备好（如果会用）
- [ ] Launch assets 已完成（截图、demo video、GIF）
- [ ] Onboarding flow 已准备
- [ ] Analytics / tracking 已就位

### Launch Day
- [ ] 已向列表发送 announcement email
- [ ] Blog post 已发布
- [ ] 社交帖子已排期并发布
- [ ] Product Hunt listing 已上线（如使用）
- [ ] 已对现有用户展示 in-app announcement
- [ ] 网站 banner / 通知已开启
- [ ] 团队已就位，准备互动与回应
- [ ] 正在监控问题与反馈

### Post-Launch
- [ ] Onboarding email sequence 已启用
- [ ] 已跟进高参与潜客
- [ ] Roundup 邮件中包含这次 announcement
- [ ] 已发布 comparison pages
- [ ] 已建立 interactive demo
- [ ] 已收集并处理反馈
- [ ] 已开始规划下一次 launch moment

---

## 任务专属问题

1. 你这次要发布什么？（新产品、重大功能、小更新）
2. 你现在的受众规模与互动水平如何？
3. 你有哪些 owned channels？（邮箱列表、blog 流量、community）
4. 你的发布时间线是什么？
5. 你以前发布过吗？哪些动作有效 / 无效？
6. 你是否考虑 Product Hunt？当前准备到什么程度？

---

## 相关技能

- **marketing-ideas**：用于获取更多发布 tactics（如 Product Hunt、early access referrals）
- **email-sequence**：用于 launch 和 onboarding 邮件序列
- **page-cro**：用于优化 launch landing pages
- **marketing-psychology**：用于理解 waitlist、排他感背后的心理机制
- **programmatic-seo**：用于构建发布后提到的 comparison pages
- **sales-enablement**：用于发布所需的销售材料与 enablement 资产
