# Claude Agent SDK Skills

[中文文档](./README_CN.md) | English

Custom Claude Code skills for expert assistance with the Claude Agent SDK (TypeScript and Python).

## Overview

This project provides specialized skills for Claude Code that deliver expert knowledge about the Claude Agent SDK. These skills help you build AI-powered applications with proper API usage, best practices, and comprehensive code examples.

## Available Skills

### agent-sdk-ts

TypeScript Agent SDK expert providing:

- Core SDK functions: `query()`, `tool()`, `createSdkMcpServer()`
- Configuration options and use cases
- Agent definitions and subagent patterns
- Tool input/output types for all built-in tools
- MCP server configurations (stdio, SSE, HTTP, SDK)
- Hook events and callback patterns
- Permission modes and custom authorization
- File checkpointing and rewind functionality
- Session management and resumption
- Structured outputs with JSON schemas
- Sandbox configuration and security

### agent-sdk-py

Python Agent SDK expert providing:

- Core SDK functions: `query()`, `ClaudeSDKClient`, `tool()`, `create_sdk_mcp_server()`
- Choosing between `query()` vs `ClaudeSDKClient` for different use cases
- Configuration options with `ClaudeAgentOptions`
- Message types: `UserMessage`, `AssistantMessage`, `SystemMessage`, `ResultMessage`
- Content blocks: `TextBlock`, `ThinkingBlock`, `ToolUseBlock`, `ToolResultBlock`
- Agent definitions and subagent patterns
- MCP server configurations
- Hook events and callback patterns
- Custom permission handling with `can_use_tool` callbacks
- Session management and conversation continuity
- Custom tools with `@tool` decorator
- Error handling: `CLINotFoundError`, `ProcessError`, `CLIJSONDecodeError`

## Installation

1. Copy the `.claude/skills/` directory to your project
2. Ensure Claude Code is installed: `npm install -g @anthropic-ai/claude-code`
3. The skills will be automatically available when you run Claude Code

## Usage

These skills are automatically invoked by Claude Code when you ask questions about:

- SDK API usage and patterns
- Agent configuration and setup
- MCP server integration
- Hooks and permissions
- File checkpointing
- Tool development
- Error handling
- Best practices

Example prompts:

- "How do I use the query() function in the Python SDK?"
- "Create a custom MCP tool with TypeScript"
- "Set up a permission hook to block certain operations"
- "Handle streaming input with the SDK"

## Documentation References

Each skill includes comprehensive documentation references:

- **TypeScript**: See `.claude/skills/agent-sdk-ts/AGENT_SDK_DOCS.md`
- **Python**: See `.claude/skills/agent-sdk-py/AGENTS_SDK_DOCS.md`

## Requirements

- Claude Code CLI installed
- Node.js/npm (for TypeScript SDK)
- Python 3.8+ (for Python SDK)
- Appropriate SDK package installed:
  - TypeScript: `@anthropic-ai/claude-agent-sdk`
  - Python: `claude-agent-sdk`

## Project Structure

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

## Contributing

Contributions are welcome! Please feel free to submit issues or pull requests to improve these skills or update documentation.

## License

This project is provided as-is for educational and development purposes.

## Resources

- [Claude Code Documentation](https://github.com/anthropics/claude-code)
- [Claude Agent SDK Documentation](https://docs.anthropic.com/)
- [Anthropic API Reference](https://docs.anthropic.com/en/api/getting-started)
