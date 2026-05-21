# Claude Adapter

This repository preserves the upstream Claude Code marketplace layout.

## Claude Code install

Install any listed plugin using the marketplace name:

```text
/plugin install {plugin-name}@claude-plugins-official
```

Or browse plugins inside Claude Code:

```text
/plugin > Discover
```

## Marketplace format

Claude Code reads `.claude-plugin/marketplace.json` as the registry. Keep this file in the upstream schema so this fork remains compatible with Claude Code and easy to merge with upstream.

## Why this adapter exists

This fork adds generic AI-tool docs without removing Claude-native support. `.claude-plugin/` remains the Claude adapter. `AGENTS.md` and `docs/adapters/` are the cross-agent adapter layer.