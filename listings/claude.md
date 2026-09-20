# Claude Connectors Directory — notes

**Docs:** https://claude.com/docs/connectors/building/submission

## Blockers to confirm before submit
- Needs Claude **Team or Enterprise** org + Directory role.
- Policy: authenticated remote MCP should use **OAuth 2.0**. PassFast MCP is Bearer `sk_live_`.
  - Option A: custom connector (users paste URL + headers) — already works without directory.
  - Option B: eng adds OAuth.
  - Option C: docs-only until OAuth.

## If proceeding (custom / approved path)
- URL: `https://passfa.st/mcp`
- Transport: Streamable HTTP
- Listing copy: same as OpenAI long description
- Privacy: https://passfa.st/privacy
- Docs: https://passfa.st/docs/mcp
- Test credentials: throwaway `sk_live_` + setup steps from README
