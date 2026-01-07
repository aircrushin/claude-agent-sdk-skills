# Claude Agent SDK Skills

[中文文档](./README_CN.md) | English

Custom Claude Code skills for expert assistance with the Claude Agent SDK (TypeScript and Python).

## Overview

This project provides specialized skills for Claude Code that deliver expert knowledge about the Claude Agent SDK. These skills help you build AI-powered applications with proper API usage, best practices, and comprehensive code examples.

## Quick Start

Get started in 3 simple steps:

1. **Install the skills:**
   ```bash
   # For a specific project
   cp -r .claude/skills /path/to/your-project/.codex/skills

   # Or globally for all projects
   mkdir -p ~/.codex/skills
   cp -r .claude/skills/* ~/.codex/skills/
   ```

2. **Restart Claude Code** to pick up the new skills

3. **Start using the skills:**
   ```
   @agent-sdk-ts How do I create an agent with custom tools?
   @agent-sdk-py Explain the query() function
   ```

That's it! The skills will provide expert guidance based on the official Agent SDK documentation.

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

### Option 1: Repository-Level Installation (Recommended for Team Projects)

Place skills in your repository so they're available to all team members working on the project:

```bash
# Copy skills to your repository's .codex directory
cp -r .claude/skills /path/to/your-project/.codex/skills
```

**Skill scopes for repositories:**
- **Current directory**: `$CWD/.codex/skills` - Skills for a specific folder/module
- **Parent directory**: `$CWD/../.codex/skills` - Shared skills for nested folders
- **Repository root**: `$REPO_ROOT/.codex/skills` - Skills for the entire repo

### Option 2: User-Level Installation (Personal Use)

Install skills globally for use across all your projects:

```bash
# Create user skills directory if it doesn't exist
mkdir -p ~/.codex/skills

# Copy skills to user directory
cp -r .claude/skills/* ~/.codex/skills/
```

**Default locations:**
- macOS/Linux: `~/.codex/skills`
- Windows: `%USERPROFILE%\.codex\skills`

### Option 3: System-Level Installation (Machine-Wide)

Install skills for all users on a machine:

```bash
# Requires administrator privileges
sudo cp -r .claude/skills/* /etc/codex/skills/
```

### Prerequisites

Ensure Claude Code is installed:
```bash
npm install -g @anthropic-ai/claude-code
```

After installing skills, **restart Claude Code** to pick up the new skills.

## Usage

### How Skills Work

Claude Code uses **progressive disclosure** to manage skills efficiently:
1. At startup, Claude Code loads the name and description of all available skills
2. Skills can be invoked when needed (not all loaded into memory at once)
3. Only invoked skills are fully loaded into context

### Invoking Skills

There are two ways to use these skills:

#### 1. Explicit Invocation

You can directly invoke a skill when needed:

**Using slash commands:**
```
/skills
```
This opens the skill selector where you can choose `agent-sdk-ts` or `agent-sdk-py`.

**Using @ mentions:**
Type `@agent-sdk-ts` or `@agent-sdk-py` in your prompt to invoke the specific skill:
```
@agent-sdk-ts How do I create a custom MCP tool?

@agent-sdk-py Explain the query() function parameters
```

#### 2. Implicit Invocation

Claude Code will automatically invoke these skills when your questions match their expertise. You don't need to explicitly invoke them - just ask your question naturally:

```
How do I use the query() function in the Python SDK?
Create a custom MCP tool with TypeScript
Set up a permission hook to block certain operations
Handle streaming input with the SDK
```

### Common Use Cases

These skills are automatically invoked when you ask about:

**API Usage:**
- SDK functions: `query()`, `tool()`, `createSdkMcpServer()`
- Configuration options and parameters
- Message types and content blocks
- Structured outputs with JSON schemas

**Agent Development:**
- Agent definitions and patterns
- Subagent creation and management
- Session management and resumption
- Streaming input/output handling

**MCP Integration:**
- MCP server configurations (stdio, SSE, HTTP, SDK)
- Custom tool development
- Tool input/output types
- Server setup and deployment

**Advanced Features:**
- Hook events and callback patterns
- Permission modes and authorization
- File checkpointing and rewind
- Sandbox configuration
- Error handling patterns

### Example Workflows

**Setting up a new agent:**
```
@agent-sdk-ts Help me create an agent that uses a custom tool
```

**Debugging SDK issues:**
```
@agent-sdk-py I'm getting a ProcessError when starting my MCP server
```

**Learning best practices:**
```
Show me how to properly handle permissions in my agent
```

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

### Skill Directory Structure

Each skill follows the [agent skills specification](https://agentskills.io/specification) with this structure:

```text
agent-sdk-ts/
├── SKILL.md              # Required: Instructions + metadata
├── AGENT_SDK_DOCS.md     # Optional: Reference documentation
├── scripts/              # Optional: Executable code
├── references/           # Optional: Additional documentation
└── assets/              # Optional: Templates, resources
```

**File breakdown:**
- **SKILL.md**: Contains the skill's name, description, and instructions for Claude to follow
- **AGENT_SDK_DOCS.md**: Comprehensive SDK documentation for reference
- **scripts/**: Optional helper scripts (currently not used in these skills)
- **references/**: Additional documentation or examples
- **assets/**: Templates, configuration files, or other resources

### Current Project Structure

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
├── README.md             # This file
└── README_CN.md          # Chinese documentation
```

## Troubleshooting

### Skills Not Appearing

**Problem:** Skills don't show up after installation

**Solutions:**

1. Ensure you've restarted Claude Code after installing skills
2. Check that skills are in the correct directory:

   ```bash
   # Verify user-level installation
   ls -la ~/.codex/skills/

   # Verify repository-level installation
   ls -la .codex/skills/
   ```

3. Run `/skills` to see all available skills

### Skills Not Invoking Automatically

**Problem:** Claude doesn't use the skills when asking SDK questions

**Solutions:**

1. Use explicit invocation: `@agent-sdk-ts` or `@agent-sdk-py`
2. Make sure your question clearly relates to the Agent SDK
3. Check that the skill's SKILL.md file exists and is properly formatted

### Permission Errors

**Problem:** Can't copy skills to system directory

**Solution:**

```bash
# Use user directory instead (no sudo required)
mkdir -p ~/.codex/skills
cp -r .claude/skills/* ~/.codex/skills/
```

### Skills Outdated

**Problem:** Skills don't include latest SDK features

**Solution:**

```bash
# Update this repository
git pull origin main

# Re-copy skills to your project
cp -r .claude/skills/* /path/to/your-project/.codex/skills/
```

## Tips for Best Results

1. **Be specific in your questions** - The more specific your question, the better the skill can help
2. **Use explicit invocation for complex tasks** - `@agent-sdk-ts` or `@agent-sdk-py`
3. **Provide context** - Share relevant code snippets or error messages
4. **Ask for examples** - These skills are great at generating code examples
5. **Explore documentation** - Check the AGENT_SDK_DOCS.md files for comprehensive reference

## Contributing

Contributions are welcome! Please feel free to submit issues or pull requests to improve these skills or update documentation.

## License

This project is provided as-is for educational and development purposes.

## Resources

- [Claude Code Documentation](https://github.com/anthropics/claude-code)
- [Claude Agent SDK Documentation](https://docs.anthropic.com/)
- [Anthropic API Reference](https://docs.anthropic.com/en/api/getting-started)
