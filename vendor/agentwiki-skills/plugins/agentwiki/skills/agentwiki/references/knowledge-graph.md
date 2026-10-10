# Knowledge Graph

AgentWiki maintains a dual-layer graph over the workspace.

## Layer 1 — Typed edges (deterministic)

Six edge types, computed from content + structure:

| Type | Source |
|---|---|
| `parent_of` | Folder hierarchy |
| `tag_of` | Shared tag |
| `wikilink` | Explicit `[[Doc Title]]` link |
| `mention` | Inline reference (e.g., `@doc-slug`) |
| `derived_from` | Versioning lineage |
| `similar_to` | Threshold from layer 2 |

## Layer 2 — Semantic similarity (Vectorize)

Workers AI embeds each doc; Cloudflare Vectorize stores vectors. Similarity is on-demand cosine; high-confidence pairs promote into `similar_to` edges.

## MCP query patterns

### "What's related to X?"
```
graph_traverse { id: "doc_X", depth: 2 }
```
Returns neighbors with edge types. Filter by `edgeTypes: ["wikilink","tag_of"]` if you want only explicit relations.

### "How is A connected to B?"
```
graph_find_path { from: "doc_A", to: "doc_B" }
graph_explain_connection { fromId: "doc_A", toId: "doc_B" }
```

### "What links am I missing?"
```
graph_suggest_links { id: "doc_X" }
```
AI proposes wikilinks to add based on semantic neighbors.

### "Health check the workspace"
```
graph_stats
```
Returns density, degree distribution, orphan count. Orphans are candidates for tagging or merging.

## Performance notes

- Traversal capped at depth 3.
- Large workspaces (>10k docs) — prefer `graph_get` with `edgeTypes` filter over unfiltered traversal.
- Similarity edges refresh asynchronously via Cloudflare Queues; new docs may take a minute to appear in `similar_to`.
