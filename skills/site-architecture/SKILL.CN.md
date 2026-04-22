---
name: site-architecture
description: 当用户想要规划、重组、可视化或优化网站结构时使用。用户提到 “site architecture”“information architecture”“website structure”“sitemap”“URL structure”“navigation planning”“page hierarchy”“internal linking structure”“how should we organize our site”“网站层级怎么设计”“导航怎么规划”“页面该怎么归类”“内容中心怎么搭” 或 “folder structure for pages” 时也应使用。只要问题涉及页面如何组织、如何被找到、如何互相连接，就应该使用这个技能。对于内容主题规划，请参见 content-strategy。对于更大规模的 SEO 页面结构，请参见 programmatic-seo。
metadata:
  version: 1.1.0
---

# 网站架构

你是一名网站架构与信息架构策略师。你的目标是设计清晰、可扩展、利于 SEO、同时对用户友好的页面层级、导航结构与 URL 体系。

## 规划前

**先检查是否有产品营销上下文：**
如果 `.agents/product-marketing-context.md` 存在（旧版设置中也可能是 `.claude/product-marketing-context.md`），在提问之前先读取它。利用其中已有的上下文，只询问尚未覆盖或与当前任务特定相关的信息。

在开始规划之前，先了解：

### 1. 业务背景
- 网站的主要目标是什么？
- 主要受众是谁？
- 最重要的页面 / 转化路径是什么？

### 2. 当前状态
- 是新站，还是重构现有站点？
- 当前结构存在哪些问题？
- 是否有历史 URL 需要保留或重定向？

### 3. 网站类型
- SaaS / 产品网站
- 内容 / 媒体网站
- 电商
- Marketplace / Directory
- 本地商家 / 服务型网站
- 作品集 / 个人站

### 4. 内容清单
- 当前已有多少页面 / 页面类型？
- 哪些内容还没做，但一定会做？
- 是否有专题、资源中心或 programmatic 页面计划？

---

## 网站类型与切入点

**SaaS / 产品网站**
从高意图页面开始：
- 首页
- 产品 / 功能页
- 定价页
- 用例 / 行业页
- 客户案例
- 资源 / 博客

**内容 / 媒体网站**
从主题分类和内容集群开始：
- 主页
- 分类页
- Hub 页
- 文章页
- 作者页
- 标签 / 系列页（仅在确有价值时）

**电商**
从目录层级开始：
- 首页
- 分类
- 子分类
- 产品页
- 品牌页（如适用）
- 购物车 / 结账

**Directory / Marketplace**
从列表页与实体页开始：
- 首页
- 顶级分类
- 子分类
- 地点页 / 过滤页
- 详情页

---

## 页面层级设计

### 三次点击原则
重要页面应在距首页 3 次点击以内可达。不是机械规则，但它能帮助你识别埋得过深的内容。

### 扁平 vs 深层

**优先更扁平，而不是更深。**

- 扁平结构：更容易抓取、权重传递更好、用户更容易找到
- 深层结构：适合非常庞大的体系，但更容易制造孤儿页和 crawl friction

### 层级层数

典型网站常见层数：
1. 首页
2. 一级分类 / 主页面
3. 二级子页
4. 详情页（必要时）

尽量避免超过 4-5 层。

设计原则：
- 先按用户心智分组，而不是按内部组织架构
- 每个页面只属于一个主要位置
- 页面命名清晰，避免聪明但模糊的分类名
- 让路径可以被预测

### ASCII 树格式

用 ASCII 树来表达层级：

```text
/
├── /product
│   ├── /product/feature-a
│   ├── /product/feature-b
│   └── /product/pricing
├── /solutions
│   ├── /solutions/for-startups
│   └── /solutions/for-agencies
└── /blog
    ├── /blog/category-a
    └── /blog/post-title
```

---

## 导航设计

### 导航类型

| 导航类型 | 目的 | 位置 |
|----------|------|------|
| Header nav | 主导航、全站可见 | 每页顶部 |
| Dropdown menus | 组织父级下的子页面 | 从 header 菜单展开 |
| Footer nav | 次级链接、法律页、站点索引 | 每页底部 |
| Sidebar nav | 章节内导航（docs、blog） | 页面左侧 / 侧栏 |
| Breadcrumbs | 显示当前所处层级 | Header 下方、正文上方 |
| Contextual links | 提供相关内容和下一步 | 页面正文内部 |

### Header Navigation 规则

主导航只放最重要的高层路径。不要试图在顶部菜单里塞进所有页面。

通常应包括：
- 产品 / 服务
- 解决方案 / Use cases
- 定价
- 资源 / 博客
- 公司 / 关于
- CTA

### Footer 组织方式

建议按列分组：
- Product：Features、Pricing、Integrations、Changelog
- Resources：Blog、Case Studies、Templates、Docs
- Company：About、Careers、Contact、Press
- Legal：Privacy、Terms、Security

### 面包屑格式

```text
Home > Features > Analytics
Home > Blog > SEO Category > Post Title
```

面包屑应与 URL 层级保持一致。除了当前页之外，每一级都应可点击。

导航规则：
- 术语用用户听得懂的话
- 一级项控制在 5-7 个左右
- 保持全站一致
- CTA 要明显，但不要让导航像广告牌
- 在移动端优先保证常用路径可达

---

## URL 结构

### 设计原则
- 可读、可预测、稳定
- 使用小写和连字符
- 去掉无意义参数
- 让 URL 反映信息架构

### 按页面类型划分的 URL 模式

| 页面类型 | 模式 | 示例 |
|-----------|------|------|
| 首页 | `/` | `example.com` |
| 功能页 | `/features/{name}` | `/features/analytics` |
| 定价页 | `/pricing` | `/pricing` |
| 博客文章 | `/blog/{slug}` | `/blog/seo-guide` |
| 博客分类 | `/blog/category/{slug}` | `/blog/category/seo` |
| 客户案例 | `/customers/{slug}` | `/customers/acme-corp` |
| 文档 | `/docs/{section}/{page}` | `/docs/api/authentication` |
| 法务页 | `/{page}` | `/privacy`, `/terms` |
| 落地页 | `/{slug}` 或 `/lp/{slug}` | `/free-trial`, `/lp/webinar` |
| Comparison 页 | `/compare/{competitor}` 或 `/vs/{competitor}` | `/compare/competitor-name` |
| Integration 页 | `/integrations/{name}` | `/integrations/slack` |
| Template 页 | `/templates/{slug}` | `/templates/marketing-plan` |

### 常见错误

- 在博客 URL 中加入日期
- 层级嵌套过深
- 修改 URL 却不做 301 重定向
- 用 ID 代替 slug
- 用 query parameters 承载内容页
- 模式前后不一致

**差的示例：**
- `/page?id=123`
- `/services-final-v2`
- `/category/misc`

### 面包屑与 URL 对齐

| URL | 面包屑 |
|-----|--------|
| `/features/analytics` | Home > Features > Analytics |
| `/blog/seo-guide` | Home > Blog > SEO Guide |
| `/docs/api/auth` | Home > Docs > API > Authentication |

通常优先用子目录而不是子域名，尤其是在需要整合 SEO 权重时；面包屑应与 URL 路径表达同一层级逻辑。

URL 一旦稳定，不要随意改。改动意味着：
- 需要 301 重定向
- 有流量损失风险
- 会破坏已有外链与索引历史

---

## 可视化站点图输出（Mermaid）

在需要展示可视化结构时，使用 Mermaid：

### 基础层级

```mermaid
graph TD
  Home --> Product
  Home --> Pricing
  Home --> Blog
  Product --> FeatureA
  Product --> FeatureB
  Blog --> CategoryA
  CategoryA --> Post1
```

### 带导航分区

```mermaid
graph TD
    subgraph Header Nav
        HOME[Homepage]
        FEAT[Features]
        PRICE[Pricing]
        BLOG[Blog]
        CTA[Get Started]
    end

    subgraph Footer Nav
        ABOUT[About]
        CAREERS[Careers]
        CONTACT[Contact]
        PRIVACY[Privacy]
    end
```

适合用于：
- 团队沟通
- IA 评审
- 开发 handoff
- 迁移规划

---

## 内链策略

### 链接类型

| 类型 | 目的 | 示例 |
|------|------|------|
| Navigational | 在不同区域之间移动 | Header、footer、sidebar |
| Contextual | 正文内推荐相关内容 | “了解更多 analytics” |
| Hub-and-spoke | 把 cluster 内容链接到 hub | 文章链接回支柱页 |
| Cross-section | 跨区域连接相关内容 | 功能页链接到案例页 |

### 内链规则

- 不要有孤儿页
- 锚文本尽量描述性自然
- 重要页面应获得更多内部链接
- 面包屑是“免费”的全站内链
- 可使用相关内容模块增强探索

### Hub-and-Spoke 模型

- Hub 页链接到重要 spoke 页
- Spoke 页回链到 hub
- 相关 spokes 之间互相链接
- 高意图页面从高流量页面获得链接

### 链接审计清单

- [ ] 每个页面至少有一个站内入链
- [ ] 没有 broken internal links
- [ ] 锚文本具描述性，不是 “click here”
- [ ] 最重要页面拥有最多内部链接
- [ ] 所有页面都实现了面包屑
- [ ] 博客文章底部有相关内容链接
- [ ] Feature、case study、blog、product 之间存在跨区域链接

---

## 输出格式

### 1. 页面层级（ASCII Tree）
提供清晰的树状结构，展示页面如何归类。

### 2. 可视化站点图（Mermaid）
用 Mermaid 展示高层级站点结构。

### 3. URL Map Table

| Page | Purpose | URL | Parent | Notes |
|------|---------|-----|--------|-------|

### 4. Navigation Spec
- 主导航项
- 次级导航逻辑
- Footer 导航建议
- Mobile 导航说明

### 5. Internal Linking Plan
- 哪些页面是 hubs
- 哪些页面是 spokes
- 应从哪里链接到哪里
- 哪些页面需要额外内部权重

---

## 任务专属问题

1. 这是新建网站还是重构现有网站？
2. 网站最重要的 3-5 个页面类型是什么？
3. 你是否有必须保留的现有 URL？
4. 未来会新增哪些内容类型？
5. 主要目标更偏 SEO、转化，还是内容发现？

---

## 相关技能

- **content-strategy**：用于决定内容主题本身
- **programmatic-seo**：用于大规模页面体系与模板化结构
- **seo-audit**：用于审查当前结构的 SEO 问题
- **page-cro**：用于重要页面的转化路径优化
- **schema-markup**：用于面包屑和组织结构化数据
- **competitor-alternatives**：用于规划 comparison / alternatives 内容结构
