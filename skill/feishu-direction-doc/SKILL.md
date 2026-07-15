---
name: feishu-direction-doc
description: |
  Create polished Feishu/Lark documents with semantic color, rich native blocks,
  clear hierarchy, and scannable structure. Use for direction papers, decision
  one-pagers, analytical reports, proposals, knowledge articles, meeting notes,
  and product guides. Applies a blue opening callout, light-gray table headers,
  section separators, no more than three consecutive plain paragraphs, and at
  least 40% rich blocks. Publishes with an authenticated user profile through
  lark-cli when requested. 当用户说“精美飞书文档”“好看的飞书排版”“方向对齐纸”
  “决策一页纸”“彩色飞书文档”或要求把内容做成视觉清晰的飞书文档时使用。
---

# Feishu Direction Doc

Create visually clear Feishu documents with consistent color semantics, rich blocks, and a structure that helps readers find the conclusion quickly.

The style is consistent across document types, but the document outline must follow the content. Do not force every document into the same template.

## Required Reference

Before generating a document, read `references/style-spec.md` completely.

For a self-contained layout example, see the repository file `examples/decision-one-pager.xml` when available. The skill must still work when only the `skill/feishu-direction-doc` directory is installed.

## Identity And Profile Rules

When publishing:

1. Use `lark-cli` with `--as user`; never silently switch to a bot identity.
2. Use the profile explicitly named by the user.
3. Otherwise use the `LARK_PROFILE` environment variable when set.
4. If neither is available, inspect authenticated profiles. If exactly one suitable user profile exists, use it. If several work/personal profiles exist and the choice changes the destination, ask the user which one to use.
5. Never copy credentials, profile configuration, access tokens, or app secrets into the document or repository.
6. Keep work and personal accounts separate. Do not reuse a profile merely because it worked in an earlier task.

If `lark-cli` is unavailable or no authenticated user profile exists, generate the XML and explain what is needed to publish it. Do not claim that a local XML file is a published document.

## Workflow

1. **Understand the content and audience.** Determine the document type, decision surface, source material, and intended readers. Do not ask again for information the user already supplied.
2. **Read `references/style-spec.md`.** Apply its component syntax, color semantics, and richness checks.
3. **Write XML.** Organize the document naturally. Prefer a user-approved project directory or the current working directory.
4. **Inspect before publishing.** Check for sensitive data, broken XML, unsupported HTML/CSS, missing sections, and layout-rule violations.
5. **Publish as the user when requested.** Change into the directory containing the XML and pass the file by relative path.
6. **Verify.** Require a successful response with user identity and a document URL. When target routing matters, fetch/read back the created document if the available tools support it.
7. **Report the result.** Give the document link and one concise sentence. If only XML was generated, link the local artifact and state clearly that it has not been published.

## Publishing Command

Run from the XML file's directory:

```bash
lark-cli docs +create --profile "<profile>" --as user --api-version v2 \
  --doc-format xml --content @"<file-name>.xml"
```

Rules:

- `--content @file` must use a relative file path.
- The returned result must indicate success and user identity.
- Save and return the resulting document URL.
- Do not use a bot or enterprise app as an unannounced fallback.

## Minimum Layout Rules

- Start with a blue callout containing the document's most important sentence.
- Prefer structure over long prose; use tables, callouts, grids, lists, and checkboxes when they improve comprehension.
- Keep consecutive plain `<p>` blocks to three or fewer.
- Put `<hr/>` between major sections.
- Give every table header `background-color="light-gray"`.
- Use fixed semantics: blue = core conclusion, green = recommendation, red = risk, yellow = attention or pending confirmation, gray = neutral context.
- Keep rich-block density at 40% or higher and use at least three rich element types.
- Use plain, direct language. Do not add a logo unless the user asks.
- Prefer Feishu XML over Markdown when the design needs callouts, grids, checkboxes, or whiteboards.

## Structure By Document Type

| Document type | Suggested structure |
| --- | --- |
| Direction paper / decision doc | Conclusion callout → overview table → current scope → success criteria → confirmation checkboxes → recommendation callout |
| Analytical report | Conclusion callout → background → data/findings table → analysis → recommendation callout → risk callout |
| Knowledge article / adaptation | Summary callout → source-led sections → key ideas extracted with callouts or tables |
| Proposal | Goal callout → current state → options table/grid → schedule → risks |
| Meeting notes | Conclusion callout → agenda/issue table → decisions callout → action checkboxes |
| Product guide | Positioning callout → feature table → use-case grid → caution callout |

These are starting points, not mandatory templates.

## Related Tools

- Document creation and editing use `lark-cli docs` or an equivalent Feishu/Lark document tool.
- Other writing or translation skills may provide the content; this skill owns the Feishu XML presentation layer.
