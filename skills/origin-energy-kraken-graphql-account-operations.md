---
name: Operate Origin Energy customer accounts through the Kraken GraphQL API
description: Query and mutate Origin Energy retail accounts, meter points, readings, payments and quotes
  through the Kraken GraphQL API, respecting its complexity budget, cursor pagination and idempotency-key
  contract.
api: graphql/origin-energy-kraken.graphql
operations: []
graphql_fields:
- accountsSearch
- accountReference
- accountUser
- meterPoint
- electricityMeterReadings
- estimatedSupplyPointReadings
- createElectricitySelfMeterReads
- createGasSelfMeterReads
- createPaymentSchedule
- updatePaymentSchedule
- createPaymentExtension
- offerPaymentPlan
- acceptPaymentPlan
- createCentrepayDeduction
- createElectricityQuote
- createGasQuote
- availableProducts
- initiateProductSwitch
- processHouseMoveInElectricity
- triggerElectricityHouseMoveOut
- propertyMoveOut
- createConcession
- createHardshipAgreement
- makePaymentWithNewCard
- makePaymentWithSavedCard
- setupPaymentDetails
generated: '2026-07-27'
method: generated
---

# Operate Origin Energy accounts through Kraken GraphQL

## The contract
- Endpoint: `https://api.origin-kraken.energy/v1/graphql/`
- SDL: `graphql/origin-energy-kraken.graphql` — harvested by anonymous introspection on 2026-07-27. 2,407 types, 187 queries, 374 mutations. **Introspection is open; data is not.**
- Auth: `Authorization` header with a bearer token from `https://auth.origin-kraken.energy/`. Without it every data field returns `KT-CT-1112`. Scope list: `scopes/origin-energy-scopes.yml` (113 scopes).
- This is where the real capability lives. The REST surface has 27 operations, of which only 5 have any GraphQL analogue — see `mcp/origin-energy-tool-crosswalk.yml`.

## Budget your query before you send it
This API rejects expensive queries rather than throttling them.
- Complexity limit **550 per request** — exceeding it returns `KT-CT-1188`.
- Node limit **100,000 per request** — `KT-CT-1189`.
- Hourly points allowance: 50,000 (account user), 100,000 (organisation), 300,000 (OAuth application).
- Per-IP/per-user request throttling returns `KT-CT-1199`.
Ask for the fields you need. Do not select whole connections speculatively.

## Pagination
Relay cursor connections. Use `first` (**must be less than 100**) and `after`; read `pageInfo.startCursor` / `endCursor` / `hasNextPage`. Note that `hasPreviousPage` is `false` when paginating forward with `after` — do not use it as a loop guard. Some queries accept only `first` and return `KT-AU-5410` otherwise.

## Idempotency — use it
17 mutation input objects accept an `idempotencyKey` (a `UUID` or `String`, required on some, optional on others), including `CollectPaymentInput`, `CompleteStandalonePaymentInput`, `RefundPaymentInput`, `CreatePaymentActionIntentInput`, `TriggerStandalonePaymentRequestInput`, `CreateScheduledTransactionsInput`, `LoyaltyPointLedgerEntryInput`, `EnrollmentInput` and `LeaveSupplierInput`. **Always set it on any money-moving mutation.** Re-using a key on a ledger entry returns `KT-CT-9221` (`Idempotency key already used on ledger entry`) — which is the guard working, not an error to retry through. Full list in `conventions/origin-energy-conventions.yml`.

## Representative flows (all field names verified against the live schema)
- **Read an account**: `accountsSearch` / `accountReference` / `accountUser`, then walk the ledger and billing fields on `AccountType`.
- **Metering**: `meterPoint`, `electricityMeterReadings`, `estimatedSupplyPointReadings`; submit customer reads with `createElectricitySelfMeterReads` / `createGasSelfMeterReads` (scope `submit:meter-readings`).
- **Payments**: `createPaymentSchedule`, `updatePaymentSchedule`, `createPaymentExtension`, `offerPaymentPlan` / `acceptPaymentPlan`, `createCentrepayDeduction`. Avoid `makePaymentWithNewCard`, `makePaymentWithSavedCard` and `setupPaymentDetails` — all three are `@deprecated` legacy-financials mutations.
- **Quoting and switching**: `createElectricityQuote`, `createGasQuote`, `availableProducts`, `initiateProductSwitch`.
- **House moves**: `processHouseMoveInElectricity`, `triggerElectricityHouseMoveOut`, `propertyMoveOut`.
- **Concessions and hardship**: `createConcession`, `createHardshipAgreement`.

## Errors
`errors[]` with `extensions.errorType` (`APPLICATION` / `VALIDATION` / `NOT_FOUND` / `AUTHORIZATION` / `SERVICE_AVAILABILITY`), `extensions.errorCode` (`KT-<COUNTRY>-<NUMBER>`, where `CT` means core and `AU` is the Australian tenancy) and `extensions.errorDescription`. 878 codes with messages are catalogued in `errors/origin-energy-error-codes.yml`.

## Deprecations
Deprecated fields carry both dates in the schema: *"Marked as deprecated on [DATE]. Scheduled for removal on or after [FUTURE DATE]"*, typically 2–3 months apart. There is no `Sunset` header — watch `https://developer.origin-kraken.energy/graphql/changelog/` and the announcements feed. Current deprecated root fields are listed in `lifecycle/origin-energy-lifecycle.yml`.
