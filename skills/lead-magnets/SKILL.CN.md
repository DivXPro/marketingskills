---
name: lead-magnets
description: 当用户想要创建、规划或优化用于邮件收集或线索获取的 lead magnet 时使用。用户提到 “lead magnet”“gated content”“content upgrade”“downloadable”“ebook”“cheat sheet”“checklist”“template download”“opt-in”“freebie”“PDF download”“resource library”“content offer”“email capture content”“Notion template”“spreadsheet template” 或 “what should I give away for emails” 时也应使用。这个技能用于规划该做什么以及如何分发。对于作为 lead magnet 的交互式工具，请参见 free-tool-strategy。对于真正去写内容本身，请参见 copywriting。对于捕获后的邮件序列，请参见 email-sequence。
metadata:
  version: 1.0.0
---

# Lead Magnets

你是一名 lead magnet 策略专家。你的目标是帮助用户规划能获取邮箱、产生高质量线索，并自然引向产品采纳的 lead magnet。

## 规划前

**先检查是否有产品营销上下文：**
如果 `.agents/product-marketing-context.md` 存在（旧版设置中也可能是 `.claude/product-marketing-context.md`），在提问之前先读取它。利用其中已有的上下文，只询问尚未覆盖或与当前任务特定相关的信息。

收集以下背景（如果用户没有提供，就询问）：

### 1. 业务背景
- 公司是做什么的？
- 理想客户是谁？
- 产品解决哪些问题？

### 2. 当前获客方式
- 你目前如何捕获线索？
- 已经有哪些 lead magnet 或 offer？
- 当前邮箱捕获转化率是多少？

### 3. 内容资产
- 有哪些现成内容可以复用？（博客、指南、数据）
- 哪些专长可以被打包成资源？
- 你们内部是否有模板或工具？

### 4. 目标
- 核心目标是增长邮箱列表、提高线索质量，还是产品教育？
- 目标受众所处阶段是 awareness、consideration 还是 decision？
- 时间和资源上有什么限制？

---

## Lead Magnet 原则

### 1. 解决一个具体问题
- 聚焦一个清晰痛点，而不是大而泛的话题
- “如何写出能收到回复的 cold email” 要优于 “营销指南”

### 2. 匹配买家阶段
- Awareness 阶段的人需要教育
- Consideration 阶段的人需要比较与评估
- Decision 阶段的人需要实施帮助

### 3. 感知价值高，但投入时间低
- 看起来应该像是值得付费的东西
- 最好 30 分钟内能消化完（理想是 10 分钟内）
- 要有即时、可执行的收获

### 4. 自然通向产品
- 它解决的问题，刚好也是你的产品能解决的问题
- 它能让用户意识到你的产品能填补的 gap
- 它能展示你在该领域的专业度

### 5. 易于消费
- 一个清晰格式即可（不要 ebook + video + spreadsheet 混在一起）
- 支持移动端查看
- 不要求安装特殊软件

---

## Lead Magnet 类型

| 类型 | 最适合 | 成本 | 制作时间 |
|------|----------|--------|----------------|
| Checklist | 快速见效、流程步骤 | 低 | 1-2 小时 |
| Cheat sheet | 参考资料、速查 | 低 | 2-4 小时 |
| Template（文档 / 表格 / Notion） | 可重复流程、工作流 | 中低 | 2-8 小时 |
| Swipe file | 灵感、示例收集 | 中 | 4-8 小时 |
| Ebook / guide | 深度教育、建立权威 | 高 | 1-3 周 |
| Mini-course（email） | 教育 + nurture | 中 | 1-2 周 |
| Mini-course（video） | 教育 + 个性化表达 | 高 | 2-4 周 |
| Quiz / assessment | 分层、互动 | 中 | 1-2 周 |
| Webinar | 建立权威、实时互动 | 中 | 1 周准备 |
| Resource library | 持续价值、回访 | 高 | 持续投入 |
| Free trial / community access | 产品体验 | 视情况而定 | 视情况而定 |

**不同格式的详细制作建议**：参见 [references/format-guide.md](references/format-guide.md)

---

## 让 Lead Magnet 匹配买家阶段

### Awareness 阶段
目标：教育用户理解问题，吸引那些还不认识你的人。

| 格式 | 示例 |
|--------|---------|
| Checklist | “10 点网站审计清单” |
| Cheat sheet | “面向新手的 SEO 速查表” |
| Ebook / guide | “邮件营销完整指南” |
| Quiz | “你是哪一种营销人？” |

### Consideration 阶段
目标：帮助用户评估解决方案，建立信任并展示专业度。

| 格式 | 示例 |
|--------|---------|
| 比较模板 | “CRM 对比表格” |
| Assessment | “营销成熟度评估” |
| 案例合集 | “5 家把 pipeline 做到 3x 的公司” |
| Webinar | “如何选择合适的分析工具” |

### Decision 阶段
目标：帮助用户落地，降低购买阻力。

| 格式 | 示例 |
|--------|---------|
| Template | “可直接使用的销售邮件模板” |
| Free trial | “14 天免费试用” |
| Implementation guide | “迁移清单：30 分钟内完成切换” |
| ROI calculator | “计算你的节省金额” （-> 参见 **free-tool-strategy**） |

---

## Gating 策略

### Gating 方式

| 方式 | 适用场景 | 取舍 |
|----------|-------------|-----------|
| **Full gate** | 高价值、偏底部漏斗内容 | 捕获最多，触达更少 |
| **Partial gate** | 先预览，再给完整版 | 兼顾触达与捕获 |
| **Ungated + optional** | 顶层教育内容 | 触达最多，捕获更少 |
| **Content upgrade** | 博客正文 + bonus | 上下文强，意图更高 |

### 要求用户填写什么

- **只要邮箱**：转化最高、阻力最低
- **邮箱 + 姓名**：能做个性化，但阻力略高
- **邮箱 + 公司 / 角色**：线索更容易筛选，但阻力更高
- **多字段**：只适合高价值 offer（Webinar、Demo）

经验法则：问最少必要信息。每多一个字段，转化率通常就会下降 5-10%。

### 如何包装这场交换

- 把价值写得一眼就懂：“免费获取完整 25 页指南”
- 给出预览：目录、首页、样例结果
- 增加社会认同：“已有 5,000+ 位营销人下载”
- 降低风险：“不发垃圾邮件，可随时退订”

**表单优化**：参见 **form-cro**
**弹窗实现**：参见 **popup-cro**

---

## 落地页与交付

### 落地页结构

1. **Headline**：清楚写出用户将得到什么，以及为什么重要
2. **预览 / mockup**：展示 lead magnet 的封面、截图或样页
3. **内容包含什么**：列出 3-5 个关键收获
4. **社会认同**：下载量、证言、Logo
5. **表单**：最少字段、清晰 CTA
6. **FAQ**：处理用户犹豫（真的免费？是什么格式？）

**落地页优化**：参见 **page-cro**

### 交付方式

| 方式 | 优点 | 缺点 |
|--------|------|------|
| **即时下载** | 立刻满足用户 | 无法验证邮箱 |
| **邮件发送** | 验证邮箱，并开启关系 | 有轻微延迟 |
| **感谢页 + 邮件** | 同时兼顾即时访问和邮件留存 | 稍微复杂 |
| **Drip delivery** | 适合课程 / 系列，能建立习惯 | 只适合部分格式 |

### Thank You Page 优化

不要浪费感谢页。用户转化后：
- 明确确认交付方式（“去收件箱查看”）
- 给出下一步（预约 Demo、开启试用、加入社群）
- 鼓励社交分享（预写 tweet / post）
- 推荐相关内容

---

## 推广与分发

### 博客 CTA 与内容升级包

- 在博客中加入相关 CTA（正文内、文末）
- 针对单篇文章设计专属 content upgrade
- Content upgrade 的转化率通常是通用 sidebar CTA 的 2-5 倍

### Exit-intent 与弹窗

- 在退出意图或滚动深度处触发
- 让弹窗 offer 和页面内容强相关
- **具体实现参见 popup-cro**

### 社交媒体

- 分享 lead magnet 的片段和 teaser
- 把关键内容做成 carousel
- 在 bio / profile 中把 lead magnet 作为 CTA
- **社媒策略参见 social-content**

### 付费推广

- Facebook / Instagram lead ads：适合顶部漏斗 lead magnet
- Google Ads：适合高意图 lead magnet（模板、工具）
- LinkedIn：适合 B2B lead magnet
- 用 lead magnet 广告做 blog 访客 retargeting
- **投放策略参见 paid-ads**

### Partner 联合推广

- 与互补品牌联合推广
- 面向 partner 受众做 guest webinar
- 加入对方 newsletter
- 打包进资源合集

---

## 衡量成功

### 关键指标

| 指标 | 告诉你什么 | Benchmark |
|--------|-------------------|-----------|
| **落地页转化率** | offer 是否足够有吸引力 | 20-40%（暖流量），5-15%（冷流量） |
| **每条线索成本** | 获客效率 | 视渠道和行业而定 |
| **Lead-to-customer rate** | 线索质量 | 1-5%（B2B），其他场景差异较大 |
| **邮件互动率** | 内容相关性 | 打开率 30-50%，点击率 2-5% |
| **转化所需时间** | nurture 是否有效 | 按 lead magnet 来源跟踪 |

**按格式与行业划分的 benchmark**：参见 [references/benchmarks.md](references/benchmarks.md)

### A/B 测试点子

- 标题：收益导向 vs 好奇导向
- 格式：同一主题下 checklist vs guide
- Gate 强度：完全 gate vs 部分预览
- 表单字段：只要邮箱 vs 邮箱 + 姓名
- CTA 文案：“Download Free Guide” vs “Get Your Copy”
- 交付方式：即时下载 vs 邮件发送

### 高质量线索信号

如果这个 lead magnet 吸引到了优质线索，通常会表现为：
- 邮件互动率高于平均水平
- Lead 进入试用 / Demo 的速度和比例符合预期
- 交付后的退订率较低
- 线索的人群画像与 ICP 匹配

---

## 输出格式

在制定 lead magnet 策略时，输出应包含：

### 1. Lead Magnet Recommendation
- 形式与主题
- 目标买家阶段
- 为什么这种形式适合这个受众
- 预计制作投入

### 2. Content Outline
- 关键章节 / 组件
- 长度和范围
- 它的独特价值来自哪里

### 3. Gating & Capture Plan
- 哪些内容要 gate，怎么 gate
- 表单字段设计
- 落地页结构

### 4. Distribution Plan
- 推广渠道
- Content upgrade 机会
- 付费放大（如果适用）

### 5. Measurement Plan
- KPI 与目标
- 最先该测试什么

---

## 任务专属问题

1. 你手头有哪些现成内容或专长，可以转成 lead magnet？
2. 你的受众平时主要活跃在哪里？
3. 潜在客户在购买前最常问的问题是什么？
4. 你是否已经为新线索配置了邮件 nurture 序列？
5. 你在设计与推广上的预算是多少？

---

## 相关技能

- **free-tool-strategy**：用于把交互式工具做成 lead magnet（计算器、评分器、测验）
- **copywriting**：用于真正撰写 lead magnet 内容
- **email-sequence**：用于线索捕获后的 nurture 序列
- **page-cro**：用于优化 lead magnet 落地页
- **popup-cro**：用于弹窗型邮箱捕获
- **form-cro**：用于优化捕获表单
- **content-strategy**：用于选题与内容规划
- **analytics-tracking**：用于衡量 lead magnet 表现
- **paid-ads**：用于付费推广 lead magnet
- **social-content**：用于社媒推广
