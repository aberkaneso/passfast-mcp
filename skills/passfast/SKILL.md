---
name: passfast
description: |
  Use PassFast MCP to create and manage Apple Wallet and Google Wallet passes.
  Trigger when the user wants wallet passes, .pkpass files, loyalty cards, event
  tickets, boarding passes, coupons, or dual-wallet (Apple + Google) passes via API.
---

# PassFast MCP

Remote HTTPS MCP at `https://passfa.st/mcp`. Auth: `Authorization: Bearer sk_live_…`
(optional `X-App-Id`). Tools are 1:1 with PassFast OpenAPI `operationId`s.
Member/invite JWT tools are out of scope for key-auth MCP v1.

## Starter workflows

### 1. Generate a dual-wallet pass
1. `listTemplates` — pick a published template (or `publishTemplate` first).
2. `generatePass` with `wallet_type: "both"`, a unique `serial_number`, and sample fields.
3. Return Apple download path / `.pkpass` and Google save URL.

### 2. Update + share
1. Find the pass (`getPassBySerial` or `listPasses`).
2. `updatePass` / `updatePassBySerial` with a visible field change.
3. `createShareToken` — return public share link + QR for both wallets.

### 3. Template publish gate
1. `listTemplates`.
2. If unpublished, explain `publishTemplate` is required before generate.
3. Publish, then generate one test pass with `wallet_type: "both"`.

## Safety
- Never echo or commit `sk_live_` keys.
- Prefer void over hard-delete when cleaning test passes.
- Do not claim JWT member/invite tools exist on this MCP.
