---
name: aso-audit
description: 当用户想要审计或优化 App Store 或 Google Play 上架页时使用。用户提到 “ASO audit”“app store optimization”“optimize my app listing”“improve app visibility”“app store ranking”“audit my listing”“why aren't people downloading my app”“improve my app conversion”“keyword optimization for app” 或 “compare my app to competitors” 时也应使用。当用户分享 App Store 或 Google Play URL 并希望改进时，也要使用。
metadata:
  version: 1.0.0
---

# 应用商店优化审计

根据 ASO 最佳实践分析 App Store 和 Google Play 上架页。抓取实时 listing 数据，对 metadata、视觉素材和评分进行打分，然后给出一个有优先级的行动计划。

## 何时使用

- 用户分享了 App Store 或 Google Play 的 URL
- 用户要求审计或优化某个应用 listing
- 用户想把自己的 app 和竞品做比较
- 用户问 app store 排名、可见性或下载转化相关问题

## 审计前

**先检查是否有产品营销上下文：**
如果 `.agents/product-marketing-context.md` 存在（旧版设置中也可能是 `.claude/product-marketing-context.md`），在提问之前先读取它。利用其中已有的上下文，只询问尚未覆盖或与当前任务特定相关的信息。

## 阶段 1：识别商店并抓取 listing

### 从 URL 识别商店类型

```text
Apple:  apps.apple.com/{country}/app/{name}/id{digits}
Google: play.google.com/store/apps/details?id={package}
```

如果用户给的是 app 名称而不是 URL，就搜索：
`site:apps.apple.com "{app name}"` 或 `site:play.google.com "{app name}"`

### 抓取 listing

使用 WebFetch 拉取 listing 页面，并尽量提取所有可用字段：

**Apple App Store 字段：**

- App name（标题）- 30 字符限制
- Subtitle - 30 字符限制
- Description（长描述）- 不参与搜索索引，但会影响转化
- Promotional text - 170 字符，可不发新版本直接更新
- Category（主 / 次分类）
- Screenshots（数量、顺序、caption 文案）
- Preview video（是否存在、时长）
- Rating（平均分 + 数量）
- 最近评论（可见部分）
- 价格 / 内购
- Developer name
- 最近更新时间
- Version history notes
- 年龄分级
- 大小
- 语言 / 本地化信息
- In-app events（若可见）

**Google Play 字段：**

- App name（标题）- 30 字符限制
- Short description - 80 字符限制
- Full description - 4,000 字符限制，**参与搜索索引**
- Category + tags
- Feature graphic（是否存在）
- Screenshots（数量、顺序）
- Preview video（是否存在）
- Rating（平均分 + 数量）
- 最近评论（可见部分）
- 价格 / 内购
- Developer name
- 最近更新时间
- What’s new 文案
- 下载量区间
- 内容评级
- Data safety 模块
- 语言信息

如果 WebFetch 返回数据不完整（商店常有客户端渲染），要明确记录缺失，并基于当前可见信息继续工作。如果缺失字段很关键，请让用户补充粘贴。

### 视觉素材评估

WebFetch 无法提取截图图片本身或截图文案。**需要对 listing 页面截图** 来获取视觉信息：

1. 打开 listing URL 并抓取整页截图
2. 基于截图评估：图标质量、截图数量、caption 文案、信息传达质量、预览视频是否存在、Feature graphic（Google Play）
3. 如果无法使用浏览器工具，请让用户提供 listing 页截图

**Promotional text（Apple）**：这个 170 字字段通常位于 description 上方，但在抓取后的 HTML 中经常难以和正文区分。如果无法确认它是否存在，应明确说明，并建议用户去 App Store Connect 里自行检查。

---

## 阶段 1.5：评估品牌成熟度

在正式打分前，先把 app 归类到以下三个 tier 之一。这个 tier 会决定你如何解释那些偏离 “教科书式 ASO” 的做法，因为对头部品牌来说，一些看似“没优化”的选择可能其实是有意而为之。

### Tier 定义

| Tier | 信号 | 示例 |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------- |
| **Dominant** | 家喻户晓，100 万+ ratings，类目 Top 10，品牌认知几乎全民级。用户按品牌名搜索，而不是按通用关键词搜索。 | Instagram, Uber, Spotify, WhatsApp, Netflix |
| **Established** | 在所属品类里很知名，10 万+ ratings，有很强的自然安装量，品牌有认知但非全民级。 | Strava, Notion, Duolingo, Cash App, Calm |
| **Challenger** | 正在建立认知，<100K ratings，需要依赖关键词和 ASO 技巧做发现。大多数 app 都属于这一类。 | 你的 app，多数 indie / startup app |

### Tier 如何影响打分

**Dominant app** 在以下维度上要调整评分逻辑：

- **Title**：只放品牌名或品牌优先是合理的（如果品牌本身就是关键词，8 分以上合理）。这类 app 不靠通用词发现。
- **Description**：只按转化质量打分，而不是看关键词覆盖。对全民品牌来说，一段写得好的品牌型描述，通常比关键词堆砌更好。
- **Visual Assets**：用 lifestyle / 品牌摄影，而不是 UI demo，也是合理转化策略。如果产品不适合 30 秒内展示，或者品牌认知已极高，没有视频也可以接受。
- **What’s New**：高频更新场景下，通用 release notes 可以接受（8 分以上）。对大规模产品来说，精细 changelog 的 ROI 往往很低。
- **In-app events**：对安装量巨大的工具型 app（Uber、WhatsApp）而言，缺少 events 不一定扣分，因为它们本来就不依赖 discovery。
- **Localization**：按真实市场来评分，而不是按绝对数量。只做美国市场的 fintech 有英语 + 西语就可能已经足够。

**Established app** 采用“部分放宽”逻辑：

- 品牌优先标题可以接受，但最好仍带 1-2 个关键词
- 在描述策略上，给予更多“有意设计”的解释空间
- 其他维度仍按常规标准打分

**Challenger app** 则严格按教科书式 ASO 最佳实践打分：每一个字符、截图和关键词都很重要。

**核心原则：** 在扣分前先问一句：“这真的是错误，还是一个手里有数据的团队做出的有意选择？” 如果某 app 有 100 万+ ratings 和专门的 ASO 团队，就应默认他们大多数选择是基于数据的，除非明显错误。

---

## 阶段 2：对每个维度打分

使用 `references/scoring-criteria.md` 中的标准，对每个维度按 0-10 打分，并应用阶段 1.5 的品牌成熟度调整逻辑。

可参考的官方规格与 benchmark：

- `references/apple-specs.md` - Apple 官方字符限制、截图 / 视频规格、CPP / PPO 规则、拒审触发点
- `references/google-play-specs.md` - Google Play 官方限制、截图规格、Android Vitals 阈值、政策说明
- `references/benchmarks.md` - 转化数据、评分影响、视频带来的提升、截图行为、CPP / event benchmarks

### 维度与权重

| #   | 维度 | 权重 | 覆盖内容 |
| --- | -------------------- | ------ | ------------------------------------------------------------------------- |
| 1   | Title & Subtitle | 20% | 字符利用率、关键词、清晰度、品牌与关键词平衡 |
| 2   | Description | 15% | 前 3 行、关键词密度（Google）、CTA、结构、promotional text |
| 3   | Visual Assets | 25% | 截图数量 / 质量 / 文案、视频、icon、feature graphic |
| 4   | Ratings & Reviews | 20% | 平均评分、评论量、近期性、开发者回复 |
| 5   | Metadata & Freshness | 10% | 分类是否合适、更新频率、本地化数量、data safety |
| 6   | Conversion Signals | 10% | 价格定位、IAP 透明度、社会认同、下载量区间 |

**最终得分** = 加权总分，满分 100。

### 分数解释

| 分数 | 等级 | 含义 |
| ------ | ----- | --------------------------------------------------------- |
| 85-100 | A | 优化得很好；重点放在 A/B 测试和持续迭代 |
| 70-84  | B | 基础不错；存在明确可提升点 |
| 50-69  | C | 缺口明显；优先修复会有较大影响 |
| 30-49  | D | 多个维度都需要大改 |
| 0-29   | F | listing 需要整体翻新 |

---

## 阶段 3：竞品对比（可选）

如果用户提供了竞品 URL，或明确要求做对比：

1. 抓取同类目下的 2-3 个头部竞品
2. 按同样方式给它们打分
3. 制作对比表，突出用户 app 的强弱项
4. 识别关键词空白：竞品在打的词，而用户 app 没覆盖到的词

如果用户没有给竞品，可以建议他们提供 2-3 个，或者由你代为搜索该类目中的头部 app。

---

## 阶段 4：生成报告

使用 `references/report-template.md` 的结构输出。

报告必须包含：

1. **Score card** - 6 个维度的表格、分数和等级
2. **Top 3 quick wins** - 改动成本 <1 小时但影响最大的动作
3. **Detailed findings** - 按维度拆解问题和修复建议
4. **Keyword suggestions** - 基于标题 / 描述分析与竞品空白得出的关键词建议
5. **Visual asset recommendations** - 针对截图 / 视频的具体优化建议
6. **Priority action plan** - 按影响 / 成本排序的行动列表

### 报告规则

- 每条建议都必须**具体且可执行**，例如 “把 subtitle 从 X 改为 Y”，而不是 “优化 subtitle”
- 所有文字建议都要给出字符数
- 涉及 Apple / Google 差异时，要明确标注平台差异
- 明确说明哪些内容**没有付费工具就无法准确评估**（搜索量、精确排名）
- 推荐关键词时，要解释为什么这个词重要

---

## 平台专属规则

### Apple App Store - 关键事实

- 标题（30 字）+ 副标题（30 字）+ 关键词字段（100 **bytes**，隐藏）共同参与索引
- 关键词字段按 bytes 计，不是按字符；阿拉伯语 / CJK 通常每个字符占 2-3 bytes
- 长描述**不参与搜索索引**，只为转化服务
- Promotional text（170 字）**不影响搜索**
- 不要在标题 / 副标题 / 关键词字段里重复同一词，Apple 通常只记一次
- 关键词字段使用逗号，不加空格：`photo,editor,filter`
- 截图：每设备最多 10 张；搜索结果里通常只先展示前 3 张，90% 用户不会滑过第 3 张
- 自 2025 年 6 月起，截图 caption 也会被索引（用于 AI 提取）
- In-app events：最多同时发布 10 个，每个最多 31 天；会被索引并在搜索中展示
- Custom Product Pages（最多 70 个）自 2025 年 7 月起也可参与自然搜索，平均转化提升约 +5.9%
- App preview video：最多 3 个，每个 15-30 秒，静音自动播放，通常可带来 +20-40% 转化提升
- SKStoreReviewController：365 天内最多弹 3 次
- Apple 有人工 editorial 机制，因此质量和设计感更重要
- 更多规格、尺寸和拒审点参见 `references/apple-specs.md`

### Google Play - 关键事实

- 标题（30 字）+ 短描述（80 字）+ 长描述（4,000 字）共同参与索引
- 长描述**参与索引**，关键词密度自然控制在 2-3% 左右
- 没有隐藏关键词字段，所有关键词都必须出现在可见文本里
- Google 有 NLP / 语义理解，关键词堆砌会被识别并惩罚
- 标题禁止：emoji、全大写、“best” / “#1” / “free”、CTA（自 2021 年起严格执行）
- 截图：每设备最少 2 张，**最多 8 张**（不像 Apple 那样是 10 张）
- Feature graphic（1024x500，尺寸精确）是被推荐位的重要条件
- 视频**不会自动播放**，只有约 6% 用户会主动点开，因此 ROI 通常低于 iOS
- Android Vitals 会直接影响排名：crash >1.09% 或 ANR >0.47% 会降低可见性
- Promotional Content：想要获得 featured，通常要提前 14 天提交；被推荐的 app 可获得约 2x explore acquisitions
- Custom Store Listings：最多 50 个，可针对流失用户、特定国家或广告流量
- Store Listing Experiments：最多同时测 3 个变体，至少跑 7 天，一次只开一个实验
- 更多规格与政策见 `references/google-play-specs.md`

### Apple 会索引什么 vs Google 会索引什么

| 字段 | Apple 索引？ | Google 索引？ |
| --------------------- | ---------------- | ---------------------- |
| 标题 | Yes | Yes（最强信号） |
| 副标题 / 短描述 | Yes | Yes |
| 关键词字段 | Yes（隐藏） | 不存在 |
| 长描述 | No | Yes（强参与） |
| 截图 caption | Yes（自 2025 起） | No |
| In-app events | Yes | N/A（对应的是 LiveOps） |
| Developer name | No | Partial |
| IAP names | Yes | Yes |

---

## 常见问题清单

如果发现这些问题，就要明确标出。标记为 _(tier-dependent)_ 的项目，需要结合品牌成熟度来判断；对 Dominant app 来说，这些有可能是有意为之。

**所有 tier 都应标出：**

- [ ] 评分低于 4.0
- [ ] 最近更新时间超过 3 个月
- [ ] Google Play 描述没有关键词策略（密度低于 1%）
- [ ] Google Play 缺少 feature graphic
- [ ] Apple 关键词字段很可能有重复词（可从 title + subtitle 推断）
- [ ] 分类不匹配，换类目后竞争可能更低
- [ ] 截图少于 5 张

**仅对 Challenger / Established 标出**（对 Dominant 不一定算错）：

- [ ] 标题只用品牌名，浪费字符，没有关键词
- [ ] Subtitle / short description 重复了 title 中已有的关键词
- [ ] 描述前 3 行过于泛泛
- [ ] 没有 preview video
- [ ] 截图只是 UI 堆砌，没有 message / captions
- [ ] 只有 1-2 种本地化
- [ ] 没有 in-app events 或 promotional content

**所有 tier 都可标，但要给上下文说明：**

- [ ] 没有回复差评（需结合评论量规模看）
- [ ] “What’s New” 文案很泛（对 Established / Dominant 的高频发版不一定是问题）

---

## 任务专属问题

1. App Store 或 Google Play 的 URL 是什么？
2. 这是你的 app，还是竞品？
3. 这个 app 所在的类目是什么？
4. 你有没有竞品 URL 可供对比？
5. 你更关注搜索可见性、转化率，还是两者都关注？
6. 你是否能访问 App Store Connect 或 Google Play Console 数据？

---

## 相关技能

- **page-cro**：用于优化承接 app 安装流量的网页落地页
- **ad-creative**：用于生成 App Store / Google Play 广告创意
- **analytics-tracking**：用于安装归因与应用内事件追踪
- **customer-research**：用于理解用户需求和语言，从而优化 listing 文案
