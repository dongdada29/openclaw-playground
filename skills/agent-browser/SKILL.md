---
name: agent-browser
description: "Headless 浏览器自动化 CLI，基于 Chrome DevTools Protocol。支持 open/snapshot/click/fill/screenshot 等操作，适合 AI agent 网页交互。"
metadata:
  openclaw:
    emoji: "🌐"
    user-invocable: true
---

# agent-browser Skill

Vercel Labs 出品的 headless 浏览器自动化 CLI，Rust 编写，速度快。

## 环境要求

- **Chrome** - 系统已安装，无需额外下载
- **agent-browser** - 已全局安装

## 命令速查

### 基础命令

| 命令 | 功能 |
|------|------|
| `agent-browser open <url>` | 打开网页 |
| `agent-browser snapshot` | 获取 accessibility tree (AI 友好) |
| `agent-browser close` | 关闭浏览器 |

### 交互命令

| 命令 | 功能 |
|------|------|
| `agent-browser click <ref>` | 点击元素 (如 `@e2`) |
| `agent-browser fill <ref> <text>` | 填写表单 |
| `agent-browser type <ref> <text>` | 输入文字 |
| `agent-browser press <key>` | 按键 (Enter/Tab/Control+a) |

### 获取信息

| 命令 | 功能 |
|------|------|
| `agent-browser get title` | 获取页面标题 |
| `agent-browser get url` | 获取当前 URL |
| `agent-browser get text <ref>` | 获取文本内容 |

### 截图

| 命令 | 功能 |
|------|------|
| `agent-browser screenshot` | 截图 |
| `agent-browser screenshot <path>` | 保存到指定路径 |

### 语义定位

| 命令 | 功能 |
|------|------|
| `agent-browser find role button click --name "Submit"` | 按 role 查找并点击 |
| `agent-browser find text "Sign In" click` | 按文本查找并点击 |
| `agent-browser find label "Email" fill "test@test.com"` | 按 label 查找并填写 |

## 执行逻辑

当用户请求网页操作时，使用 `exec` 工具执行命令。

### 示例流程

```bash
# 1. 打开网页
agent-browser open https://example.com

# 2. 获取页面快照（AI 友好的 accessibility tree）
agent-browser snapshot

# 3. 根据 ref 点击
agent-browser click @e2

# 4. 填写表单
agent-browser fill @e3 "test@example.com"

# 5. 截图
agent-browser screenshot

# 6. 关闭
agent-browser close
```

## 注意事项

1. **ref 是动态的** - 每次 snapshot 后 ref 会变化
2. **先 snapshot 再交互** - 先获取树，再根据 ref 操作
3. **浏览器必须先 open** - 所有操作需要先打开网页
4. **close 要养成习惯** - 操作完记得关闭浏览器
