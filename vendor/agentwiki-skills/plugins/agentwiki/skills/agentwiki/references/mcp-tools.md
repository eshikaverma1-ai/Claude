# MCP Tool Catalog

Server: `https://api.agentwiki.cc/mcp` (auth via `env.API_KEY`). 28+ tools grouped below. Tool names mirror REST resources; arguments mirror Zod schemas in `packages/mcp/src/tools/*.ts`.

## Documents

| Tool | Purpose |
|---|---|
| `document_list` | Paginated list. Args: `limit?`, `offset?`, `category?`, `tag?`. |
| `document_get` | Args: `id`. Returns full content + tags. |
| `document_create` | Args: `title`, `content`, `category?`, `tags?`, `folderId?`. |
| `document_update` | Args: `id`, partial fields. |
| `document_delete` | Args: `id`. |
| `document_versions_list` | Args: `id`. |
| `document_version_create` | Args: `id`, `content`. Snapshots a version. |
| `document_links_get` | Args: `id`. Returns wikilinks in/out. |

## Search

| Tool | Purpose |
|---|---|
| `search` | Args: `query`, `type? (hybrid\|keyword\|semantic)`, `source? (docs\|storage\|all)`, `limit?`. Default hybrid. |
| `search_images` | Args: `query`, `limit?`. Vision-augmented image search. |

## Folders

| Tool | Args |
|---|---|
| `folder_list` | `kind? (doc\|storage)` (default `doc`). |
| `folder_create` | `name`, `parentId?`, `kind?`. |
| `folder_update` | `id`, `name?`, `parentId?`, `kind?`. |
| `folder_delete` | `id`, `kind?`. |

## Tags & Categories

- `tag_list` — list workspace tags.
- `category_list` — list categories.

## Uploads

| Tool | Args |
|---|---|
| `upload_file` | `filename`, `contentBase64`, `contentType?`, `folderId?`, `documentId?`, `isPublic?`. |
| `upload_list` | `limit?`, `offset?`. |

## Static sites

| Tool | Args |
|---|---|
| `site_list` | `search?`, `limit?`, `offset?`. |
| `site_get` | `id`. |
| `site_delete` | `id`. |

(Site **upload** is via REST `POST /sites` or the CLI `agentwiki sites upload`. MCP currently exposes read/list/delete.)

## Sharing

- `share_link_create` — Args: `documentId`, `expiresInDays?`. Returns token + URL.

## Knowledge graph

The graph layers (1) **typed edges** (6 types: `parent_of`, `tag_of`, `wikilink`, `mention`, `derived_from`, `similar_to`) and (2) **semantic similarity** via Vectorize.

| Tool | Purpose |
|---|---|
| `graph_get` | Whole graph. Filters: `edgeTypes?`, `category?`, `tag?`. |
| `graph_traverse` | BFS from `id`, depth `1-3`. Args: `id`, `depth?`, `edgeTypes?`. |
| `graph_find_path` | Shortest path between `from` and `to`. |
| `graph_suggest_links` | AI-suggested missing links for `id`. |
| `graph_explain_connection` | Natural-language explanation of why two docs relate. Args: `fromId`, `toId`. |
| `graph_stats` | Density, degree distribution, orphan count. |

Use the graph to answer "how is X related to Y?" or to surface neighborhood context before drafting.

## Members & API keys (admin)

| Tool | Purpose |
|---|---|
| `member_list` | List workspace members. |
| `member_update_role` | Args: `userId`, `role` (`admin\|editor\|viewer\|agent`). |
| `member_remove` | Args: `userId`. |
| `api_key_create` | Args: `name`, `scopes?`. Returns `aw_…` once. |
| `api_key_list` | List keys (no secrets). |
| `api_key_update` | Args: `id`, `name?`. |
| `api_key_revoke` | Args: `id`. |

Treat all admin tools as destructive — confirm before calling.

## Resources & Prompts

The MCP server may also expose:
- **Resources** (`resources/*`) — readable URIs for documents, folders, etc.
- **Prompts** (`prompts/*`) — pre-canned prompts (e.g., "summarize doc"). Discover with the client's prompt picker.

## Calling pattern (pseudo)

```
search { query: "auth runbook", type: "hybrid", limit: 5 }
→ pick top result.id = "doc_123"
graph_traverse { id: "doc_123", depth: 2 }
→ collect related ids [doc_456, doc_789]
document_get { id: "doc_456" }
graph_explain_connection { fromId: "doc_123", toId: "doc_789" }
```
