---
name: Compare Origin Energy retail electricity and gas plans
description: Pull Origin Energy's published electricity and gas plan reference data anonymously from the
  AER Energy Made Easy CDR gateway and read a single plan's full tariff detail. This is the only Origin
  Energy surface reachable with no credentials at all.
api: openapi/consumer-data-standards-energy-api-openapi.json
operations:
- listEnergyPlans
- getEnergyPlanDetail
generated: '2026-07-27'
method: generated
---

# Compare Origin Energy retail plans

## What this is
Origin Energy's retail plan reference data is published under the Consumer Data Standards **Get Generic Plans** and **Get Generic Plan Detail** endpoints. It is *not* served from an Origin host — Origin's own public CDR base URI returns 404 for `/cds-au/v1/energy/plans`. It is served by the Australian Energy Regulator's Energy Made Easy CDR gateway under Origin's CDR obligation.

- Base URL: `https://cdr.energymadeeasy.gov.au/origin/cds-au/v1`
- Auth: **none**. No key, no signup, no consent.
- Verified 2026-07-27: `meta.totalRecords` was 3,595.

## Rules before you call
1. **Send `x-v`.** Every Consumer Data Standards endpoint requires the `x-v` request header. Omitting it returns HTTP 400.
2. **The two endpoints are on different versions.** `listEnergyPlans` served `x-v: 1`. `getEnergyPlanDetail` requires `x-v: 3` — sending `x-v: 1` returns HTTP 406 with `urn:au-cds:error:cds-all:Header/UnsupportedVersion` and the detail `Header x-v lower than minimum supported [x-v=1, min=3]`. Do not assume one version across the surface; negotiate per endpoint and read the response `x-v`.
3. **Pagination is page-number, not cursor.** Use `page` and `page-size` (default 25). Read `meta.totalRecords` and `meta.totalPages`, and follow `links.next` rather than incrementing blindly.
4. **Set `x-fapi-interaction-id`** to an RFC 4122 UUID so the gateway echoes a correlation id you can log.

## Steps
1. `listEnergyPlans` — `GET /energy/plans` with `x-v: 1`. Filter with `type` (STANDING / MARKET / REGULATED), `fuelType` (ELECTRICITY / GAS / DUAL) and `effective`. Page through with `page` / `page-size`.
2. For each record you care about, take `planId` (observed form: `ORI724759MRE14@EME` — an Origin plan code suffixed `@EME` for Energy Made Easy).
3. `getEnergyPlanDetail` — `GET /energy/plans/{planId}` with `x-v: 3`. This returns the full tariff structure: rates, discounts, incentives, fees, solar feed-in and the distributor.

## Errors
The envelope is the CDS `ResponseErrorListV2` shape: `errors[]` of `{code, title, detail, meta}` with `urn:au-cds:` codes. See `errors/origin-energy-problem-types.yml`.

## What this skill cannot do
It cannot read any individual customer's usage, billing or account data. That requires CDR accreditation — see `origin-energy-cdr-consented-energy-data.md`.
