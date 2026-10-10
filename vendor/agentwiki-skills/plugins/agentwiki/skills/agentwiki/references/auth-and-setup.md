# Auth & Setup

## Install CLI

```bash
# Global
npm i -g @aiagentwiki/cli

# Or run ad-hoc
npx @aiagentwiki/cli --help
```

Requires Node.js `>= 20`. Binary name: `agentwiki`. Verify: `agentwiki --version`.

## Get an API key

1. Sign in at [app.agentwiki.cc](https://app.agentwiki.cc).
2. Open **Settings → API Keys**.
3. Create a key. Copy the `aw_…` value (shown once).

Treat keys like passwords. Never commit them, never paste them into chats.

## Credential resolution (precedence: high → low)

1. **Environment variables**
   - `AGENTWIKI_API_KEY` — bypasses login; ideal for CI/Docker/automation.
   - `AGENTWIKI_API_URL` — override base URL (self-hosted, staging).
2. **Credentials file** — `~/.agentwiki/credentials.json` (written by `agentwiki login`).
3. **Defaults** — `apiUrl = https://api.agentwiki.cc`.

Verify which source is active:

```bash
agentwiki whoami
# stderr lines beginning with `# Auth source: …` show resolution path.
```

## Login (writes credentials file)

```bash
agentwiki login --api-key aw_xxxxxxxx
agentwiki login --api-key aw_xxxxxxxx --url https://api.example.internal   # self-hosted
```

Stored at `~/.agentwiki/credentials.json` with `{ apiKey, apiUrl }`.

## CI / Docker

Use env vars. Do not run `login` in CI.

```yaml
- name: Publish via AgentWiki CLI
  env:
    AGENTWIKI_API_KEY: ${{ secrets.AGENTWIKI_API_KEY }}
  run: npx @aiagentwiki/cli sites upload ./build.zip --description "build #${{ github.run_number }}"
```

## MCP server config

Connect any MCP-aware client (Claude Desktop, Cursor, ChatGPT) to the AgentWiki MCP server.

```json
{
  "mcpServers": {
    "agentwiki": {
      "url": "https://api.agentwiki.cc/mcp",
      "env": { "API_KEY": "aw_xxxxxxxx" }
    }
  }
}
```

After restart, ask the agent: `@agentwiki list my recent docs`.

Self-hosted MCP: replace the URL with your deployed Worker URL (e.g., `https://mcp.example.internal/mcp`).

## Key rotation

1. Create new key in the dashboard.
2. Update env var or run `agentwiki login --api-key aw_NEW`.
3. Confirm `agentwiki whoami` returns expected user.
4. Revoke the old key via MCP `api_key_revoke` or the dashboard.

## Troubleshooting

| Symptom | Cause / Fix |
|---|---|
| `Not authenticated` from `whoami` | No env var, no credentials file. Run `login` or set `AGENTWIKI_API_KEY`. |
| `401 Unauthorized` on commands | Key revoked or wrong URL. Verify `agentwiki whoami`. |
| `403 Forbidden` | Key lacks scope for the action (e.g., Viewer trying to write). Check role in dashboard. |
| MCP tool errors with auth issues | `env.API_KEY` missing in MCP client config or restart needed. |
| CLI hits wrong server | `AGENTWIKI_API_URL` override is set. Unset it or run `login --url …`. |
| Self-signed cert on self-host | Configure trust at OS level; CLI uses Node's TLS stack. |
