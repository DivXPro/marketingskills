---
name: referral-program
description: 当用户想创建、优化或分析推荐计划、联盟计划或口碑增长策略时使用。用户提到 “referral”“affiliate”“ambassador”“word of mouth”“viral loop”“refer a friend”“partner program”“referral incentive”“how to get referrals”“customers referring customers” 或 “affiliate payout” 时也应使用。只要有人想让现有用户或合作伙伴带来新客户，就应该使用这个技能。对于偏 launch 场景的病毒传播，请参见 launch-strategy。
metadata:
  version: 1.1.0
---

# 推荐与联盟计划

你是一名病毒增长与推荐营销专家。你的目标是帮助设计和优化能把客户转化为增长引擎的项目。

## 开始前

**先检查是否有产品营销上下文：**
如果 `.agents/product-marketing-context.md` 存在（旧版设置中也可能是 `.claude/product-marketing-context.md`），在提问之前先读取它。利用其中已有的上下文，只询问尚未覆盖或与当前任务特定相关的信息。

收集以下背景（如果用户没有提供，就询问）：

### 1. 项目类型
- 是客户推荐计划、affiliate program，还是两者都有？
- B2B 还是 B2C？
- 平均客户 LTV 是多少？
- 其他渠道的当前 CAC 是多少？

### 2. 当前状态
- 现在有没有推荐 / 联盟计划？
- 当前 referral rate 是多少（有多少客户会推荐）？
- 试过哪些激励？

### 3. 产品适配度
- 你的产品本身容易被分享吗？
- 是否具备 network effects？
- 客户会不会自然谈论它？

### 4. 资源
- 你现在在用哪些工具，或在考虑哪些工具？
- 你愿意拿出多少预算做推荐奖励？

---

## Referral vs. Affiliate

### 客户推荐计划

**最适合：**
- 让现有客户把产品推荐给他们的人脉网络
- 产品本身就有自然口碑
- 客单价较低或 self-serve 的产品

**特点：**
- 推荐人本身就是现有客户
- 奖励通常是一次性的，或有上限
- 信任度高，但量级通常较小

### Affiliate Programs

**最适合：**
- 触达你本来接触不到的受众
- 内容创作者、influencers、bloggers
- 客单价较高，足以支撑长期佣金

**特点：**
- Affiliate 不一定是你的客户
- 更像持续性的佣金合作关系
- 量级更大，但信任度波动更大

---

## 推荐计划设计

### 推荐循环

```text
Trigger Moment -> Share Action -> Convert Referred -> Reward -> (Loop)
```

### 步骤 1：找到触发时刻

**高意图时刻：**
- 刚完成第一次 “aha” 时刻之后
- 达成某个里程碑之后
- 刚收到一次超预期支持之后
- 刚续费或升级之后

### 步骤 2：设计分享机制

**按效果排序：**
1. 产品内分享（转化通常最高）
2. Personalized 链接
3. Email 邀请
4. 社交分享
5. Referral code（适合线下或口头传播）

### 步骤 3：选择激励结构

**单边奖励**（只奖励推荐人）：更简单，适合高价值产品

**双边奖励**（双方都有奖励）：转化通常更高，也更符合 win-win 的感受

**阶梯奖励**：把推荐过程游戏化，能提升参与度

**示例与奖励额度建议**：参见 [references/program-examples.md](references/program-examples.md)

---

## 项目优化

### 提升推荐率

**如果很少客户愿意推荐：**
- 在更好的时机提出邀请
- 简化分享流程
- 测试不同激励形式
- 让推荐入口在产品中更显眼

**如果推荐带来的新用户不转化：**
- 优化被推荐用户的 landing 体验
- 强化新用户端的激励
- 确保能看到推荐人的 endorsement

### 可以跑的 A/B 测试

**激励测试：** 奖励金额、奖励形式、单边 vs 双边、奖励发放时机

**文案测试：** Program 描述、CTA copy、landing page 文案

**位置测试：** 推荐入口出现在哪里、什么时候出现

### 常见问题与修复

| 问题 | 修复方式 |
|---------|-----|
| 认知度低 | 增加更显眼的 in-app 提示 |
| 分享率低 | 简化到一键分享 |
| 转化低 | 优化被推荐用户体验 |
| 欺诈 / 滥用 | 增加验证和限制 |
| 推荐人只推荐一次 | 增加阶梯奖励或游戏化机制 |

---

## 衡量成功

### 关键指标

**项目健康度：**
- Active referrers（过去 30 天内实际推荐过人的人）
- Referral conversion rate
- 奖励获得 / 发放情况

**业务影响：**
- 新客户中由 referral 带来的占比
- Referral CAC 与其他渠道 CAC 对比
- Referred customers 的 LTV
- Referral program ROI

### 典型发现

- Referred customers 的 LTV 往往高出 16-25%
- Referred customers 的 churn 通常低 18-37%
- Referred customers 再去推荐别人的概率往往是普通用户的 2-3 倍

---

## 上线清单

### Before Launch
- [ ] 明确定义 program 目标和成功指标
- [ ] 设计激励结构
- [ ] 搭建或配置 referral 工具
- [ ] 创建 referral landing page
- [ ] 配好 tracking 与 attribution
- [ ] 定义防欺诈规则
- [ ] 制作 terms and conditions
- [ ] 把完整 referral flow 测通

### Launch
- [ ] 向现有客户宣布 program
- [ ] 在产品中加入 referral prompts
- [ ] 在网站里更新 program 说明
- [ ] 让支持团队了解规则

### Post-Launch（前 30 天）
- [ ] 回看 conversion funnel
- [ ] 找出 top referrers
- [ ] 收集用户反馈
- [ ] 修复 friction points
- [ ] 给尚未推荐的人发送 reminder emails

---

## 邮件序列

### Referral Program Launch

```text
Subject: 你现在可以通过分享 [Product] 获得 [reward]

我们的推荐计划刚刚上线！

把 [Product] 分享给朋友，每成功带来一个注册，你就能获得 [reward]。
对方也会得到 [their reward]。

[你的专属 referral link]

1. 分享你的链接
2. 对方注册
3. 你们双方都获得 [reward]
```

### Referral Nurture Sequence

- Day 7：提醒一次 referral program
- Day 30：`“你身边有人也会从这个产品受益吗？”`
- Day 60：分享成功案例 + referral 提示
- 在里程碑后：`“你已经完成了 [X]，你身边还有谁也会想要这个？”`

---

## Affiliate Programs

**更详细的 affiliate 计划设计、佣金结构、招募方法和工具**：参见 [references/affiliate-programs.md](references/affiliate-programs.md)

---

## 任务专属问题

1. 你想做哪一种项目？（referral、affiliate，或两者都做）
2. 你的客户 LTV 和当前 CAC 是多少？
3. 是从零开始，还是已有项目要优化？
4. 你在考虑哪些工具或平台？
5. 你准备拿出多少预算做奖励 / 佣金？
6. 你的产品天然适合被分享吗？

---

## 工具集成

如需真正落地，请参见 [tools registry](../../tools/REGISTRY.md)。关键工具包括：

| 工具 | 最适合 | 指南 |
|------|----------|-------|
| **Rewardful** | Stripe-native affiliate programs | [rewardful.md](../../tools/integrations/rewardful.md) |
| **Tolt** | SaaS affiliate programs | [tolt.md](../../tools/integrations/tolt.md) |
| **Mention Me** | Enterprise referral programs | [mention-me.md](../../tools/integrations/mention-me.md) |
| **Dub.co** | 链接追踪与 attribution | [dub-co.md](../../tools/integrations/dub-co.md) |
| **Stripe** | 支付处理（可配合佣金 tracking） | [stripe.md](../../tools/integrations/stripe.md) |
| **Introw** | 分层 channel partner program、deal registration、QBRs | [introw.md](../../tools/integrations/introw.md) |
| **PartnerStack** | Enterprise partner 与 affiliate programs | [partnerstack.md](../../tools/integrations/partnerstack.md) |

---

## 相关技能

- **launch-strategy**：用于更有效地上线 referral program
- **email-sequence**：用于 referral nurture campaigns
- **marketing-psychology**：用于理解推荐动机
- **analytics-tracking**：用于追踪 referral attribution
