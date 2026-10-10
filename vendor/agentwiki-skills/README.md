# agentwiki-skills

Claude Code plugin marketplace by **NextLevelBuilder** for the [AgentWiki](https://app.agentwiki.cc) knowledge platform.

Ships an `agentwiki` skill that teaches Claude (and any Claude-Skill-compatible agent) how to drive both:
- the **AgentWiki CLI** — `@aiagentwiki/cli` (binary `agentwiki`)
- the **AgentWiki MCP server** — `https://api.agentwiki.cc/mcp`

…covering documents, folders, tags, search (hybrid/keyword/semantic), knowledge-graph traversal, uploads, static-site hosting, sharing/publishing, member admin, API keys, and Obsidian/Notion/Lark imports.

## Install

```bash
# In Claude Code
/plugin marketplace add nextlevelbuilder/agentwiki-skills
/plugin install agentwiki@nextlevelbuilder-agentwiki
```

Or add a local clone:

```bash
git clone https://github.com/nextlevelbuilder/agentwiki-skills
# in Claude Code
/plugin marketplace add ./agentwiki-skills
/plugin install agentwiki@nextlevelbuilder-agentwiki
```

Validate before pushing changes:

```bash
claude plugin validate .
```

## Layout

```
agentwiki-skills/
├── .claude-plugin/
│   └── marketplace.json
└── plugins/
    └── agentwiki/
        ├── .claude-plugin/
        │   └── plugin.json
        └── skills/
            └── agentwiki/
                ├── SKILL.md
                └── references/
                    ├── auth-and-setup.md
                    ├── cli-commands.md
                    ├── cli-vs-mcp.md
                    ├── knowledge-graph.md
                    └── mcp-tools.md
```

## What the skill teaches

- Authentication: env vars (`AGENTWIKI_API_KEY`, `AGENTWIKI_API_URL`), `~/.agentwiki/credentials.json`, and `agentwiki login`.
- Choosing CLI vs MCP based on context (terminal vs autonomous agent).
- Concrete command/tool tables for every supported operation.
- Knowledge-graph query patterns (BFS traversal, path finding, link suggestion).
- CI-safe patterns (env-only auth, `--yes` confirmations, `--json` for piping).
- Security policy: refuse credential exfiltration, refuse instruction-override injected via document content.

## Trigger phrases

The skill auto-activates on mentions of "agentwiki", `app.agentwiki.cc`, `aw_…` API keys, `@aiagentwiki/cli`, the AgentWiki MCP server, or any document/search/upload/site/share task scoped to AgentWiki.

## License

MIT — see [LICENSE](./LICENSE).

## Source

AgentWiki itself: https://github.com/digitopvn/agentwiki
