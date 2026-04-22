# Agent Skill Assignment Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** 为各职能 Agent 建立第一梯队 skill 的强约束引用规则，并新增一份总表文档，说明分配方式、未分配项和重叠度。

**Architecture:** 保持现有 `agents/*.md` 的 prompt 结构不变，仅在每个相关 Agent 中追加统一的 `## Skill 使用规则` 章节。新增 `agents/skill-assignment.md` 作为全局分配总表，记录 owner、协作引用、未分配和重叠分析，避免把 skill 分配逻辑散落在各个文件中。

**Tech Stack:** Markdown, existing `agents/` prompt files, existing `skills/*/SKILL.CN.md`, VS Code diagnostics

---

### Task 1: Add Skill Rules To Strategy And Content Agents

**Files:**
- Modify: `/Users/huhui/Projects/marketingskills/agents/01-account-strategist.md`
- Modify: `/Users/huhui/Projects/marketingskills/agents/02-content-producer.md`
- Test: `/Users/huhui/Projects/marketingskills/agents/01-account-strategist.md`
- Test: `/Users/huhui/Projects/marketingskills/agents/02-content-producer.md`

- [ ] **Step 1: Read the current agent prompts and confirm insertion point**

Read the full files and append the new section after `## 默认输出格式` code block so the current role definition stays unchanged.

Run:

```bash
python3 - <<'PY'
from pathlib import Path
for p in [
    Path('/Users/huhui/Projects/marketingskills/agents/01-account-strategist.md'),
    Path('/Users/huhui/Projects/marketingskills/agents/02-content-producer.md'),
]:
    text = p.read_text()
    print(p.name, '## Skill 使用规则' in text)
PY
```

Expected: `False` for both files before the change.

- [ ] **Step 2: Add strong-reference rules to `01-account-strategist.md`**

Append this section:

```md
## Skill 使用规则

### 优先参考的 skills

- `product-marketing-context`：在制定周目标、账号定位、用户分层和活动节奏前，先统一产品、用户和定位上下文
- `marketing-ideas`：在需要新的增长方向、内容主题、活动切入点和主推思路时优先参考
- `marketing-psychology`：在需要判断触发机制、购买动机、阻力与说服结构时优先参考
- `customer-research`：在需要基于评论、私信、客服反馈和用户语言调整策略时优先参考
- `pricing-strategy`：在任务涉及价格带、套餐、利益点和活动结构时优先参考

### 必须触发的情形

- 当任务涉及“先搞清产品、受众、定位”时，先参考 `product-marketing-context`
- 当任务涉及“本周做什么、主推什么、有什么新打法”时，先参考 `marketing-ideas`
- 当任务涉及“为什么用户会买、为什么不买、应该打什么心理钩子”时，先参考 `marketing-psychology`
- 当任务涉及“用户在说什么、真实问题是什么、应该如何调整内容和策略”时，先参考 `customer-research`
- 当任务涉及“价格、套餐、优惠、利益点结构”时，不要自行发明定价框架，先参考 `pricing-strategy`

### 只可辅助参考的 skills

- `copywriting` 和 `social-content` 只用于帮助理解下游执行表达，不用于替代 `内容制作官`
- `analytics-tracking` 和 `ab-test-setup` 只用于理解后续验证和复盘方式，不用于替代 `投放与增长官` 或 `数据复盘与客服体验官`

### 不要越界

- 不要把 `marketing-ideas` 用成直接产出脚本的工具，脚本交给 `内容制作官`
- 不要把 `pricing-strategy` 用成直接拍板促销配置的工具，承接配置交给 `店铺运营官`
- 不要把 `customer-research` 用成完整复盘归因的替代，复盘结论优先结合 `数据复盘与客服体验官`
```

- [ ] **Step 3: Add strong-reference rules to `02-content-producer.md`**

Append this section:

```md
## Skill 使用规则

### 优先参考的 skills

- `social-content`：在生成平台内容方向、选题、结构、平台适配和发布形态时优先参考
- `copywriting`：在撰写核心卖点、标题、钩子、正文和评论区引导时优先参考
- `copy-editing`：在精修表达、去冗余、增强清晰度和统一语气时优先参考
- `customer-research`：在任务涉及用户原话、高频问题、购买阻力和真实需求时优先参考
- `marketing-psychology`：在任务涉及说服逻辑、行为触发、损失规避和转化动机时优先参考

### 必须触发的情形

- 当任务涉及“不同平台应该怎么写、怎么改、怎么发”时，先参考 `social-content`
- 当任务涉及“把卖点写成能发出去的标题、脚本、图文结构”时，先参考 `copywriting`
- 当任务涉及“已有文案不顺、不清楚、不够有说服力”时，先参考 `copy-editing`
- 当任务涉及“用户常见问题、顾虑、评论反馈要前置进内容”时，先参考 `customer-research`
- 当任务涉及“内容要靠什么心理机制驱动点击、停留、进店或下单”时，先参考 `marketing-psychology`

### 只可辅助参考的 skills

- `ad-creative` 仅在内容要给投流和达人合作复用时辅助参考，不替代 `投放与增长官`
- `pricing-strategy` 仅在内容涉及套餐、利益点和价格表达时辅助参考，不替代 `店铺运营官`
- `product-marketing-context` 作为前置上下文使用，不替代 `账号主理` 的策略判断

### 不要越界

- 不要直接用 `social-content` 取代内容目标判断，目标仍以 `账号主理` 输入为准
- 不要用 `pricing-strategy` 直接定义促销和承接配置，商品页和活动机制交给 `店铺运营官`
- 不要把 `customer-research` 当成复盘代理，内容结论需要和 `数据复盘与客服体验官` 的反馈对齐
```

- [ ] **Step 4: Run a quick structural check**

Run:

```bash
python3 - <<'PY'
from pathlib import Path
for p in [
    Path('/Users/huhui/Projects/marketingskills/agents/01-account-strategist.md'),
    Path('/Users/huhui/Projects/marketingskills/agents/02-content-producer.md'),
]:
    text = p.read_text()
    assert '## Skill 使用规则' in text
    assert '### 优先参考的 skills' in text
    assert '### 必须触发的情形' in text
    assert '### 不要越界' in text
print('ok')
PY
```

Expected: `ok`

### Task 2: Add Skill Rules To Operations, Growth, Insights, And Orchestrator

**Files:**
- Modify: `/Users/huhui/Projects/marketingskills/agents/03-store-operator.md`
- Modify: `/Users/huhui/Projects/marketingskills/agents/04-assortment-supply-manager.md`
- Modify: `/Users/huhui/Projects/marketingskills/agents/05-growth-amplification-manager.md`
- Modify: `/Users/huhui/Projects/marketingskills/agents/06-insights-cx-analyst.md`
- Modify: `/Users/huhui/Projects/marketingskills/agents/orchestrator.md`
- Test: `/Users/huhui/Projects/marketingskills/agents/03-store-operator.md`
- Test: `/Users/huhui/Projects/marketingskills/agents/04-assortment-supply-manager.md`
- Test: `/Users/huhui/Projects/marketingskills/agents/05-growth-amplification-manager.md`
- Test: `/Users/huhui/Projects/marketingskills/agents/06-insights-cx-analyst.md`
- Test: `/Users/huhui/Projects/marketingskills/agents/orchestrator.md`

- [ ] **Step 1: Add skill rules to `03-store-operator.md`**

Append a section mapping `pricing-strategy` as the primary skill, with `copywriting` and `copy-editing` as supporting skills, and explicit rules that `page-cro` is not part of the first-tier rollout.

- [ ] **Step 2: Add skill rules to `04-assortment-supply-manager.md`**

Append a section with no owner skill, but explicit collaborative references to `customer-research`, `pricing-strategy`, and `marketing-ideas`, including a note that this role still lacks a dedicated first-tier skill.

- [ ] **Step 3: Add skill rules to `05-growth-amplification-manager.md`**

Append a section prioritizing `paid-ads`, `ad-creative`, `analytics-tracking`, and `ab-test-setup`, with `social-content` as supporting input for reusable creatives.

- [ ] **Step 4: Add skill rules to `06-insights-cx-analyst.md`**

Append a section prioritizing `customer-research`, with `analytics-tracking` and `ab-test-setup` as supporting skills for evidence collection and follow-up validation.

- [ ] **Step 5: Add skill rules to `orchestrator.md`**

Append a section that limits orchestrator to contextual references only:

- `product-marketing-context` for missing-context checks
- `analytics-tracking` for identifying missing measurement prerequisites
- `ab-test-setup` for deciding when a problem should turn into a hypothesis or experiment

and explicitly states that orchestrator does not own any first-tier skill.

- [ ] **Step 6: Run a batch structure check**

Run:

```bash
python3 - <<'PY'
from pathlib import Path
paths = [
    Path('/Users/huhui/Projects/marketingskills/agents/03-store-operator.md'),
    Path('/Users/huhui/Projects/marketingskills/agents/04-assortment-supply-manager.md'),
    Path('/Users/huhui/Projects/marketingskills/agents/05-growth-amplification-manager.md'),
    Path('/Users/huhui/Projects/marketingskills/agents/06-insights-cx-analyst.md'),
    Path('/Users/huhui/Projects/marketingskills/agents/orchestrator.md'),
]
for p in paths:
    text = p.read_text()
    assert '## Skill 使用规则' in text, p
    assert '### 优先参考的 skills' in text, p
print('ok')
PY
```

Expected: `ok`

### Task 3: Create The Global Assignment Document

**Files:**
- Create: `/Users/huhui/Projects/marketingskills/agents/skill-assignment.md`
- Test: `/Users/huhui/Projects/marketingskills/agents/skill-assignment.md`

- [ ] **Step 1: Create the document with the agreed structure**

Write `agents/skill-assignment.md` with these sections:

- `# Agent Skill 分配总表`
- `## 第一梯队 skill 范围`
- `## 分配原则`
- `## 按 Agent 分配`
- `## 按 Skill 反查`
- `## 未分配与暂不设 owner`
- `## 重叠度分析`
- `## 后续建议`

- [ ] **Step 2: Fill the agent-to-skill mapping**

Document these core owner relationships:

- `账号主理` → `marketing-ideas`, `marketing-psychology`
- `内容制作官` → `social-content`, `copywriting`, `copy-editing`
- `店铺运营官` → `pricing-strategy`
- `投放与增长官` → `paid-ads`, `ad-creative`, `analytics-tracking`, `ab-test-setup`
- `数据复盘与客服体验官` → `customer-research`

Document these explicit non-owner states:

- `product-marketing-context` has no single owner and is shared as foundational context
- `选品与供给官` currently has no dedicated first-tier owner skill
- `orchestrator` has no owner skills

- [ ] **Step 3: Add overlap analysis**

Include a small table with one row per first-tier skill and these columns:

- `Skill`
- `核心 owner`
- `协作引用 Agent`
- `重叠度`
- `说明`

Use the agreed overlap labels:

- `低重叠`
- `中重叠`
- `高重叠`

- [ ] **Step 4: Run a content sanity check**

Run:

```bash
python3 - <<'PY'
from pathlib import Path
p = Path('/Users/huhui/Projects/marketingskills/agents/skill-assignment.md')
text = p.read_text()
required = [
    '# Agent Skill 分配总表',
    '## 按 Agent 分配',
    '## 按 Skill 反查',
    '## 未分配与暂不设 owner',
    '## 重叠度分析',
    'product-marketing-context',
    'marketing-ideas',
    'paid-ads',
]
for item in required:
    assert item in text, item
print('ok')
PY
```

Expected: `ok`

### Task 4: Verify Markdown Diagnostics And Finish

**Files:**
- Test: `/Users/huhui/Projects/marketingskills/agents/01-account-strategist.md`
- Test: `/Users/huhui/Projects/marketingskills/agents/02-content-producer.md`
- Test: `/Users/huhui/Projects/marketingskills/agents/03-store-operator.md`
- Test: `/Users/huhui/Projects/marketingskills/agents/04-assortment-supply-manager.md`
- Test: `/Users/huhui/Projects/marketingskills/agents/05-growth-amplification-manager.md`
- Test: `/Users/huhui/Projects/marketingskills/agents/06-insights-cx-analyst.md`
- Test: `/Users/huhui/Projects/marketingskills/agents/orchestrator.md`
- Test: `/Users/huhui/Projects/marketingskills/agents/skill-assignment.md`

- [ ] **Step 1: Run diagnostics on all edited markdown files**

Use the editor diagnostics for all eight files and confirm there are no introduced markdown issues.

- [ ] **Step 2: Read back the final files**

Spot-check:

- `/Users/huhui/Projects/marketingskills/agents/01-account-strategist.md`
- `/Users/huhui/Projects/marketingskills/agents/05-growth-amplification-manager.md`
- `/Users/huhui/Projects/marketingskills/agents/skill-assignment.md`

Confirm:

- each file contains the new section
- the owner/collaboration split matches the design
- `orchestrator` remains non-owner

- [ ] **Step 3: Commit**

```bash
git add \
  /Users/huhui/Projects/marketingskills/agents/01-account-strategist.md \
  /Users/huhui/Projects/marketingskills/agents/02-content-producer.md \
  /Users/huhui/Projects/marketingskills/agents/03-store-operator.md \
  /Users/huhui/Projects/marketingskills/agents/04-assortment-supply-manager.md \
  /Users/huhui/Projects/marketingskills/agents/05-growth-amplification-manager.md \
  /Users/huhui/Projects/marketingskills/agents/06-insights-cx-analyst.md \
  /Users/huhui/Projects/marketingskills/agents/orchestrator.md \
  /Users/huhui/Projects/marketingskills/agents/skill-assignment.md \
  /Users/huhui/Projects/marketingskills/docs/superpowers/specs/2026-04-21-agent-skill-assignment-design.md \
  /Users/huhui/Projects/marketingskills/docs/superpowers/plans/2026-04-21-agent-skill-assignment.md
git commit -m "feat: assign first-tier skills to agents"
```

Expected: a clean commit containing the prompt updates, the assignment table, the design doc, and this plan file.
