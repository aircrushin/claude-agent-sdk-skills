# Claude Agent SDK 技能

中文 | [English](./README.md)

为 Claude Agent SDK（TypeScript 和 Python）提供专业辅助的自定义 Claude Code 技能。

## 概述

本项目为 Claude Code 提供专门的技能，帮助您深入了解 Claude Agent SDK 的专业知识。这些技能帮助您构建 AI 驱动的应用程序，包含正确的 API 使用、最佳实践和全面的代码示例。

## 快速开始

只需 3 个简单步骤即可开始使用：

1. **安装技能：**
   ```bash
   # 用于特定项目
   cp -r .claude/skills /path/to/your-project/.codex/skills

   # 或全局安装用于所有项目
   mkdir -p ~/.codex/skills
   cp -r .claude/skills/* ~/.codex/skills/
   ```

2. **重启 Claude Code** 以加载新技能

3. **开始使用技能：**
   ```
   @agent-sdk-ts 如何创建带有自定义工具的代理？
   @agent-sdk-py 解释一下 query() 函数
   ```

就是这么简单！这些技能将基于官方 Agent SDK 文档为您提供专业指导。

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

### 选项 1：仓库级安装（推荐用于团队项目）

将技能放在您的仓库中，使所有团队成员都能使用：

```bash
# 将技能复制到您仓库的 .codex 目录
cp -r .claude/skills /path/to/your-project/.codex/skills
```

**仓库的技能作用域：**
- **当前目录**：`$CWD/.codex/skills` - 用于特定文件夹/模块的技能
- **父目录**：`$CWD/../.codex/skills` - 用于嵌套文件夹的共享技能
- **仓库根目录**：`$REPO_ROOT/.codex/skills` - 用于整个仓库的技能

### 选项 2：用户级安装（个人使用）

全局安装技能以在所有项目中使用：

```bash
# 如果用户技能目录不存在则创建
mkdir -p ~/.codex/skills

# 将技能复制到用户目录
cp -r .claude/skills/* ~/.codex/skills/
```

**默认位置：**
- macOS/Linux：`~/.codex/skills`
- Windows：`%USERPROFILE%\.codex\skills`

### 选项 3：系统级安装（整台机器）

为机器上的所有用户安装技能：

```bash
# 需要管理员权限
sudo cp -r .claude/skills/* /etc/codex/skills/
```

### 前置要求

确保已安装 Claude Code：
```bash
npm install -g @anthropic-ai/claude-code
```

安装技能后，**重启 Claude Code** 以加载新技能。

## 使用方法

### 技能如何工作

Claude Code 使用**渐进式披露**来高效管理技能：
1. 启动时，Claude Code 加载所有可用技能的名称和描述
2. 技能可以在需要时被调用（不会一次性全部加载到内存）
3. 只有被调用的技能才会完整加载到上下文中

### 调用技能

有两种方式使用这些技能：

#### 1. 显式调用

您可以直接在需要时调用技能：

**使用斜杠命令：**
```
/skills
```
这将打开技能选择器，您可以选择 `agent-sdk-ts` 或 `agent-sdk-py`。

**使用 @ 提及：**
在提示词中输入 `@agent-sdk-ts` 或 `@agent-sdk-py` 来调用特定技能：
```
@agent-sdk-ts 如何创建自定义 MCP 工具？

@agent-sdk-py 解释一下 query() 函数的参数
```

#### 2. 隐式调用

当您的问题匹配技能的专业领域时，Claude Code 会自动调用这些技能。您无需显式调用 - 直接自然地提出问题即可：

```
如何在 Python SDK 中使用 query() 函数？
使用 TypeScript 创建自定义 MCP 工具
设置权限 hook 以阻止某些操作
使用 SDK 处理流式输入
```

### 常见用例

当您询问以下内容时，这些技能会被自动调用：

**API 使用：**
- SDK 函数：`query()`、`tool()`、`createSdkMcpServer()`
- 配置选项和参数
- 消息类型和内容块
- 使用 JSON schema 的结构化输出

**代理开发：**
- 代理定义和模式
- 子代理创建和管理
- 会话管理和恢复
- 流式输入/输出处理

**MCP 集成：**
- MCP 服务器配置（stdio、SSE、HTTP、SDK）
- 自定义工具开发
- 工具输入/输出类型
- 服务器设置和部署

**高级功能：**
- Hook 事件和回调模式
- 权限模式和授权
- 文件检查点和回滚
- 沙盒配置
- 错误处理模式

### 示例工作流程

**设置新代理：**
```
@agent-sdk-ts 帮我创建一个使用自定义工具的代理
```

**调试 SDK 问题：**
```
@agent-sdk-py 启动 MCP 服务器时遇到 ProcessError
```

**学习最佳实践：**
```
展示如何在代理中正确处理权限
```

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

### 技能目录结构

每个技能遵循 [agent skills specification](https://agentskills.io/specification)，具有以下结构：

```text
agent-sdk-ts/
├── SKILL.md              # 必需：指令 + 元数据
├── AGENT_SDK_DOCS.md     # 可选：参考文档
├── scripts/              # 可选：可执行代码
├── references/           # 可选：附加文档
└── assets/              # 可选：模板、资源
```

**文件说明：**
- **SKILL.md**：包含技能的名称、描述和 Claude 遵循的指令
- **AGENT_SDK_DOCS.md**：全面的 SDK 文档供参考
- **scripts/**：可选的辅助脚本（当前这些技能中未使用）
- **references/**：额外的文档或示例
- **assets/**：模板、配置文件或其他资源

### 当前项目结构

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
├── README.md             # 英文文档
└── README_CN.md          # 本文件（中文文档）
```

## 故障排除

### 技能未显示

**问题：** 安装后技能未显示

**解决方案：**

1. 确保在安装技能后已重启 Claude Code
2. 检查技能是否在正确的目录中：

   ```bash
   # 验证用户级安装
   ls -la ~/.codex/skills/

   # 验证仓库级安装
   ls -la .codex/skills/
   ```

3. 运行 `/skills` 查看所有可用技能

### 技能未自动调用

**问题：** 询问 SDK 问题 时 Claude 不使用这些技能

**解决方案：**

1. 使用显式调用：`@agent-sdk-ts` 或 `@agent-sdk-py`
2. 确保您的问题明确与 Agent SDK 相关
3. 检查技能的 SKILL.md 文件是否存在且格式正确

### 权限错误

**问题：** 无法将技能复制到系统目录

**解决方案：**

```bash
# 改用用户目录（无需 sudo）
mkdir -p ~/.codex/skills
cp -r .claude/skills/* ~/.codex/skills/
```

### 技能过时

**问题：** 技能不包含最新的 SDK 功能

**解决方案：**

```bash
# 更新此仓库
git pull origin main

# 重新将技能复制到您的项目
cp -r .claude/skills/* /path/to/your-project/.codex/skills/
```

## 最佳实践技巧

1. **提出具体的问题** - 问题越具体，技能的帮助就越大
2. **对复杂任务使用显式调用** - `@agent-sdk-ts` 或 `@agent-sdk-py`
3. **提供上下文** - 分享相关的代码片段或错误消息
4. **请求示例** - 这些技能非常适合生成代码示例
5. **探索文档** - 查看 AGENT_SDK_DOCS.md 文件以获取全面参考

## 贡献

欢迎贡献！请随时提交问题或拉取请求以改进这些技能或更新文档。

## 许可证

本项目按原样提供，用于教育和开发目的。

## 资源

- [Claude Code 文档](https://github.com/anthropics/claude-code)
- [Claude Agent SDK 文档](https://docs.anthropic.com/)
- [Anthropic API 参考](https://docs.anthropic.com/en/api/getting-started)
