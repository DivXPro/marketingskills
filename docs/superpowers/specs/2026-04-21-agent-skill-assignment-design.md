# Agent Skill Assignment Design

**日期**：2026-04-21  
**范围**：`agents/` 目录下的职能 Agent 与第一梯队 marketing skills 的引用与分配  
**目标**：让各职能 Agent 在执行过程中优先参考匹配的 skill，并形成一份可维护的分配总表，用于说明分配原则、未分配项和重叠情况。

## 背景

当前仓库已经具备两层资产：

- `skills/`：marketing skills 原始能力库，包含英文原版与中文说明版 `SKILL.CN.md`
- `agents/`：面向 social commerce 场景的职能 Agent prompt

现状问题是：

- Agent prompt 里尚未建立明确的 skill 引用规则
- 哪个 Agent 应优先参考哪些 skill 还没有固定下来
- skill 分配是否重叠、哪些尚未分配，也没有统一文档

本次设计不新增新的 skill，不改造 orchestrator 的路由逻辑，只做“第一梯队 skill 的分配与引用”。

## 设计目标

本次改动需要同时满足以下目标：

1. 让相关 Agent 在工作时优先参考匹配的 skill，而不是仅靠人工记忆
2. 引用方式必须足够明确，属于 prompt 级强约束，而不是松散建议
3. 不让 skill 分配破坏现有角色边界，避免每个 Agent 都变成“万能营销顾问”
4. 单独保留一份分配文档，方便后续继续扩展、补空白和调整边界

## 适用范围

本次只处理“第一梯队 skill”：

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

涉及的 Agent：

- `agents/01-account-strategist.md`
- `agents/02-content-producer.md`
- `agents/03-store-operator.md`
- `agents/04-assortment-supply-manager.md`
- `agents/05-growth-amplification-manager.md`
- `agents/06-insights-cx-analyst.md`
- `agents/orchestrator.md`

## 核心方案

采用“双层落地”：

### 层 1：在 Agent prompt 中建立强约束引用

对适配的 Agent 文件增加统一章节：`## Skill 使用规则`

每个 Agent 中至少包含以下内容：

- `优先参考的 skills`：该 Agent 最常用、最相关的 skill
- `触发条件`：遇到哪些任务时必须先参考哪些 skill
- `边界规则`：哪些 skill 只可作为辅助参考，不得用来扩大角色职责

写法要求：

- 明确、可执行，偏 system prompt 风格
- 使用“当任务涉及……，优先参考……”
- 使用“不要自行发明……，先参考……”的强约束句式
- 不写泛泛的技能介绍，不复制 `SKILL.CN.md` 正文

### 层 2：建立单独的 skill 分配总表

新增文档：`agents/skill-assignment.md`

文档需要覆盖：

- 分配原则
- 按 Agent 的 skill 分配
- 按 skill 反向查看归属
- 哪些已分配，哪些尚未分配
- 重叠度与重叠原因

## 分配原则

### 1. 基础上下文优先

`product-marketing-context` 作为所有 Agent 可共享的基础 skill，但只作为“通用前置上下文”，不作为某一职能能力的唯一 owner。

### 2. 每个 skill 尽量只有一个核心 owner

每个第一梯队 skill 优先指定一个核心 owner Agent，用于体现主归属。  
其他 Agent 如需引用，只标记为“协作引用”。

### 3. 重叠必须有理由

允许重叠，但必须属于以下类型之一：

- 同一 skill 为上游策略与下游执行同时提供支持
- 同一 skill 既用于产出，也用于复盘
- 同一 skill 作为基础方法论，被多个 Agent 合理共享

### 4. orchestrator 不抢 owner

`orchestrator` 只作为调度与停机判断角色，不作为任何第一梯队 skill 的核心 owner。  
它只允许少量“协作引用”，用于判断何时该调用哪些职能 Agent。

### 5. 未分配是明确状态，不是遗漏

如果某个 skill 当前不适合稳定挂到任何 Agent，或者只适合临时辅助，就在总表中明确标记“未分配”或“暂不设 owner”，而不是强塞到某个 Agent。

## 初步分配设计

### 账号主理 / 内容策略官

核心 owner：

- `marketing-ideas`
- `marketing-psychology`

协作引用：

- `product-marketing-context`
- `customer-research`
- `pricing-strategy`

理由：

- 负责方向、定位、内容支柱、活动节奏，最适合承接创意、策略与心理驱动相关 skill
- 需要基于上下文与用户洞察工作，但不应吞掉具体内容生产或投放执行

### 内容制作官

核心 owner：

- `social-content`
- `copywriting`
- `copy-editing`

协作引用：

- `customer-research`
- `marketing-psychology`

理由：

- 核心任务是把策略和商品卖点变成可发布内容
- 需要直接借助内容和文案技能
- 用户语言和心理触发适合作为辅助输入，而不是其主职责来源

### 店铺运营官

核心 owner：

- `pricing-strategy`

协作引用：

- `copywriting`
- `copy-editing`

理由：

- 负责商品承接、活动承接、价格结构和转化表达
- `pricing-strategy` 更接近其日常判断
- 文案类 skill 主要用于标题、卖点、详情页优化

### 选品与供给官

核心 owner：

- 暂不设

协作引用：

- `customer-research`
- `pricing-strategy`
- `marketing-ideas`

理由：

- 仓库当前没有专门面向“选品 / 货盘 / 供给 / 履约”的第一梯队 skill
- 强行指定 owner 容易失真
- 通过协作引用先补足能力，再为未来自建 skill 留出空间

### 投放与增长官

核心 owner：

- `paid-ads`
- `ad-creative`
- `analytics-tracking`
- `ab-test-setup`

协作引用：

- `social-content`

理由：

- 与现有 marketing skills 的匹配度最高
- 负责投流、素材、测量、实验设计，是四个增长相关 skill 的天然 owner

### 数据复盘与客服体验官

核心 owner：

- `customer-research`

协作引用：

- `analytics-tracking`
- `ab-test-setup`

理由：

- 该角色更偏“归因、洞察、反馈整理、问题回流”
- `customer-research` 适合作为它的主要方法来源
- 数据与实验类 skill 会频繁使用，但 owner 更适合放在增长角色

### Orchestrator

核心 owner：

- 不设

协作引用：

- `product-marketing-context`
- `analytics-tracking`
- `ab-test-setup`

理由：

- 只负责判断何时需要上下文、测量与实验纪律
- 不直接产出专业结论

## 未分配口径

当前“未分配”分两种情况：

### 1. 没有核心 owner，但有协作引用

例如：

- `product-marketing-context`

说明：

- 它会被多个 Agent 使用，但不适合收归某一个 Agent 独占

### 2. 当前明确不设核心 owner

例如：

- `选品与供给官` 暂无专属第一梯队 skill

说明：

- 这是能力空白的记录，不是文档遗漏
- 后续可通过新增 `social-commerce-merchandising` 或 `platform-store-ops` 类 skill 补齐

## 重叠度设计

总表中的重叠度按以下口径描述：

- `低重叠`：该 skill 只有 1 个 owner，且仅 0-1 个协作引用 Agent
- `中重叠`：该 skill 有 1 个 owner，且 2-3 个 Agent 合理协作引用
- `高重叠`：该 skill 被 4 个及以上 Agent 引用，需检查是否过于泛化

同时给出重叠原因：

- `基础上下文共享`
- `上游策略与下游执行共享`
- `产出与复盘共享`
- `边界风险，需要后续收敛`

## 文件改动设计

### 需要修改

- `agents/01-account-strategist.md`
- `agents/02-content-producer.md`
- `agents/03-store-operator.md`
- `agents/04-assortment-supply-manager.md`
- `agents/05-growth-amplification-manager.md`
- `agents/06-insights-cx-analyst.md`
- `agents/orchestrator.md`

### 需要新增

- `agents/skill-assignment.md`

### 不改动

- `skills/` 下已有 `SKILL.md` 与 `SKILL.CN.md`
- `README.md` 与 `README.CN.md`

## 具体改法

### Agent 文件改法

在每个相关 Agent 文件中新增一个统一章节：

- `## Skill 使用规则`

章节内容结构固定为：

- 优先参考的 skills
- 必须触发的情形
- 只可辅助参考的 skills
- 不要越界的说明

### 总表文档改法

`agents/skill-assignment.md` 采用以下结构：

- 第一梯队 skill 范围
- 分配原则
- 按 Agent 分配
- 按 skill 反查
- 未分配情况
- 重叠度分析
- 后续建议

## 风险与控制

### 风险 1：Agent 被塞入过多 skill

控制方式：

- 坚持 owner 与协作引用分层
- 不让每个 Agent 都挂满全部第一梯队 skill

### 风险 2：orchestrator 越界

控制方式：

- orchestrator 只保留少量协作引用
- 不让其成为任何第一梯队 skill 的 owner

### 风险 3：选品与供给官被错误包装为“已完善”

控制方式：

- 在总表中明确记录其专属 skill 仍为空白
- 把“未分配”视为显式设计结果

## 验收标准

完成后应满足：

1. 每个相关 Agent 文件都能直接看出“遇到什么任务优先参考哪些 skill”
2. `agents/skill-assignment.md` 能完整说明如何分配、哪些还未分配、重叠度如何判断
3. 不会出现 orchestrator 抢 owner 或角色职责明显越界
4. 第一梯队 skill 都能在总表中被追踪到归属状态
