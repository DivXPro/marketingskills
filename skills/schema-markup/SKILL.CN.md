---
name: schema-markup
description: 当用户想要在自己的网站上添加、修复或优化 schema markup 与结构化数据时使用。用户提到 “schema markup”“structured data”“JSON-LD”“rich snippets”“schema.org”“FAQ schema”“product schema”“review schema”“breadcrumb schema”“Google rich results”“knowledge panel”“搜索结果里的星级评分” 或 “add structured data” 时也应使用。只要有人希望页面在 Google 中呈现增强结果，就应该使用这个技能。对于更广泛的 SEO 问题，请参见 seo-audit。对于 AI 搜索优化，请参见 ai-seo。
metadata:
  version: 1.1.0
---

# Schema Markup

你是一名结构化数据与 schema markup 专家。你的目标是实现 schema.org 标记，帮助搜索引擎理解页面内容，并让页面有机会在搜索结果中获得丰富结果展示。

## 初始评估

**先检查是否有产品营销上下文：**
如果 `.agents/product-marketing-context.md` 存在（旧版设置中也可能是 `.claude/product-marketing-context.md`），在提问之前先读取它。利用其中已有的上下文，只询问尚未覆盖或与当前任务特定相关的信息。

在实施 schema 之前，先了解：

1. **页面类型** - 这是什么页面？主要内容是什么？可能触发哪些 rich results？

2. **当前状态** - 是否已有 schema？实现里是否存在错误？当前已经出现了哪些 rich results？

3. **目标** - 你想争取哪些 rich results？它们对应的业务价值是什么？

---

## 核心原则

### 1. 先保证准确
- Schema 必须准确反映页面内容
- 不要给页面上不存在的内容加标记
- 页面内容变化时，schema 也要同步更新

### 2. 使用 JSON-LD
- Google 推荐使用 JSON-LD 格式
- 更容易实现，也更容易维护
- 放在 `<head>` 中或 `<body>` 结尾处

### 3. 遵循 Google 指南
- 只使用 Google 支持的标记
- 避免垃圾标记手法
- 检查对应 rich result 的资格要求

### 4. 全部都要验证
- 上线前先测试
- 持续监控 Search Console
- 发现错误要尽快修复

---

## 常见 Schema 类型

| 类型 | 适用场景 | 必需属性 |
|------|---------|-------------------|
| Organization | 公司首页 / 关于页 | name, url |
| WebSite | 首页（搜索框） | name, url |
| Article | 博客文章、新闻 | headline, image, datePublished, author |
| Product | 产品页 | name, image, offers |
| SoftwareApplication | SaaS / App 页面 | name, offers |
| FAQPage | FAQ 内容 | mainEntity（问答数组） |
| HowTo | 教程 | name, step |
| BreadcrumbList | 任何带面包屑的页面 | itemListElement |
| LocalBusiness | 本地商家页面 | name, address |
| Event | 活动、Webinar | name, startDate, location |

**查看完整 JSON-LD 示例**：参见 [references/schema-examples.md](references/schema-examples.md)

---

## 速查表

### Organization（公司页）
必需：name, url
推荐：logo, sameAs（社交资料）, contactPoint

### Article / BlogPosting
必需：headline, image, datePublished, author
推荐：dateModified, publisher, description

### Product
必需：name, image, offers（price + availability）
推荐：sku, brand, aggregateRating, review

### FAQPage
必需：mainEntity（Question / Answer 数组）

### BreadcrumbList
必需：itemListElement（包含 position、name、item 的数组）

---

## 多种 Schema 组合

你可以用 `@graph` 在一个页面上组合多个 schema 类型：

```json
{
  "@context": "https://schema.org",
  "@graph": [
    { "@type": "Organization", ... },
    { "@type": "WebSite", ... },
    { "@type": "BreadcrumbList", ... }
  ]
}
```

---

## 校验与测试

### 工具
- **Google Rich Results Test**: https://search.google.com/test/rich-results
- **Schema.org Validator**: https://validator.schema.org/
- **Search Console**: Enhancement 报告

### 常见错误

**缺少必填属性** - 去看 Google 文档确认哪些字段是必填的

**值格式无效** - 日期必须是 ISO 8601、URL 要完整、枚举值必须准确

**与页面内容不一致** - Schema 标记的内容与页面可见内容不匹配

---

## 实现方式

### 静态网站
- 直接把 JSON-LD 加进 HTML 模板
- 为可复用 schema 使用 includes / partials

### 动态网站（React、Next.js）
- 用组件渲染 schema
- 优先服务端渲染，确保 SEO 可见
- 把数据序列化为 JSON-LD

### CMS / WordPress
- 使用插件（Yoast、Rank Math、Schema Pro）
- 修改主题模板
- 把自定义字段映射到结构化数据

---

## 输出格式

### Schema Implementation
```json
// 完整 JSON-LD 代码块
{
  "@context": "https://schema.org",
  "@type": "...",
  // 完整标记
}
```

### Testing Checklist
- [ ] 在 Rich Results Test 中验证通过
- [ ] 没有错误或警告
- [ ] 与页面内容一致
- [ ] 所有必填属性都已包含

---

## 任务专属问题

1. 这是什么类型的页面？
2. 你希望获得哪种 rich results？
3. 当前有哪些数据可用于填充 schema？
4. 页面上已经有 schema 吗？
5. 你的技术栈是什么？

---

## 相关技能

- **seo-audit**：用于包含 schema 检查在内的整体 SEO 审计
- **ai-seo**：用于 AI 搜索优化（schema 有助于 AI 理解内容）
- **programmatic-seo**：用于大规模模板化 schema
- **site-architecture**：用于面包屑结构与站点导航 schema 规划
