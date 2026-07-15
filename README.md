**English** · [中文](README.zh.md)

<h1 align="center">Feishu Direction Doc</h1>

<p align="center">
  <em>Turn plain content into structured, visually clear Feishu documents.</em><br>
  <em>把普通内容排成一眼能抓住重点的飞书文档。</em>
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-green.svg" alt="License"></a>
  <a href="https://skills.sh"><img src="https://img.shields.io/badge/skills.sh-Compatible-brightgreen" alt="skills.sh"></a>
  <img src="https://img.shields.io/badge/Claude%20Code-Skill-blue" alt="Claude Code Skill">
  <img src="https://img.shields.io/badge/Codex-Compatible-blueviolet" alt="Codex Compatible">
</p>

**Feishu Direction Doc is a Claude Code / Codex skill for producing polished Feishu documents with semantic color, rich blocks, strong hierarchy, and scannable structure.** It works for decision papers, analytical reports, proposals, knowledge articles, meeting notes, and product documentation.

```bash
npx skills add quzhi-ai/feishu-direction-doc
```

[Why it exists](#why-it-exists) · [Design system](#design-system) · [Install](#install) · [Requirements](#requirements) · [What is included](#what-is-included)

---

## Why It Exists

Many generated documents are text-complete but visually weak. Important conclusions get buried, risks look like ordinary paragraphs, and readers must work too hard to find the decision surface.

This skill applies a small, consistent design system:

- a blue summary callout at the beginning
- semantic color for conclusions, recommendations, risks, and open questions
- tables, callouts, grids, lists, and checkboxes instead of paragraph walls
- light-gray table headers and section separators
- at least 40% rich blocks and no more than three consecutive plain paragraphs

The result is not a fixed template. The document structure follows the content; the visual language stays consistent.

## Design System

| Meaning | Treatment |
| --- | --- |
| Core idea / conclusion | Blue callout |
| Recommendation / positive principle | Green callout |
| Risk / red line | Red callout |
| Attention / pending confirmation | Yellow callout |
| Neutral context | Gray callout |

The skill prefers Feishu XML so it can use native callouts, grids, checkboxes, tables, and whiteboards instead of approximating them with plain Markdown.

## Supported Document Types

- direction papers and decision one-pagers
- analytical reports
- proposals and implementation plans
- knowledge articles and adapted translations
- meeting notes and action lists
- product guides

## Install

### One command

```bash
npx skills add quzhi-ai/feishu-direction-doc
```

### Claude Code

```bash
git clone https://github.com/quzhi-ai/feishu-direction-doc.git
cp -r feishu-direction-doc/skill/feishu-direction-doc ~/.claude/skills/
```

### Codex

```bash
git clone https://github.com/quzhi-ai/feishu-direction-doc.git
cp -r feishu-direction-doc/skill/feishu-direction-doc ~/.codex/skills/
```

Then ask your agent:

```text
Use feishu-direction-doc to turn this report into a polished Feishu document.
```

## Requirements

Publishing requires:

1. [`lark-cli`](https://github.com/larksuite/cli) installed.
2. An authenticated Feishu/Lark user profile with permission to create documents.
3. The profile name supplied in the request or through `LARK_PROFILE`.

The skill creates documents as the authenticated **user**, not as a bot. It does not contain credentials and does not bundle `lark-cli`.

```bash
npm install -g @larksuite/cli
```

If you only want the layout rules, the skill can also generate XML without publishing it.

## What Is Included

```text
feishu-direction-doc/
├── README.md
├── README.zh.md
├── LICENSE
├── RELEASE_NOTES.md
├── demos/
│   └── donate/
│       ├── wechat-pay.jpg
│       └── alipay.jpg
├── examples/
│   └── decision-one-pager.xml
└── skill/
    └── feishu-direction-doc/
        ├── SKILL.md
        ├── agents/
        │   └── openai.yaml
        └── references/
            └── style-spec.md
```

## Example Output Structure

```text
Blue conclusion callout
→ context and scope
→ comparison table or grid
→ green recommendation
→ red risks
→ confirmation checkboxes
```

See [`examples/decision-one-pager.xml`](examples/decision-one-pager.xml) for a reusable, anonymized XML example.

## Security And Account Boundaries

- Never commit access tokens, app secrets, or local profile files.
- Keep work and personal Feishu profiles separate.
- Use the profile explicitly selected for the current task.
- Verify that document creation returns user identity and a readable URL.

## Support The Project

If Feishu Direction Doc helps you create clearer documents, you can buy the author a coffee:

| WeChat Pay | Alipay |
|:---:|:---:|
| <img src="demos/donate/wechat-pay.jpg" width="200"> | <img src="demos/donate/alipay.jpg" width="200"> |

## Star History

<p align="center">
  <a href="https://star-history.com/#quzhi-ai/feishu-direction-doc&Date">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=quzhi-ai/feishu-direction-doc&type=Date&theme=dark" />
      <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=quzhi-ai/feishu-direction-doc&type=Date" />
      <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=quzhi-ai/feishu-direction-doc&type=Date" width="600" />
    </picture>
  </a>
</p>

## License

MIT. See [LICENSE](LICENSE).
