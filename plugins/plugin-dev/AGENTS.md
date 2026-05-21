# plugin-dev Agent Adapter

This plugin is part of `claude-plugins-official`, but it can also be used by other AI coding tools as a file-based capability package.

## Generic use

1. Read this file first when starting from `plugins/plugin-dev`.
2. Read `README.md` for plugin-specific setup and limits.
3. Read `.claude-plugin/plugin.json` for metadata, commands, and Claude adapter details.
4. Load `skills/`, `commands/`, `agents/`, and `.mcp.json` only as needed for the requested workflow.
5. If your host does not support Claude slash commands, treat command names as workflow IDs and execute the corresponding instructions manually.
6. If your host does not support MCP, ask the user for equivalent files, credentials, links, or exports before continuing.

## Safety

Review any scripts, hooks, MCP servers, install commands, and external network access before executing them. Do not authenticate services, install dependencies, or run plugin-provided commands without explicit user approval.

## Upstream compatibility

Keep the Claude plugin structure intact. Add generic-agent guidance in `AGENTS.md` rather than renaming `.claude-plugin/`, `.mcp.json`, `skills/`, `commands/`, or `agents/`.