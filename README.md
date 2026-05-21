# Claude Code Plugins Directory

A curated directory of high-quality plugins for Claude Code.

This fork also adds a generic AI-tool adapter layer so Codex, Cursor, Windsurf, Gemini CLI, OpenCode, and other agents can discover and add these plugins and skills from the same repository link.

If you are an AI agent or coding tool, start with [AGENTS.md](AGENTS.md). For host-specific notes, see [docs/AGENT_INSTALL.md](docs/AGENT_INSTALL.md) and [docs/adapters/](docs/adapters/). Each local plugin under `plugins/` also has its own `AGENTS.md` entrypoint.

> **Important:** Make sure you trust a plugin before installing, updating, or using it. Anthropic does not control what MCP servers, files, or other software are included in plugins and cannot verify that they will work as intended or that they will not change. See each plugin's homepage for more information.

## Structure

- **`/plugins`** - Internal plugins developed and maintained by Anthropic; this fork adds per-plugin `AGENTS.md` files for generic AI tools.
- **`/external_plugins`** - Third-party plugins from partners and the community.
- **`/.claude-plugin/marketplace.json`** - Claude Code marketplace registry; generic tools can parse this as a plugin index.
- **`/docs/adapters`** - Host-specific guidance for Claude Code, Codex, and generic AI tools.

## Installation

Plugins can be installed directly from this marketplace via Claude Code's plugin system.

To install, run:

```text
/plugin install {plugin-name}@claude-plugins-official
```

Or browse for the plugin in:

```text
/plugin > Discover
```

## Generic AI Tool Usage

Tools that do not support Claude Code plugins directly can still use this repository as a marketplace and capability library.

1. Read `AGENTS.md`.
2. Parse `.claude-plugin/marketplace.json` to find a plugin by name, category, description, author, or homepage.
3. Resolve the plugin source. Local official plugins live under `plugins/<plugin-name>`.
4. Read the plugin's `AGENTS.md`, `README.md`, `.claude-plugin/plugin.json`, `skills/`, `commands/`, `agents/`, and `.mcp.json` as needed.
5. Convert slash commands and skills into the host tool's native command, skill, or instruction format.
6. Map MCP configuration into the host's connector system, or ask the user for equivalent files, exports, credentials, or links.

## Contributing

### Internal Plugins

Internal plugins are developed by Anthropic team members. See `/plugins/example-plugin` for a reference implementation.

### External Plugins

Third-party partners can submit plugins for inclusion in the marketplace. External plugins must meet quality and security standards for approval. To submit a new plugin, use the [plugin directory submission form](https://clau.de/plugin-directory-submission).

## Plugin Structure

Each plugin follows a standard structure:

```text
plugin-name/
├── AGENTS.md            # Generic AI-tool entrypoint added by this fork
├── .claude-plugin/
│   └── plugin.json      # Plugin metadata (required)
├── .mcp.json            # MCP server configuration (optional)
├── commands/            # Slash commands (optional)
├── agents/              # Agent definitions (optional)
├── skills/              # Skill definitions (optional)
└── README.md            # Documentation
```

## Upstream Compatibility

This fork keeps the upstream marketplace and plugin formats intact.

- Keep `.claude-plugin/marketplace.json` in the Claude marketplace schema.
- Keep plugin folders, `.claude-plugin/`, `.mcp.json`, `commands/`, `agents/`, and `skills/` in their upstream meanings.
- Put cross-agent guidance in `AGENTS.md` and `docs/` rather than rewriting each plugin's implementation.

## License

Please see each linked plugin for the relevant LICENSE file.

## Documentation

For more information on developing Claude Code plugins, see the [official documentation](https://code.claude.com/docs/en/plugins).
