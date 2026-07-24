---
name: Import wells and production data
description: Create/upsert well headers in ComboCurve and attach daily and monthly production volumes.
api: openapi/combocurve-openapi.yml
operations: [post-wells, get-wells, put-wells, post-daily-productions, post-monthly-productions]
---

# Import wells and production data

Loads a batch of wells into ComboCurve and attaches their production history. Grounded in real ComboCurve REST API v1 operations.

## Auth
Every request needs BOTH headers (see `authentication/combocurve-authentication.yml`):
- `Authorization: Bearer <signed JWT>` — signed from your Service Account Key.
- `x-api-key: <company API key>` — from the ComboCurve API & Sync page.
Base URL: `https://api.combocurve.com`. Content-Type `application/json`.

## Steps
1. **Insert wells** — `post-wells` (`POST /v1/wells`). Send an array of well documents; key each with `dataSource` + `chosenID`. Keep the body under 24 MB and each string field under 16 KB.
2. **Verify / list** — `get-wells` (`GET /v1/wells`) with `skip`/`take` (default take=25) and filters like `api14`, `chosenID`, `state`, `county`. Use the returned `cursor` for the next page.
3. **Update headers** — `put-wells` (`PUT /v1/wells`) to upsert changed fields on existing wells (matched on well identifiers).
4. **Attach daily production** — `post-daily-productions` (`POST /v1/daily-productions`) with an array of daily volume rows referencing each well.
5. **Attach monthly production** — `post-monthly-productions` (`POST /v1/monthly-productions`) for monthly volumes.

## Rules
- Writes are throttled to 200 requests/min (reads 800/min); on HTTP 429 back off and batch.
- No idempotency-key header; upserts are keyed on well identifier fields — dedupe before sending.
- Errors are standard HTTP status codes with a JSON body (see `errors/combocurve-problem-types.yml`).
