# Skill CN Translation Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** 将 `skills/*/SKILL.CN.md` 全部改写为与对应英文 `SKILL.md` 逐段对齐的完整中文译本。

**Architecture:** 以每个技能目录中的英文 `SKILL.md` 作为唯一事实来源，保留 frontmatter 字段结构、Markdown 层级、表格、列表、编号和交叉引用，仅将自然语言内容完整翻译为中文。执行上按技能分组批量改写，再统一做结构校验与诊断检查，避免遗漏或风格飘移。

**Tech Stack:** Markdown, YAML frontmatter, Trae file tools, VS Code diagnostics

---

### Task 1: 建立翻译批次与校验基线

**Files:**
- Create: `docs/superpowers/plans/2026-04-22-skill-cn-translation.md`
- Modify: `skills/*/SKILL.CN.md`
- Test: `skills/*/SKILL.md`

- [ ] **Step 1: 盘点全部中英文技能文件对**

Run: `find skills -mindepth 2 -maxdepth 2 \\( -name 'SKILL.md' -o -name 'SKILL.CN.md' \\) | sort`
Expected: 每个技能目录同时列出 `SKILL.md` 与 `SKILL.CN.md`，共 36 组左右文件对。

- [ ] **Step 2: 确认翻译边界**

```markdown
翻译边界：
- 保留 `name`、`metadata.version`
- 将 `description` 翻译为等义中文
- 删除现有“索引版/导航版”衍生段落
- 保留英文技能名、路径、文件名、编号引用
- 保持标题层级、表格列数、列表顺序与原文一致
```

- [ ] **Step 3: 抽样确认现状差异**

Run: `diff -u skills/marketing-ideas/SKILL.md skills/marketing-ideas/SKILL.CN.md | head -n 80`
Expected: 输出显示中文文件并非英文原文的完整对应译本，而是导航式内容，证明需要整文件重写。

- [ ] **Step 4: 提交计划文档**

```bash
git add docs/superpowers/plans/2026-04-22-skill-cn-translation.md
git commit -m "docs: add skill cn translation plan"
```

### Task 2: 翻译 CRO 与转化优化相关技能

**Files:**
- Modify: `skills/page-cro/SKILL.CN.md`
- Modify: `skills/popup-cro/SKILL.CN.md`
- Modify: `skills/form-cro/SKILL.CN.md`
- Modify: `skills/signup-flow-cro/SKILL.CN.md`
- Modify: `skills/onboarding-cro/SKILL.CN.md`
- Modify: `skills/paywall-upgrade-cro/SKILL.CN.md`
- Test: `skills/page-cro/SKILL.md`
- Test: `skills/popup-cro/SKILL.md`
- Test: `skills/form-cro/SKILL.md`
- Test: `skills/signup-flow-cro/SKILL.md`
- Test: `skills/onboarding-cro/SKILL.md`
- Test: `skills/paywall-upgrade-cro/SKILL.md`

- [ ] **Step 1: 逐个读取英文原文并重写对应中文文件**

```markdown
每个文件按以下模板执行：
1. 复制英文文件的 frontmatter 键结构
2. 翻译 `description`
3. 按原顺序翻译标题、正文、表格、列表、提示语
4. 保留原有技能名、文件路径、引用编号、相关技能 slug
```

- [ ] **Step 2: 检查每个文件的 Markdown 结构是否与英文一致**

Run: `python3 - <<'PY'\nfrom pathlib import Path\npairs=[\n'page-cro','popup-cro','form-cro','signup-flow-cro','onboarding-cro','paywall-upgrade-cro'\n]\nfor name in pairs:\n    en=Path('skills')/name/'SKILL.md'\n    cn=Path('skills')/name/'SKILL.CN.md'\n    print(name, en.exists(), cn.exists(), sum(1 for _ in en.open()), sum(1 for _ in cn.open()))\nPY`
Expected: 所有文件都存在，中文文件行数与英文文件接近，不再是极短导航版。

- [ ] **Step 3: 人工抽样核对标题与表格**

```markdown
重点核对：
- `##` / `###` 层级是否完整保留
- 表格分隔列数是否与英文一致
- 编号和交叉引用如 `#12`、`SKILL.md`、`references/...` 是否未被误译
```

- [ ] **Step 4: 提交该批次**

```bash
git add skills/page-cro/SKILL.CN.md skills/popup-cro/SKILL.CN.md skills/form-cro/SKILL.CN.md skills/signup-flow-cro/SKILL.CN.md skills/onboarding-cro/SKILL.CN.md skills/paywall-upgrade-cro/SKILL.CN.md
git commit -m "docs: fully translate cro skill cn files"
```

### Task 3: 翻译内容、SEO 与站点相关技能

**Files:**
- Modify: `skills/content-strategy/SKILL.CN.md`
- Modify: `skills/copywriting/SKILL.CN.md`
- Modify: `skills/copy-editing/SKILL.CN.md`
- Modify: `skills/seo-audit/SKILL.CN.md`
- Modify: `skills/ai-seo/SKILL.CN.md`
- Modify: `skills/programmatic-seo/SKILL.CN.md`
- Modify: `skills/schema-markup/SKILL.CN.md`
- Modify: `skills/site-architecture/SKILL.CN.md`
- Modify: `skills/aso-audit/SKILL.CN.md`
- Modify: `skills/ad-creative/SKILL.CN.md`
- Modify: `skills/social-content/SKILL.CN.md`
- Test: `skills/content-strategy/SKILL.md`
- Test: `skills/copywriting/SKILL.md`
- Test: `skills/copy-editing/SKILL.md`
- Test: `skills/seo-audit/SKILL.md`
- Test: `skills/ai-seo/SKILL.md`
- Test: `skills/programmatic-seo/SKILL.md`
- Test: `skills/schema-markup/SKILL.md`
- Test: `skills/site-architecture/SKILL.md`
- Test: `skills/aso-audit/SKILL.md`
- Test: `skills/ad-creative/SKILL.md`
- Test: `skills/social-content/SKILL.md`

- [ ] **Step 1: 完整翻译内容与 SEO 技能组**

```markdown
翻译时统一术语：
- funnel -> 漏斗
- positioning -> 定位
- messaging -> 信息传达 / 核心表达（按语境）
- conversion -> 转化
- search intent -> 搜索意图
- schema markup -> Schema 标记
```

- [ ] **Step 2: 保留示例、框架与输出格式**

```markdown
不要删减：
- 示例 prompt
- 审核清单
- 输出格式模板
- 相关技能和工具引用
```

- [ ] **Step 3: 抽样对比两个复杂文件**

Run: `python3 - <<'PY'\nfrom pathlib import Path\nfor name in ['content-strategy','programmatic-seo']:\n    en=Path('skills')/name/'SKILL.md'\n    cn=Path('skills')/name/'SKILL.CN.md'\n    print('\\n==',name,'==')\n    print('EN headings',sum(1 for line in en.read_text().splitlines() if line.startswith('#')))\n    print('CN headings',sum(1 for line in cn.read_text().splitlines() if line.startswith('#')))\nPY`
Expected: 中文标题数量与英文标题数量一致。

- [ ] **Step 4: 提交该批次**

```bash
git add skills/content-strategy/SKILL.CN.md skills/copywriting/SKILL.CN.md skills/copy-editing/SKILL.CN.md skills/seo-audit/SKILL.CN.md skills/ai-seo/SKILL.CN.md skills/programmatic-seo/SKILL.CN.md skills/schema-markup/SKILL.CN.md skills/site-architecture/SKILL.CN.md skills/aso-audit/SKILL.CN.md skills/ad-creative/SKILL.CN.md skills/social-content/SKILL.CN.md
git commit -m "docs: fully translate content and seo skill cn files"
```

### Task 4: 翻译增长、获客与渠道相关技能

**Files:**
- Modify: `skills/marketing-ideas/SKILL.CN.md`
- Modify: `skills/launch-strategy/SKILL.CN.md`
- Modify: `skills/free-tool-strategy/SKILL.CN.md`
- Modify: `skills/lead-magnets/SKILL.CN.md`
- Modify: `skills/email-sequence/SKILL.CN.md`
- Modify: `skills/cold-email/SKILL.CN.md`
- Modify: `skills/paid-ads/SKILL.CN.md`
- Modify: `skills/referral-program/SKILL.CN.md`
- Modify: `skills/community-marketing/SKILL.CN.md`
- Modify: `skills/competitor-alternatives/SKILL.CN.md`
- Modify: `skills/churn-prevention/SKILL.CN.md`
- Modify: `skills/analytics-tracking/SKILL.CN.md`
- Test: `skills/marketing-ideas/SKILL.md`
- Test: `skills/launch-strategy/SKILL.md`
- Test: `skills/free-tool-strategy/SKILL.md`
- Test: `skills/lead-magnets/SKILL.md`
- Test: `skills/email-sequence/SKILL.md`
- Test: `skills/cold-email/SKILL.md`
- Test: `skills/paid-ads/SKILL.md`
- Test: `skills/referral-program/SKILL.md`
- Test: `skills/community-marketing/SKILL.md`
- Test: `skills/competitor-alternatives/SKILL.md`
- Test: `skills/churn-prevention/SKILL.md`
- Test: `skills/analytics-tracking/SKILL.md`

- [ ] **Step 1: 完整翻译渠道与增长技能组**

```markdown
执行要求：
- 保留 campaign 名称、广告平台名、产品名
- 将策略说明、触发语、使用时机完整翻译
- 保留列表中的技能 slug，不翻译目录名
```

- [ ] **Step 2: 检查大表格与编号引用**

Run: `python3 - <<'PY'\nfrom pathlib import Path\nfor name in ['marketing-ideas','paid-ads','analytics-tracking']:\n    text=(Path('skills')/name/'SKILL.CN.md').read_text()\n    print(name, text.count('|'), text.count('#'))\nPY`
Expected: 这些文件保留表格与编号引用，不会因翻译丢失结构。

- [ ] **Step 3: 抽样人工核对术语一致性**

```markdown
重点统一：
- growth -> 增长
- lead -> 线索
- attribution -> 归因
- onboarding -> 引导 / 入门流程（按上下文）
- retention -> 留存
```

- [ ] **Step 4: 提交该批次**

```bash
git add skills/marketing-ideas/SKILL.CN.md skills/launch-strategy/SKILL.CN.md skills/free-tool-strategy/SKILL.CN.md skills/lead-magnets/SKILL.CN.md skills/email-sequence/SKILL.CN.md skills/cold-email/SKILL.CN.md skills/paid-ads/SKILL.CN.md skills/referral-program/SKILL.CN.md skills/community-marketing/SKILL.CN.md skills/competitor-alternatives/SKILL.CN.md skills/churn-prevention/SKILL.CN.md skills/analytics-tracking/SKILL.CN.md
git commit -m "docs: fully translate growth skill cn files"
```

### Task 5: 翻译研究、策略与销售运营相关技能

**Files:**
- Modify: `skills/customer-research/SKILL.CN.md`
- Modify: `skills/product-marketing-context/SKILL.CN.md`
- Modify: `skills/marketing-psychology/SKILL.CN.md`
- Modify: `skills/pricing-strategy/SKILL.CN.md`
- Modify: `skills/sales-enablement/SKILL.CN.md`
- Modify: `skills/revops/SKILL.CN.md`
- Modify: `skills/ab-test-setup/SKILL.CN.md`
- Test: `skills/customer-research/SKILL.md`
- Test: `skills/product-marketing-context/SKILL.md`
- Test: `skills/marketing-psychology/SKILL.md`
- Test: `skills/pricing-strategy/SKILL.md`
- Test: `skills/sales-enablement/SKILL.md`
- Test: `skills/revops/SKILL.md`
- Test: `skills/ab-test-setup/SKILL.md`

- [ ] **Step 1: 完整翻译策略与运营技能组**

```markdown
注意点：
- 保留实验命名、统计术语、销售工具名
- 保留模板中的变量占位符
- 将问题清单与决策框架完整翻译
```

- [ ] **Step 2: 抽样核对 frontmatter 描述字段**

Run: `python3 - <<'PY'\nfrom pathlib import Path\nfor name in ['customer-research','pricing-strategy','ab-test-setup']:\n    lines=(Path('skills')/name/'SKILL.CN.md').read_text().splitlines()\n    print(name, lines[0], lines[1], lines[2])\nPY`
Expected: frontmatter 完整，`description` 为中文且与英文语义对应。

- [ ] **Step 3: 检查模板占位符未被破坏**

```markdown
重点检查：
- `{{variable}}`
- `<placeholder>`
- 反引号中的文件路径、命令、技能名
```

- [ ] **Step 4: 提交该批次**

```bash
git add skills/customer-research/SKILL.CN.md skills/product-marketing-context/SKILL.CN.md skills/marketing-psychology/SKILL.CN.md skills/pricing-strategy/SKILL.CN.md skills/sales-enablement/SKILL.CN.md skills/revops/SKILL.CN.md skills/ab-test-setup/SKILL.CN.md
git commit -m "docs: fully translate strategy skill cn files"
```

### Task 6: 最终结构校验与诊断

**Files:**
- Modify: `skills/*/SKILL.CN.md`
- Test: `skills/*/SKILL.md`

- [ ] **Step 1: 批量检查中文文件是否全部存在且非空**

Run: `python3 - <<'PY'\nfrom pathlib import Path\nfiles=sorted(Path('skills').glob('*/SKILL.CN.md'))\nprint('count', len(files))\nfor path in files:\n    size=path.stat().st_size\n    if size == 0:\n        print('EMPTY', path)\nPY`
Expected: 输出数量约为 36，且没有空文件。

- [ ] **Step 2: 批量检查标题数量是否与英文接近**

Run: `python3 - <<'PY'\nfrom pathlib import Path\nfor cn in sorted(Path('skills').glob('*/SKILL.CN.md')):\n    en=cn.with_name('SKILL.md')\n    enh=sum(1 for l in en.read_text().splitlines() if l.startswith('#'))\n    cnh=sum(1 for l in cn.read_text().splitlines() if l.startswith('#'))\n    if enh != cnh:\n        print('HEADING_MISMATCH', cn.parent.name, enh, cnh)\nPY`
Expected: 无输出；若有输出，逐个修正标题遗漏。

- [ ] **Step 3: 获取编辑后诊断信息**

Run: `GetDiagnostics` for recently edited `SKILL.CN.md` files
Expected: 无语法类诊断错误，尤其是 YAML frontmatter 与 Markdown 结构错误。

- [ ] **Step 4: 提交最终结果**

```bash
git add skills/*/SKILL.CN.md
git commit -m "docs: fully translate all skill cn files"
```
