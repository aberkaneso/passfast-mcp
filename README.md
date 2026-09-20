# PassFast MCP

Remote HTTPS [Model Context Protocol](https://modelcontextprotocol.io) server for **[PassFast](https://passfa.st)** — Apple Wallet + Google Wallet passes from any MCP client (Cursor, Claude, ChatGPT, Codex, Grok).

| | |
|---|---|
| **Endpoint** | `https://passfa.st/mcp` |
| **Alias** | `https://passfa.st/api/mcp` |
| **Docs** | https://passfa.st/docs/mcp · https://passfa.st/mcp.md |
| **OpenAPI** | https://passfa.st/openapi.yaml |
| **Signup / keys** | https://passfa.st/signup |
| **Privacy / Terms** | https://passfa.st/privacy · https://passfa.st/terms |

This repository is the **public metadata + install kit** for marketplace listings (official MCP Registry, Grok Build plugins, open directories). The server itself is hosted at `passfa.st` — there is no local stdio binary here.

## Auth

```
Authorization: Bearer sk_live_YOUR_SECRET_KEY
X-App-Id: YOUR_APP_ID   # optional for single-app orgs
```

- Secret keys only (`sk_live_`). Publishable `pk_live_` keys are rejected.
- No OAuth, no PassFast agent account — the MCP client *is* the agent.
- Member/invite tools need a user JWT and are **out of scope** for key-auth MCP v1.

## Install

### Cursor

Copy [`cursor/mcp.json`](./cursor/mcp.json) into `~/.cursor/mcp.json` or project `.cursor/mcp.json`, then replace the placeholders.

### Claude (HTTP)

```json
{
  "mcpServers": {
    "passfast": {
      "type": "http",
      "url": "https://passfa.st/mcp",
      "headers": {
        "Authorization": "Bearer sk_live_YOUR_SECRET_KEY",
        "X-App-Id": "YOUR_APP_ID"
      }
    }
  }
}
```

Stdio-only clients: `npx mcp-remote https://passfa.st/mcp` with the same headers via your client’s env/header support.

### Generic / registry

See [`server.json`](./server.json) for the official MCP Registry remote descriptor (Streamable HTTP + auth headers).

## What agents can do

- List / publish templates; generate dual-wallet passes; download `.pkpass`
- Update / void passes; share links + QR
- Upload images & signing credentials; manage apps / org / API keys
- Same billing as the HTTP API (see https://passfa.st/#pricing)

## Starter prompts

See [`skills/passfast/SKILL.md`](./skills/passfast/SKILL.md).

## Marketplace submissions

Prepared listing fields live under [`listings/`](./listings/). Status checklist: [`SUBMIT.md`](./SUBMIT.md).

## License

MIT © Aberkane Software
