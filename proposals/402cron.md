# 402cron

## Basic details
- Project name: 402cron
- What does it do? (2–3 sentences): Paid cron for AI agents. An agent registers a public HTTPS URL and a cron schedule, and the service calls it on time with a signed request, billing one prepaid delivery per attempt. Deliveries are bought in packs over x402; there is no account and no API key — the paying wallet is the identity.
- Type: API (plus a remote MCP server)
- Official website: https://402cron.com
- Logo URL: https://402cron.com/og.png
- Documentation or getting-started link: https://402cron.com/llms.txt (OpenAPI: https://402cron.com/openapi.json; MCP: https://402cron.com/mcp)
- Public support channel: abuse@402cron.com (the contact published in the terms and in /.well-known/ai-plugin.json)

## Networks and activity
- Networks: Base
- Public explorer or analytics link, if available: https://basescan.org/address/0xbc0dcc70d8b5d85541d86ffc68d988fd59c22e68 (the current production receiving address, since 2026-10-30; the same operator's aiskills402.com, 402registry.com and 402post.com receive on it too). Historical: until 2026-10-30 the receiving address was 0x8e37022edcf0f21cf3c9f93fee9d4d32519f36f4 (https://basescan.org/address/0x8e37022edcf0f21cf3c9f93fee9d4d32519f36f4); it is no longer used, and every transaction to it is historical.
- App contract/program or receiving addresses, with their networks, if available: Base (eip155:8453) payee 0xbc0dcc70d8b5d85541d86ffc68d988fd59c22e68 (current, production, since 2026-10-30). Historical, no longer used: 0x8e37022edcf0f21cf3c9f93fee9d4d32519f36f4 (until 2026-10-30)
- Proof that you represent the project: see "Ownership reference" below; official X account of the operator: https://x.com/AiGenMaster.

## Payments — only if your product accepts payments
- Paid endpoint and HTTP method: GET https://402cron.com/buy/{pack} — a prepaid pack of deliveries: trial, 20 deliveries for $0.02 (20000 atomic); starter, 2,000 for $1; month, 50,000 for $25. Packs never expire. Free: pricing, docs and /health.
- Facilitator used: Coinbase CDP (https://api.cdp.coinbase.com/platform/v2/x402)
- Payment scheme/version: x402 v2, exact (USDC transferWithAuthorization; extra name "USD Coin", version "2")
- Token contract/mint and decimals: USDC on Base, 0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913, 6 decimals
- Successful payment transaction link for each supported network: see "Payment example" below.
- Facilitator applicants: Not applicable

## Website application
- Website application reference, if you have one: none
- Related issue or previous pull request, if any: none. The same operator's AISkills402, 402registry and 402post (same payee) are proposed in separate pull requests.

## Payment example — HISTORICAL (Base mainnet, paid by an outside wallet, to the earlier receiving address 0x8e37…36f4)
- Request: GET https://402cron.com/buy/trial (20 deliveries)
- Amount: 0.02 USDC (20000 atomic, 6 decimals) on Base mainnet (eip155:8453), 2026-10-23 23:35 UTC
- Payer: 0x7722dfae6bbed2fd02dc07455c2f5bf14be25e4a — not a wallet of the operator
- Transaction: https://basescan.org/tx/0xc15f5bb0ca40200d6a8d5f0595b01af0b323b2430269a70585521a08d50ae28a (block 53004600, status success; USDC Transfer 0x7722…5e4a → 0x8e37…36f4, 0.02 USDC; submitted by the facilitator's relayer 0x59b7ebc67a3d627fabaf06768c818638452ae704)

## Operator test on the current recipient — OPERATOR TEST, not customer activity
- 2026-11-01 05:24 UTC: https://basescan.org/tx/0x35ecf26f8651a64a71a86c99e13dcf0c6decc6144e15795ed1c6b41d27b77421 (block 53360656, status success; USDC Transfer 0xa340…f8dc → 0xbc0d…2e68, 0.02 USDC; one delivery pack).
- Payer 0xa340966d806f114483d671f6bf934daebbdff8dc is the operator's own test wallet (stated in https://402cron.com/llms.txt). This payment shows that the current production recipient works; it is not presented as customer activity.

## Ownership reference
- https://402cron.com/llms.txt, section "Operator": Georgi Kalchev and "GitHub: https://github.com/paranormalen2" — the account that opened this pull request.
- The listing repository https://github.com/paranormalen2/402cron-mcp is in the same account; docs and examples: https://github.com/402cron/402cron (linked from the same llms.txt section). The Official MCP Registry entry com.402cron/402cron is published under the domain-verified namespace.
- Official X account of the operator: https://x.com/AiGenMaster (linked from https://402cron.com).

## Buyer guide
- Packs, prices, how to buy and what a delivery costs: https://402cron.com/llms.txt, sections "Packs" and "What you need"; https://402cron.com/docs (how to buy, register a task and read a delivery).

## Recovery and retained evidence
- Recovery guide (lost response or lost token, including after the replay window; free, authenticated by a signature of the paying wallet, no second purchase): https://402cron.com/docs and the token descriptions in https://402cron.com/openapi.json (`POST /recover`).
- 2026-10-26 delivery evidence for the historical payment: https://github.com/X402blockchains/x402-registry/pull/24#issuecomment-6417005581
- 2026-11-01 operator test: raw response, decoded PAYMENT-RESPONSE, on-chain receipt, our rows and recovery run: https://github.com/X402blockchains/x402-registry/pull/24#issuecomment-6554024963
- Private keys, usable signed payment authorizations and access tokens are not published; tokens and keys shown in the evidence were truncated and revoked.
