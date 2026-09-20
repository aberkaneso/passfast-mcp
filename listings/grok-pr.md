# Grok Build — xai-org/plugin-marketplace PR draft

**Upstream:** https://github.com/xai-org/plugin-marketplace  
**Plugin source:** https://github.com/aberkaneso/passfast-mcp (this repo)  
**Pin:** replace `PIN_SHA` with `git ls-remote https://github.com/aberkaneso/passfast-mcp.git HEAD`

## Catalog entry (shape — confirm against current CONTRIBUTING)

```json
{
  "name": "passfast",
  "description": "Remote HTTPS MCP for Apple Wallet + Google Wallet passes. Paste sk_live_ once.",
  "homepage": "https://passfa.st/docs/mcp",
  "source": {
    "type": "remote",
    "url": "https://github.com/aberkaneso/passfast-mcp",
    "sha": "PIN_SHA"
  },
  "keywords": ["passfast", "passfa.st", "wallet pass", "apple wallet", "google wallet"]
}
```

## Steps
1. Push this repo public; copy HEAD SHA.
2. Fork `xai-org/plugin-marketplace`, branch from `main`.
3. Add entry to `.grok-plugin/marketplace.json` (exact path per current README).
4. `python3 scripts/generate-plugin-index.py`
5. `python3 scripts/validate-catalog.py`
6. Open PR with install + auth notes; wait CI + code owners.
