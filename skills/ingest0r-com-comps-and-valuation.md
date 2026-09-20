---
generated: '2026-09-19'
method: generated
name: Get comparable sales and an implied value range for a Cook County property
description: Resolve the subject address, then fetch arm's-length comparable sales and the provider's implied low/median/high range — free within the daily allowance, then $0.10 per call.
api: openapi/ingest0r-com-openapi.yml
operations: [v1_search, v1_comps]
mcp_tools: [search_chicago_property_by_address, find_chicago_comparable_sales]
source: >-
  Grounded in arazzo/ingest0r-com-address-to-valuation-workflow.yml; operationIds verified in
  openapi/ingest0r-com-openapi.yml. The comps method text is the OpenAPI v1_comps description verbatim.
---

# Get comparable sales and an implied value range for a Cook County property

Base URL `https://api.ingest0r.com`. The most expensive route ($0.10 past the free allowance) — use the free steps first.

## Steps
1. **Resolve the subject** — `v1_search` (`GET /v1/search/{q}`) as in the address-to-dossier skill; require `match_quality: exact`.
2. **Fetch comps** — `v1_comps` (`GET /v1/comps/{pin}`; MCP `find_chicago_comparable_sales`). Returns `comps[]` (each carrying its distance in metres from the subject), `method` (which widening rung was used) and `implied_range` (low / median / high).
3. **Read `method` before quoting the range** — per the spec, comps are "recent arm's-length sales in the same assessor neighborhood and property class over the last 18 months"; "thin markets widen automatically (36 months, then the property-class group) and the response reports which rung was used". A widened rung is a weaker valuation.
4. **Optionally corroborate** — `v1_dossier` for the subject's own `sales_history[]` and `assessment_history[]` ($0.03) to compare against `implied_range`.

## Rules
- The provider states this is "a lightweight automated valuation", "not an appraisal, title report, or legal advice" (pricing terms.warranty). Present it as such.
- Non-arm's-length and multi-parcel deeds are already filtered out by the provider.
- Allowance and 402 handling are identical to the dossier skill: `X-Free-Tier-Remaining` on 200, x402 v2 on 402 (amount `100000` = $0.10 USDC), retry with `PAYMENT-SIGNATURE`.
- Errors and limits: `errors/ingest0r-com-problem-types.yml`, `rate-limits/ingest0r-com-rate-limits.yml`.
