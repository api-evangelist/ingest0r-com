# ingest0r

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

ingest0r operates the Cook County (Chicago) property records API at api.ingest0r.com — a pay-per-call, agent-native REST API over Cook County, Illinois public records (~1.9M parcels, refreshed nightly) that resolves a street address to its parcel PIN, then returns parcel details, recorded sales and deed history, building permits linked to the PIN, property-tax assessment history and comparable-sales valuation as one joined answer. There is no signup and no API key: address search and a fixed sample are always free, the first 25 PIN-route calls per client per day return real data free, and past that the routes answer HTTP 402 and are settled per call in USDC on Base or Solana through the x402 protocol ($0.01, $0.03 and $0.10). The provider publishes an OpenAPI 3.1, an A2A agent card, a live streamable-HTTP MCP server with five tools, llms.txt, an x402 resource list, a machine-readable price card and changelog, and a security.txt — all on api.ingest0r.com. The operator identifies itself only as "independent" (the agent card's provider.organization) with a personal contact address; the apex ingest0r.com has no DNS A record, so the API host is the website.

**Areas:** Company · Real Estate · Property Records · Property Data · Public Records · Open Data · Government Data · Geocoding · Property Tax · Building Permits · Comparable Sales · Valuation

## ingest0r on APIs.io

Everything profiled for ingest0r is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/ingest0r-com/](https://apis.io/providers/ingest0r-com/)** — or go straight to one of the APIs or properties below.

### APIs (5)

- [Cook County (Chicago) Property Records MCP Server](https://apis.io/apis/ingest0r-com/cook-county-property-records-mcp-server/) — A live remote MCP server at https://api.ingest0r.com/mcp (streamable-http, JSON-RPC 2.0 over HTTP POST, protocol 2025-11-25, serverInfo…
- [ingest0r Comps API](https://apis.io/apis/ingest0r-com/ingest0r-com-comps-api/) — The Comps API from ingest0r — 1 operation(s) for comps.
- [ingest0r Dossier API](https://apis.io/apis/ingest0r-com/ingest0r-com-dossier-api/) — The Dossier API from ingest0r — 1 operation(s) for dossier.
- [ingest0r Parcel API](https://apis.io/apis/ingest0r-com/ingest0r-com-parcel-api/) — The Parcel API from ingest0r — 1 operation(s) for parcel.
- [ingest0r Search API](https://apis.io/apis/ingest0r-com/ingest0r-com-search-api/) — The Search API from ingest0r — 1 operation(s) for search.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### Arazzo workflows (1)

Multi-step workflows that chain operations into a business task.

- [Cook County address to dossier and comps](https://apis.io/arazzos/ingest0r-com/ingest0r-com-address-to-valuation-workflow/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [cook-county-chicago-property-data](https://apis.io/servers/ingest0r-com/cook-county-chicago-property-data/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Ingest0R Com Agentic Access](https://apis.io/agentic-access/ingest0r-com/ingest0r-com-agentic-access/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Ingest0R Com Openapi Overlay](https://apis.io/overlays/ingest0r-com/ingest0r-com-openapi-overlay/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Ingest0R Com Authentication](https://apis.io/security/ingest0r-com/ingest0r-com-authentication/)
- [Ingest0R Com Domain Security](https://apis.io/security/ingest0r-com/ingest0r-com-domain-security/)
- [Ingest0R Com Vulnerability Disclosure](https://apis.io/security/ingest0r-com/ingest0r-com-vulnerability-disclosure/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Ingest0R Com Plans Pricing](https://apis.io/plans/ingest0r-com/ingest0r-com-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Ingest0R Com Rate Limits](https://apis.io/rate-limits/ingest0r-com/ingest0r-com-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://api.ingest0r.com/)
- [Documentation](https://api.ingest0r.com/llms.txt)
- [Pricing](https://api.ingest0r.com/pricing)
- [Changelog](https://api.ingest0r.com/changelog.json)

## API Evangelist rating

**Kin Score 46.6** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 75.0 |
| Contract quality | 49.6 |
| Contract governance | 18.2 |
| Operational transparency | 55.3 |
| Developer ergonomics | 37.5 |
| Access clarity | 42.1 |

**Agent readiness 41.1** — agent-native

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | na |
| MCP Server | documented (partial credit) |
| Auth Clarity | bearer (partial credit) |
| Idempotency | na |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | verified |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | near-conformant (partial credit) |
| Dry Run Mode | na |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | na |

**Regulatory alignment 22.5** — Government & Public Sector

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/ingest0r-com/](https://apis.io/providers/ingest0r-com/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for ingest0r: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/ingest0r-com/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
