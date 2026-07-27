---
name: Migrate customer accounts onto the Origin Energy Kraken platform
description: Use the Kraken data-import REST API to validate, schedule and track the import of customer
  accounts, businesses, historical statements, transactions, notes and payment instructions onto Origin
  Energy's Kraken tenancy.
api: openapi/origin-energy-kraken-data-import-openapi.yml
operations:
- V2 Validate Account
- V2 Schedule Account Creation
- V2 Account Import Status
- V1 Validate Account
- V1 Create Or Update Account Import Process
- V1 Process Account Import Process
- V1 Get Account Transfer Status
- V1 Get Pending Account Import Processes
- V1 Get All Account Import Processes
- V1 Get Imported Accounts
- V1 Create Business
- V1 Create Business Payment Instruction
- V1 Create Payment Instruction
- V1 Create Historical Statements
- V1 Create Transactions
- V1 Create Account Notes
generated: '2026-07-27'
method: generated
---

# Migrate customer accounts onto Origin Energy's Kraken platform

## Access
- Base URL: `https://api.origin-kraken.energy/v1/`
- Auth: `Authorization` header carrying a bearer token from `https://auth.origin-kraken.energy/`. The same token authenticates GraphQL and REST. Clients are provisioned by Origin out of band — the discovery document advertises no registration endpoint.
- The specs also declare `DataImportViewerAPIKeyAuthentication` (a `Token `-prefixed key). Use whichever Origin issued you.

## Prefer the v2 path
The v2 operations are the current import surface; the v1 ones are the older per-step process.

1. `V2 Validate Account` — `POST /v2/data-import/accounts/validate/`. Dry-run the payload before you schedule anything. Fix every validation error here, not after scheduling.
2. `V2 Schedule Account Creation` — `POST /v2/data-import/accounts/`. Schedules the import asynchronously and returns immediately.
3. `V2 Account Import Status` — `GET /v2/data-import/accounts/{import_supplier_code}/{external_identifier}/`. Poll for `status` plus `latest_event` and `latest_error`.

## The v1 path (still published)
4. `V1 Validate Account`, then `V1 Create Or Update Account Import Process`, then `V1 Process Account Import Process` to execute it.
5. Track with `V1 Get Account Transfer Status`, `V1 Get Pending Account Import Processes`, `V1 Get All Account Import Processes`, `V1 Get Imported Accounts` — all keyed on `import_supplier_code`.

## Attaching the rest of the customer record
6. `V1 Create Business` and `V1 Create Business Payment Instruction` for business customers.
7. `V1 Create Payment Instruction` for direct debit / card instructions.
8. `V1 Create Historical Statements` and `V1 Create Transactions` to carry the customer's financial history across.
9. `V1 Create Account Notes` for free-text account notes.

## Rules
- **Datetimes are ISO 8601** and you should always include a timezone. If you omit it the platform defaults to `Europe/London` — a Kraken platform default, not an Australian one. For an AU tenancy that will silently shift dates. This is the single most common error in this flow.
- The import is **asynchronous**. Scheduling returns 201 with no result body; the outcome only appears on the status endpoint.
- One import operation is rate limited (a 429 is declared on the spec). Back off rather than retrying tightly.
- Errors are a flat JSON object: `{detail, code, domain}`, or `non_field_errors` for payload-level failures. See `errors/origin-energy-problem-types.yml`.
- There is **no idempotency key on the REST surface**. Guard against double submission with your own `external_identifier` / `import_supplier_code` uniqueness before you call.
