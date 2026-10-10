# CLI vs MCP — picking the right interface

| Situation | Use |
|---|---|
| User is in a terminal | CLI |
| Scripting / CI / Docker / cron | CLI (env var auth) |
| Bulk operations piped via `jq` / `xargs` | CLI |
| Interactive AI client (Claude Desktop, Cursor) | MCP |
| Agent-driven multi-step reasoning over the workspace | MCP |
| Knowledge-graph traversal | MCP (CLI has no graph commands) |
| Member / API-key administration | MCP |
| Imports (Obsidian / Notion / Lark) | CLI (MCP has no import tools) |
| Static site upload | CLI `sites upload` (preferred) |

## Mental model

- **CLI = imperative shell**. One command, one HTTP call, exits. Good for known operations and pipelines.
- **MCP = structured tool surface**. Models pick tools dynamically; cheap to chain reads (search → graph → get → explain) within one agent turn.

## When in doubt

If the agent is *driving* (autonomous research/synthesis) → MCP.
If the human is *driving* (typing commands) → CLI.

## Auth parity

Both interfaces use the same `aw_…` API key. A key valid for CLI is valid for MCP and vice-versa. Roles (Admin/Editor/Viewer/Agent) determine which tools/commands succeed.
