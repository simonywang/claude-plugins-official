# Generic Agent Adapter

Use this guide for any AI tool that can read repository files but does not natively install Claude Code plugins.

## Agent procedure

1. Read root `AGENTS.md`.
2. Read `.claude-plugin/marketplace.json` as a registry.
3. Ask the user which plugin or capability they want, or infer it from the request.
4. Resolve the plugin source from the registry.
5. Read the plugin `README.md` and `.claude-plugin/plugin.json` if present.
6. Load relevant `skills/`, `commands/`, `agents/`, and `.mcp.json` files.
7. Treat slash commands as workflow names if the host does not support them.
8. Ask for missing credentials, documents, or data before running workflows.

## What not to do

- Do not claim Claude plugin installation succeeded unless the host actually supports it.
- Do not execute plugin-provided scripts, MCP servers, or external commands without user approval and source review.
- Do not ignore pinned SHAs or refs in marketplace entries.
- Do not authenticate external services until the user confirms the target plugin and data access.

## Connector fallback

If MCP is unavailable, ask the user for the data normally provided by the connector, such as issue exports, database credentials, design links, app tokens, project files, or service-specific reports.