# OpenClaw Playground

探索和测试 OpenClaw 功能的实验室项目。

## 包含 Skills

| Skill | 说明 |
|-------|------|
| [agent-browser](./skills/agent-browser) | Vercel Labs 出品的 headless 浏览器自动化 CLI |

## 测试记录

### agent-browser (2026-03-26)

**功能测试：**

| 功能 | 状态 |
|------|------|
| open | ✅ |
| snapshot | ✅ |
| find/click | ⚠️ |
| click --new-tab | ✅ |
| screenshot | ✅ |
| close | ✅ |

**关键发现：**
- ref 每次 snapshot 后会变化
- 点击时使用 `--new-tab` 更可靠
- 支持 accessibility tree，AI 友好

**命令示例：**
```bash
agent-browser open https://example.com
agent-browser snapshot
agent-browser click @e2 --new-tab
agent-browser screenshot ~/Desktop/test.png
agent-browser close
```
