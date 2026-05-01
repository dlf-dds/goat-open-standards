# Status — per-standard maturity

Maturity tiers per [goat integrations/INDEX.md](https://github.com/dlf-dds/DesertBreadBird/blob/main/docs/integrations/INDEX.md):

| Tier | Meaning |
|---|---|
| **reference** | First shim of its class; conventions are validated against it. Only one at a time per class. |
| **production** | Used in at least one operational deployment with documented evidence (runbook + soak verdict + measurement entry). |
| **pilot** | Code exists, deployed in at least one validation env, no production evidence yet. |
| **proposed** | Skeleton present, no working translation yet. |
| **planned** | Decision made to build, no skeleton yet. |

## Standards

| Standard | Tier | Upstream source | License | Notes |
|---|---|---|---|---|
| CoT (Cursor on Target) | reference (in-tree) | TAK Working Group / open spec | open spec | Reference implementation lives in goat trunk at `ops/shims/tak/` per [shim-pattern §11.3](https://github.com/dlf-dds/DesertBreadBird/blob/main/docs/design/shim-pattern.md). This repo's `cot/` subdirectory exists for non-TAK CoT producers. |
| ISA | planned | open MIL-STD family | TBD per spec source | No work started. |
| SAPIENT | planned | DSTL / NATO open spec | TBD per spec source | No work started. |
| OMNI | planned | open / community-spec | TBD per spec source | No work started. |

## Change history

| Date | Change |
|---|---|
| 2026-05-01 | Initial — repo created as the consolidated open-standards home per goat ADR 0217 |
