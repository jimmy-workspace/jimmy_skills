# AI 资讯 RSS 信息源

所有源均经过验证可用。标注 `[GitHub RSS]` 的来自 [Olshansk/rss-feeds](https://github.com/Olshansk/rss-feeds) 项目，通过 GitHub Actions 自动生成。

## 一、聚合源（覆盖面最广，优先拉取）

| 名称 | RSS 地址 | 说明 |
|------|---------|------|
| Planet AI | `https://planet-ai.net/rss.xml` | 聚合 38+ AI 源（OpenAI/Anthropic/Google/Meta/HuggingFace 等），一个顶多个 |
| TLDR AI 日报 | `https://bullrich.dev/tldr-rss/ai.rss` | 每日 AI 行业精选摘要 |

## 二、科技媒体（直接 RSS，稳定可靠）

| 名称 | RSS 地址 | 说明 |
|------|---------|------|
| Hacker News AI | `https://hnrss.org/newest?q=AI+OR+LLM+OR+GPT&points=50` | HN 上 50+ 赞的 AI 帖子 |
| TechCrunch AI | `https://techcrunch.com/category/artificial-intelligence/feed/` | 顶级科技媒体 AI 栏目 |
| Google AI Blog | `https://blog.google/technology/ai/rss/` | Google 官方 AI 博客 |

## 三、AI 公司官方博客（GitHub RSS 项目）

| 名称 | RSS 地址 | 说明 |
|------|---------|------|
| Anthropic News | `https://raw.githubusercontent.com/Olshansk/rss-feeds/main/feeds/feed_anthropic_news.xml` | Claude 发布/公司动态 |
| Claude Blog | `https://raw.githubusercontent.com/Olshansk/rss-feeds/main/feeds/feed_claude.xml` | Claude 产品更新 |
| xAI News | `https://raw.githubusercontent.com/Olshansk/rss-feeds/main/feeds/feed_xainews.xml` | Grok 发布/公司动态 |
| Google AI | `https://raw.githubusercontent.com/Olshansk/rss-feeds/main/feeds/feed_google_ai.xml` | Gemini/Nano Banana/DeepMind |
| The Batch | `https://raw.githubusercontent.com/Olshansk/rss-feeds/main/feeds/feed_the_batch.xml` | Andrew Ng 的 AI 周报 |
| Ollama | `https://raw.githubusercontent.com/Olshansk/rss-feeds/main/feeds/feed_ollama.xml` | 本地大模型工具 |

## 四、AI 开发工具

| 名称 | RSS 地址 | 说明 |
|------|---------|------|
| Cursor Changelog | `https://raw.githubusercontent.com/Olshansk/rss-feeds/main/feeds/feed_cursor.xml` | Cursor IDE 更新日志 |
| Claude Code Changelog | `https://raw.githubusercontent.com/Olshansk/rss-feeds/main/feeds/feed_anthropic_changelog_claude_code.xml` | Claude Code CLI 更新 |

## 五、大佬动态

> ⚠️ Twitter/X RSS 在 RSSHub 公共实例上已不可用（2023 年起）。以下改用 WebSearch 方式获取。

当 RSS 源不足时，Skill 应使用 WebSearch 工具搜索以下关键词获取大佬最新动态：

| 人物 | 搜索关键词 | 身份 |
|------|-----------|------|
| Elon Musk | `Elon Musk AI xAI Grok` | xAI CEO |
| Jensen Huang | `Jensen Huang NVIDIA AI` | NVIDIA CEO |
| Sam Altman | `Sam Altman OpenAI` | OpenAI CEO |
| Andrej Karpathy | `Karpathy AI` | 前 Tesla AI 负责人 |
| Yann LeCun | `Yann LeCun Meta AI` | Meta AI 首席科学家 |
| Peter Steinberger | `Peter Steinberger OpenClaw OpenAI` | OpenClaw 创始人 |
| Dario Amodei | `Dario Amodei Anthropic` | Anthropic CEO |
| Demis Hassabis | `Demis Hassabis DeepMind` | Google DeepMind CEO |

## 六、国内源

> ⚠️ RSSHub 公共实例对国内源不稳定（403/超时）。以下提供 RSSHub 路由作为首选，失败时改用 WebSearch。

| 名称 | RSS 地址（首选） | WebSearch 备用关键词 |
|------|---------|------|
| 机器之心 | `https://rsshub.app/jiqizhixin/daily` | `机器之心 AI 今日` |
| 量子位 | `https://rsshub.app/qbitai/category/资讯` | `量子位 AI 资讯` |
| 36氪 AI | `https://rsshub.app/36kr/newsflashes` | `36氪 AI 快讯` |

## 自定义源

如需增减信息源，直接编辑此文件。

可用资源：
- RSSHub 路由文档：https://docs.rsshub.app
- Olshansk/rss-feeds 项目：https://github.com/Olshansk/rss-feeds
- Planet AI 聚合：https://planet-ai.net
