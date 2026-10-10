# CLI Command Catalog

Binary: `agentwiki` (from `@aiagentwiki/cli`). All commands hit the AgentWiki REST API; auth via env or `~/.agentwiki/credentials.json`. Most listing commands accept `--json` for piping.

## Auth

| Command | Description |
|---|---|
| `agentwiki login --api-key aw_… [--url <url>]` | Save credentials to `~/.agentwiki/credentials.json`. |
| `agentwiki whoami` | Show authenticated user + auth source. Exit 1 if unauth. |

## Documents (`doc`)

| Command | Notes |
|---|---|
| `agentwiki doc list [--limit 20] [--offset 0] [--category <c>] [--tag <t>] [--json]` | Lists docs. |
| `agentwiki doc get <id> [--json] [--markdown]` | `--markdown` prints content only. |
| `agentwiki doc create --title "T" (--content "…" \| --file path.md) [--category <c>] [--tags a,b] [--folder <id>]` | Either `--content` or `--file`. |
| `agentwiki doc update <id> [--title …] [--content … \| --file …] [--category …] [--tags …]` | Partial update. |
| `agentwiki doc delete <id>` | Hard delete. |
| `agentwiki doc search <query> [--type hybrid\|keyword\|semantic] [--source docs\|storage\|all] [--limit 10] [--json]` | Default `hybrid` blends FTS + semantic. |
| `agentwiki doc share <id> [--expires 30]` | Returns share URL token. |
| `agentwiki doc publish <id>` | Publishes as public HTML. |

## Top-level search

```bash
agentwiki search "<query>" [--type hybrid|keyword|semantic] [--source docs|storage|all] [--limit 10] [--json]
agentwiki search-images "<query>" [--limit 10] [--json]
```

## Folders

Two namespaces: **doc-folders** (organize documents) and **storage-folders** (organize uploaded files).

```bash
agentwiki doc-folders list|tree [--json] [--full-ids]
agentwiki doc-folders create <name> [--parent <id>]
agentwiki doc-folders rename <id> <new-name>
agentwiki doc-folders move <id> --parent <id|root>
agentwiki doc-folders delete <id> [--yes]

agentwiki storage-folders list|tree|create|rename|move|delete   # same shape

# Shortcuts
agentwiki doc-tree [--json] [--full-ids]
agentwiki storage-tree [--json] [--full-ids]

# Deprecated alias kept for back-compat
agentwiki folder list
agentwiki folder create <name> [--parent <id>]
```

`delete` requires interactive confirm or `--yes` (CI-safe).

## Tags

```bash
agentwiki tag list [--json]
agentwiki tag create <name>
```

## Uploads

Files (any binary). Public by default — anyone with the URL can fetch.

```bash
agentwiki upload list [--json]
agentwiki upload put <file> [--private] [--folder <id>] [--doc <id>] [--json]
agentwiki upload public <id> [--off]                # toggle public/private
agentwiki upload describe <id> (--text "…" | --clear)
agentwiki upload regenerate <id>                    # re-trigger AI summary
```

Notes:
- Server-side AI extracts a summary; check status via `upload list` (`extractionStatus`).
- `regenerate` returns 429 with `retryAfterSeconds` when in cooldown.

## Static sites

Host an HTML file or a ZIP of a built site (entrypoint: `index.html`).

```bash
agentwiki sites upload <file.html|file.zip> [--description "…"] [--auto-summary]
agentwiki sites list [--search <q>] [--limit 20] [--offset 0] [--json]
agentwiki sites get <id> [--json]
agentwiki sites delete <id>
```

Public URL is returned on upload (`<apiUrl>/s/<id>`).

## Imports

```bash
agentwiki import obsidian <vault-path>     # imports .md vault preserving folders
agentwiki import notion <zip-path>          # imports a Notion HTML/Markdown export
agentwiki import lark                       # interactive Lark/Feishu import
agentwiki import history [--limit 20] [--json]
```

## Output flags & exit codes

- `--json` available on most list/get/search/upload commands.
- Exit 0 on success, 1 on auth/validation/network failure.
- `whoami` writes auth source to **stderr** so stdout stays parseable.

## Common recipes

```bash
# Pull markdown of top hit for a query
ID=$(agentwiki search "rate limiting" --json --limit 1 | jq -r '.results[0].id')
agentwiki doc get "$ID" --markdown > rate-limiting.md

# Bulk-tag every doc in a folder
for id in $(agentwiki doc list --json --limit 100 | jq -r '.data[].id'); do
  agentwiki doc update "$id" --tags "reviewed-2026-q2"
done

# Move all storage folders under one parent to root
agentwiki storage-folders list --json --full-ids \
  | jq -r '.folders[] | select(.parentId=="<parent>") | .id' \
  | xargs -I{} agentwiki storage-folders move {} --parent root
```
