# Origin Energy (origin-energy)

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

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/origin-energy/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/origin-energy/refs/heads/main/apis.yml)

**URL:** [https://www.originenergy.com.au/](https://www.originenergy.com.au/)

## Tags

- Energy
- Australia
- Utilities
- Electricity
- Gas
- Energy Retail
- Consumer Data Right
- Smart Metering
- Solar
- DER
- Demand Response
- Energy Markets

## Timestamps

- **Created:** 2026-07-27
- **Modified:** 2026-07-27

## Mandate

| Field | Value |
|-------|-------|
| Regime | Consumer Data Right, energy sector (`cdr-energy`) |
| Status | `live-implemented` — verified, not claimed |
| Data standard | Consumer Data Standards Australia, CDR Energy API 1.36.0 |
| Consumer data API | Yes — accredited data recipients only, on consumer consent |
| Open market data | No — Origin publishes none; AEMO publishes NEM data |
| Access gate | `accredited-only` (CDR) / `customer-account-required` (Kraken) |

Verified on 2026-07-27 by three independent technical checks rather than by any Origin claim: a CDR Register entry (`https://api.cdr.gov.au/cdr-register/v1/energy/data-holders/brands/summary`, HTTP 200) naming Origin Energy with `publicBaseUri` `https://public.mydata.cdr.originenergy.com.au`; anonymous HTTP 200 responses from the Consumer Data Standards discovery endpoints on that base URI; and a TLS certificate on `api.mydata.cdr.originenergy.com.au` issued by *CDR Intermediate CA 2025* under the Australian Competition and Consumer Commission's CDR Root CA, with the connection reset when no client certificate is presented.

## APIs

### Origin Energy CDR Energy API

Origin's Consumer Data Right resource endpoint, serving the Consumer Data Standards energy APIs to accredited data recipients over mutual TLS.

- **Human URL:** [https://consumerdatastandardsaustralia.github.io/standards/#energy-apis](https://consumerdatastandardsaustralia.github.io/standards/#energy-apis)
- **Base URL:** `https://api.mydata.cdr.originenergy.com.au`

#### Properties

- [OpenAPI](openapi/consumer-data-standards-energy-api-openapi.json) — CDR Energy API 1.36.0, published by the Data Standards Body
- [OpenAPI](openapi/consumer-data-standards-common-api-openapi.json) — CDR Common API 1.36.0
- [Documentation](https://consumerdatastandardsaustralia.github.io/standards/#energy-apis)
- [Registration](https://www.cdr.gov.au/for-providers/accreditation)

### Origin Energy CDR Public Discovery API

The only Origin-hosted surface reachable without credentials. Operational metadata only.

- **Human URL:** [https://consumerdatastandardsaustralia.github.io/standards/#discovery-apis](https://consumerdatastandardsaustralia.github.io/standards/#discovery-apis)
- **Base URL:** `https://public.mydata.cdr.originenergy.com.au/cds-au/v1`

### Origin Energy Plan Reference Data API (AER Energy Made Easy)

3,595 Origin electricity and gas plans, anonymously retrievable — from a `.gov.au` host, not an Origin one.

- **Human URL:** [https://www.energymadeeasy.gov.au/](https://www.energymadeeasy.gov.au/)
- **Base URL:** `https://cdr.energymadeeasy.gov.au/origin/cds-au/v1`

### Origin Energy Kraken REST API

- **Human URL:** [https://developer.origin-kraken.energy/rest/](https://developer.origin-kraken.energy/rest/)
- **Base URL:** `https://api.origin-kraken.energy/v1`

#### Properties

- [OpenAPI](openapi/origin-energy-kraken-default-openapi.yml) — 9 paths
- [OpenAPI](openapi/origin-energy-kraken-data-import-openapi.yml) — 16 paths
- [OpenAPI](openapi/origin-energy-kraken-orders-openapi.yml) — 2 paths
- [API Reference](https://developer.origin-kraken.energy/rest/reference/)
- [Getting Started](https://developer.origin-kraken.energy/rest/guides/api-basics/)

### Origin Energy Kraken GraphQL API

- **Human URL:** [https://developer.origin-kraken.energy/graphql/](https://developer.origin-kraken.energy/graphql/)
- **Base URL:** `https://api.origin-kraken.energy/v1/graphql/`

### Origin Energy Kraken External Events

- **Human URL:** [https://developer.origin-kraken.energy/events/](https://developer.origin-kraken.energy/events/)

### Origin Energy Kraken Authorization Server

- **Human URL:** [https://developer.origin-kraken.energy/graphql/guides/basics/](https://developer.origin-kraken.energy/graphql/guides/basics/)
- **Base URL:** `https://auth.origin-kraken.energy`

#### Properties

- [OpenID Configuration](well-known/origin-energy-kraken-openid-configuration.json) — 113 scopes, no dynamic client registration

## Common Properties

- [Website](https://www.originenergy.com.au/)
- [Developer Portal](https://developer.origin-kraken.energy/)
- [API Announcements](https://developer.origin-kraken.energy/announcements/)
- [Blog](https://www.originenergy.com.au/blog/)
- [GitHub Organization](https://github.com/origin-energy)
- [LinkedIn](https://www.linkedin.com/company/origin-energy)
- [Consumer Data Right](https://www.cdr.gov.au/)

## Features

| Name | Description |
|------|-------------|
| Electricity and Gas Retail | Sells electricity and natural gas to residential and business customers across the National Electricity Market and Western Australian gas market. |
| Generation and LNG | Operates the Eraring Power Station, gas-fired peaking plant and renewable assets, and holds an interest in Australia Pacific LNG. |
| Origin Loop Virtual Power Plant | Aggregates customer solar, batteries and connected devices into one of Australia's largest virtual power plants for demand response and grid services. |
| Kraken Retail Platform | Runs its retail billing, CRM and customer operations on Octopus Energy's Kraken platform, in which Origin holds an equity stake. |
| Consumer Data Right Data Holding | Designated energy data holder under the Consumer Data Right, sharing customer usage, billing and DER data with accredited data recipients on consumer consent. |

## Use Cases

| Name | Description |
|------|-------------|
| Consented Energy Data Sharing | An accredited CDR data recipient obtains an Origin customer's usage, billing and service point data with that customer's consent. |
| Retail Plan Comparison | Anyone can pull Origin's 3,595 published plans anonymously from the AER Energy Made Easy CDR gateway. |
| Partner Platform Integration | Origin partner organisations integrate with the Kraken REST and GraphQL APIs for account, payment, order and meter reading workflows. |
| Customer Migration | The Kraken data-import REST API ingests accounts, historical statements, transactions and payment instructions during platform migrations. |

## Review

See [review.yml](review.yml) for the full probe log — every URL requested, every HTTP status observed, the mandate verification chain, the consumer-data versus market-data split, the access gate, and the auth model.
