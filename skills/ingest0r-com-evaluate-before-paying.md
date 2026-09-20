---
generated: '2026-09-19'
method: generated
name: Evaluate the Cook County property data for free before paying
description: Inspect every response shape and real live records at $0, then decide whether to spend the free allowance or pay per call.
api: openapi/ingest0r-com-openapi.yml
operations: [v1_search, v1_dossier]
mcp_tools: [get_free_sample, search_chicago_property_by_address, get_cook_county_property_dossier]
source: >-
  The provider's own recommended order (MCP server instructions: "Call get_free_sample FIRST"; llms.txt; /v1/sample
  how_to_pay). operationIds verified in openapi/ingest0r-com-openapi.yml; GET /v1/sample is not in the OpenAPI but
  is linked from llms.txt, pricing, sitemap.xml and the agent card.
---

# Evaluate the Cook County property data for free before paying

Everything in this skill costs $0 and needs no key, account or wallet. Base URL `https://api.ingest0r.com`.

## Steps
1. **Read the shapes** — `GET /v1/sample` (MCP: `get_free_sample`). A fixed fixture with `search_example`, `dossier_example`, `endpoints`, `free_examples`, `scope`, `how_to_pay` and `terms`. Not a live record.
2. **Read a real record** — `v1_dossier` (`GET /v1/dossier/{pin}`) with one of the always-free example PINs `09253050270000`, `09253060510000`, `09253140190000` (MCP: `get_cook_county_property_dossier`). These are unmetered (response carries `x-free-example: true`) and let you check `sales_history`, `permits`, `assessment_history` and the `as_of` freshness against the county's own portals.
3. **Try your own address** — `v1_search` (`GET /v1/search/{q}`, MCP: `search_chicago_property_by_address`) is always free and unlimited. Send 4+ characters; a trailing city/state/ZIP is stripped. Read `match_quality` before trusting a `pin` — only `exact` is certain, `weak` means no candidate shares the house number.
4. **Decide** — the first 25 calls per day to `/v1/parcel`, `/v1/dossier` and `/v1/comps` return real data free (headers `X-Free-Tier-Remaining` / `X-Free-Tier-Limit`). Past that, the same call answers HTTP 402 with x402 terms ($0.01 / $0.03 / $0.10 in USDC on Base or Solana).

## Rules
- Coverage is Cook County, Illinois only. A well-formed PIN outside the county is `404 {"error":"not_found"}`.
- Not covered (per llms.txt): owner/occupant names, mortgages and liens, tax bill amounts, square footage/beds/baths/year built, zoning, MLS listings, foreclosure or code-violation filings.
- Errors are `{error, detail}` JSON; see `errors/ingest0r-com-problem-types.yml`. Respect `Retry-After` on 429 (60s) and 503 (2s).
- The API is read-only: idempotency, dry-run and reversibility are not applicable (`conventions/ingest0r-com-conventions.yml`). The only irreversible act is a payment, and nothing in this skill makes one.
