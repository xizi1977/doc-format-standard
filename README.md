# doc-format-standard

一套面向 AI 生产文档的格式、Markdown 清洗、DOCX 排版与去 AI 化行文规范 Skill，适用于 Codex、Kimi、Manus、Claude Code 等 AI 工具处理文档类任务。

## 简介

本 Skill 用于约束 AI 在生成、审查、清洗和转换文档时的行为，可配合 Codex、Kimi、Manus、Claude Code 等工具使用，重点解决以下问题：

- Markdown 转 DOCX 后残留 `#`、`**`、`---`、代码围栏、表格管道符等符号。
- Word 正文缩进、行距、段前段后、序号格式不统一。
- 标题编号、正文编号、图表编号混乱。
- 表格不是 Word 真实表格，或表格超出页面边距。
- 文档存在明显 AI 化套话、空泛表达和营销式语言。
- 长文档修改时直接把全文打印到聊天界面，影响阅读和审查。

## 适用场景

- 生成技术方案文档。
- 编写功能模块说明。
- 撰写项目交付物。
- Markdown 转 DOCX / Word。
- DOCX 格式规范化审查。
- AI 生成文档的去 AI 化审校。
- Codex / Kimi / Manus / Claude Code 项目中的文档格式统一约束。

## 规范涵盖内容

| 章节 | 说明 |
|---|---|
| 页面与版式 | A4、页边距、颜色、装饰控制 |
| 字体与字号 | 标题、正文、表格、代码块字号要求 |
| 正文段落 | 两端对齐、首行缩进、行距、段前段后 |
| 标题编号 | 1、1.1、1.1.1 统一层级 |
| 正文序号 | （1）（2）（3）、1）2）3）、a）b）c） |
| Markdown 清洗 | 清理 #、**、---、代码围栏、表格管道符等残留 |
| 表格规范 | Markdown 表格转真实 Word 表格，表题、表头、跨页规则 |
| 图示规范 | 黑白线框图、图题、编号、正文引用 |
| 目录页码 | 自动目录、页码、页眉页脚要求 |
| 去 AI 化 | 删除空泛套话、营销表达、未证实指标 |
| 交付验收 | DOCX 交付前检查清单 |

## Codex 使用方式

将本仓库中的 `AGENTS.md` 放到需要处理文档的项目根目录，Codex 会优先读取其中的项目级执行规则。

建议项目结构：

```text
project-root/
├─ AGENTS.md
├─ docs/
│  ├─ input.md
│  └─ output.docx
└─ README.md
```

推荐给 Codex 的任务描述：

```text
请按照 AGENTS.md 和 doc-format-standard 的要求，将 docs/input.md 转换为正式 DOCX 文档。
要求：
1. 清理所有 Markdown 残留符号；
2. 设置标题、正文、表格、代码块样式；
3. 统一正文首行缩进、行距、段前段后；
4. 统一标题编号和正文列表编号；
5. 将 Markdown 表格转换为真实 Word 表格；
6. 生成 DOCX 后执行交付前检查；
7. 不要在聊天界面打印全文，只输出修改摘要和文件路径。
```

## Kimi 使用方式

将 `SKILL.md`、`AGENTS.md` 或 `templates/markdown-to-docx-prompt.md` 中的规则作为上下文提供给 Kimi，再上传需要处理的 Markdown 文档，让 Kimi 按规则进行清洗、审查或生成转换任务提示词。

推荐给 Kimi 的任务描述：

```text
请严格按照 doc-format-standard 的文档格式规范，审查并清洗我上传的 Markdown 文档。
重点检查：Markdown 残留、标题编号、正文缩进、字体字号、黑白正式样式、表格转换、代码块保护区、图表编号和 DOCX 交付前验收项。
不要改变原文事实和技术内容，只输出问题清单、修改建议和可交付版本。
```

## Manus 使用方式

将 `doc-format-standard/` 目录整体复制到 Manus 的 Skills 目录下：

```bash
cp -r doc-format-standard/ ~/skills/
```

## 文件说明

| 文件 | 作用 |
|---|---|
| `SKILL.md` | Skill 主规范，定义文档格式、Markdown 清洗、DOCX 排版和验收要求 |
| `AGENTS.md` | Codex 项目级执行规则，可复制到项目根目录 |
| `checklists/docx-delivery-checklist.md` | DOCX 交付前检查清单 |
| `templates/markdown-to-docx-prompt.md` | Markdown 转 DOCX 任务提示词模板 |

## 许可证

MIT License — 开源免费使用。
