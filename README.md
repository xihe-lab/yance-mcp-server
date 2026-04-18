# YanceLint MCP Server

让 AI（Claude Code）实时感知代码规约违规。

## 安装

```bash
npm install
npx tsc
```

## 注册到 Claude Code

在 `~/.claude.json` 中添加：

```json
{
  "mcpServers": {
    "yancelint": {
      "command": "node",
      "args": ["/path/to/yance-mcp-server/dist/index.js"],
      "env": {
        "YANCELINT_SERVER_URL": "http://localhost:63742"
      }
    }
  }
}
```

## 工具列表

| 工具 | 描述 |
|:---|:---|
| `get_file_violations` | 获取指定文件的规约违规列表 |
| `get_project_summary` | 获取项目级扫描摘要 |
| `check_health` | 检查 YanceLint Server 运行状态 |

## 前置条件

需要 YanceLint 插件在 IntelliJ IDEA 中运行，HTTP Server 在 `localhost:63742` 监听。