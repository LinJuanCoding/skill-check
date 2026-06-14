# 示例报告（虚构示例，格式参考）

# Skill 安检报告

## 一、审查结论

**Skill 名称**：demo-writer
**审查来源**：GitHub 远程（安装前）· some-org/demo-writer
**审查时间**：2026-06-14
**审查范围**：SKILL.md、README.md、LICENSE.md、references/style-guide.md。无 scripts/、hooks.json、.mcp.json、可执行脚本。

### 摘要

| 风险等级 | 建议 | 一句话结论 |
|----------|------|------------|
| 低 | 可安装 | 纯 Markdown 写作 Skill，未发现外传、读凭据或自动执行脚本；权限与写作用途一致。 |

### 发现项

**红线**：无

**黄线**：

| # | 位置 | 摘录 | 说明 |
|---|------|------|------|
| 1 | README.md | `git clone … ~/.skills/` | 无风险，给用户看的安装说明，非 Agent 指令 |
| 2 | style-guide.md | 外部文档链接 | 无风险，文档引用 |
| 3 | SKILL.md | 对照 references/style-guide.md | 仅读 Skill 内参考文件，与写作验收匹配 |

**MCP / Hooks / 脚本**：无

### 能力-权限匹配

| 声称 | 实际 |
|------|------|
| 润色/改稿 | 处理用户提供的文本 |
| 改后自检 | 读 Skill 内 references/style-guide.md |
| 透明交付 | 逐处说明改动，允许还原 |

一致。未要求读 .env、外传、跑终端、装 MCP/Hooks。

### 来源可信度

作者 some-org（非 fork）· 公开仓库 · 无碰瓷命名 · MIT 许可（非安全问题）

---

## 二、Skill 信息

### 声称能力

帮助用户润色、改写自己写的文字；少动原文、保留个人风格；改完后对照 style-guide 检查动过的句子。

### 目录结构

```
demo-writer/
├── SKILL.md
├── README.md
├── LICENSE.md
└── references/
    └── style-guide.md
```

约 20 KB，无隐藏大文件、压缩包或 .env。
