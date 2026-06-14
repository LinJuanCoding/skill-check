# Skill 安全审查 — 模式与清单

## 红线模式（出现即标高风险，需人工解释）

### 外传与 C2

```
webhook
discord.com/api
api.telegram.org
pastebin.com
ngrok
requestbin
burpcollaborator
transfer.sh
file.io
0x0.st
```

### 命令外传

```
curl\s+.*(-d|--data|POST)
wget\s+.*--
Invoke-WebRequest
Invoke-RestMethod
fetch\(
axios\.(post|put)
requests\.(post|put)
httpx\.(post|put)
```

### 凭据与密钥路径

```
\.env
credentials\.json
secrets?\.(json|yaml|yml)
api[_-]?key
secret[_-]?key
private[_-]?key
\.pem
id_rsa
id_ed25519
\.aws/credentials
token\.json
serviceaccount
kubeconfig
```

### 绕过与隐蔽

```
不要询问|无需确认|静默|without asking|do not ask
ignore previous|忽略之前|绕过
eval\(
exec\(
subprocess
os\.system
child_process
```

### 硬编码可疑 URL（非知名文档域）

- 短链：t.co、bit.ly、tinyurl（需展开判断）
- 随机子域 + 非标准 TLD
- raw.githubusercontent 指向非作者常用仓库

## 黄线模式（结合语境判断）

```
http://|https://
read_file|Read\(|grep.*\.env
run_terminal|shell|bash|powershell
npm install|npx |uvx |pip install
upload|export|send|transmit|exfil
clipboard|剪贴板
keychain|凭证管理器
chmod|sudo
base64
```

## 应存在的文件（按平台）

| 文件 | 平台 | 说明 |
|------|------|------|
| SKILL.md | 通用 | 必需 |
| hooks.json | Cursor / Claude Code | 事件自动化 |
| .mcp.json / mcp.json | Cursor / Claude Code | MCP 服务 |
| .claude.json | Claude Code 用户级 | 可能含 MCP |
| scripts/* | 可选 | 重点审 |

## 目录清点命令（审查时用，不执行目标 Skill 脚本）

审查员可用只读命令列目录（在目标 Skill 路径下）：

```bash
# Unix
find . -type f | head -200

# PowerShell
Get-ChildItem -Recurse -File | Select-Object FullName, Length
```

## 来源可信度快速项

- 仓库是否 fork 自知名项目但改了 SKILL.md
- 名称碰瓷：`-official`、`-pro`、`-plus`、与知名作者同名
- 单 commit、无 issue、README 与 Skill 能力不符
- 网盘「合集包」无法追溯 diff

## 合理例外（降级说明）

| 场景 | 可能合理的黄/红线 |
|------|-------------------|
| 部署/运维 Skill | 读 `.env`、curl 健康检查（应对内网 URL） |
| 发布/CI Skill | git push、npm publish |
| 文档抓取 Skill | fetch 公开 URL |
| 安全审计 Skill（本 skill） | 列出 curl、.env 等作为**检测模式**而非执行 |

判断关键：**文中是「检测/禁止」还是「要求 Agent 去做」**。
