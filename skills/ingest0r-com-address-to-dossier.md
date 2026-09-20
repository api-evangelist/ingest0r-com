---
generated: '2026-09-19'
method: generated
name: Resolve a Chicago address to its parcel and pull the full property dossier
description: Turn a street address into a Cook County PIN, then fetch the parcel record or the full dossier (sales, permits, assessments) — free within the daily allowance, then $0.01–$0.03 per call.
api: openapi/ingest0r-com-openapi.yml
operations: [v1_search, v1_parcel, v1_dossier]
mcp_tools: [search_chicago_property_by_address, get_cook_county_parcel, get_cook_county_property_dossier]
source: >-
  Grounded in arazzo/ingest0r-com-address-to-valuation-workflow.yml; operationIds verified in
  openapi/ingest0r-com-openapi.yml; header behaviour observed live 2026-09-19 on the free surface.
---

# Resolve a Chicago address to its parcel and pull the full property dossier

Base URL `https://api.ingest0r.com`. No credential. Payment, when it applies, is x402 (see `authentication/ingest0r-com-authentication.yml`).

## Steps
1. **Address to PIN** — `v1_search` (`GET /v1/search/{q}`; MCP `search_chicago_property_by_address` takes `address`). Always free. URL-encode the address (`/v1/search/1%20E%20113th%20St`). Pick a candidate from `matches[]` only when `match_quality` is `exact` (or `likely` with a human check); stop on `weak`/`none` and ask for a better address.
2. **Choose depth** — `v1_parcel` (`GET /v1/parcel/{pin}`, $0.01 past the allowance) returns the parcel with address, class, township, ward, census tract, schools, walkability, airport noise and lat/lon. `v1_dossier` (`GET /v1/dossier/{pin}`, $0.03) returns the same basics **plus** `sales_history[]`, `permits[]` (linked to the PIN by the provider — the raw permit feed has no PIN), `assessment_history[]` and `assessment_note`. Call dossier directly if you need history; parcel is a subset.
3. **Read the allowance** — every metered 200 carries `X-Free-Tier: true`, `X-Free-Tier-Limit: 25`, `X-Free-Tier-Remaining: n` (resets 00:00 UTC). On MCP the same appears under `_free_tier` in the tool result.
4. **Handle 402** — past the allowance the route returns `402` with an x402 v2 `PaymentRequired` body (also base64 in the `PAYMENT-REQUIRED` header): `accepts[]` names USDC on Base (`eip155:8453`, amount `10000` = $0.01 or `30000` = $0.03) and Solana. Pay with an x402 client and retry the identical GET with `PAYMENT-SIGNATURE`. On MCP the 402 arrives as `_meta["x402/error"]` and payment goes in `_meta["x402/payment"]`. Never pay a route-template URL (`/v1/parcel/{pin}` literally) — it always 402s and returns nothing.
5. **Cite** — keep `as_of`, `source` and `cite` from the answer; they are the provenance the provider attaches to every record.

## Errors
- `400 invalid_pin` — pass 10 or 14 digits, dashes ok (`14-08-120-017-0000`).
- `404 not_found` — valid PIN outside Cook County.
- `429 rate_limited` (120/min per IP, `Retry-After: 60`), `503 busy` (`Retry-After: 2`). Full catalog: `errors/ingest0r-com-problem-types.yml`.

## Notes
- Read-only API: no idempotency key, dry-run or reversal applies (`conventions/ingest0r-com-conventions.yml`). A payment is final; the free allowance is the rehearsal.
- Schema is additive-only within `/v1`; `X-Schema-Version` (0.4.2) is on every response.
