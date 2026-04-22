---
name: analytics-tracking
description: 当用户想搭建、改进或审计分析追踪与测量方案时使用。用户提到 “set up tracking”“GA4”“Google Analytics”“conversion tracking”“event tracking”“UTM parameters”“tag manager”“GTM”“analytics implementation”“tracking plan”“how do I measure this”“track conversions”“attribution”“Mixpanel”“Segment”“are my events firing” 或 “analytics isn't working” 时也应使用。只要有人在问“我怎么知道这个东西有没有效果”，或者想衡量营销结果，就应该使用这个技能。A/B 测试的测量请参见 ab-test-setup。
metadata:
  version: 1.1.0
---

# 分析与追踪埋点

你是一名分析实施与测量专家。你的目标是帮助搭建能支持营销和产品决策的追踪体系，让数据真正可行动。

## 初始评估

**先检查是否有产品营销上下文：**
如果 `.agents/product-marketing-context.md` 存在（旧版设置中也可能是 `.claude/product-marketing-context.md`），在提问之前先读取它。利用其中已有的上下文，只询问尚未覆盖或与当前任务特定相关的信息。

在实施 tracking 前，先搞清楚：

1. **业务背景** - 这些数据要支持哪些决策？关键转化是什么？
2. **当前状态** - 现在已经有了哪些 tracking？在用哪些工具？
3. **技术背景** - 技术栈是什么？是否有隐私 / 合规要求？

---

## 核心原则

### 1. 为决策而追踪，不是为数据而追踪
- 每个事件都应该能支持一个决策
- 避免 vanity metrics
- 事件质量 > 事件数量

### 2. 从问题开始
- 你到底需要知道什么？
- 你会基于这些数据采取什么动作？
- 从这些问题倒推，你到底需要追踪什么

### 3. 一致地命名
- 命名规范很重要
- 实施前先定好模式
- 所有决定都要文档化

### 4. 维护数据质量
- 验证实现是否正确
- 持续监控问题
- 干净数据 > 更多数据

---

## Tracking Plan 框架

### 结构

```text
Event Name | Category | Properties | Trigger | Notes
---------- | -------- | ---------- | ------- | -----
```

### 事件类型

| 类型 | 示例 |
|------|----------|
| Pageviews | 自动采集，配合元数据增强 |
| User Actions | 按钮点击、表单提交、功能使用 |
| System Events | 注册完成、购买、订阅变更 |
| Custom Conversions | 目标完成、漏斗阶段推进 |

**完整事件列表示例**：参见 [references/event-library.md](references/event-library.md)

---

## 事件命名规范

### 推荐格式：Object-Action

```text
signup_completed
button_clicked
form_submitted
article_read
checkout_payment_completed
```

### 最佳实践
- 全部小写，并用下划线分隔
- 尽量具体：`cta_hero_clicked` 优于 `button_clicked`
- 上下文放到 properties 里，而不是塞进 event name
- 避免空格和特殊字符
- 记录命名决策

---

## 关键事件

### 营销站点

| 事件 | Properties |
|-------|------------|
| cta_clicked | button_text, location |
| form_submitted | form_type |
| signup_completed | method, source |
| demo_requested | - |

### 产品 / App

| 事件 | Properties |
|-------|------------|
| onboarding_step_completed | step_number, step_name |
| feature_used | feature_name |
| purchase_completed | plan, value |
| subscription_cancelled | reason |

**按业务类型分类的完整事件库**：参见 [references/event-library.md](references/event-library.md)

---

## 事件属性

### 标准属性

| 类别 | Properties |
|----------|------------|
| Page | page_title, page_location, page_referrer |
| User | user_id, user_type, account_id, plan_type |
| Campaign | source, medium, campaign, content, term |
| Product | product_id, product_name, category, price |

### 最佳实践
- 使用一致的 property names
- 带上必要上下文
- 不要重复平台自动采集的属性
- 避免在 properties 中写入 PII

---

## GA4 实施

### 快速设置

1. 创建 GA4 property 和 data stream
2. 安装 `gtag.js` 或 GTM
3. 开启 enhanced measurement
4. 配置 custom events
5. 在 Admin 中把关键事件标记为 conversions

### 自定义事件示例

```javascript
gtag('event', 'signup_completed', {
  'method': 'email',
  'plan': 'free'
});
```

**详细 GA4 实施**：参见 [references/ga4-implementation.md](references/ga4-implementation.md)

---

## Google Tag Manager

### 容器结构

| 组件 | 作用 |
|-----------|---------|
| Tags | 真正执行的代码（GA4、pixels） |
| Triggers | 什么时候触发 tag（page view、click） |
| Variables | 动态值（click text、data layer） |

### Data Layer 模式

```javascript
dataLayer.push({
  'event': 'form_submitted',
  'form_name': 'contact',
  'form_location': 'footer'
});
```

**详细 GTM 实施**：参见 [references/gtm-implementation.md](references/gtm-implementation.md)

---

## UTM 参数策略

### 标准参数

| 参数 | 用途 | 示例 |
|-----------|---------|---------|
| utm_source | 流量来源 | google, newsletter |
| utm_medium | 营销媒介 | cpc, email, social |
| utm_campaign | Campaign 名称 | spring_sale |
| utm_content | 区分不同版本 | hero_cta |
| utm_term | 付费搜索关键词 | running+shoes |

### 命名规范
- 全部小写
- 使用下划线或连字符，并保持统一
- 具体但简洁：`blog_footer_cta`，而不是 `cta1`
- 用表格集中记录全部 UTM

---

## 调试与验证

### 测试工具

| 工具 | 用途 |
|------|---------|
| GA4 DebugView | 实时查看事件是否进来 |
| GTM Preview Mode | 发布前测试 triggers |
| 浏览器扩展 | Tag Assistant、dataLayer Inspector |

### 验证清单

- [ ] 事件是否在正确 trigger 上触发
- [ ] Property values 是否填充正确
- [ ] 没有重复事件
- [ ] 在不同浏览器和移动端都正常
- [ ] Conversions 是否记录正确
- [ ] 没有 PII 泄漏

### 常见问题

| 问题 | 检查项 |
|-------|-------|
| 事件不触发 | Trigger 配置、GTM 是否加载 |
| 值不对 | Variable 路径、data layer 结构 |
| 重复事件 | 是否有多个 container、trigger 是否重复触发 |

---

## 隐私与合规

### 注意事项
- EU / UK / CA 往往需要 cookie consent
- 不要在 analytics properties 中放 PII
- 检查 data retention 设置
- 确认支持用户删除数据

### 实施方式
- 使用 consent mode（等待用户同意后再采集）
- IP 匿名化
- 只收集真正需要的数据
- 与 consent management platform 集成

---

## 输出格式

### Tracking Plan 文档

```markdown
# [Site/Product] Tracking Plan

## Overview
- Tools: GA4, GTM
- Last updated: [Date]

## Events

| Event Name | Description | Properties | Trigger |
|------------|-------------|------------|---------|
| signup_completed | User completes signup | method, plan | Success page |

## Custom Dimensions

| Name | Scope | Parameter |
|------|-------|-----------|
| user_type | User | user_type |

## Conversions

| Conversion | Event | Counting |
|------------|-------|----------|
| Signup | signup_completed | Once per session |
```

---

## 任务专属问题

1. 你当前在用什么工具？（GA4、Mixpanel 等）
2. 你想追踪哪些关键动作？
3. 这些数据要帮助你做什么决策？
4. 谁来实施？开发团队还是营销团队？
5. 是否有隐私 / consent 要求？
6. 现在已经追踪了哪些内容？

---

## 工具集成

如需真正实施，请参见 [tools registry](../../tools/REGISTRY.md)。关键分析工具包括：

| 工具 | 最适合 | MCP | 指南 |
|------|----------|:---:|-------|
| **GA4** | Web analytics、Google 生态 | ✓ | [ga4.md](../../tools/integrations/ga4.md) |
| **Mixpanel** | Product analytics、event tracking | - | [mixpanel.md](../../tools/integrations/mixpanel.md) |
| **Amplitude** | Product analytics、cohort analysis | - | [amplitude.md](../../tools/integrations/amplitude.md) |
| **PostHog** | 开源 analytics、session replay | - | [posthog.md](../../tools/integrations/posthog.md) |
| **Segment** | CDP、数据路由 | - | [segment.md](../../tools/integrations/segment.md) |

---

## 相关技能

- **ab-test-setup**：用于实验测量
- **seo-audit**：用于自然流量分析
- **page-cro**：用于基于这些数据做转化优化
- **revops**：用于 pipeline 指标、CRM tracking 和收入归因
