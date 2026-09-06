# Autonomous Micro Business Control Plane

## Mission
Operate a portfolio of small internet businesses with minimal Founder operating time. Agents perform research, validation, implementation preparation, operation analysis, and optimization. Founder performs only material decisions and unavoidable account/payment/permission actions.

## Separation of concerns

This repository is the business control plane. Do not place product source code here after migration.

- ChatGPT lanes A/B/C: DISCOVER -> ASSESS -> VALIDATE and BUILD/LAUNCH gate preparation.
- Lane M: Portfolio Governor only. It allocates attention, evaluates economics, raises Founder Gates, and dispatches product work. It must not become a sequential implementation bottleneck.
- Codex bootstrap agent: creates/bootstrap product repositories after BUILD approval.
- Codex product agents: independently improve assigned products within explicit constraints.

## Durable coordination

GitHub state is authoritative across agents. Do not rely on chat/thread memory as the only handoff mechanism.

Canonical state:
- `portfolio/runtime/`
- `portfolio/products/`
- `portfolio/registry/`
- `portfolio/history/`
- `work-orders/`

## Product repository boundary

At BUILD approval, create a standalone repo named `mb-###-<slug>`.

Product repo owns:
- code
- tests
- CI/CD
- deployment
- technical SEO implementation
- analytics instrumentation
- product-local AGENTS.md

Control plane owns:
- why the product exists
- lifecycle stage
- economics
- priorities
- experiment decisions
- Founder Gates
- durable history

## Autonomy limits

Codex product agents may autonomously perform zero-cost, reversible technical/product improvements when they do not materially change business/legal/privacy risk.

Founder approval is required before:
- paid or recurring spend
- new paid API/service/domain
- material privacy/data expansion
- material legal/platform risk
- BUILD or LAUNCH
- major monetization model change
- irreversible migration
- KILL/SCALE decision when material

## Work-order protocol

A work order is executable only when `status=READY` and it identifies a product repo or is a bootstrap order after Founder BUILD approval.

Codex must return evidence: changed refs/PR, tests, deployment result when applicable, blockers, and any proposed Founder Gate.

## Portfolio Governor behavior

Lane M should not process products serially as an operator. It should:
1. read product manifests and recent work results,
2. rank opportunities by expected value / cost / risk,
3. mark executable work READY,
4. let independent Codex product agents run,
5. review outcomes and reallocate attention,
6. surface only material Founder decisions.
