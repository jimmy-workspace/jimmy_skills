# Jimmy's Skills Collection

个人常用 AI Agent Skill 集合，适用于 [Codex CLI](https://github.com/openai/codex) 和 [Cursor](https://cursor.com)。

## 快速安装

### Codex CLI

```bash
python ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo jimmy-workspace/jimmy_skills --path skills/<skill-name>
```

### Cursor

```bash
git clone https://github.com/jimmy-workspace/jimmy_skills.git
cp -r jimmy_skills/skills/<skill-name> ~/.cursor/skills/
```

### 项目级（团队共享）

```bash
cp -r jimmy_skills/skills/<skill-name> your-project/.cursor/skills/
```

## Skill 列表

| Skill | 说明 | 触发词 | 平台 |
|-------|------|--------|------|
| [ai-news-digest](skills/ai-news-digest) | 每日 AI 资讯聚合，RSS + Tavily 搜索拉取国际+国内 AI 内容，筛选 Top 10 输出手机友好摘要 | `AI日报` `AI资讯` `AI新闻` `每日推送` | Codex / Cursor |
| [ai-article-writer](skills/ai-article-writer) | AI 爆款文章写作框架，融合卡兹克写作风格，从选题到排版的完整 SOP | `写文章` `爆款文章` `公众号文章` `卡兹克风格` | Codex / Cursor |
| [github-search](skills/github-search) | 搜索筛选 GitHub 开源项目，输出结构化推荐报告 | `找开源项目` `github搜索` `开源项目推荐` | Codex / Cursor |
| [thinking-partner](skills/thinking-partner) | 思考拍档，陪你从混沌中理清局面、锁定核心问题、拆解卡点、共创解法 | `帮我想想` `理清思路` `拆解问题` | Codex / Cursor |

## 目录结构

```
skills/
├── ai-news-digest/
│   ├── SKILL.md
│   ├── config/
│   │   └── api-keys.env
│   └── references/
│       └── sources.md
├── ai-article-writer/
│   ├── SKILL.md
│   ├── self-check.md
│   └── templates.md
├── github-search/
│   └── SKILL.md
└── thinking-partner/
    └── SKILL.md
```

## 添加新 Skill

1. 在 `skills/` 下创建文件夹
2. 编写 `SKILL.md`（包含 YAML frontmatter）
3. 按需添加 `scripts/`、`references/`、`assets/`
4. 在上方表格追加一行

```yaml
---
name: your-skill-name
description: 功能描述 + 触发条件。当用户说"xxx"、"yyy"时触发。
---
```

## License

MIT
