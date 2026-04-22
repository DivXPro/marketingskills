# Second-Tier Skill Assignment Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** 将第二梯队 skill 接入现有 social commerce harness，同时更新 `agents/skill-assignment.md` 和相关 `agents/*.md` 的 `Skill 使用规则`。

**Architecture:** 继续沿用第一梯队的 owner / 协作引用 / 未分配结构，不推翻现有 owner 口径。对 `agents/skill-assignment.md` 做扩展，增加第二梯队的范围、中文对照、按 Agent 分配、按 Skill 反查、未分配与重叠分析；对相关 Agent prompt 做增量追加，把第二梯队 skill 写进既有的 `## Skill 使用规则` 中。

**Tech Stack:** Markdown, existing `agents/*.md` prompt files, existing `skills/*/SKILL.CN.md`, VS Code diagnostics

---

### Task 1: Extend The Assignment Table With Second-Tier Skills

**Files:**
- Modify: `/Users/huhui/Projects/marketingskills/agents/skill-assignment.md`
- Test: `/Users/huhui/Projects/marketingskills/agents/skill-assignment.md`

- [ ] **Step 1: Add the second-tier skill range and Chinese labels**

Update the top of `agents/skill-assignment.md` so it contains a new section for second-tier skills:

- `launch-strategy` / 发布策略
- `community-marketing` / 社区营销
- `referral-program` / 推荐计划
- `email-sequence` / 邮件序列
- `page-cro` / 页面转化优化
- `churn-prevention` / 流失预防

The file must continue to keep the existing first-tier list intact.

- [ ] **Step 2: Extend the per-agent assignment section**

Modify `## 按 Agent 分配` with these additions:

- `账号主理` adds owner `launch-strategy` and collaborative reference `community-marketing`
- `内容制作官` adds owner `email-sequence` and collaborative reference `community-marketing`
- `店铺运营官` adds owner `page-cro`
- `投放与增长官` adds owner `referral-program` and collaborative reference `launch-strategy`
- `数据复盘与客服体验官` adds owner `churn-prevention`
- `选品与供给官` remains with no second-tier owner and only supporting references
- `orchestrator` remains with no owner and limited collaborative references

- [ ] **Step 3: Extend the reverse lookup and unassigned sections**

Add second-tier entries to `## 按 Skill 反查`, and explicitly record:

- `community-marketing` has no single owner
- `选品与供给官` still has no dedicated second-tier owner skill
- `page-cro` is now assigned and is no longer listed as “未纳入第一梯队分配的相关 skill”

- [ ] **Step 4: Extend overlap analysis**

Update the skill overlap table with second-tier skills and update the per-agent overlap counts if they change.

- [ ] **Step 5: Run a content sanity check**

Run:

```bash
/usr/bin/python3 -c "from pathlib import Path; text=Path('/Users/huhui/Projects/marketingskills/agents/skill-assignment.md').read_text(); required=['launch-strategy','community-marketing','referral-program','email-sequence','page-cro','churn-prevention']; [(_ for _ in ()).throw(AssertionError(item)) for item in required if item not in text]; print('assignment-second-tier-ok')"
```

Expected: `assignment-second-tier-ok`

### Task 2: Update Strategy And Content Agents

**Files:**
- Modify: `/Users/huhui/Projects/marketingskills/agents/01-account-strategist.md`
- Modify: `/Users/huhui/Projects/marketingskills/agents/02-content-producer.md`
- Test: `/Users/huhui/Projects/marketingskills/agents/01-account-strategist.md`
- Test: `/Users/huhui/Projects/marketingskills/agents/02-content-producer.md`

- [ ] **Step 1: Extend `01-account-strategist.md`**

Add second-tier rules to the existing `## Skill 使用规则` section:

- `launch-strategy` as a second-tier owner skill for launch rhythm, campaign timing, announcement planning, and release sequencing
- `community-marketing` as a supporting skill for long-term interaction, theme continuity, and audience participation

The additions must remain consistent with the existing first-tier structure.

- [ ] **Step 2: Extend `02-content-producer.md`**

Add second-tier rules to the existing `## Skill 使用规则` section:

- `email-sequence` as a second-tier owner skill when the deliverable is a multi-step nurture, follow-up, or lifecycle content series
- `community-marketing` as a supporting skill for replies, recurring formats, community prompts, and interaction design

- [ ] **Step 3: Run structure verification**

Run:

```bash
/usr/bin/python3 -c "from pathlib import Path; paths=[Path('/Users/huhui/Projects/marketingskills/agents/01-account-strategist.md'),Path('/Users/huhui/Projects/marketingskills/agents/02-content-producer.md')]; required=['launch-strategy','community-marketing','email-sequence']; text='\\n'.join(p.read_text() for p in paths); [(_ for _ in ()).throw(AssertionError(item)) for item in required if item not in text]; print('strategy-content-second-tier-ok')"
```

Expected: `strategy-content-second-tier-ok`

### Task 3: Update Operations, Growth, Insights, And Orchestrator

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

- [ ] **Step 1: Extend `03-store-operator.md`**

Add `page-cro` as a second-tier owner skill and explicitly explain that in this project it maps to:

- 商品详情页
- 活动页
- 店铺首页
- 直播承接页

not only website landing pages.

- [ ] **Step 2: Extend `04-assortment-supply-manager.md`**

Add `page-cro` and `churn-prevention` only as supporting references, and restate that this role still has no second-tier owner skill.

- [ ] **Step 3: Extend `05-growth-amplification-manager.md`**

Add `referral-program` as a second-tier owner skill and `launch-strategy` as a supporting skill for campaign timing and release-linked amplification.

- [ ] **Step 4: Extend `06-insights-cx-analyst.md`**

Add `churn-prevention` as a second-tier owner skill for cancellation, refund, churn, and win-back analysis.

- [ ] **Step 5: Extend `orchestrator.md`**

Add second-tier collaborative references only:

- `launch-strategy` for release/campaign orchestration recognition
- `page-cro` for page or承接 optimization recognition
- `churn-prevention` for churn / refund / recovery recognition

and explicitly preserve its non-owner status.

- [ ] **Step 6: Run structure verification**

Run:

```bash
/usr/bin/python3 -c "from pathlib import Path; paths=[Path('/Users/huhui/Projects/marketingskills/agents/03-store-operator.md'),Path('/Users/huhui/Projects/marketingskills/agents/04-assortment-supply-manager.md'),Path('/Users/huhui/Projects/marketingskills/agents/05-growth-amplification-manager.md'),Path('/Users/huhui/Projects/marketingskills/agents/06-insights-cx-analyst.md'),Path('/Users/huhui/Projects/marketingskills/agents/orchestrator.md')]; text='\\n'.join(p.read_text() for p in paths); required=['page-cro','referral-program','churn-prevention','launch-strategy']; [(_ for _ in ()).throw(AssertionError(item)) for item in required if item not in text]; print('ops-growth-insights-second-tier-ok')"
```

Expected: `ops-growth-insights-second-tier-ok`

### Task 4: Verify Diagnostics And Final State

**Files:**
- Test: `/Users/huhui/Projects/marketingskills/agents/01-account-strategist.md`
- Test: `/Users/huhui/Projects/marketingskills/agents/02-content-producer.md`
- Test: `/Users/huhui/Projects/marketingskills/agents/03-store-operator.md`
- Test: `/Users/huhui/Projects/marketingskills/agents/04-assortment-supply-manager.md`
- Test: `/Users/huhui/Projects/marketingskills/agents/05-growth-amplification-manager.md`
- Test: `/Users/huhui/Projects/marketingskills/agents/06-insights-cx-analyst.md`
- Test: `/Users/huhui/Projects/marketingskills/agents/orchestrator.md`
- Test: `/Users/huhui/Projects/marketingskills/agents/skill-assignment.md`

- [ ] **Step 1: Run diagnostics on all edited Markdown files**

Use editor diagnostics to confirm there are no introduced issues.

- [ ] **Step 2: Read back final spot-check files**

Spot-check:

- `/Users/huhui/Projects/marketingskills/agents/01-account-strategist.md`
- `/Users/huhui/Projects/marketingskills/agents/03-store-operator.md`
- `/Users/huhui/Projects/marketingskills/agents/skill-assignment.md`

Confirm:

- second-tier skills are present
- owner/collaboration split matches the design
- `community-marketing` remains non-owner
- `orchestrator` remains non-owner

- [ ] **Step 3: Commit**

```bash
/usr/bin/git add \
  /Users/huhui/Projects/marketingskills/agents/01-account-strategist.md \
  /Users/huhui/Projects/marketingskills/agents/02-content-producer.md \
  /Users/huhui/Projects/marketingskills/agents/03-store-operator.md \
  /Users/huhui/Projects/marketingskills/agents/04-assortment-supply-manager.md \
  /Users/huhui/Projects/marketingskills/agents/05-growth-amplification-manager.md \
  /Users/huhui/Projects/marketingskills/agents/06-insights-cx-analyst.md \
  /Users/huhui/Projects/marketingskills/agents/orchestrator.md \
  /Users/huhui/Projects/marketingskills/agents/skill-assignment.md \
  /Users/huhui/Projects/marketingskills/docs/superpowers/specs/2026-04-21-second-tier-skill-assignment-design.md \
  /Users/huhui/Projects/marketingskills/docs/superpowers/plans/2026-04-21-second-tier-skill-assignment.md
/usr/bin/git commit -m "feat: assign second-tier skills to agents"
```

Expected: a commit containing the second-tier prompt updates, the expanded assignment table, the design doc, and this plan file.
