# Autonomous Micro Business — Control Plane v2 Migration

## Target architecture

- `autonomous-micro-business` becomes the orchestration/control-plane repository.
- Each product receives its own repository at BUILD approval: `mb-###-<slug>`.
- Orchestration repository owns only business state, lifecycle, history, work orders, and agent policy.
- Product repositories own source code, tests, CI/CD, deployment, analytics instrumentation, and technical implementation.
- Lane M becomes Portfolio Governor. Product-level execution is delegated to Codex product agents.

## Lifecycle boundary

DISCOVER -> ASSESS -> VALIDATE: orchestration repo only.

Founder BUILD approval -> allocate/confirm MB-ID -> create product repo -> bootstrap template -> Codex BUILD work order.

LAUNCH -> product remains in product repo; orchestration records product state and Lane M owns portfolio governance.

## Codex dispatch contract

GitHub is the durable handoff boundary between ChatGPT lanes and Codex.

1. Orchestrator writes a canonical product/work-order record.
2. A `codex-ready` GitHub issue or work-order record is created.
3. Codex bootstrap/product agent executes within the designated product repo.
4. Codex returns PR/test/deploy evidence.
5. Orchestrator updates canonical state/history.

## Repository ownership rules

### Orchestration repo

- `portfolio/runtime/*`
- `portfolio/products/*`
- `portfolio/registry/*`
- `portfolio/history/*`
- `work-orders/*`
- `system/*`
- `playbooks/*`
- `templates/*`
- root `AGENTS.md`

### Product repo

- source code
- tests
- deployment config
- product-specific `AGENTS.md`
- technical docs
- analytics instrumentation

## Migration rule for current repository

`LeeJx12/fcc-preflight-test` remains intact until all live products have been copied into standalone repositories and their live deployments are verified. Then archive it; do not delete history.

No existing product is returned to an incubation lane during migration.

## Founder gates

Founder approval remains required for BUILD, LAUNCH, paid/recurring spend, material legal/privacy/platform risk, major irreversible decisions, and KILL/SCALE decisions where material.
