# AISkills402

## Basic details
- Project name: AISkills402
- What does it do? (2–3 sentences): A store of tested AI agent skill files (SKILL.md, Agent Skills format). An agent searches the catalog for free and buys the file of one skill once over x402, for cents in USDC on Base; re-downloads and new versions of a bought skill are free. Each skill card says how the skill was tested on a strong and a weak model, with and without the skill.
- Type: API (plus a free remote MCP server for search)
- Official website: https://aiskills402.com
- Logo URL: https://aiskills402.com/apple-icon.png
- Documentation or getting-started link: https://aiskills402.com/llms.txt (OpenAPI: https://api.aiskills402.com/openapi.json; MCP: https://mcp.aiskills402.com/mcp)
- Public support channel: hello@aiskills402.com (the contact published on the site and in /.well-known/ai-plugin.json)

## Networks and activity
- Networks: Base
- Public explorer or analytics link, if available: https://basescan.org/address/0xbc0dcc70d8b5d85541d86ffc68d988fd59c22e68 (the current production receiving address, since 2026-10-30; the same operator's 402registry.com, 402cron.com and 402post.com receive on it too). Historical: until 2026-10-30 the receiving address was 0x8e37022edcf0f21cf3c9f93fee9d4d32519f36f4 (https://basescan.org/address/0x8e37022edcf0f21cf3c9f93fee9d4d32519f36f4); it is no longer used, and every transaction to it is historical.
- App contract/program or receiving addresses, with their networks, if available: Base (eip155:8453) payee 0xbc0dcc70d8b5d85541d86ffc68d988fd59c22e68 (current, production, since 2026-10-30). Historical, no longer used: 0x8e37022edcf0f21cf3c9f93fee9d4d32519f36f4 (until 2026-10-30)
- Proof that you represent the project: see "Ownership reference" below; official X account of the operator: https://x.com/AiGenMaster.

## Payments — only if your product accepts payments
- Paid endpoint and HTTP method: GET https://api.aiskills402.com/v1/skills/{slug}/file — a one-time purchase of one skill file. The price is on each skill card and in the 402 (from $0.01; for example cold-email is $0.03, 30000 atomic). Also GET /v1/packs/file?skills=… (10 or more skills in one payment, discounted). Free: the catalog, skill cards, MCP search, and re-download with the purchase token.
- Facilitator used: Coinbase CDP (https://api.cdp.coinbase.com/platform/v2/x402)
- Payment scheme/version: x402 v2, exact (USDC transferWithAuthorization; extra name "USD Coin", version "2")
- Token contract/mint and decimals: USDC on Base, 0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913, 6 decimals
- Successful payment transaction link for each supported network: see "Payment example" below.
- Facilitator applicants: Not applicable

## Website application
- Website application reference, if you have one: none
- Related issue or previous pull request, if any: none. The same operator's 402registry, 402cron and 402post (same payee) are proposed in separate pull requests.

## Payment example — HISTORICAL (Base mainnet, paid by an outside wallet, to the earlier receiving address 0x8e37…36f4)
- Request: GET https://api.aiskills402.com/v1/skills/cold-email/file (one skill file)
- Amount: 0.03 USDC (30000 atomic, 6 decimals) on Base mainnet (eip155:8453), 2026-10-01 12:01 UTC
- Payer: 0xc9c7b38c0942914fc8ea12063bc92dcd3b581670 — not a wallet of the operator
- Transaction: https://basescan.org/tx/0x72d2dfe803256939db9ad2d5b89ced1a1afb79c527b4b02fb01b7fe3f304927d (block 52033362, status success; USDC Transfer 0xc9c7…1670 → 0x8e37…36f4, 0.03 USDC; submitted by the facilitator's relayer 0xb87e1a2cc2b4643f2892768e80e41167f17c5860)
- The operator's own test purchases come only from 0xa340966d806f114483d671f6bf934daebbdff8dc (stated in llms.txt, "Verify before paying") and are always labelled as operator tests, never as customer activity (see "Operator test on the current recipient" below).

## Operator test on the current recipient — OPERATOR TEST, not customer activity
- 2026-11-01 05:21 UTC: https://basescan.org/tx/0x6cad077cbe46467a3815b99bcb07484db7ea8ed22feceff69f44e7e02ead79fd (block 53360586, status success; USDC Transfer 0xa340…f8dc → 0xbc0d…2e68, 0.01 USDC; one skill file).
- Payer 0xa340966d806f114483d671f6bf934daebbdff8dc is the operator's own test wallet (stated in https://aiskills402.com/llms.txt). This payment shows that the current production recipient works; it is not presented as customer activity.

## Ownership reference
- https://aiskills402.com/llms.txt, section "Contact": the operator Georgi Kalchev, and the line "Operator on GitHub: https://github.com/paranormalen2" — the account that opened this pull request.
- The listing repository https://github.com/paranormalen2/aiskills402-mcp is in the same account; the Official MCP Registry entry com.aiskills402/mcp is published under the domain-verified namespace.
- Official X account of the operator: https://x.com/AiGenMaster (linked from https://aiskills402.com).

## Buyer guide
- Exact x402 v2 flow (402 PAYMENT-REQUIRED → PAYMENT-SIGNATURE → PAYMENT-RESPONSE receipt), what is charged when settlement fails or is uncertain, and what to verify before signing: https://aiskills402.com/llms.txt, sections "How to buy (HTTP)", "What you are charged" and "Verify before paying"; https://aiskills402.com/trust.

## Recovery and retained evidence
- Recovery guide (lost response or lost token, including after the replay window; free, authenticated by a signature of the paying wallet, no second purchase): https://aiskills402.com/trust#recover ("Lost your download token") and `/v1/recover` in https://api.aiskills402.com/openapi.json.
- 2026-10-26 delivery evidence for the historical payment: https://github.com/X402blockchains/x402-registry/pull/22#issuecomment-6416954497
- 2026-11-01 operator test: redacted raw response, decoded PAYMENT-RESPONSE, on-chain receipt and recovery run: https://github.com/X402blockchains/x402-registry/pull/22#issuecomment-6554012981
- Private keys, usable signed payment authorizations and access tokens are not published; tokens and keys shown in the evidence were truncated and revoked.
