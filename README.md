# goat-open-standards

Open data-standard shims into the **goat** fabric.

## 1. License

Apache License 2.0. See [`LICENSE`](LICENSE).

Per-standard subdirectories may bundle generated bindings or reference fixtures from upstream standards bodies; each subdirectory's `STATUS.md` declares the upstream source and the license posture for that standard.

## 2. Scope

This repo is the consolidated home for shims that translate **community-governed open data standards** to/from the goat substrate. Per [goat ADR 0217](https://github.com/dlf-dds/DesertBreadBird/blob/main/docs/adr/0217-shim-repo-containment.md) and [shim-pattern §11](https://github.com/dlf-dds/DesertBreadBird/blob/main/docs/design/shim-pattern.md), open standards converge on shared schema / audit / lineage shape, so consolidation avoids real duplication.

In scope:

- **CoT** — Cursor on Target (TAK Working Group / open spec)
- **ISA** — Imagery Support Architecture (open MIL-STD family)
- **SAPIENT** — DSTL / NATO open spec for multi-sensor autonomous information exchange
- **OMNI** — open / community-spec sensor messaging
- Future open MIL-STDs and community-governed interop formats

Not in scope:

- **Commercial vendor SDKs** (even when published). Each gets its own dedicated repo per ADR 0217 — e.g. `dlf-dds/goat-lattice-shim`. Published-API does not equal community-governed-standard.
- **Vendor product specifics** (TAK server admin RPCs, mission-package handling, etc.). Those go in vendor-specific repos.

## 3. Substrate dependency

Every standard's shim in this repo depends on **`goat-shim-framework`** (in the goat trunk: <https://github.com/dlf-dds/DesertBreadBird>) for:

- Identity binding (Ed25519 keypair, signed-announce builder)
- Mandatory data-dictionary registration
- Audit-hook plumbing
- Namespace-policer (enforces shim-pattern §2.3 namespace isolation)
- Restart-semantics scaffolding

Custom auth / schema / audit / namespace code in a per-standard subdirectory is a defect — reach for the framework first.

## 4. Per-standard layout

Each standard lives under its own subdirectory:

```text
goat-open-standards/
├── cot/
│   ├── STATUS.md          # tier, upstream source, license, maturity
│   ├── README.md          # standard-specific runbook + topic registry
│   └── src/, test/, ops/
├── isa/
├── sapient/
├── omni/
└── ...
```

A new standard adds a directory + a row in [`STATUS.md`](STATUS.md). The shim conventions (the goat shim-pattern §2 five conventions, §4.5 review checklist) apply to every per-standard subdirectory unchanged.

## 5. CoT — relationship to the in-tree TAK shim

The reference TAK-to-Zenoh shim (CoT format) currently lives **in-tree in the goat trunk** at [`ops/shims/tak/`](https://github.com/dlf-dds/DesertBreadBird/tree/main/ops/shims/tak) per shim-pattern §11.3 (the TAK in-tree exception — it predates the per-class containment decision and is the reference implementation conventions are validated against). CoT-the-format may migrate from the trunk into this repo in the future, but only if doing so produces a strictly better outcome. Not currently scheduled.

In the meantime: this repo's `cot/` subdirectory exists for non-TAK CoT producers (other ground-station software, third-party sensor formatters). The in-tree shim and any in-repo work share the same conventions.

## 6. Discoverability

This repo is registered in goat's [`docs/integrations/INDEX.md`](https://github.com/dlf-dds/DesertBreadBird/blob/main/docs/integrations/INDEX.md) — the canonical "what shims exist" surface.

## 7. Status

This repo is **scaffolding only** as of 2026-05-01. See [`STATUS.md`](STATUS.md) for per-standard maturity tiers. Coordination work is tracked at [goat implementation-plan Block 49](https://github.com/dlf-dds/DesertBreadBird/blob/main/docs/project/implementation-plan.md).
