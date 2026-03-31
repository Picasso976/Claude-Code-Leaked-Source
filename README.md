# 📂 Claude Code — Source Archive (Leaked 2026-03-31)

![License: Research Only](https://img.shields.io/badge/License-Research_Only-orange)
![Runtime: Bun](https://img.shields.io/badge/Runtime-Bun-black?logo=bun)
![Framework: React Ink](https://img.shields.io/badge/UI-React_Ink-blue?logo=react)

An archived snapshot of the official **Anthropic Claude Code CLI** source code. This metadata and source tree were exposed via an inadvertent `.map` file inclusion in the `@anthropic-ai/claude-code` npm package (v2.1.88) on March 31, 2026.

> [!IMPORTANT]  
> This repository is for **research, educational, and historical purposes only**. It contains client-side TypeScript source extracted from public source maps. It does **not** contain model weights, system prompts, or private API keys.

---

## 🔍 Overview
**Claude Code** is Anthropic's flagship terminal-based AI engineering agent. Unlike standard chat interfaces, it operates as a "Loop-in-the-Shell" agent capable of autonomous file manipulation, command execution, and multi-agent coordination.

### Technical Stack
* **Runtime:** Bun (utilizing `bun:bundle` and native performance features)
* **UI:** React + Ink (Terminal-based UI)
* **CLI Logic:** Commander.js
* **Validation:** Zod v4
* **Protocols:** MCP (Model Context Protocol) & LSP (Language Server Protocol)
* **Scale:** ~1,900+ files | ~500,000+ lines of code

---

## 🛠 Core Architecture

### 1. The Tooling System (`src/tools/`)
The agent utilizes over 40 specialized tools with strict schema validation and permission gates.
* **System Tools:** `BashTool`, `FileEditTool`, `GrepTool` (ripgrep integration).
* **Web/Data:** `WebSearchTool`, `WebFetchTool`, `JupyterTool`.
* **Advanced:** `AgentTool` (sub-agent spawning), `MCPTool`, `SkillTool`.

### 2. Command Interface (`src/commands/`)
The CLI supports a rich "Slash Command" ecosystem:
* **Dev Workflow:** `/commit`, `/review`, `/diff`, `/pr`.
* **Agent State:** `/memory`, `/context`, `/compact`, `/history`.
* **Advanced Utilities:** `/mcp`, `/vim`, `/voice`, `/tasks`.

### 3. The Query Engine (`src/QueryEngine.ts`)
The "brain" of the CLI (~46k lines). It manages:
* The core LLM streaming and tool-calling loops.
* Token budget tracking and context window management.
* Granular permission approval flows (Default, Plan, Auto, Bypass).

---

## 📂 Directory Structure

```bash
src/
├── main.tsx           # Entrypoint & Ink Renderer
├── QueryEngine.ts     # Core LLM orchestration engine
├── Tool.ts            # Tool type definitions
├── tools/             # ~40 tool implementations (Bash, File, Web, etc.)
├── commands/          # ~50 slash command logic implementations
├── components/        # ~140 Ink UI components
├── coordinator/       # Multi-agent/Team orchestration
├── bridge/            # IDE Integration (VS Code, JetBrains)
├── memdir/            # Persistent agent memory
└── voice/             # Voice-to-command logic
```

**🚀 Unreleased & Internal Features**

*The leaked source reveals several "feature-flagged" modules and internal tools:
*Kairos: A proactive daemon mode supporting Crons, webhooks, and push notifications.
*Buddy: A tamagotchi-style companion sprite system for the terminal.
*Team Sync: Advanced memory synchronization for inter-agent messaging.
*Remote Sessions: Features for mobile-to-desktop handoff and remote agent triggers.

---

**⚖️ Disclaimer & Credits**

*Original Discovery: Reported by @Fried_rice (Chaofan Shou) on March 31, 2026.
*Intellectual Property: All code and logic remain the property of Anthropic PBC.
*This archive is provided "as-is" to assist the AI safety and developer communities in understanding modern autonomous agent architectures.

---

Archived on: March 31, 2026
Original leak discovery: @Fried_rice

>⭐If you're researching AI agent architectures, tool-use systems, or modern CLI agent design, this is an unprecedented look inside one of the most advanced closed-source coding agents available in 2026.

---
