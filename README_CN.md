# Claude Agent SDK 技能

中文 | [English](./README.md)

为 Claude Agent SDK（TypeScript 和 Python）提供专业辅助的自定义 Claude Code 技能。

## 概述

本项目为 Claude Code 提供专门的技能，帮助您深入了解 Claude Agent SDK 的专业知识。这些技能帮助您构建 AI 驱动的应用程序，包含正确的 API 使用、最佳实践和全面的代码示例。

## 可用技能

### agent-sdk-ts

TypeScript Agent SDK 专家，提供：

- 核心 SDK 函数：`query()`、`tool()`、`createSdkMcpServer()`
- 配置选项和用例
- 代理定义和子代理模式
- 所有内置工具的工具输入/输出类型
- MCP 服务器配置（stdio、SSE、HTTP、SDK）
- Hook 事件和回调模式
- 权限模式和自定义授权
- 文件检查点和回滚功能
- 会话管理和恢复
- 使用 JSON schema 的结构化输出
- 沙盒配置和安全

### agent-sdk-py

Python Agent SDK 专家，提供：

- 核心 SDK 函数：`query()`、`ClaudeSDKClient`、`tool()`、`create_sdk_mcp_server()`
- 在不同用例中选择 `query()` 或 `ClaudeSDKClient`
- 使用 `ClaudeAgentOptions` 的配置选项
- 消息类型：`UserMessage`、`AssistantMessage`、`SystemMessage`、`ResultMessage`
- 内容块：`TextBlock`、`ThinkingBlock`、`ToolUseBlock`、`ToolResultBlock`
- 代理定义和子代理模式
- MCP 服务器配置
- Hook 事件和回调模式
- 使用 `can_use_tool` 回调的自定义权限处理
- 会话管理和对话连续性
- 使用 `@tool` 装饰器的自定义工具
- 错误处理：`CLINotFoundError`、`ProcessError`、`CLIJSONDecodeError`

## 安装

1. 将 `.claude/skills/` 目录复制到您的项目中
2. 确保已安装 Claude Code：`npm install -g @anthropic-ai/claude-code`
3. 运行 Claude Code 时，这些技能将自动可用

## 使用方法

当您询问以下问题时，Claude Code 会自动调用这些技能：

- SDK API 使用和模式
- 代理配置和设置
- MCP 服务器集成
- Hook 和权限
- 文件检查点
- 工具开发
- 错误处理
- 最佳实践

示例提示词：

- "如何在 Python SDK 中使用 query() 函数？"
- "使用 TypeScript 创建自定义 MCP 工具"
- "设置权限 hook 以阻止某些操作"
- "使用 SDK 处理流式输入"

## 文档参考

每个技能都包含全面的文档参考：

- **TypeScript**：参见 `.claude/skills/agent-sdk-ts/AGENT_SDK_DOCS.md`
- **Python**：参见 `.claude/skills/agent-sdk-py/AGENTS_SDK_DOCS.md`

## 系统要求

- 已安装 Claude Code CLI
- Node.js/npm（用于 TypeScript SDK）
- Python 3.8+（用于 Python SDK）
- 已安装相应的 SDK 包：
  - TypeScript：`@anthropic-ai/claude-agent-sdk`
  - Python：`claude-agent-sdk`

## 项目结构

```text
claude-agent-sdk-skill/
├── .claude/
│   └── skills/
│       ├── agent-sdk-ts/
│       │   ├── SKILL.md
│       │   └── AGENT_SDK_DOCS.md
│       └── agent-sdk-py/
│           ├── SKILL.md
│           └── AGENTS_SDK_DOCS.md
└── README.md
```

## 贡献

欢迎贡献！请随时提交问题或拉取请求以改进这些技能或更新文档。

## 许可证

本项目按原样提供，用于教育和开发目的。

## 资源

- [Claude Code 文档](https://github.com/anthropics/claude-code)
- [Claude Agent SDK 文档](https://docs.anthropic.com/)
- [Anthropic API 参考](https://docs.anthropic.com/en/api/getting-started)
