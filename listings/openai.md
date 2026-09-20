# OpenAI Plugins Directory — form pack (With MCP)

**Portal:** OpenAI Platform → plugin submission → **With MCP** → Universal  
**Docs:** https://developers.openai.com/plugins/deploy/submission

## Listing
- **Name:** PassFast
- **Short:** (see `short-description.txt`)
- **Long:** PassFast is a developer API for Apple Wallet and Google Wallet passes. This plugin exposes the same key-auth public API over remote MCP (Streamable HTTP). Tools map 1:1 to OpenAPI `operationId`s — list/publish templates, generate dual-wallet passes, download `.pkpass`, update/void, share links, manage images/credentials/apps. Auth: paste `Authorization: Bearer sk_live_…` once (optional `X-App-Id`). No OAuth. JWT member/invite tools are out of scope for MCP v1.
- **Category:** Developer tools / Productivity
- **Homepage:** https://passfa.st/
- **Docs:** https://passfa.st/docs/mcp
- **Support:** https://passfa.st/ (or support email once confirmed)
- **Privacy:** https://passfa.st/privacy
- **Terms:** https://passfa.st/terms
- **Logo:** `assets/icon.svg` (export PNG 512 if portal requires)

## MCP
- **Type:** Universal
- **URL:** `https://passfa.st/mcp`
- **Auth:** Bearer API key (`sk_live_`)
- **Reviewer credentials:** throwaway `sk_live_` + `X-App-Id` (Mohamed mints; not production customer keys)
- **Domain verify:** host token at `https://passfa.st/.well-known/openai-apps-challenge` (Ship Lead)

## Test cases (5 positive / 3 negative)
**Positive**
1. List templates with PassFast MCP and summarize names + publish state.
2. If a template is unpublished, publish it, then generate a dual-wallet pass with serial `REVIEW-001`.
3. Get pass by serial `REVIEW-001` and update one visible field.
4. Create a share token for that pass and return the public link.
5. Download the Apple `.pkpass` for `REVIEW-001`.

**Negative**
1. Call with `pk_live_` → expect reject / clear auth error.
2. `generatePass` with a fake template id → not_found.
3. `voidPassBySerial` for `NO-SUCH-SERIAL` → not_found.

## Starter prompts
Use the three JTBD prompts in `skills/passfast/SKILL.md`.
