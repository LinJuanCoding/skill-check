# skill-check

安装 Agent Skill **之前**，用 AI 做静态安全审查。

支持审查本地已装 Skill、GitHub / Git 链接（浅克隆到临时目录，**不写入** skills 目录）。输出**结论前置**的安检报告：风险等级、红线/黄线、能力-权限是否匹配，以及这个 Skill 到底是干什么的。

适用于 Cursor、Claude Code、Codex 等带 Skill 机制的 Agent 环境。

## 快速安装

**Cursor（个人，推荐）**

```bash
git clone --depth 1 https://github.com/LinJuanCoding/skill-check.git ~/.cursor/skills/skill-check
```

**Cursor（仅当前项目）**

```bash
git clone --depth 1 https://github.com/LinJuanCoding/skill-check.git .cursor/skills/skill-check
```

**Claude Code**

```bash
git clone --depth 1 https://github.com/LinJuanCoding/skill-check.git ~/.claude/skills/skill-check
```

安装后新开 Agent 对话，或 Reload Window。

## 怎么用

在对话里 @ 本 Skill，或直接说：

```
@skill-check 审查 https://github.com/someone/some-skill.git
@skill-check 审查 ~/.cursor/skills/mywriter
skill 安全吗？能装吗？
```

Agent 会只读扫描目标文件，**不执行**被审查 Skill 里的脚本。

## 仓库里有什么

| 文件 | 说明 |
|------|------|
| [SKILL.md](SKILL.md) | 审查流程、报告模板、远程 URL 审查步骤 |
| [references/audit-patterns.md](references/audit-patterns.md) | 红线/黄线关键词与路径清单 |
| [references/example-report.md](references/example-report.md) | 完整报告示例（renwei-writing） |

## 报告长什么样

1. **审查结论**（前置）：风险等级、建议、红线/黄线、能力-权限、来源可信度  
2. **Skill 信息**（后置）：声称能力、目录结构  

不包含安装清单、局限性长文、修复建议等干扰决策的板块。

## 能查什么 / 查不了什么

**能发现**：正文里的危险指令、脚本、MCP/Hooks 配置、读凭据/外传话术、权限与用途不匹配。

**不能保证**：二进制内部逻辑、运行时下载、作者后续更新、MCP 进程内恶意行为。静态审查 ≠ 绝对安全。

## License

MIT — 见 [LICENSE](LICENSE)。

## 作者

出海搞副业 · [LinJuanCoding](https://github.com/LinJuanCoding)
