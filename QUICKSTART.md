# Quick Start

This repository can be used in two modes:

- **Claude-native mode:** install plugins through Claude Code's official plugin marketplace format.
- **Generic AI tool mode:** give the repo URL to Codex, Cursor, Windsurf, Gemini CLI, OpenCode, or another agent and have it read `AGENTS.md`.

## Use with any AI tool

1. Give the tool this repository URL.
2. Tell it: `Read AGENTS.md first. Use .claude-plugin/marketplace.json as the plugin registry.`
3. Ask it to find the plugin you want by name, category, description, author, or homepage.
4. The tool should resolve the plugin source from the registry:
   - local plugin: `./plugins/<name>` or `./external_plugins/<name>`
   - external git repository: `source.url`
   - external subdirectory: `source.url` plus `source.path`
5. The tool should then read the plugin's `README.md`, `.claude-plugin/plugin.json`, `skills/`, `commands/`, `agents/`, and `.mcp.json` as needed.
6. If the host does not support Claude slash commands, treat commands as workflow names.
7. If the host does not support MCP, provide the needed documents, exports, credentials, or links directly.

For more detail, see [docs/AGENT_INSTALL.md](docs/AGENT_INSTALL.md).

## Install in Claude Code

Plugins can be installed directly from this marketplace via Claude Code's plugin system.

```text
/plugin install {plugin-name}@claude-plugins-official
```

You can also browse plugins in Claude Code:

```text
/plugin > Discover
```

## What this repository contains

- `plugins/`: internal plugins developed and maintained in the official marketplace.
- `external_plugins/`: third-party plugins from partners and the community.
- `.claude-plugin/marketplace.json`: the registry that lists plugin names, descriptions, categories, authors, sources, and homepages.
- `docs/adapters/`: notes for Claude Code, Codex, and generic AI tools.

## Safety check before installing

Before installing or using a plugin, read its source and review any `.mcp.json`, scripts, hooks, external commands, and authentication requirements. Do not authenticate services, install dependencies, or run plugin-provided commands unless you trust the source and understand what the plugin can access.