---
name: churn-prevention
description: "当用户想降低流失、优化取消流程、设计保留方案或恢复失败扣款时使用。适合围绕留存、挽回和用户价值延长做系统性设计。"
metadata:
  version: 1.1.0
---

# 流失预防

这是 `churn-prevention` 的中文本地化说明版。它不是逐句硬译，而是把原始 `SKILL.md` 整理成更适合中文用户直接执行的工作手册；需要逐段对照英文原版时，请同时查看同目录下的 `SKILL.md`。

## 适用场景

当用户想降低流失、优化取消流程、设计保留方案或恢复失败扣款时使用。适合围绕留存、挽回和用户价值延长做系统性设计。

## 使用方式

- 先读取 `.agents/product-marketing-context.md`（或旧路径 `.claude/product-marketing-context.md`），避免重复提问并沿用已有定位信息。
- 围绕“开始前”推进任务，并在需要时回看原版 `Before Starting` 小节获取更细颗粒度指引。
- 按原版 `How This Skill Works` 小节推进，确保不遗漏该技能特有的方法、检查点或框架。
- 按原版 `Cancel Flow Design` 小节推进，确保不遗漏该技能特有的方法、检查点或框架。
- 按原版 `Churn Prediction & Proactive Retention` 小节推进，确保不遗漏该技能特有的方法、检查点或框架。

## 重点关注

原版技能里最值得优先对照的细项通常包括：
- `1. Current Churn Situation`
- `2. Billing & Platform`
- `3. Product & Usage Data`
- `4. Constraints`
- `The Cancel Flow Structure`
- `Exit Survey Design`
- `Dynamic Save Offers`
- `Save Offer Types`

## 典型交付物

- 结构化建议
- 优先级清单
- 后续执行提示

## 原始章节导航

- `开始前`（原版：`Before Starting`）
- `How This Skill Works`
- `Cancel Flow Design`
- `Churn Prediction & Proactive Retention`
- `Involuntary Churn: Payment Recovery`
- `Metrics & Measurement`
- `常见错误`（原版：`Common Mistakes`）
- `工具集成`（原版：`Tool Integrations`）
- `相关技能`（原版：`Related Skills`）

## 相关技能

- `email-sequence`
- `paywall-upgrade-cro`
- `pricing-strategy`
- `onboarding-cro`
- `analytics-tracking`
- `ab-test-setup`

## 使用建议

- 如果你是第一次在这个仓库里使用该技能，先看中文版本建立整体认知，再按需回看英文原版中的细节、模板和边界条件。
- 如果任务涉及多技能串联，优先遵守原版 `Related Skills` 和交叉引用中的边界说明，避免把一个技能的职责做得过宽。
