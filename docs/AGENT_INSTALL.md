# Generic Agent Install Guide

This guide explains how non-Claude AI tools can add and use the plugins and skills listed in this marketplace while preserving Claude compatibility.

## Recommended prompt

Send the repository URL to your AI tool and say:

```text
Read AGENTS.md first. Use .claude-plugin/marketplace.json as a plugin registry. Find the plugin I ask for, resolve its source, then load its README.md, plugin.json, skills, commands, agents, and MCP config as needed.
```

## Host capability levels

| Host capability | How to use this repo |
|---|---|
| Claude Code plugin support | Install through the marketplace name `claude-plugins-official`; see `docs/adapters/claude.md`. |
| Coding agent with repo access | Read `AGENTS.md`, then parse `.claude-plugin/marketplace.json` and resolve plugin sources. |
| Chat agent with file upload only | Upload `AGENTS.md`, `.claude-plugin/marketplace.json`, and the selected plugin files. |
| Agent with MCP support | Map each plugin's `.mcp.json` to the host's MCP connector mechanism. |
| Agent without MCP support | Ask the user for the data normally provided by the connector. |

## Registry source mapping

| Marketplace source shape | Generic-agent handling |
|---|---|
| `"source": "./plugins/name"` | Read the local plugin directory in this repo. |
| `"source": "./external_plugins/name"` | Read the local external plugin directory in this repo. |
| `"source": {"source": "git-subdir", "url": "...", "path": "...", "ref": "...", "sha": "..."}` | Fetch the repo, prefer the pinned `sha`, then read the subdirectory at `path`. |
| `"source": {"source": "url", "url": "...", "sha": "..."}` | Fetch or clone the referenced repository, prefer the pinned `sha`. |

## Plugin file mapping

| File or folder | Meaning outside Claude |
|---|---|
| `.claude-plugin/marketplace.json` | Marketplace registry. Keep in upstream format. |
| `<plugin>/.claude-plugin/plugin.json` | Plugin metadata and Claude adapter manifest. |
| `<plugin>/skills/**/SKILL.md` | Reusable skill instructions. Convert or execute as host-native skills. |
| `<plugin>/commands/` | Slash-command workflows. Treat command names as workflow IDs. |
| `<plugin>/agents/` | Agent definitions or background workflow designs. |
| `<plugin>/.mcp.json` | Connector requirements. Map to host MCP or ask user for equivalent data. |
| `<plugin>/README.md` | Setup, usage, and limits. |

## Keeping upstream mergeable

Do not rename marketplace fields, plugin folders, `.claude-plugin/`, `.mcp.json`, `skills/`, `commands/`, or `agents/` just to make them generic. Add adapter guidance in `AGENTS.md` and `docs/adapters/`.