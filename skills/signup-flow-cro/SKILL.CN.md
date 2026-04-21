---
name: signup-flow-cro
description: "当用户想优化注册、开户、试用激活或账号创建流程时使用。适合减少字段摩擦、提升完成率、优化验证体验并设计测试方案。"
metadata:
  version: 1.1.0
---

# 注册流程转化优化

这是 `signup-flow-cro` 的中文本地化说明版。它不是逐句硬译，而是把原始 `SKILL.md` 整理成更适合中文用户直接执行的工作手册；需要逐段对照英文原版时，请同时查看同目录下的 `SKILL.md`。

## 适用场景

当用户想优化注册、开户、试用激活或账号创建流程时使用。适合减少字段摩擦、提升完成率、优化验证体验并设计测试方案。

## 使用方式

- 先读取 `.agents/product-marketing-context.md`（或旧路径 `.claude/product-marketing-context.md`），避免重复提问并沿用已有定位信息。
- 围绕“初始评估”推进任务，并在需要时回看原版 `Initial Assessment` 小节获取更细颗粒度指引。
- 围绕“核心原则”推进任务，并在需要时回看原版 `Core Principles` 小节获取更细颗粒度指引。
- 围绕“逐字段优化”推进任务，并在需要时回看原版 `Field-by-Field Optimization` 小节获取更细颗粒度指引。
- 围绕“单步与多步流程”推进任务，并在需要时回看原版 `Single-Step vs. Multi-Step` 小节获取更细颗粒度指引。

## 重点关注

原版技能里最值得优先对照的细项通常包括：
- `1. Minimize Required Fields`
- `2. Show Value Before Asking for Commitment`
- `3. Reduce Perceived Effort`
- `4. Remove Uncertainty`
- `Email Field`
- `Password Field`
- `Name Field`
- `Social Auth Options`

## 典型交付物

- `Audit Findings`（原版：`Audit Findings`）
- `Recommended Changes`（原版：`Recommended Changes`）
- `Form Redesign (if requested)`（原版：`Form Redesign (if requested)`）

## 原始章节导航

- `初始评估`（原版：`Initial Assessment`）
- `核心原则`（原版：`Core Principles`）
- `逐字段优化`（原版：`Field-by-Field Optimization`）
- `单步与多步流程`（原版：`Single-Step vs. Multi-Step`）
- `信任建立与阻力降低`（原版：`Trust and Friction Reduction`）
- `移动端注册优化`（原版：`Mobile Signup Optimization`）
- `提交后的体验`（原版：`Post-Submit Experience`）
- `测量`（原版：`Measurement`）
- `输出格式`（原版：`Output Format`）
- `常见注册流程模式`（原版：`Common Signup Flow Patterns`）
- `实验想法`（原版：`Experiment Ideas`）
- `任务专属问题`（原版：`Task-Specific Questions`）

## 相关技能

- `onboarding-cro`
- `form-cro`
- `page-cro`
- `ab-test-setup`

## 使用建议

- 如果你是第一次在这个仓库里使用该技能，先看中文版本建立整体认知，再按需回看英文原版中的细节、模板和边界条件。
- 如果任务涉及多技能串联，优先遵守原版 `Related Skills` 和交叉引用中的边界说明，避免把一个技能的职责做得过宽。
