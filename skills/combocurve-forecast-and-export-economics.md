---
name: Forecast wells and export economics
description: Read forecasts and forecast volumes for a project, then trigger an economics export job in ComboCurve.
api: openapi/combocurve-openapi.yml
operations: [get-forecasts, post-forecasts, get-forecast-monthly-volumes, get-econ-runs, post-exports]
---

# Forecast wells and export economics

Reads a project's forecasts and volumes and exports economic results. Grounded in real ComboCurve REST API operations.

## Auth
Both headers required (`Authorization` signed JWT bearer + `x-api-key`) against `https://api.combocurve.com`.

## Steps
1. **List forecasts** — `get-forecasts` (`GET /v1/projects/{projectId}/forecasts`) to find the forecast for a project.
2. **Create a forecast** — `post-forecasts` (`POST /v1/projects/{projectId}/forecasts`) when one does not exist.
3. **Read forecast volumes** — `get-forecast-monthly-volumes` (`GET /v1/projects/{projectId}/forecasts/{forecastId}/monthly-volumes`) for monthly forecast output (daily via `get-forecast-daily-volumes`).
4. **Inspect econ runs** — `get-econ-runs` (`GET /v1/projects/{projectId}/scenarios/{scenarioId}/econ-runs`) to find completed economics runs.
5. **Export** — `post-exports` (`POST /v1/exports`) for v1, or the v2 async export jobs (`POST /v2/exports/econ-monthly`, `/v2/exports/econ-one-liners`) then poll the returned `jobId` at `GET /v2/exports/econ-monthly/{jobId}`.

## Rules
- v2 exports are asynchronous — poll the job status endpoint until complete.
- Paginate reads with `skip`/`take`/`cursor`; sort with the `sort` param.
- Respect the 800 read / 200 write per-minute limits; handle HTTP 429 with backoff.
