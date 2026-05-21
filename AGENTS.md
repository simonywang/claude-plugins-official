# AGENTS.md

This repository is a generic AI-agent usable fork of Anthropic's `claude-plugins-official` marketplace.

The goal is twofold:

- Let Claude Code, Codex, Cursor, Windsurf, Gemini CLI, OpenCode, and other AI tools discover and add the plugins and skills listed here.
- Preserve the upstream Claude marketplace structure so this fork can continue to absorb upstream updates with minimal conflict.

## Startup rule for AI agents

When an AI agent receives this repository link, read this file first, then route through the relevant adapter guide:

- Claude Code: `docs/adapters/claude.md`
- OpenAI Codex: `docs/adapters/codex.md`
- Other coding agents or chat agents: `docs/adapters/generic-agent.md`

Do not assume the host supports Claude plugin installation. If it does not, treat `.claude-plugin/marketplace.json` as a plugin registry and each plugin as a capability package.

## How to use this marketplace generically

1. Read `.claude-plugin/marketplace.json`.
2. Locate the plugin by `name`, `category`, `description`, `author`, or `homepage`.
3. Resolve the plugin source:
   - If `source` is a string like `./plugins/name`, read that local directory.
   - If `source.source` is `git-subdir`, fetch the repository at `source.url`, then read `source.path` at the pinned `ref` or `sha`.
   - If `source.source` is `url`, fetch or clone `source.url` at the pinned `sha` when available.
4. In the resolved plugin directory, read `.claude-plugin/plugin.json` if present.
5. Load available capability files:
   - `skills/**/SKILL.md` for reusable skills.
   - `commands/` for slash-command workflows.
   - `agents/` for subagents or background workflows.
   - `.mcp.json` for connector requirements.
   - `README.md` for user-facing setup and limits.
6. If the host cannot install Claude plugins directly, convert plugin commands and skills into the host's native format or execute them as file-based instructions.
7. If MCP is unavailable, ask the user for the documents, credentials, exports, or links that the connector would normally provide.

## Trust and security

Plugins may contain MCP servers, commands, scripts, or references to external repositories. Before installing or executing anything:

- Read the plugin source and homepage.
- Check the pinned `sha` or `ref` when present.
- Review `.mcp.json`, scripts, install commands, hooks, and external network requirements.
- Do not run destructive actions or authenticate external services without explicit user approval.

## Upstream compatibility rules

This fork should stay easy to merge with Anthropic's upstream `claude-plugins-official` repository.

- Keep `.claude-plugin/marketplace.json` in the upstream Claude marketplace format.
- Do not rename plugin folders, marketplace fields, `.claude-plugin/`, `.mcp.json`, `commands/`, `agents/`, or `skills/` just to make them generic.
- Put cross-agent guidance in `AGENTS.md` and `docs/` instead of rewriting every marketplace entry.
- Treat Claude Code as one adapter, not the only supported runtime.

## Minimum context loading

Start with the minimum useful files:

1. `AGENTS.md`
2. `README.md`
3. `.claude-plugin/marketplace.json`
4. The selected plugin source directory or external source repo/path
5. That plugin's `README.md`, `.claude-plugin/plugin.json`, `skills/`, `commands/`, `agents/`, and `.mcp.json` as needed

Load more only when the selected plugin or task requires it.