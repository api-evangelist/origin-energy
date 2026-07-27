---
name: Schedule and track an order on the Origin Energy Kraken platform
description: Submit an order to Origin Energy's Kraken order-management API and poll it to completion,
  handling the asynchronous validation and error model correctly.
api: openapi/origin-energy-kraken-orders-openapi.yml
operations:
- V2 Schedule Order
- V2 Order Status
generated: '2026-07-27'
method: generated
---

# Schedule and track a Kraken order

## Access
- Base URL: `https://api.origin-kraken.energy/`
- Auth: `Authorization` bearer token from `https://auth.origin-kraken.energy/`, or the `DataImportViewerAPIKeyAuthentication` key Origin issued you.

## Steps
1. `V2 Schedule Order` — `POST /v2/orders/`. The payload carries an `external_order_id` you choose, plus `accounts[]`, `businesses[]` and `order_lines[]` (for example a `CONTRACT_RENEWAL` line targeting a business with a contract block). A 201 means the order was **scheduled**, not completed — Kraken validates the payload and creates an order-management task to run asynchronously.
2. `V2 Order Status` — `GET /v2/orders/{external_order_id}/`. Poll it. The response carries `status` (`PROCESSED` / `ERRORED`), `created_at`, `modified_at`, `latest_error` and `latest_event` (`ORDER_PROCESS_SUCCEEDED` / `ORDER_PROCESS_ERRORED`).

## The idempotency contract you actually get
`external_order_id` is the de-duplication key. Re-submitting an order whose id has already been processed returns HTTP 400 with `order_process_already_processed` and the detail `The order with external order ID <id> has already been processed.` Treat that as a success signal on retry, not as a failure — it is the closest thing this surface has to an idempotent create.

## Errors
- 400 `order_process_failed_validation` with `domain: order_process` — the payload failed validation. The response details the failing fields; fix them against the schema rather than retrying.
- 404 `not_found` — no order process exists for that `external_order_id`. If you just scheduled it, you polled too early.
- 500 — the order process has no status set for the given id.
See `errors/origin-energy-problem-types.yml`.
