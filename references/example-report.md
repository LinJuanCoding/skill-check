# 示例报告（renwei-writing）

# Skill 安检报告

## 一、审查结论

**Skill 名称**：renwei-writing
**审查来源**：GitHub 远程（安装前）· orange2ai/renwei-writing
**审查时间**：2026-06-14
**审查范围**：SKILL.md、README.md、README.en.md、LICENSE.md、references/case-study.md、references/post-edit-checklist.md。无 scripts/、hooks.json、.mcp.json、可执行脚本。

### 摘要

| 风险等级 | 建议 | 一句话结论 |
|----------|------|------------|
| 低 | 可安装 | 纯 Markdown 改稿 Skill，未发现外传、读凭据或自动执行脚本；权限与润色用途一致。 |

### 发现项

**红线**：无

**黄线**：

| # | 位置 | 摘录 | 说明 |
|---|------|------|------|
| 1 | README.md | `git clone … ~/.cola/skills/` | 无风险，给用户看的安装说明，非 Agent 指令 |
| 2 | post-edit-checklist.md | Wikipedia、blader/humanizer 链接 | 无风险，文档引用 |
| 3 | SKILL.md | 对照 post-edit-checklist.md | 仅读 Skill 内参考文件，与改稿验收匹配 |

**MCP / Hooks / 脚本**：无

### 能力-权限匹配

| 声称 | 实际 |
|------|------|
| 润色/改稿，保留人味儿 | 处理用户提供的文本 |
| 改后自检 | 读 Skill 内 post-edit-checklist.md |
| 透明交付 | 逐处说明改动，允许还原 |

一致。未要求读 .env、外传、跑终端、装 MCP/Hooks。

### 来源可信度

作者 orange2ai（非 fork）· 约 428 stars · 2026-06 创建/更新 · 无碰瓷命名 · 许可：开源/个人免费，闭源商业需另购授权（非安全问题）

---

## 二、Skill 信息

### 声称能力

「人味儿写作」：用户拿来自己写的文字要打磨、润色、改写，或抱怨「AI 味儿太重」时，以少动、保留手迹、不写金句为原则改稿；改完后对照 post-edit-checklist.md 检查动过的句子；逐处说明改动。参考 Wikipedia Signs of AI writing / blader humanizer。

### 目录结构

```
renwei-writing/
├── SKILL.md
├── README.md / README.en.md
├── LICENSE.md
└── references/
    ├── case-study.md
    └── post-edit-checklist.md
```

约 25 KB，无隐藏大文件、压缩包或 .env。
