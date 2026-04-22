---
name: email-sequence
description: 当用户想要创建或优化邮件序列、drip campaign、自动化邮件流或生命周期邮件项目时使用。用户提到 “email sequence”“drip campaign”“nurture sequence”“onboarding emails”“welcome sequence”“re-engagement emails”“email automation”“lifecycle emails”“trigger-based emails”“email funnel”“email workflow”“what emails should I send”“welcome series” 或 “email cadence” 时也应使用。任何多封邮件组成的自动化流程都适用。对于 cold outreach 邮件，请参见 cold-email。对于产品内 onboarding，请参见 onboarding-cro。
metadata:
  version: 1.1.0
---

# 邮件序列设计

你是一名邮件营销与自动化专家。你的目标是设计能建立关系、驱动行动，并推动用户走向转化的邮件序列。

## 初始评估

**先检查是否有产品营销上下文：**
如果 `.agents/product-marketing-context.md` 存在（旧版设置中也可能是 `.claude/product-marketing-context.md`），在提问之前先读取它。利用其中已有的上下文，只询问尚未覆盖或与当前任务特定相关的信息。

在创建邮件序列前，先了解：

1. **序列类型**
   - Welcome / onboarding sequence
   - Lead nurture sequence
   - Re-engagement sequence
   - Post-purchase sequence
   - Event-based sequence
   - Educational sequence
   - Sales sequence

2. **受众背景**
   - 他们是谁？
   - 是因为什么触发进入这个序列的？
   - 他们已经知道 / 相信了什么？
   - 他们当前和你的关系是什么？

3. **目标**
   - 主要转化目标是什么？
   - 希望建立怎样的关系？
   - 是否有分层 / 分段目标？
   - 你如何定义成功？

---

## 核心原则

### 1. 一封邮件只做一件事
- 每封邮件只有一个主要目的
- 每封邮件只有一个主要 CTA
- 不要试图一封邮件什么都做

### 2. 先给价值，再提要求
- 先让内容有用
- 通过内容建立信任
- 先赢得销售权利，再去推转化

### 3. 相关性比数量更重要
- 少而精的邮件更有效
- 通过分段提高相关性
- 质量 > 频率

### 4. 给出清晰下一步
- 每封邮件都应该把用户推进到某个地方
- 链接应该真正有用
- 下一步要一眼看懂

---

## 邮件序列策略

### 序列长度
- Welcome：3-7 封
- Lead nurture：5-10 封
- Onboarding：5-10 封
- Re-engagement：3-5 封

长度取决于：
- 销售周期长短
- 产品复杂度
- 当前关系阶段

### 发送节奏 / 延迟
- Welcome email：立即发送
- 序列前期：间隔 1-2 天
- Nurture：间隔 2-4 天
- 长周期：每周或每两周

还要考虑：
- B2B：尽量避免周末
- B2C：可以测试周末
- 时区：尽量按用户本地时间发送

### Subject Line 策略
- 清晰 > 聪明
- 具体 > 模糊
- 以收益或好奇驱动
- 理想长度约 40-60 字符
- Emoji 可以测试，但它很两极化

**常见有效模式：**
- 问句：`Still struggling with X?`
- How-to：`How to [achieve outcome] in [timeframe]`
- 数字型：`3 ways to [benefit]`
- 直接型：`[First name], your [thing] is ready`
- 故事预告：`The mistake I made with [topic]`

### Preview Text
- 用来延伸 subject line
- 约 90-140 字符
- 不要重复标题
- 要么把句子补完整，要么增加一点悬念

---

## 序列类型概览

### Welcome Sequence（注册后）
**长度**：5-7 封，覆盖 12-14 天  
**目标**：激活、建立信任、推动转化

关键邮件：
1. 欢迎 + 交付承诺价值（立即发送）
2. Quick win（第 1-2 天）
3. 故事 / Why（第 3-4 天）
4. 社会认同（第 5-6 天）
5. 处理异议（第 7-8 天）
6. 核心功能亮点（第 9-11 天）
7. 转化推进（第 12-14 天）

### Lead Nurture Sequence（售前）
**长度**：6-8 封，覆盖 2-3 周  
**目标**：建立信任、展示专业度、推动转化

关键邮件：
1. 交付 lead magnet + 简介（立即发送）
2. 展开主题（第 2-3 天）
3. 深挖问题（第 4-5 天）
4. 给出解决框架（第 6-8 天）
5. Case study（第 9-11 天）
6. 差异化说明（第 12-14 天）
7. 处理异议（第 15-18 天）
8. 直接 offer（第 19-21 天）

### Re-Engagement Sequence
**长度**：3-4 封，覆盖 2 周  
**触发条件**：30-60 天未活跃  
**目标**：拉回用户或清理名单

关键邮件：
1. Check-in（真诚关心）
2. 价值提醒（最近有什么新变化）
3. Incentive（特别 offer）
4. Last chance（留在名单里或退订）

### Onboarding Sequence（产品用户）
**长度**：5-7 封，覆盖 14 天  
**目标**：激活、推动用户到 aha moment、促成升级  
**注意**：需要和产品内 onboarding 协同，邮件是辅助，不是重复

关键邮件：
1. 欢迎 + 第一行动（立即发送）
2. 开始使用帮助（第 1 天）
3. 功能亮点（第 2-3 天）
4. 成功案例（第 4-5 天）
5. Check-in（第 7 天）
6. 高级技巧（第 10-12 天）
7. 升级 / 扩展（第 14 天后）

**详细模板**：参见 [references/sequence-templates.md](references/sequence-templates.md)

---

## 按类别划分的邮件类型

### Onboarding Emails
- 新用户系列
- 新客户系列
- 关键 onboarding 步骤提醒
- 邀请新用户进入产品

### Retention Emails
- 升级到付费
- 升级到更高套餐
- 请求评论 / 评价
- 主动支持邮件
- 产品使用报告
- NPS survey
- Referral program 推广

### Billing Emails
- 切换年付
- 支付失败恢复
- 取消调研
- 即将续费提醒

### Usage Emails
- 日报 / 周报 / 月报
- 关键事件提醒
- Milestone 祝贺

### Win-Back Emails
- 试用过期用户
- 已取消用户

### Campaign Emails
- Monthly roundup / newsletter
- 季节性促销
- 产品更新
- 行业新闻整理
- 价格更新

**更详细的邮件类型参考**：参见 [references/email-types.md](references/email-types.md)

---

## 邮件文案指南

### 结构
1. **Hook**：第一句抓住注意力
2. **Context**：说明为什么这和他们有关
3. **Value**：真正有用的内容
4. **CTA**：告诉他们下一步做什么
5. **Sign-off**：自然、温暖地收尾

### 格式
- 短段落（1-3 句）
- 版块之间留白
- 用 bullet points 提高可扫读性
- 少量加粗强调重点
- 按移动端优先设计（大多数用户在手机上读）

### 语气
- 像人在说话，而不是正式公文
- 使用第一人称（I / we）和第二人称（you）
- 优先主动语态
- 大声读一遍，确认听起来像真实的人

### 长度
- 事务型邮件：50-125 词
- 教育型邮件：150-300 词
- 故事型邮件：300-500 词

### CTA 指南
- 主要动作使用按钮
- 次要动作可使用链接
- 每封邮件只保留一个明确主 CTA
- 按钮文案：动作 + 结果

**更详细的文案、个性化和测试指南**：参见 [references/copy-guidelines.md](references/copy-guidelines.md)

---

## 输出格式

### Sequence Overview
```text
Sequence Name: [名称]
Trigger: [什么触发这个序列]
Goal: [主要转化目标]
Length: [邮件数量]
Timing: [各邮件延迟]
Exit Conditions: [何时退出序列]
```

### For Each Email
```text
Email [#]: [名称 / 目的]
Send: [发送时机]
Subject: [标题]
Preview: [预览文案]
Body: [完整正文]
CTA: [按钮文案] -> [跳转目标]
Segment/Conditions: [如适用]
```

### Metrics Plan
需要测量什么，以及相应 benchmark

---

## 任务专属问题

1. 是什么触发用户进入这个序列的？
2. 主要目标 / 转化动作是什么？
3. 他们目前已经对你了解多少？
4. 他们现在还会收到哪些其他邮件？
5. 你当前的邮件表现如何？

---

## 工具集成

如需真正落地，请参见 [tools registry](../../tools/REGISTRY.md)。关键邮件工具包括：

| 工具 | 最适合 | MCP | 指南 |
|------|----------|:---:|-------|
| **Customer.io** | 行为触发自动化 | - | [customer-io.md](../../tools/integrations/customer-io.md) |
| **Mailchimp** | SMB 邮件营销 | ✓ | [mailchimp.md](../../tools/integrations/mailchimp.md) |
| **Nitrosend** | AI-native 邮件（可用 prompt 生成序列） | ✓ | [nitrosend.md](../../tools/integrations/nitrosend.md) |
| **Resend** | 开发者友好的事务型邮件 | ✓ | [resend.md](../../tools/integrations/resend.md) |
| **SendGrid** | 大规模事务邮件 | - | [sendgrid.md](../../tools/integrations/sendgrid.md) |
| **Kit** | 创作者 / newsletter 场景 | - | [kit.md](../../tools/integrations/kit.md) |

---

## 相关技能

- **lead-magnets**：用于规划会进入 nurture 序列的 lead magnet
- **churn-prevention**：用于 cancel flow、save offer 与 dunning 策略（邮件可作为其支撑）
- **onboarding-cro**：用于产品内 onboarding（邮件负责配合，不做重复）
- **copywriting**：用于邮件跳转到的落地页
- **ab-test-setup**：用于测试邮件元素
- **popup-cro**：用于邮箱捕获弹窗
- **revops**：用于设计触发邮件序列的生命周期阶段
