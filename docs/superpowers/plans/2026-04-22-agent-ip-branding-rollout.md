# Agent IP Branding Rollout Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Roll out the approved `林地增长联盟` IP naming system into the project’s entry and agent docs without changing any formal role boundaries or routing rules.

**Architecture:** Keep the existing file names, formal role names, and task-routing structure intact. Add lightweight alias mappings in the docs layer so users can see the new animal IP identities while the system continues to operate on the original agent structure.

**Tech Stack:** Markdown docs, git, ripgrep-based verification

---

## File Map

- Modify: `CLAUDE.md`
  Purpose: Keep the entry protocol unchanged while adding a lightweight “formal role -> IP alias” mapping in the project positioning and related-doc references.
- Modify: `agents/README.md`
  Purpose: Make the IP system visible in the central role overview and explain that the alliance naming is a display layer, not a structural change.
- Modify: `agents/orchestrator.md`
  Purpose: Show the alias mapping in the orchestrator-managed role list so routing references stay readable to humans.
- Modify: `agents/01-account-strategist.md`
  Purpose: Add the `白狐策略师` alias near the title/introduction without changing role responsibilities.
- Modify: `agents/02-content-producer.md`
  Purpose: Add the `喜鹊制作人` alias near the title/introduction without changing role responsibilities.
- Modify: `agents/03-store-operator.md`
  Purpose: Add the `三花猫店掌柜` alias near the title/introduction without changing role responsibilities.
- Modify: `agents/04-assortment-supply-manager.md`
  Purpose: Add the `松鼠管仓` alias near the title/introduction without changing role responsibilities.
- Modify: `agents/05-growth-amplification-manager.md`
  Purpose: Add the `兔子增长手` alias near the title/introduction without changing role responsibilities.
- Modify: `agents/06-insights-cx-analyst.md`
  Purpose: Add the `猫鼬观察员` alias near the title/introduction without changing role responsibilities.

## Implementation Rules

- Keep all existing file names unchanged.
- Keep all existing formal role names unchanged.
- Do not rewrite routing logic, role boundaries, or required inputs/outputs.
- Add aliases only in explanatory or introductory text.
- Use the approved final mapping only:

```text
林地增长联盟
- orchestrator -> 猫头鹰召集人
- 01-account-strategist -> 白狐策略师
- 02-content-producer -> 喜鹊制作人
- 03-store-operator -> 三花猫店掌柜
- 04-assortment-supply-manager -> 松鼠管仓
- 05-growth-amplification-manager -> 兔子增长手
- 06-insights-cx-analyst -> 猫鼬观察员
```

### Task 1: Update The Central Role Index

**Files:**
- Modify: `agents/README.md`

- [ ] **Step 1: Add alliance context under the opening description**

Insert a short paragraph after the existing opening explanation so the file introduces the IP layer before the role list.

```md
这套角色同时采用一套展示层 IP 设定，统一归属于“林地增长联盟”。

- 这套命名用于增强角色辨识度和协作感
- 它是展示层别名，不替代原有文件名、正式角色名和职责边界
```

- [ ] **Step 2: Update the role list to include IP aliases**

Replace the existing role list block:

```md
- `01-account-strategist.md`：账号主理 / 内容策略官
- `02-content-producer.md`：内容制作官
- `03-store-operator.md`：店铺运营官
- `04-assortment-supply-manager.md`：选品与供给官
- `05-growth-amplification-manager.md`：投放与增长官
- `06-insights-cx-analyst.md`：数据复盘与客服体验官
```

With:

```md
- `01-account-strategist.md`：账号主理 / 内容策略官（白狐策略师）
- `02-content-producer.md`：内容制作官（喜鹊制作人）
- `03-store-operator.md`：店铺运营官（三花猫店掌柜）
- `04-assortment-supply-manager.md`：选品与供给官（松鼠管仓）
- `05-growth-amplification-manager.md`：投放与增长官（兔子增长手）
- `06-insights-cx-analyst.md`：数据复盘与客服体验官（猫鼬观察员）
```

- [ ] **Step 3: Add the orchestrator alias in the recommended hierarchy section**

Replace this line:

```md
- 默认入口调度：`orchestrator`
```

With:

```md
- 默认入口调度：`orchestrator`（猫头鹰召集人）
```

- [ ] **Step 4: Verify the file contains all seven aliases**

Run:

```bash
grep -E "猫头鹰召集人|白狐策略师|喜鹊制作人|三花猫店掌柜|松鼠管仓|兔子增长手|猫鼬观察员" agents/README.md
```

Expected: seven matching lines or a grouped output covering all approved aliases.

- [ ] **Step 5: Commit**

```bash
git add agents/README.md
git commit -m "docs: add alliance aliases to agents readme"
```

### Task 2: Update The Entry Protocol Doc

**Files:**
- Modify: `CLAUDE.md`

- [ ] **Step 1: Add the alliance note in the project positioning section**

Append this bullet under `## 项目定位`:

```md
- 展示层角色别名统一归属于“林地增长联盟”，用于增强角色辨识度，不替代正式角色结构
```

- [ ] **Step 2: Add the orchestrator alias in the orchestrator section**

Replace:

```md
- `orchestrator` 负责路由、停机、交接和汇总
```

With:

```md
- `orchestrator`（猫头鹰召集人）负责路由、停机、交接和汇总
```

- [ ] **Step 3: Add aliases in the related-doc index**

Replace the related-doc role bullets:

```md
- 总调度入口：`agents/orchestrator.md`
- 账号主理：`agents/01-account-strategist.md`
- 内容制作官：`agents/02-content-producer.md`
- 店铺运营官：`agents/03-store-operator.md`
- 选品与供给官：`agents/04-assortment-supply-manager.md`
- 投放与增长官：`agents/05-growth-amplification-manager.md`
- 数据复盘与客服体验官：`agents/06-insights-cx-analyst.md`
```

With:

```md
- 总调度入口：`agents/orchestrator.md`（猫头鹰召集人）
- 账号主理：`agents/01-account-strategist.md`（白狐策略师）
- 内容制作官：`agents/02-content-producer.md`（喜鹊制作人）
- 店铺运营官：`agents/03-store-operator.md`（三花猫店掌柜）
- 选品与供给官：`agents/04-assortment-supply-manager.md`（松鼠管仓）
- 投放与增长官：`agents/05-growth-amplification-manager.md`（兔子增长手）
- 数据复盘与客服体验官：`agents/06-insights-cx-analyst.md`（猫鼬观察员）
```

- [ ] **Step 4: Verify that no routing rules were changed accidentally**

Run:

```bash
grep -n "默认先进入 `orchestrator`\\|角色交接规则\\|按开发协作处理的任务" CLAUDE.md
```

Expected: the existing routing and exclusion sections still exist, with only alias annotations added nearby.

- [ ] **Step 5: Commit**

```bash
git add CLAUDE.md
git commit -m "docs: add alliance aliases to entry protocol"
```

### Task 3: Update The Orchestrator View

**Files:**
- Modify: `agents/orchestrator.md`

- [ ] **Step 1: Add the alliance context below the title**

Insert this paragraph after the opening two paragraphs:

```md
在展示层设定中，你同时也是“林地增长联盟”的 `猫头鹰召集人`。这个称呼只用于帮助用户理解角色关系，不改变你的轻量调度边界。
```

- [ ] **Step 2: Update the managed-role list with aliases**

Replace:

```md
- `01-account-strategist.md`：账号主理 / 内容策略官
- `02-content-producer.md`：内容制作官
- `03-store-operator.md`：店铺运营官
- `04-assortment-supply-manager.md`：选品与供给官
- `05-growth-amplification-manager.md`：投放与增长官
- `06-insights-cx-analyst.md`：数据复盘与客服体验官
```

With:

```md
- `01-account-strategist.md`：账号主理 / 内容策略官（白狐策略师）
- `02-content-producer.md`：内容制作官（喜鹊制作人）
- `03-store-operator.md`：店铺运营官（三花猫店掌柜）
- `04-assortment-supply-manager.md`：选品与供给官（松鼠管仓）
- `05-growth-amplification-manager.md`：投放与增长官（兔子增长手）
- `06-insights-cx-analyst.md`：数据复盘与客服体验官（猫鼬观察员）
```

- [ ] **Step 3: Preserve the “lightweight orchestrator” boundary language**

After editing, ensure these lines still remain semantically unchanged:

```md
你是一个轻量调度器，不是总指挥官。你负责“路由与停机条件”，不负责长期接管策略、内容、店铺、选品、投放或复盘工作。
```

If the line was touched accidentally, restore it exactly.

- [ ] **Step 4: Verify alias coverage and boundary language**

Run:

```bash
grep -E "猫头鹰召集人|白狐策略师|喜鹊制作人|三花猫店掌柜|松鼠管仓|兔子增长手|猫鼬观察员|轻量调度器，不是总指挥官" agents/orchestrator.md
```

Expected: all aliases appear and the “轻量调度器，不是总指挥官” sentence remains present.

- [ ] **Step 5: Commit**

```bash
git add agents/orchestrator.md
git commit -m "docs: add alliance aliases to orchestrator"
```

### Task 4: Add Alias Lines To The Strategy And Content Agents

**Files:**
- Modify: `agents/01-account-strategist.md`
- Modify: `agents/02-content-producer.md`

- [ ] **Step 1: Add the strategy alias under the title/introduction**

Insert after `你是“账号主理 / 内容策略官”。`:

```md
在“林地增长联盟”的展示层设定中，你也被称为“白狐策略师”。
```

- [ ] **Step 2: Add the content alias under the title/introduction**

Insert after `你是“内容制作官”。`:

```md
在“林地增长联盟”的展示层设定中，你也被称为“喜鹊制作人”。
```

- [ ] **Step 3: Verify the new lines exist and the duty sections stay intact**

Run:

```bash
grep -n "白狐策略师\\|喜鹊制作人\\|## 你的职责" agents/01-account-strategist.md agents/02-content-producer.md
```

Expected: each file shows its alias line and still contains its `## 你的职责` section.

- [ ] **Step 4: Commit**

```bash
git add agents/01-account-strategist.md agents/02-content-producer.md
git commit -m "docs: add alliance aliases to strategy and content agents"
```

### Task 5: Add Alias Lines To The Store And Supply Agents

**Files:**
- Modify: `agents/03-store-operator.md`
- Modify: `agents/04-assortment-supply-manager.md`

- [ ] **Step 1: Add the store alias under the title/introduction**

Insert after `你是“店铺运营官”。`:

```md
在“林地增长联盟”的展示层设定中，你也被称为“三花猫店掌柜”。
```

- [ ] **Step 2: Add the supply alias under the title/introduction**

Insert after `你是“选品与供给官”。`:

```md
在“林地增长联盟”的展示层设定中，你也被称为“松鼠管仓”。
```

- [ ] **Step 3: Verify the new lines exist and the input sections remain unchanged**

Run:

```bash
grep -n "三花猫店掌柜\\|松鼠管仓\\|## 你需要的输入" agents/03-store-operator.md agents/04-assortment-supply-manager.md
```

Expected: each file shows its alias line and still contains its input requirements section.

- [ ] **Step 4: Commit**

```bash
git add agents/03-store-operator.md agents/04-assortment-supply-manager.md
git commit -m "docs: add alliance aliases to store and supply agents"
```

### Task 6: Add Alias Lines To The Growth And Insights Agents

**Files:**
- Modify: `agents/05-growth-amplification-manager.md`
- Modify: `agents/06-insights-cx-analyst.md`

- [ ] **Step 1: Add the growth alias under the title/introduction**

Insert after `你是“投放与增长官”。`:

```md
在“林地增长联盟”的展示层设定中，你也被称为“兔子增长手”。
```

- [ ] **Step 2: Add the insights alias under the title/introduction**

Insert after `你是“数据复盘与客服体验官”。`:

```md
在“林地增长联盟”的展示层设定中，你也被称为“猫鼬观察员”。
```

- [ ] **Step 3: Verify the new lines exist and the output sections remain unchanged**

Run:

```bash
grep -n "兔子增长手\\|猫鼬观察员\\|## 你的输出必须包含" agents/05-growth-amplification-manager.md agents/06-insights-cx-analyst.md
```

Expected: each file shows its alias line and still contains its required output section.

- [ ] **Step 4: Commit**

```bash
git add agents/05-growth-amplification-manager.md agents/06-insights-cx-analyst.md
git commit -m "docs: add alliance aliases to growth and insights agents"
```

### Task 7: Final Consistency Pass

**Files:**
- Modify: `CLAUDE.md`
- Modify: `agents/README.md`
- Modify: `agents/orchestrator.md`
- Modify: `agents/01-account-strategist.md`
- Modify: `agents/02-content-producer.md`
- Modify: `agents/03-store-operator.md`
- Modify: `agents/04-assortment-supply-manager.md`
- Modify: `agents/05-growth-amplification-manager.md`
- Modify: `agents/06-insights-cx-analyst.md`

- [ ] **Step 1: Verify every approved alias appears in the rollout surface**

Run:

```bash
grep -R -n -E "猫头鹰召集人|白狐策略师|喜鹊制作人|三花猫店掌柜|松鼠管仓|兔子增长手|猫鼬观察员|林地增长联盟" CLAUDE.md agents/README.md agents/orchestrator.md agents/0*.md
```

Expected: all approved aliases appear in the intended docs, with no missing role.

- [ ] **Step 2: Verify no rejected old store alias remains**

Run:

```bash
grep -R -n "刺猬店掌柜" CLAUDE.md agents/README.md agents/orchestrator.md agents/0*.md
```

Expected: no output.

- [ ] **Step 3: Review the final git diff for scope control**

Run:

```bash
git diff -- CLAUDE.md agents/README.md agents/orchestrator.md agents/01-account-strategist.md agents/02-content-producer.md agents/03-store-operator.md agents/04-assortment-supply-manager.md agents/05-growth-amplification-manager.md agents/06-insights-cx-analyst.md
```

Expected: only alias additions and small explanatory text changes, with no routing/rule rewrites.

- [ ] **Step 4: Commit**

```bash
git add CLAUDE.md agents/README.md agents/orchestrator.md agents/01-account-strategist.md agents/02-content-producer.md agents/03-store-operator.md agents/04-assortment-supply-manager.md agents/05-growth-amplification-manager.md agents/06-insights-cx-analyst.md
git commit -m "docs: roll out alliance aliases across agent docs"
```

## Self-Review

- Spec coverage check: the plan covers the approved alliance name, all seven alias mappings, and the “display layer only” constraint.
- Placeholder scan: there are no `TBD`, `TODO`, “implement later”, or unresolved references in the tasks.
- Consistency check: every task uses the same approved mapping:

```text
猫头鹰召集人
白狐策略师
喜鹊制作人
三花猫店掌柜
松鼠管仓
兔子增长手
猫鼬观察员
```
