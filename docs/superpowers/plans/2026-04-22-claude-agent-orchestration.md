# CLAUDE Agent Orchestration Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** 把 `CLAUDE.md` 重写为社交媒体电商多 Agent 的总控入口文档，让自然语言业务任务默认先进入 `orchestrator`，并对用户显式展示承接与路由过程。

**Architecture:** 只修改 `CLAUDE.md`，把旧的 skill 仓库说明替换为新的入口协议文档；具体角色职责和 skill 边界继续引用 `agents/` 下现有文档，不在 `CLAUDE.md` 中重复维护。实施时先确认旧文档中的可复用片段，再整体重写为“项目定位 -> 工作模式 -> 默认路由 -> 用户覆盖 -> 非业务任务排除 -> 文档索引”的结构。

**Tech Stack:** Markdown, existing `CLAUDE.md`, existing `agents/*.md`, VS Code diagnostics

---

### Task 1: Confirm Source Material And Rewrite Scope

**Files:**
- Modify: `/Users/huhui/Projects/marketingskills/CLAUDE.md`
- Reference: `/Users/huhui/Projects/marketingskills/agents/README.md`
- Reference: `/Users/huhui/Projects/marketingskills/agents/orchestrator.md`
- Test: `/Users/huhui/Projects/marketingskills/CLAUDE.md`

- [ ] **Step 1: Read the current entry document and the two routing references**

Run:

```bash
python3 - <<'PY'
from pathlib import Path
paths = [
    Path('/Users/huhui/Projects/marketingskills/CLAUDE.md'),
    Path('/Users/huhui/Projects/marketingskills/agents/README.md'),
    Path('/Users/huhui/Projects/marketingskills/agents/orchestrator.md'),
]
for p in paths:
    text = p.read_text()
    print(p.name, len(text.splitlines()))
PY
```

Expected: prints three filenames with non-zero line counts.

- [ ] **Step 2: Confirm the old `CLAUDE.md` is still marketplace-oriented**

Run:

```bash
python3 - <<'PY'
from pathlib import Path
text = Path('/Users/huhui/Projects/marketingskills/CLAUDE.md').read_text()
checks = [
    'Agent Skills',
    'Claude Code Plugin',
    'Checking for Updates',
    'Dynamic content injection',
]
for item in checks:
    print(item, item in text)
PY
```

Expected: all four checks print `True`, confirming the file still reflects the old repository positioning.

- [ ] **Step 3: Lock the rewrite scope**

Use this exact rewrite rule in the implementation:

```md
- 保留：对当前项目仍然有用的高层说明
- 删除：skill marketplace、frontmatter 规范、旧插件说明、更新检查流程
- 新增：orchestrator 默认入口、角色交接协议、用户覆盖规则、非业务任务排除规则、文档索引
```

### Task 2: Rewrite `CLAUDE.md` As The Main Agent Entry

**Files:**
- Modify: `/Users/huhui/Projects/marketingskills/CLAUDE.md`
- Test: `/Users/huhui/Projects/marketingskills/CLAUDE.md`

- [ ] **Step 1: Replace the title and opening positioning**

The top of the file should become:

```md
# CLAUDE.md

本项目当前不是单纯的 marketing skill 汇集仓库，而是一个面向“社交媒体账号 + 电商平台店铺”运营场景的多 Agent 工作环境。

你在这里的默认职责不是直接吞掉所有业务任务，而是先识别任务是否属于业务运营问题；如果属于，则优先经由 `agents/orchestrator.md` 做任务分类、信息充分性判断和角色分发，再由合适的业务 Agent 承接具体工作。
```

- [ ] **Step 2: Add the working-mode section**

Insert a section covering the three input types:

```md
## 工作模式

### 1. 业务任务

- 只要用户是在讨论内容、店铺、选品、投放、复盘、客服体验、活动或增长问题，就按业务任务处理
- 业务任务默认先进入 `orchestrator`

### 2. 显式点名角色

- 如果用户明确说“让某个 agent 来做”，则按指定角色承接
- 但仍需遵守该角色自身的输入要求、边界和停机规则

### 3. 非业务任务

- 如果用户是在维护仓库、修改文档、调整 prompts、实现脚本或讨论项目结构，则不进入业务 agent 路由
- 这类任务按普通开发或文档协作处理
```

- [ ] **Step 3: Add the default `orchestrator` protocol**

Insert a section requiring this routing behavior:

```md
## 默认业务任务入口

当用户以自然语言提出业务任务时，先参考 `agents/orchestrator.md`。

你必须优先完成以下动作：

1. 判断任务类型
2. 判断信息是否充分
3. 判断是否应停下来向用户补信息
4. 判断应该交给哪个业务 Agent 承接

不要在还没有经过上述判断之前，直接越过 `orchestrator` 给出完整业务结论。
```

- [ ] **Step 4: Add the user-visible handoff format**

Insert a section containing this exact structure:

````md
## 对用户可见的交接协议

处理业务任务时，要显式展示当前承接状态，至少包含：

```text
当前承接：
- orchestrator / 具体业务 agent

任务类型：
- 周计划 / 内容生产 / 店铺承接 / 放量增长 / 复盘诊断

信息是否充分：
- 充分 / 不充分

缺失信息：
- ...

下一步：
- 继续由谁承接
- 对方要解决什么问题
```
````

- [ ] **Step 5: Add role delegation and override rules**

Insert a section covering role mapping and user override:

```md
## 角色交接规则

- 周目标、主推方向、内容支柱类问题，交给 `01-account-strategist.md`
- 脚本、标题、图文结构、内容版本类问题，交给 `02-content-producer.md`
- 商品页、活动页、利益点、承接链路类问题，交给 `03-store-operator.md`
- SKU 优先级、供给、履约、货盘适配类问题，交给 `04-assortment-supply-manager.md`
- 投流、放量、预算、达人、实验类问题，交给 `05-growth-amplification-manager.md`
- 数据复盘、评论洞察、客服体验、退款与流失类问题，交给 `06-insights-cx-analyst.md`

## 用户覆盖默认路由

- 如果用户明确说“直接让某个 agent 来做”，允许跳过默认路由
- 但不要因为用户点名就忽略该角色对输入完整性的要求
- 信息不足时，仍然先补信息，不编造结论
```

- [ ] **Step 6: Add non-business exclusions and document index**

Append these two sections:

```md
## 不进入业务路由的任务

- 修改 `CLAUDE.md`
- 编辑 `agents/*.md`
- 调整 `skills/*`
- 讨论仓库结构、脚本实现、验证方式或文档写法

## 相关文档

- 总调度入口：`agents/orchestrator.md`
- 角色总览：`agents/README.md`
- 账号主理：`agents/01-account-strategist.md`
- 内容制作官：`agents/02-content-producer.md`
- 店铺运营官：`agents/03-store-operator.md`
- 选品与供给官：`agents/04-assortment-supply-manager.md`
- 投放与增长官：`agents/05-growth-amplification-manager.md`
- 数据复盘与客服体验官：`agents/06-insights-cx-analyst.md`
- skill 边界：`agents/skill-assignment.md`
```

### Task 3: Verify The Rewrite Matches The Design

**Files:**
- Test: `/Users/huhui/Projects/marketingskills/CLAUDE.md`
- Reference: `/Users/huhui/Projects/marketingskills/docs/superpowers/specs/2026-04-22-claude-agent-orchestration-design.md`

- [ ] **Step 1: Run a content-presence check**

Run:

```bash
python3 - <<'PY'
from pathlib import Path
text = Path('/Users/huhui/Projects/marketingskills/CLAUDE.md').read_text()
required = [
    '## 工作模式',
    '## 默认业务任务入口',
    '## 对用户可见的交接协议',
    '## 角色交接规则',
    '## 用户覆盖默认路由',
    '## 不进入业务路由的任务',
    '## 相关文档',
    'agents/orchestrator.md',
    '01-account-strategist.md',
    '06-insights-cx-analyst.md',
]
for item in required:
    assert item in text, item
print('ok')
PY
```

Expected: `ok`

- [ ] **Step 2: Confirm old marketplace-only headings are gone**

Run:

```bash
python3 - <<'PY'
from pathlib import Path
text = Path('/Users/huhui/Projects/marketingskills/CLAUDE.md').read_text()
forbidden = [
    '### Required Frontmatter',
    '## Claude Code Plugin',
    '## Checking for Updates',
    '### Dynamic content injection',
]
for item in forbidden:
    assert item not in text, item
print('ok')
PY
```

Expected: `ok`

- [ ] **Step 3: Read the final file and compare against the design**

Check manually that the file satisfies these three spec points:

```md
1. 业务任务默认先经 `orchestrator`
2. 路由过程对用户显式可见
3. 非业务任务不进入业务 agent 流程
```

### Task 4: Validate Markdown Diagnostics And Hand Off

**Files:**
- Test: `/Users/huhui/Projects/marketingskills/CLAUDE.md`
- Create: `/Users/huhui/Projects/marketingskills/docs/superpowers/specs/2026-04-22-claude-agent-orchestration-design.md`
- Create: `/Users/huhui/Projects/marketingskills/docs/superpowers/plans/2026-04-22-claude-agent-orchestration.md`

- [ ] **Step 1: Run diagnostics on the edited markdown file**

Use editor diagnostics on:

```text
/Users/huhui/Projects/marketingskills/CLAUDE.md
```

Expected: no newly introduced markdown issues.

- [ ] **Step 2: Spot-check the spec and the plan exist**

Run:

```bash
python3 - <<'PY'
from pathlib import Path
paths = [
    Path('/Users/huhui/Projects/marketingskills/docs/superpowers/specs/2026-04-22-claude-agent-orchestration-design.md'),
    Path('/Users/huhui/Projects/marketingskills/docs/superpowers/plans/2026-04-22-claude-agent-orchestration.md'),
]
for p in paths:
    assert p.exists(), p
    print(p.name, 'ok')
PY
```

Expected:

```text
2026-04-22-claude-agent-orchestration-design.md ok
2026-04-22-claude-agent-orchestration.md ok
```

- [ ] **Step 3: Commit**

```bash
git add \
  /Users/huhui/Projects/marketingskills/CLAUDE.md \
  /Users/huhui/Projects/marketingskills/docs/superpowers/specs/2026-04-22-claude-agent-orchestration-design.md \
  /Users/huhui/Projects/marketingskills/docs/superpowers/plans/2026-04-22-claude-agent-orchestration.md
git commit -m "docs: add claude agent orchestration protocol"
```

Expected: one commit containing the rewritten entry document plus the supporting spec and plan files.
