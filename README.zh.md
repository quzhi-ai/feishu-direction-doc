**中文** · [English](README.md)

<h1 align="center">飞书精美文档排版 Skill</h1>

<p align="center">
  <em>把普通内容排成一眼能抓住重点的飞书文档。</em><br>
  <em>不是套固定模板，而是给不同体裁一套稳定的视觉语言。</em>
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-green.svg" alt="License"></a>
  <a href="https://skills.sh"><img src="https://img.shields.io/badge/skills.sh-Compatible-brightgreen" alt="skills.sh"></a>
  <img src="https://img.shields.io/badge/Claude%20Code-Skill-blue" alt="Claude Code Skill">
  <img src="https://img.shields.io/badge/Codex-Compatible-blueviolet" alt="Codex Compatible">
</p>

**Feishu Direction Doc 是一个面向 Claude Code / Codex 的飞书文档排版 Skill。** 它会用颜色语义、原生富 block、清晰层级和结构化表达，把方向纸、分析报告、方案、知识文章、会议纪要和产品说明排成更容易阅读和决策的飞书文档。

```bash
npx skills add quzhi-ai/feishu-direction-doc
```

[为什么需要它](#为什么需要它) · [视觉规则](#视觉规则) · [安装](#安装) · [使用前提](#使用前提) · [项目结构](#项目结构)

---

## 为什么需要它

很多 AI 生成文档“内容齐了”，但仍然不好读：结论埋在段落里，风险和背景长得一样，读者很难快速找到要确认的事情。

这个 Skill 用一套简单、稳定的规则解决这些问题：

- 文首必须有蓝色结论 callout
- 结论、推荐、风险、待确认分别使用固定颜色
- 能用表格、框、分栏、列表、checkbox，就不堆长段落
- 表头统一浅灰，章节之间用分隔线
- 富 block 密度不低于 40%，连续纯段落不超过 3 个

它不是固定模板。文档结构跟着内容走，视觉语言保持一致。

## 视觉规则

| 语义 | 表达方式 |
| --- | --- |
| 核心观点 / 结论 | 蓝色 callout |
| 推荐 / 正面原则 | 绿色 callout |
| 风险 / 红线 | 红色 callout |
| 注意 / 待确认 | 黄色 callout |
| 中性说明 | 灰色 callout |

Skill 优先生成飞书 XML，直接使用飞书原生的 callout、表格、分栏、checkbox 和画板，而不是用纯 Markdown 勉强模拟版式。

## 适用场景

- 方向纸、决策一页纸
- 分析报告
- 方案文档、实施计划
- 知识文章、翻译改写
- 会议纪要、行动清单
- 产品说明

## 安装

### 一条命令安装

```bash
npx skills add quzhi-ai/feishu-direction-doc
```

### Claude Code 手动安装

```bash
git clone https://github.com/quzhi-ai/feishu-direction-doc.git
cp -r feishu-direction-doc/skill/feishu-direction-doc ~/.claude/skills/
```

### Codex 手动安装

```bash
git clone https://github.com/quzhi-ai/feishu-direction-doc.git
cp -r feishu-direction-doc/skill/feishu-direction-doc ~/.codex/skills/
```

安装后可以直接说：

```text
请用 feishu-direction-doc 把这份报告做成精美飞书文档。
```

## 使用前提

如果要直接发布到飞书，需要：

1. 安装 [`lark-cli`](https://github.com/larksuite/cli)。
2. 已登录一个有文档创建权限的飞书/Lark User profile。
3. 在请求中明确 profile，或设置环境变量 `LARK_PROFILE`。

Skill 会以登录用户身份创建文档，不会使用 bot 身份，也不包含任何账号凭证。只想使用排版规则时，也可以让它仅生成 XML，不发布到飞书。

```bash
npm install -g @larksuite/cli
```

## 项目结构

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

脱敏示例见 [`examples/decision-one-pager.xml`](examples/decision-one-pager.xml)。

## 账号与安全边界

- 不要提交 access token、app secret 或本地 profile 配置。
- 公司飞书与个人飞书 profile 必须分开。
- 只使用当前任务明确选择的 profile，不猜测旧账号。
- 创建后确认返回的是 user identity，并检查文档链接可读。

## 支持项目

如果这个 Skill 帮你做出了更清晰的飞书文档，欢迎请作者喝杯咖啡：

| 微信支付 | 支付宝 |
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

## 开源协议

MIT，详见 [LICENSE](LICENSE)。
