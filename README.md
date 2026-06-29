# release-pipeline-demo

Mock CI/CD release pipeline for demoing the GitHub Actions UI.

**Everything is simulated** (`echo`/`sleep`) — nothing is built, scanned, or deployed.

Flow:

```
build + unit/integration/lint/sec/codegen/review/api checks (parallel)
        │
        ▼
deploy → staging   ⏸ MANUAL APPROVAL
        │
        ▼
smoke · staging (api-gateway · agent · ingestion-worker · web)
        │
        ▼
promote → prod     ⏸ MANUAL APPROVAL
        ├──────────────┐
        ▼              ▼
deploy → prod-us   deploy → prod-eu
        │              │
        ▼              ▼
smoke · prod-us    smoke · prod-eu
(per service)      (per service)
```
