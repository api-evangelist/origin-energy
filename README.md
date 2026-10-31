# Origin Energy

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

Origin Energy Limited is Australia's largest energy retailer, an ASX-listed integrated gas and electricity company headquartered in Sydney that supplies roughly 4.5 million electricity, natural gas, LPG and broadband customer accounts, operates the Eraring Power Station and a large gas-fired and renewable generation portfolio, holds a stake in the Australia Pacific LNG project, and runs the Origin Loop virtual power plant. It sits at the retail end of the National Electricity Market value chain, buying and generating wholesale energy and selling it to households and businesses. Its API posture is defined almost entirely by regulation rather than by a developer strategy: Origin is a designated energy data holder under Australia's Consumer Data Right and that obligation is genuinely implemented — it appears on the CDR Register with its own public base URI, serves the Consumer Data Standards discovery endpoints anonymously, and presents an mTLS resource endpoint whose TLS certificate is issued by the ACCC's own CDR Certificate Authority — but every byte of actual customer usage, billing and DER data behind that surface is reachable only by an accredited data recipient acting on a consumer's consent. Alongside the mandate, Origin runs its retail business on Octopus Energy's Kraken platform (Origin holds an equity stake in Octopus and Kraken Technologies), which exposes a publicly readable partner developer portal with downloadable OpenAPI definitions, a GraphQL API, an external events catalogue and an OpenID Connect authorisation server — none of it self-serve. Origin publishes no open grid, market or system data of its own; the only anonymously retrievable data is its retail plan reference data, and that is served from the Australian Energy Regulator's Energy Made Easy CDR gateway, not from an Origin host.

**Areas:** Energy · Australia · Utilities · Electricity · Gas · Energy Retail · Consumer Data Right · Smart Metering · Solar · DER · Demand Response · Energy Markets

## Origin Energy on APIs.io

Everything profiled for Origin Energy is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/origin-energy/](https://apis.io/providers/origin-energy/)** — or go straight to one of the APIs or properties below.

### APIs (25)

- [Origin Energy Kraken GraphQL API](https://apis.io/apis/origin-energy/origin-energy-kraken-graphql-api/) — The primary Kraken platform API for Origin Energy accounts, agreements, meter points, readings, payments, quotes and devices. Served at…
- [Origin Energy Kraken External Events](https://apis.io/apis/origin-energy/origin-energy-kraken-events/) — Origin's publicly readable Kraken External Events reference, cataloguing several hundred versioned event types emitted by the platform. Confirmed HTTP 200…
- [Origin Energy Kraken Authorization Server](https://apis.io/apis/origin-energy/origin-energy-kraken-auth-api/) — The OpenID Connect authorisation server issuing the bearer tokens used by both the Kraken REST and GraphQL APIs. Its discovery document at…
- [Origin Energy Account Import API](https://apis.io/apis/origin-energy/origin-energy-account-import-api/) — APIs for importing accounts.
- [Origin Energy Business Import API](https://apis.io/apis/origin-energy/origin-energy-business-import-api/) — APIs for importing businesses with business contracts
- [Origin Energy Data Holder Customers API](https://apis.io/apis/origin-energy/origin-energy-data-holder-customers-api/) — Data Holder Customer endpoints
- [Origin Energy Data Holder Operations API](https://apis.io/apis/origin-energy/origin-energy-data-holder-operations-api/) — Data Holder Operations endpoints
- [Origin Energy Data Import API](https://apis.io/apis/origin-energy/origin-energy-data-import-api/) — The data-import API from Origin Energy — 1 operation(s) for data-import.
- [Origin Energy Distributed Energy Resources API](https://apis.io/apis/origin-energy/origin-energy-distributed-energy-resources-api/) — Distributed Energy Resource endpoints
- [Origin Energy Electricity Service Points API](https://apis.io/apis/origin-energy/origin-energy-electricity-service-points-api/) — Electricity Service Point endpoints
- [Origin Energy Electricity Usage API](https://apis.io/apis/origin-energy/origin-energy-electricity-usage-api/) — Electricity Usage endpoints
- [Origin Energy Account Balances API](https://apis.io/apis/origin-energy/origin-energy-energy-account-balances-api/) — Energy Account Balance endpoints
- [Origin Energy Account Billing API](https://apis.io/apis/origin-energy/origin-energy-energy-account-billing-api/) — Energy Account Billing endpoints
- [Origin Energy Accounts API](https://apis.io/apis/origin-energy/origin-energy-energy-accounts-api/) — Energy Account endpoints
- [Origin Energy Plans API](https://apis.io/apis/origin-energy/origin-energy-energy-plans-api/) — Energy Plan endpoints
- [Origin Energy External Client Healthcheck API](https://apis.io/apis/origin-energy/origin-energy-external-client-healthcheck-api/) — The external-client-healthcheck API from Origin Energy — 1 operation(s) for external-client-healthcheck.
- [Origin Energy External Events API](https://apis.io/apis/origin-energy/origin-energy-external-events-api/) — The external-events API from Origin Energy — 1 operation(s) for external-events.
- [Origin Energy Orders API](https://apis.io/apis/origin-energy/origin-energy-orders-api/) — APIs for placing and managing orders.
- [Origin Energy Post Account Import API](https://apis.io/apis/origin-energy/origin-energy-post-account-import-api/) — APIs for importing additional data after an account has been imported.
- [Origin Energy Post Business Import API](https://apis.io/apis/origin-energy/origin-energy-post-business-import-api/) — APIs for importing additional data after a business has been imported.
- [Origin Energy Query API](https://apis.io/apis/origin-energy/origin-energy-query-api/) — APIs for querying import status and retrieving data
- [Origin Energy Accounts API](https://apis.io/apis/origin-energy/origin-energy-accounts-api/) — The Accounts API from Origin Energy — 1 operation(s) for accounts.
- [Origin Energy Energetiq Public Key API](https://apis.io/apis/origin-energy/origin-energy-energetiq-public-key-api/) — The Energetiq Public Key API from Origin Energy — 1 operation(s) for energetiq public key.
- [Origin Energy Unbundled Network Charges API](https://apis.io/apis/origin-energy/origin-energy-unbundled-network-charges-api/) — The Unbundled Network Charges API from Origin Energy — 1 operation(s) for unbundled network charges.
- [Origin Energy Voice API](https://apis.io/apis/origin-energy/origin-energy-voice-api/) — The Voice API from Origin Energy — 2 operation(s) for voice.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Origin Energy Kraken External Events](https://apis.io/asyncapis/origin-energy/origin-energy-kraken-external-events/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [origin-energy](https://apis.io/servers/origin-energy/origin-energy/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Origin Energy Agentic Access](https://apis.io/agentic-access/origin-energy/origin-energy-agentic-access/)

#### JSON Schema (39)

The data models the API reads and writes.

- [AccountNote](https://apis.io/schemas/origin-energy/origin-energy-account-note/)
- [AccountTransferStatus](https://apis.io/schemas/origin-energy/origin-energy-account-transfer-status/)
- [AdHoc](https://apis.io/schemas/origin-energy/origin-energy-ad-hoc/)
- [AdHocResponse](https://apis.io/schemas/origin-energy/origin-energy-ad-hoc-response/)
- [BusinessImportProcess](https://apis.io/schemas/origin-energy/origin-energy-business-import-process/)
- [BusinessImportProcessCreation](https://apis.io/schemas/origin-energy/origin-energy-business-import-process-creation/)
- [BusinessPaymentInstruction](https://apis.io/schemas/origin-energy/origin-energy-business-payment-instruction/)
- [CreateAccountNotesResponse](https://apis.io/schemas/origin-energy/origin-energy-create-account-notes-response/)
- [CreateBusinessPaymentInstructionResponse](https://apis.io/schemas/origin-energy/origin-energy-create-business-payment-instruction-response/)
- [CreateOrUpdateAccountImportProcess](https://apis.io/schemas/origin-energy/origin-energy-create-or-update-account-import-process/)
- [CreatePaymentInstructionResponse](https://apis.io/schemas/origin-energy/origin-energy-create-payment-instruction-response/)
- [EnergyAccountDetailResponseV4](https://apis.io/schemas/origin-energy/origin-energy-energy-account-detail-response-v4/)
- [EnergyAccountListResponseV2](https://apis.io/schemas/origin-energy/origin-energy-energy-account-list-response-v2/)
- [EnergyBalanceListResponse](https://apis.io/schemas/origin-energy/origin-energy-energy-balance-list-response/)
- [EnergyBalanceResponse](https://apis.io/schemas/origin-energy/origin-energy-energy-balance-response/)
- [EnergyBillingListResponseV3](https://apis.io/schemas/origin-energy/origin-energy-energy-billing-list-response-v3/)
- [EnergyConcessionsResponse](https://apis.io/schemas/origin-energy/origin-energy-energy-concessions-response/)
- [EnergyDerDetailResponse](https://apis.io/schemas/origin-energy/origin-energy-energy-der-detail-response/)
- [EnergyDerListResponse](https://apis.io/schemas/origin-energy/origin-energy-energy-der-list-response/)
- [EnergyInvoiceListResponse](https://apis.io/schemas/origin-energy/origin-energy-energy-invoice-list-response/)
- [EnergyPaymentScheduleResponse](https://apis.io/schemas/origin-energy/origin-energy-energy-payment-schedule-response/)
- [EnergyPlanListResponse](https://apis.io/schemas/origin-energy/origin-energy-energy-plan-list-response/)
- [EnergyPlanResponseV3](https://apis.io/schemas/origin-energy/origin-energy-energy-plan-response-v3/)
- [EnergyServicePointDetailResponseV2](https://apis.io/schemas/origin-energy/origin-energy-energy-service-point-detail-response-v2/)
- [EnergyServicePointListResponseV2](https://apis.io/schemas/origin-energy/origin-energy-energy-service-point-list-response-v2/)
- …and 14 more published on APIs.io

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Origin Energy Context](https://apis.io/jsonld/origin-energy/origin-energy-context/)

#### Collections (5)

Postman and Open Collection request collections.

- [CDR Common API](https://apis.io/collections/origin-energy/open-consumer-data-standards-common-api/)
- [CDR Energy API](https://apis.io/collections/origin-energy/open-consumer-data-standards-energy-api/)
- [Kraken](https://apis.io/collections/origin-energy/open-origin-energy-kraken-data-import/)
- [Kraken](https://apis.io/collections/origin-energy/open-origin-energy-kraken-default/)
- [Kraken](https://apis.io/collections/origin-energy/open-origin-energy-kraken-orders/)

#### Overlays (27)

OpenAPI overlays, including conversational phrasing for each operation.

- [Origin Energy Account Import Overlay](https://apis.io/overlays/origin-energy/origin-energy-account-import-overlay/)
- [Origin Energy Accounts Overlay](https://apis.io/overlays/origin-energy/origin-energy-accounts-overlay/)
- [Origin Energy Business Import Overlay](https://apis.io/overlays/origin-energy/origin-energy-business-import-overlay/)
- [Origin Energy Cds Common Overlay](https://apis.io/overlays/origin-energy/origin-energy-cds-common-overlay/)
- [Origin Energy Cds Energy Overlay](https://apis.io/overlays/origin-energy/origin-energy-cds-energy-overlay/)
- [Origin Energy Data Holder Customers Overlay](https://apis.io/overlays/origin-energy/origin-energy-data-holder-customers-overlay/)
- [Origin Energy Data Holder Operations Overlay](https://apis.io/overlays/origin-energy/origin-energy-data-holder-operations-overlay/)
- [Origin Energy Data Import Overlay](https://apis.io/overlays/origin-energy/origin-energy-data-import-overlay/)
- [Origin Energy Distributed Energy Resources Overlay](https://apis.io/overlays/origin-energy/origin-energy-distributed-energy-resources-overlay/)
- [Origin Energy Electricity Service Points Overlay](https://apis.io/overlays/origin-energy/origin-energy-electricity-service-points-overlay/)
- [Origin Energy Electricity Usage Overlay](https://apis.io/overlays/origin-energy/origin-energy-electricity-usage-overlay/)
- [Origin Energy Energetiq Public Key Overlay](https://apis.io/overlays/origin-energy/origin-energy-energetiq-public-key-overlay/)
- [Origin Energy Energy Account Balances Overlay](https://apis.io/overlays/origin-energy/origin-energy-energy-account-balances-overlay/)
- [Origin Energy Energy Account Billing Overlay](https://apis.io/overlays/origin-energy/origin-energy-energy-account-billing-overlay/)
- [Origin Energy Energy Accounts Overlay](https://apis.io/overlays/origin-energy/origin-energy-energy-accounts-overlay/)
- [Origin Energy Energy Plans Overlay](https://apis.io/overlays/origin-energy/origin-energy-energy-plans-overlay/)
- [Origin Energy External Client Healthcheck Overlay](https://apis.io/overlays/origin-energy/origin-energy-external-client-healthcheck-overlay/)
- [Origin Energy External Events Overlay](https://apis.io/overlays/origin-energy/origin-energy-external-events-overlay/)
- [Origin Energy Kraken Data Import Overlay](https://apis.io/overlays/origin-energy/origin-energy-kraken-data-import-overlay/)
- [Origin Energy Kraken Default Overlay](https://apis.io/overlays/origin-energy/origin-energy-kraken-default-overlay/)
- [Origin Energy Kraken Orders Overlay](https://apis.io/overlays/origin-energy/origin-energy-kraken-orders-overlay/)
- [Origin Energy Orders Overlay](https://apis.io/overlays/origin-energy/origin-energy-orders-overlay/)
- [Origin Energy Post Account Import Overlay](https://apis.io/overlays/origin-energy/origin-energy-post-account-import-overlay/)
- [Origin Energy Post Business Import Overlay](https://apis.io/overlays/origin-energy/origin-energy-post-business-import-overlay/)
- [Origin Energy Query Overlay](https://apis.io/overlays/origin-energy/origin-energy-query-overlay/)
- …and 2 more published on APIs.io

#### Governance rules (1)

Spectral rulesets for the provider's contracts.

- [Origin Energy API Rules](https://apis.io/rules/origin-energy/origin-energy-rules/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Origin Energy Authentication](https://apis.io/security/origin-energy/origin-energy-authentication/)
- [Origin Energy Domain Security](https://apis.io/security/origin-energy/origin-energy-domain-security/)
- [Origin Energy Vulnerability Disclosure](https://apis.io/security/origin-energy/origin-energy-vulnerability-disclosure/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Origin Energy Scopes](https://apis.io/scopes/origin-energy/origin-energy-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Origin Energy Plans Pricing](https://apis.io/plans/origin-energy/origin-energy-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Origin Energy Rate Limits](https://apis.io/rate-limits/origin-energy/origin-energy-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.originenergy.com.au/)
- [Documentation](https://developer.origin-kraken.energy/)
- [Getting started](https://developer.origin-kraken.energy/graphql/guides/basics/)
- [API reference](https://developer.origin-kraken.energy/graphql/reference/)
- [Changelog](https://developer.origin-kraken.energy/announcements/)
- [Security](https://bugcrowd.com/engagements/originenergy-og1)
- [GitHub](https://github.com/origin-energy)
- [Status](https://public.mydata.cdr.originenergy.com.au/cds-au/v1/discovery/status)

## API Evangelist rating

**Kin Score 59.6** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 78.6 |
| Contract quality | 70.7 |
| Contract governance | 35.6 |
| Operational transparency | 84.2 |
| Developer ergonomics | 53.0 |
| Access clarity | 0.0 |

**Agent readiness 40.3** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | served (partial credit) |
| Idempotency | documented (partial credit) |
| Error Semantics | verified |
| OpenAPI Examples | partial |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | — |
| Operation Distinctiveness | distinct |

**Regulatory alignment 39.3** — Energy & Utilities

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/origin-energy/](https://apis.io/providers/origin-energy/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Origin Energy: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/origin-energy/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
