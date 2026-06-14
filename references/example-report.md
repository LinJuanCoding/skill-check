# 示例报告（skill-check）

# Skill 安检报告

## 一、审查结论

**目标**：https://github.com/LinJuanCoding/skill-check
**审查模式**：安装前远程审查（未安装）
**审查时间**：2026-06-14
**审查范围**：SKILL.md、README.md、LICENSE、references/audit-patterns.md、references/example-report.md。无 scripts/、hooks.json、.mcp.json、可执行脚本。

### 摘要

| 风险等级 | 建议 | 一句话结论 |
|----------|------|------------|
| 低 | 可安装 | 纯 Markdown 安检 Skill，自身无脚本/MCP/Hooks；正文中的 clone、WebFetch 仅用于审查目标 Skill，且要求不执行被审脚本。 |

### 发现项

**红线**：无

**黄线**：

| # | 位置 | 摘录 | 说明 |
|---|------|------|------|
| 1 | SKILL.md | `git clone --depth 1 <url> <临时目录>` | 无风险，对被审查仓库浅克隆到临时目录 |
| 2 | SKILL.md | `mcp_web_fetch` / WebFetch | 无风险，clone 失败时只读拉取目标文件 |
| 3 | audit-patterns.md | webhook、curl、.env 等词表 | 无风险，检测模式列举，非执行指令 |
| 4 | README.md | `git clone … skill-check.git` | 无风险，给用户看的安装说明，非 Agent 指令 |

**MCP / Hooks / 脚本**：无

### 能力-权限匹配

| 声称 | 实际 |
|------|------|
| 安装前审查 Skill 安全 | 只读扫描目标目录文本，输出报告 |
| 支持 GitHub URL | 指导将目标浅克隆到临时目录后审查 |
| 不执行被审脚本 | 正文要求不执行目标脚本、不外传被审内容 |
| 模式扫描 | 读 audit-patterns.md 作关键词对照 |

一致。未要求读用户 .env、外传用户数据、为自身安装 MCP/Hooks。

### 来源可信度

出海搞副业 · LinJuanCoding（非 fork）· MIT 许可（非安全问题）

---

## 二、Skill 信息

### 声称能力

安装或启用第三方 Skill 之前做静态安全审查。支持本地路径与 GitHub/Git URL（浅克隆到临时目录，不写入 skills 目录）。输出结论前置报告（风险等级、红线/黄线、能力-权限、来源可信度 + Skill 是什么）。触发词包括 skill-check、查 skill、skill 安全吗、能装吗 等。

### 目录结构

```
skill-check/
├── SKILL.md
├── README.md
├── LICENSE
└── references/
    ├── audit-patterns.md
    └── example-report.md
```

约 15 KB，无隐藏大文件、压缩包或 .env。
