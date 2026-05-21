# Codex Adapter

Use this guide when OpenAI Codex receives this repository link.

## Startup

1. Read root `AGENTS.md` first.
2. Read `README.md` and `QUICKSTART.md` for repository orientation.
3. Parse `.claude-plugin/marketplace.json` as the plugin registry.
4. Select the requested plugin by name, category, author, homepage, or description.
5. Resolve the plugin source:
   - local string source: read the local directory.
   - `git-subdir`: fetch the remote repo and read the specified path at the pinned ref or SHA.
   - `url`: fetch the referenced repo at the pinned SHA when available.
6. Load only the files needed for the requested workflow: plugin `README.md`, `.claude-plugin/plugin.json`, `skills/`, `commands/`, `agents/`, and `.mcp.json`.

## Running a plugin workflow

Codex does not need Claude plugin installation to use the content. Treat this repo as a marketplace plus capability library.

- Slash commands are workflow IDs.
- `skills/` contain reusable skill instructions.
- `commands/` contain command-style workflows.
- `agents/` contain agent definitions or background workflow designs.
- `.mcp.json` describes connector requirements that may need to be mapped to Codex tools, app connectors, MCP servers, or user-provided files.

## Editing this fork

When asked to modify the repo, keep upstream compatibility in mind:

- Prefer adding generic-agent docs under `docs/` over changing every plugin entry.
- Avoid renaming `.claude-plugin/`, marketplace fields, plugin folders, `skills/`, `commands/`, or `agents/` unless the user explicitly accepts the upstream merge cost.
- Keep edits scoped and verify changed markdown/JSON files by reading them back.