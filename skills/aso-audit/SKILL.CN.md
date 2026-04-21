---
name: aso-audit
description: "当用户想审查或优化 App Store / Google Play 上架页时使用。适合处理标题、副标题、关键词、截图、评论和转化表现等 ASO 问题。"
metadata:
  version: 1.0.0
---

# 应用商店优化审计

这是 `aso-audit` 的中文本地化说明版。它不是逐句硬译，而是把原始 `SKILL.md` 整理成更适合中文用户直接执行的工作手册；需要逐段对照英文原版时，请同时查看同目录下的 `SKILL.md`。

## 适用场景

当用户想审查或优化 App Store / Google Play 上架页时使用。适合处理标题、副标题、关键词、截图、评论和转化表现等 ASO 问题。

## 使用方式

- 先读取 `.agents/product-marketing-context.md`（或旧路径 `.claude/product-marketing-context.md`），避免重复提问并沿用已有定位信息。
- 按原版 `When to Use` 小节推进，确保不遗漏该技能特有的方法、检查点或框架。
- 按原版 `Before Auditing` 小节推进，确保不遗漏该技能特有的方法、检查点或框架。
- 按原版 `Phase 1 — Identify Store & Fetch` 小节推进，确保不遗漏该技能特有的方法、检查点或框架。
- 按原版 `Phase 1.5 — Assess Brand Maturity` 小节推进，确保不遗漏该技能特有的方法、检查点或框架。

## 重点关注

原版技能里最值得优先对照的细项通常包括：
- `Detect store type from URL`
- `Fetch the listing`
- `Visual asset assessment`
- `Tier definitions`
- `How tier affects scoring`
- `Dimensions and Weights`
- `Score interpretation`
- `Report rules`

## 典型交付物

- 结构化建议
- 优先级清单
- 后续执行提示

## 原始章节导航

- `When to Use`
- `Before Auditing`
- `Phase 1 — Identify Store & Fetch`
- `Phase 1.5 — Assess Brand Maturity`
- `Phase 2 — Score Each Dimension`
- `Phase 3 — Competitor Comparison (Optional)`
- `Phase 4 — Generate Report`
- `Platform-Specific Rules`
- `Common Issues Checklist`
- `任务专属问题`（原版：`Task-Specific Questions`）
- `相关技能`（原版：`Related Skills`）

## 相关技能

- `page-cro`
- `ad-creative`
- `analytics-tracking`
- `customer-research`

## 使用建议

- 如果你是第一次在这个仓库里使用该技能，先看中文版本建立整体认知，再按需回看英文原版中的细节、模板和边界条件。
- 如果任务涉及多技能串联，优先遵守原版 `Related Skills` 和交叉引用中的边界说明，避免把一个技能的职责做得过宽。
