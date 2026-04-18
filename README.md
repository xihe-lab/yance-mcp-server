# YanceLint MCP Server

[![npm](https://img.shields.io/npm/v/@xihe-lab/yance-mcp-server)](https://www.npmjs.com/package/@xihe-lab/yance-mcp-server)
[![License](https://img.shields.io/npm/l/@xihe-lab/yance-mcp-server)](https://www.apache.org/licenses/LICENSE-2.0)

让 AI（Claude Code）实时感知代码规约违规。

## 简介

YanceLint MCP Server 是 [YanceLint](https://github.com/xihe-lab/yance-idea) 的 Model Context Protocol (MCP) 接口，让支持 MCP 的 AI 工具（如 Claude Code）能够实时获取代码规约检查结果。

## 安装

```bash
# 方式 1：npx 直接运行（推荐，无需安装）
npx @xihe-lab/yance-mcp-server

# 方式 2：全局安装
npm install -g @xihe-lab/yance-mcp-server
yance-mcp-server

# 方式 3：项目级安装
npm install @xihe-lab/yance-mcp-server
npx yance-mcp-server
```

## 注册到 Claude Code

### 推荐：npx 方式（无需安装）

在 `~/.claude.json` 中添加：

```json
{
  "mcpServers": {
    "yancelint": {
      "command": "npx",
      "args": ["-y", "@xihe-lab/yance-mcp-server"]
    }
  }
}
```

`npx` 会自动从 npm 拉取最新版本运行，无需手动安装。

### 全局安装方式

```json
{
  "mcpServers": {
    "yancelint": {
      "command": "yance-mcp-server"
    }
  }
}
```

### 项目级安装方式

```json
{
  "mcpServers": {
    "yancelint": {
      "command": "npx",
      "args": ["yance-mcp-server"]
    }
  }
}
```

## 工具列表

| 工具 | 描述 |
| :--- | :--- |
| `get_file_violations` | 获取指定文件的规约违规列表（来自 P3C/ESLint/Stylelint/Checkstyle） |
| `get_project_summary` | 获取项目级扫描摘要，包含各工具违规总数 |
| `check_health` | 检查 YanceLint Server 运行状态 |

## 前置条件

需要 [YanceLint 插件](https://github.com/xihe-lab/yance-idea) 在 IntelliJ IDEA 中运行：

1. 安装 YanceLint 插件到 IDEA
2. 打开项目时，HTTP Server 自动在 `localhost:63742` 启动
3. 确保 ESLint/Stylelint/P3C/Checkstyle 相关工具已配置

## 使用示例

在 Claude Code 中：

```text
> 检查 src/pages/Home.tsx 有什么规约违规
```

AI 会自动调用 `get_file_violations` 工具获取违规列表并给出修复建议。

## 相关项目

- [yance-idea](https://github.com/xihe-lab/yance-idea) — YanceLint IntelliJ IDEA 插件
- [Claude Code](https://github.com/anthropics/claude-code) — Anthropic 官方 AI 编程助手

## 许可证

Apache License 2.0

Copyright 2025 Xihe Lab (羲和实验室)

详见 [LICENSE](LICENSE) 和 [NOTICE](NOTICE) 文件。

## 联系方式

- 网站：https://www.xihe-lab.com
- 问题反馈：https://github.com/xihe-lab/yance-mcp-server/issues