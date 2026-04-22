# Second-Tier Skill Assignment Design

**日期**：2026-04-21  
**范围**：为现有 social commerce harness 增补第二梯队 skill 分配，并同步更新 `agents/*.md` 的 `Skill 使用规则` 与 `agents/skill-assignment.md` 总表。  
**目标**：让第二梯队 skill 不只是出现在总表里，也能直接进入各职能 Agent 的执行提示中，用于实际工作时的参考与约束。

## 背景

当前仓库已经完成第一梯队 skill 分配，覆盖：

- `product-marketing-context`
- `social-content`
- `copywriting`
- `copy-editing`
- `customer-research`
- `paid-ads`
- `ad-creative`
- `analytics-tracking`
- `ab-test-setup`
- `pricing-strategy`
- `marketing-ideas`
- `marketing-psychology`

并已落到：

- `agents/*.md` 的 `## Skill 使用规则`
- `agents/skill-assignment.md`

现在需要继续把第二梯队 skill 纳入体系，但要避免两个问题：

1. 把所有候选 skill 机械地塞进所有 Agent，导致边界模糊
2. 只更新总表，不更新 Agent prompt，最终文档和执行脱节

因此本轮采用“双更新”：

- 更新总表
- 同步更新相关 Agent 的 `Skill 使用规则`

## 本轮处理的第二梯队

本轮纳入以下第二梯队 skill：

- `launch-strategy` / 发布策略
- `community-marketing` / 社区营销
- `referral-program` / 推荐计划
- `email-sequence` / 邮件序列
- `page-cro` / 页面转化优化
- `churn-prevention` / 流失预防

## 设计目标

本轮设计需要满足：

1. 第二梯队 skill 进入总表，形成与第一梯队一致的 owner / 协作引用 / 重叠分析
2. 相关 Agent prompt 同步增加第二梯队的强约束引用，而不是只写在总表
3. 不改变第一梯队已经稳定下来的 owner 结构
4. `orchestrator` 继续保持非 owner 身份

## 核心方案

采用“方案 2：总表 + agent 引用”。

### 层 1：更新总表

对 `agents/skill-assignment.md` 增加第二梯队内容：

- 第二梯队 skill 范围
- 中文对照
- 按 Agent 分配
- 按 Skill 反查
- 未分配说明
- 重叠度分析

### 层 2：更新 Agent prompt

对相关 Agent 的 `## Skill 使用规则` 做增量扩展，增加第二梯队 skill 的：

- 优先参考
- 必须触发的情形
- 只可辅助参考的 skills
- 不要越界

## 第二梯队初步分配

### 账号主理 / 内容策略官

核心 owner：

- `launch-strategy` / 发布策略

协作引用：

- `community-marketing` / 社区营销

理由：

- `launch-strategy` 更接近活动节奏、主题包装、发布时间线和组织逻辑
- `community-marketing` 对账号主理有价值，但更适合作为长期互动和氛围建设的辅助输入

### 内容制作官

核心 owner：

- `email-sequence` / 邮件序列

协作引用：

- `community-marketing` / 社区营销

理由：

- `email-sequence` 仍然是内容触达产物，适合由内容制作官掌握表达与结构
- `community-marketing` 对内容选题和互动表达有帮助，但不是其主 owner

### 店铺运营官

核心 owner：

- `page-cro` / 页面转化优化

理由：

- 在当前无独立站场景下，`page-cro` 不再只指网站落地页，也可迁移到商品详情页、活动页、店铺首页和直播承接页
- 与店铺运营官的职责边界最贴合

### 投放与增长官

核心 owner：

- `referral-program` / 推荐计划

协作引用：

- `launch-strategy` / 发布策略

理由：

- `referral-program` 更接近增长机制设计与放大逻辑
- `launch-strategy` 对活动放量有帮助，但不应从账号主理手中抢 owner

### 数据复盘与客服体验官

核心 owner：

- `churn-prevention` / 流失预防

理由：

- 当前 harness 里最接近取消、退款、流失、挽回视角的是该角色
- 该 skill 与客服反馈、退款原因、挽回动作天然相关

### 选品与供给官

核心 owner：

- 暂不设

协作引用：

- `page-cro` / 页面转化优化
- `churn-prevention` / 流失预防

理由：

- 第二梯队也没有直接命中“选品 / 供给 / 履约”本身的方法 skill
- 继续保留空白位，避免虚假补全

### Orchestrator

核心 owner：

- 不设

协作引用：

- `launch-strategy` / 发布策略
- `page-cro` / 页面转化优化
- `churn-prevention` / 流失预防

理由：

- 仅用于判断任务是否已进入发布编排、承接优化或流失诊断阶段
- 不直接替代具体职能角色产出结论

## 不接入或不设 owner 的原则

### `community-marketing`

本轮不设唯一 owner。

原因：

- 它同时影响账号主理的长期品牌与内容主题判断
- 也影响内容制作官的互动形式、社区话题和表达方式
- 现阶段更适合作为双协作 skill，而不是硬指定单 owner

### `选品与供给官`

本轮仍不设第二梯队 owner。

原因：

- 第二梯队新增 skill 依然不能直接覆盖货盘、供给、履约和商品结构的经营判断

## 重叠度口径

沿用第一梯队规则：

- `低重叠`：1 个核心 owner，0-1 个协作引用 Agent
- `中重叠`：1 个核心 owner，2-3 个协作引用 Agent
- `高重叠`：4 个及以上 Agent 引用，或无 owner 但被广泛共享

本轮重点关注的高风险点：

- `community-marketing` 是否需要 owner
- `page-cro` 在店铺运营官之外是否被过多角色扩散
- `launch-strategy` 是否会与账号主理已有策略能力过度重叠

## 文件改动设计

### 需要修改

- `agents/01-account-strategist.md`
- `agents/02-content-producer.md`
- `agents/03-store-operator.md`
- `agents/04-assortment-supply-manager.md`
- `agents/05-growth-amplification-manager.md`
- `agents/06-insights-cx-analyst.md`
- `agents/orchestrator.md`
- `agents/skill-assignment.md`

### 不改动

- 现有 `skills/*/SKILL.md`
- 现有 `skills/*/SKILL.CN.md`
- 第一梯队的 owner 归属口径

## Agent prompt 的具体改法

### 账号主理

增加：

- 何时优先参考 `launch-strategy`
- 何时把 `community-marketing` 当作辅助输入

### 内容制作官

增加：

- 何时优先参考 `email-sequence`
- 何时参考 `community-marketing` 进行互动与社群表达设计

### 店铺运营官

增加：

- 何时优先参考 `page-cro`
- 明确 `page-cro` 在当前场景下等价于商品页、活动页、店铺首页承接优化

### 选品与供给官

增加：

- `page-cro` 和 `churn-prevention` 只做辅助参考
- 继续明确“没有第二梯队 owner skill”

### 投放与增长官

增加：

- 何时优先参考 `referral-program`
- 何时辅助参考 `launch-strategy`

### 数据复盘与客服体验官

增加：

- 何时优先参考 `churn-prevention`

### Orchestrator

增加：

- 何时把问题判断为发布编排问题
- 何时把问题判断为承接优化问题
- 何时把问题判断为流失/退款/挽回问题

## 风险与控制

### 风险 1：第二梯队让边界变宽

控制方式：

- 保持 owner 数量克制
- 对 `community-marketing` 不强设 owner
- 对 `选品与供给官` 不虚构完整能力

### 风险 2：`page-cro` 被误读为网站专属

控制方式：

- 在文档和 Agent prompt 中明确其在当前场景下迁移到商品详情页、活动页和店铺承接页

### 风险 3：第二梯队与第一梯队打架

控制方式：

- 第二梯队只做增量补充，不推翻第一梯队已定 owner

## 验收标准

完成后应满足：

1. `agents/skill-assignment.md` 能同时覆盖第一梯队和第二梯队
2. 相关 Agent 的 `Skill 使用规则` 中出现第二梯队 skill 的触发逻辑
3. `orchestrator` 继续不设 owner
4. `community-marketing` 的非 owner 状态被明确记录
5. `page-cro` 被明确解释为当前平台电商承接场景下的迁移用法
