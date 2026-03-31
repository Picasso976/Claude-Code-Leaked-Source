# Claude Code — Leaked Source (2026-03-31)

**Archived snapshot of Anthropic's Claude Code CLI source code, leaked via an exposed source map in the official npm package.**

On March 31, 2026, the complete TypeScript source for Anthropic's official Claude Code CLI was publicly exposed through a `.map` file included in the published `@anthropic-ai/claude-code` npm package (version ~2.1.88). The source map referenced the full, unobfuscated source tree, which was then extracted and made available as a downloadable ZIP from Anthropic's public R2 storage bucket.

The leak was first reported by Chaofan Shou (@Fried_rice) on X:

> "Claude code source code has been leaked via a map file in their npm registry!"  
> — [@Fried_rice](https://x.com/Fried_rice), March 31, 2026

This repository serves as a clean, documented archive of the leaked `src/` directory for research, educational, and historical purposes.

## What is Claude Code?

Claude Code is Anthropic's official terminal-based AI coding agent. It lets you interact directly with Claude (via the Anthropic API) to perform real software engineering work inside your terminal or IDE:

- Edit files and run shell commands
- Search codebases with ripgrep
- Manage Git workflows
- Spawn sub-agents and coordinate multi-agent teams
- Handle Jupyter notebooks, web search/fetch, and more

**Key technical details (verified from the leaked source):**
- **Language**: TypeScript (strict mode)
- **Runtime**: Bun
- **Terminal UI**: React + Ink
- **Scale**: ~1,900+ files / ~500,000+ lines of code
- **CLI framework**: Commander.js
- **Schema validation**: Zod
- **Code search**: ripgrep (via GrepTool)
- **Additional protocols**: MCP (Model Context Protocol), LSP (Language Server Protocol)

## Core Architecture Highlights

### 1. Tool System (`src/tools/`)
~40 self-contained tools with strict input schemas, permission models, and execution logic.

Notable tools include:
- `BashTool` — Shell command execution
- `FileReadTool` / `FileWriteTool` / `FileEditTool` — File operations (including PDFs, images, notebooks)
- `GlobTool` / `GrepTool` — File pattern and content search
- `WebFetchTool` / `WebSearchTool` — Web access
- `AgentTool` — Sub-agent spawning
- `SkillTool` — Reusable workflow execution
- `MCPTool` / `LSPTool` — Protocol integrations
- `TaskCreateTool` / `TaskUpdateTool`, `CronCreateTool`, `RemoteTriggerTool`, etc.

### 2. Command System (`src/commands/`)
Slash-command interface (`/command`).

Examples:
- `/commit`, `/review`, `/diff`
- `/doctor`, `/memory`, `/skills`, `/tasks`
- `/compact`, `/context`, `/cost`
- `/mcp`, `/vim`, `/resume`, `/share`

### 3. Other Major Systems
- **QueryEngine.ts** — Core LLM streaming, tool-calling loop, retry logic, token tracking
- **Permission System** — Granular approval flows (default/plan/auto/bypass modes)
- **Bridge System** (`src/bridge/`) — Bidirectional integration with VS Code and JetBrains IDEs
- **Coordinator / Multi-Agent** — Team creation, memory sync, inter-agent messaging
- **Skills & Plugins** — Extensible workflow and plugin architecture
- **Feature Flags** — Bun `bun:bundle` flags (e.g., `VOICE_MODE`, `KAIROS`, `PROACTIVE`, `AGENT_TRIGGERS`)

**Notable unreleased / internal features visible in source:**
- Kairos (proactive/daemon mode with cron, webhooks, push notifications)
- Buddy (tamagotchi-style companion sprite system)
- Advanced memory extraction and team memory synchronization
- Voice input, remote sessions, desktop/mobile handoff

## Directory Structure (Top-Level)
