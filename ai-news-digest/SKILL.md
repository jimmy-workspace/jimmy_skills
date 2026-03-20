---
name: ai-news-digest
description: 每日 AI 资讯聚合摘要。从 RSS + Tavily 搜索拉取国际和国内最新 AI 内容（新闻、Twitter/X 大佬动态、技术突破），筛选 Top 10 并生成适合手机阅读的摘要。当用户说"AI日报"、"今日AI"、"AI资讯"、"AI新闻"、"每日推送"、"AI摘要"、"ai-news"时触发。
---

# AI 每日资讯聚合

从国际+国内 AI 信息源拉取最新内容，筛选最有价值的 Top 10，输出手机友好的摘要格式。

- 信息源清单：[sources.md](references/sources.md)
- API Key 配置：[config/api-keys.env](config/api-keys.env)

## 前置：加载 API Key

读取 `config/api-keys.env` 文件，获取 `TAVILY_API_KEY`。后续 Tavily 搜索需要此 key。

## 工作流程

### 第一步：拉取 RSS 信息源

使用 WebFetch 拉取 sources.md 中「一～四」部分的 RSS 源。

拉取规则：
- 优先拉取「一、聚合源」（Planet AI、TLDR AI），覆盖面最广
- 再拉取「二、科技媒体」和「三、AI 公司官方博客」补充细节
- 每个源取最新 10-20 条，只取最近 24 小时内的内容（根据 pubDate 判断）
- 如果某个源拉取失败，跳过并继续，不要中断流程

### 第二步：Tavily 搜索补充 Twitter/X 大佬动态和国内源

使用 Tavily Search API 获取 RSS 覆盖不到的内容（Twitter/X、国内源）。

API 调用方式：
```
POST https://api.tavily.com/search
Headers: Content-Type: application/json
Body: {
  "api_key": "<TAVILY_API_KEY>",
  "query": "<搜索关键词>",
  "search_depth": "basic",
  "max_results": 5,
  "include_domains": ["x.com", "twitter.com"],  // 搜大佬动态时限定
  "days": 1
}
```

搜索任务列表（从 sources.md「五、大佬动态」获取）：

1. **大佬动态**（限定 x.com/twitter.com）：
   - `"Elon Musk AI xAI Grok"`
   - `"Sam Altman OpenAI"`
   - `"Karpathy AI"`
   - `"Jensen Huang NVIDIA AI"`
   - `"Peter Steinberger OpenClaw"`
   - 其他大佬按需搜索，每次选 3-5 个最活跃的

2. **国内 AI 资讯**（不限定域名）：
   - `"AI 新闻 今天"`
   - `"DeepSeek OR Kimi OR 通义千问 最新"`
   - 对 RSS 拉取失败的国内源，使用 sources.md「六」中的备用搜索关键词

搜索规则：
- 设置 `days: 1` 限定最近 24 小时
- 大佬动态搜索限定 `include_domains: ["x.com", "twitter.com"]`
- 国内资讯搜索不限域名，让 Tavily 自动覆盖
- 总搜索次数控制在 8-12 次以内（节省额度）

### 第三步：聚合筛选

将 RSS + Tavily 所有内容合并后执行：

1. **去重**：相同标题或链接的条目只保留一条
2. **过滤噪音**：去掉广告、招聘、无实质内容的条目
3. **相关性排序**：优先保留以下类型
   - AI 模型发布/重大更新（GPT、Claude、Gemini、Grok、Llama、DeepSeek 等）
   - AI 产品/工具发布（出图、视频、Agent 等）
   - AI 行业重大事件（融资、收购、政策）
   - AI 大佬在 Twitter/X 上的重要观点或争议
   - 有深度的技术分析文章
4. **筛选 Top 10**：挑出最有价值的 10 条

### 第四步：生成摘要

对每条内容生成一句话中文摘要（15-30 字），要求：
- 点明核心信息，不要泛泛而谈
- 英文内容翻译为中文
- 保持信息密度
- Twitter/X 内容标注来源人

### 第五步：输出

使用以下固定格式输出（适合飞书/手机端阅读）：

```
🤖 AI 日报 | YYYY-MM-DD

1. **[标题]**
   摘要内容
   🔗 链接

2. **[标题]**
   摘要内容
   🔗 链接

...（共 10 条）

---
数据来源：Planet AI、TechCrunch、Anthropic、X/Twitter、Hacker News、机器之心 等
```

格式规则：
- 标题加粗，中文标题优先（英文原标题可翻译）
- 每条之间空一行
- 链接单独一行，前缀 🔗
- 底部注明实际使用的数据来源
- 国际和国内内容混排，按价值排序，不强制分组

## 注意事项

- 如果当天内容不足 10 条，有多少输出多少，不要凑数
- 如果 Tavily API 调用失败，回退到 WebSearch 兜底
- 如果所有源都拉取失败，仅用 WebSearch 搜索 `AI news today` 和 `AI 新闻 今天`
- 不要输出 RSS 原始 XML 或 Tavily 原始 JSON，只输出最终摘要格式
