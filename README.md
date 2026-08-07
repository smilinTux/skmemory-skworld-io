# SKMemory

🧠 **Sovereign knowledge management and agent memory systems**

> *"Your agent never forgets"*

SKMemory provides persistent, sync-enabled memory for AI agents across sessions, platforms, and devices.

🌐 **Website**: https://skmemory.skworld.io  
📖 **Documentation**: [Architecture](https://github.com/smilinTux/skmemory)  
🐧 **Organization**: [smilinTux](https://github.com/smilinTux)  
💻 **Code Repository**: [github.com/smilinTux/skmemory](https://github.com/smilinTux/skmemory)

## What is SKMemory?

SKMemory is a universal memory system for AI agents that provides:

- **Three-Tier Architecture**: Short-term (today), medium-term (yesterday), long-term (historical)
- **Lazy Loading**: Token-efficient context management
- **Cross-Device Sync**: Syncthing integration for seamless multi-device operation
- **Multi-Agent Support**: Multiple agents (Lumina, Jarvis, etc.) with isolated memories
- **Deep Search**: Full-text search across all memory tiers
- **OpenClaw Plugin**: Native integration with OpenClaw

## Key Features

| Feature | Description |
|---------|-------------|
| **Three-Tier Memory** | Today (full), Yesterday (summaries), Historical (searchable) |
| **Lazy Loading** | Only relevant memories loaded into context (saves tokens) |
| **Multi-Agent** | Create agents from template: `cp -a lumina-template jarvis` |
| **Sync-Enabled** | All memories in `~/.skcapstone/` sync via Syncthing |
| **Deep Search** | `skmemory search-deep "project gentis"` |
| **UUID Naming** | Conflict-free file naming across devices |

## Quick Start

### Prerequisites

- Python 3.10+
- Syncthing (for cross-device sync)
- Git

### Installation

```bash
# Method 1: From PyPI (when published)
pip install skmemory

# Method 2: From Source (recommended)
git clone https://github.com/smilinTux/skmemory.git ~/clawd/skcapstone-repos/skmemory
cd ~/clawd/skcapstone-repos/skmemory
pip install -e .
```

### Setup

```bash
# Create agent from template
cp -a ~/.skcapstone/agents/lumina-template ~/.skcapstone/agents/lumina

# Edit configuration
vim ~/.skcapstone/agents/lumina/config/skmemory.yaml
# Change: agent.name: lumina

# Import seeds
skmemory import-seeds ~/.skcapstone/agents/lumina/seeds/
```

### Register with AI Platforms

```bash
# Auto-register with all platforms
python -m skmemory.register_mcp

# Or specific platform
python -m skmemory.register_mcp --env opencode
python -m skmemory.register_mcp --env claude
python -m skmemory.register_mcp --env openclaw
```

## Architecture

```
┌─────────────────────────────────────────────┐
│           SKMemory Architecture               │
├─────────────────────────────────────────────┤
│                                             │
│  Three-Tier Memory:                         │
│  ┌──────────┬──────────┬────────────────┐   │
│  │  Short   │  Medium  │     Long       │   │
│  │  (Today) │(Yesterday)│  (Historical) │   │
│  └──────────┴──────────┴────────────────┘   │
│                                             │
│  Storage:                                   │
│  ├── Flat Files (source of truth)           │
│  ├── SQLite (local cache)                   │
│  └── SKVector/SKGraph (optional backends)   │
│                                             │
│  Sync: Syncthing                            │
│  └── ~/.skcapstone/agents/{name}/           │
│                                             │
└─────────────────────────────────────────────┘
```

## Core Commands

```bash
# Show token-optimized context
skmemory show-context
skmemory show-context --agent lumina

# Deep search all memories
skmemory search-deep "project architecture"
skmemory search-deep "client meeting" --limit 20

# Promote memory tier
skmemory promote abc123 mid-term
skmemory promote def456 long-term

# Import Cloud 9 seeds
skmemory import-seeds ~/.skcapstone/agents/lumina/seeds/

# Check memory health
skmemory health
```

## Cross-Platform Integration

### OpenCode

Config file: `~/.opencode/mcp.json`

```json
{
  "mcpServers": {
    "skmemory": {
      "command": "python",
      "args": ["-m", "skmemory.mcp_server"],
      "env": {
        "SKMEMORY_AGENT": "lumina"
      }
    }
  }
}
```

### Claude Code

Config file: `~/.config/claude/claude_desktop_config.json`

```json
{
  "mcpServers": {
    "skmemory": {
      "command": "python",
      "args": ["-m", "skmemory.mcp_server"],
      "env": {
        "SKMEMORY_AGENT": "lumina"
      }
    }
  }
}
```

### OpenClaw

Plugin automatically loaded from:
- `~/clawd/skcapstone-repos/skmemory/openclaw-plugin/`

## Multi-Agent Setup

```bash
# Create Jarvis agent
cp -a ~/.skcapstone/agents/lumina-template ~/.skcapstone/agents/jarvis
vim ~/.skcapstone/agents/jarvis/config/skmemory.yaml
# Change: agent.name: jarvis

# Switch between agents
export SKMEMORY_AGENT=lumina
skmemory show-context

export SKMEMORY_AGENT=jarvis
skmemory show-context
```

## New Machine Setup

```bash
# 1. Install prerequisites
sudo apt-get install python3 python3-pip syncthing

# 2. Clone repositories
git clone https://github.com/smilinTux/skmemory.git ~/clawd/skcapstone-repos/skmemory
git clone https://github.com/smilinTux/skcapstone.git ~/clawd/skcapstone-repos/skcapstone

# 3. Install packages
pip install -e ~/clawd/skcapstone-repos/skmemory
pip install -e ~/clawd/skcapstone-repos/skcapstone

# 4. Setup Syncthing
# Add ~/.skcapstone/ to Syncthing

# 5. Register MCP servers
python -m skmemory.register_mcp
```

## Ecosystem

- 🧠 **SKMemory** - Memory persistence (this repo)
- 🛡️ **SKCapstone** - Agent framework
- 🛡️ **SKSecurity** - Security and audit
- ☁️ **Cloud 9** - Trust and skills
- 🔐 **CapAuth** - Sovereign identity

## Community

- 🌐 **Website**: [skmemory.skworld.io](https://skmemory.skworld.io)
- 🐧 **Organization**: [smilinTux](https://github.com/smilinTux)
- 📧 **Contact**: hello@skmemory.skworld.io
- 🔧 **Issues**: [GitHub Issues](https://github.com/smilinTux/skmemory/issues)
- 💬 **Discussions**: [GitHub Discussions](https://github.com/smilinTux/skmemory/discussions)

## License

GPL-3.0 — Free forever, open source, community-driven.

---

**A smilinTux Product** • Remember Everything, Forget Nothing • #staycuriousANDkeepsmilin
