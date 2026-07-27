---
name: Retrieve an Origin Energy customer's energy data under Consumer Data Right consent
description: Operate the Consumer Data Right energy APIs against Origin Energy's data holder endpoint
  as an accredited data recipient with a consumer's consent — accounts, balances, invoices, billing, concessions,
  payment schedules, electricity service points, usage and DER.
api: openapi/consumer-data-standards-energy-api-openapi.json
operations:
- listEnergyAccounts
- getEnergyAccountDetail
- getEnergyAccountBalance
- listEnergyAccountBalancesBulk
- getEnergyAccountInvoices
- getBillingForEnergyAccount
- getEnergyAccountConcessions
- getEnergyAccountPaymentSchedule
- listElectricityServicePoints
- getElectricityServicePointDetail
- getElectricityServicePointUsage
- listElectricityUsageForServicePoints
- getElectricityDERForServicePoint
- getCustomer
- getStatus
- getOutages
generated: '2026-07-27'
method: generated
---

# Retrieve Origin Energy customer data under Consumer Data Right consent

## Before anything: you cannot call this without accreditation
- Resource host: `https://api.mydata.cdr.originenergy.com.au`
- The host completes a TLS handshake and then **resets the connection** if no client certificate is presented. Its certificate (`OU=Consumer Data Right, O=Origin Energy, CN=api.mydata.cdr.originenergy.com.au, C=AU`) is issued by the ACCC's `CDR Intermediate CA 2025`. Verified 2026-07-27.
- To get a client certificate you must be an accredited person under the Consumer Data Right: apply to the ACCC, meet the CDR Rule Schedule 2 information-security controls, be listed on the CDR Register, obtain certificates from the CDR Certificate Authority, then collect the consumer's explicit consent and complete the authorisation flow with Origin. There is no sandbox key and no self-serve tier.
- See `authentication/origin-energy-authentication.yml`.

## Headers on every call
`x-v` (mandatory), optionally `x-min-v`, `x-fapi-interaction-id` (RFC 4122 UUID correlation id, echoed back), and where the consumer is present `x-fapi-auth-date`, `x-fapi-customer-ip-address` and `x-cds-client-headers`.

## Check the surface is up first (no credentials needed)
1. `getStatus` — `GET https://public.mydata.cdr.originenergy.com.au/cds-au/v1/discovery/status` with `x-v: 1`. Returns `{"data":{"status":"OK","explanation":"All services operational"}}`.
2. `getOutages` — `GET .../discovery/outages`. Returns planned outage windows.
Both are anonymous. Do not start a consented pull without checking them.

## Account flow
3. `listEnergyAccounts` — `GET /energy/accounts`. Filter with `open-status` (OPEN / CLOSED / ALL). Page with `page` / `page-size`.
4. `getEnergyAccountDetail` — `GET /energy/accounts/{accountId}` for plan, tariff and service point linkage.
5. `getEnergyAccountBalance` — single account; or `listEnergyAccountBalancesBulk` for every consented account in one call. Prefer the bulk form: it is one request against the consumer's whole consent rather than N.
6. `getEnergyAccountInvoices`, `getBillingForEnergyAccount` — invoices and billing transactions. Both accept `oldest-date` / `newest-date`.
7. `getEnergyAccountConcessions`, `getEnergyAccountPaymentSchedule` — concessions and payment arrangements.

## Metering and generation flow
8. `listElectricityServicePoints` — `GET /energy/electricity/servicepoints`. `servicePointId` is a tokenised NMI.
9. `getElectricityServicePointDetail` — meter and register detail for one service point.
10. `getElectricityServicePointUsage` — interval reads for one service point; use `oldest-date` / `newest-date` and `interval-reads` (NONE / MIN_30 / FULL). Or `listElectricityUsageForServicePoints` (POST) to request a specific set of service points in one call.
11. `getElectricityDERForServicePoint` — distributed energy resource records (solar, battery, inverter).

## Conventions
- Pagination: `page` / `page-size`, default 25; read `meta.totalRecords` and follow `links.next`.
- Versioning: per endpoint via `x-v`. Version mismatches return HTTP 406 `urn:au-cds:error:cds-all:Header/UnsupportedVersion`.
- Errors: `ResponseErrorListV2` — `errors[]` of `{code, title, detail, meta}`. See `errors/origin-energy-problem-types.yml`.
- There is no idempotency key on this surface; every operation is a read (the POST forms are filter-by-body reads, not writes).

## Scope boundary
This contract is published by the Data Standards Body, not by Origin. Origin implements it; it does not author it. Do not treat the spec in `openapi/` as an Origin artifact.
