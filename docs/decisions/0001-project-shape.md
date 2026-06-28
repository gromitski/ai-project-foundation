# ADR 0001: Project shape

## Status

Proposed | Accepted | Superseded

**Date:** YYYY-MM-DD

---

## Decision

Build `<project-name>` as a **static-first** web application with **no custom backend** for the initial milestone.

---

## Context

- Who the users are and what they need at MVP
- Team size and maintenance budget
- Hosting and operational constraints
- Need for fast iteration and easy rollback

---

## Options considered

| Option | Summary |
| ------ | ------- |
| **A — Static-first (chosen)** | Pre-build or generate assets; host on CDN |
| **B — Traditional server** | App server + database from day one |
| **C — Serverless API** | Static front-end + functions for all dynamic needs |

---

## Chosen approach

**Option A** — static-first on `<hosting-provider>`.

Reasoning:

- Simpler deployment and lower operational cost at MVP
- Fewer moving parts; easier debugging and rollback
- Fits content/browse-heavy products where most work can happen at build time or client-side

---

## Consequences

**Positive:**

- Cheap hosting, global CDN, predictable builds
- Clear separation between build-time and runtime

**Negative / trade-offs:**

- Some dynamic behaviour requires edge functions or client-side workarounds
- Large catalogues need careful data-sharding strategy (document separately if needed)

---

## Review trigger

Revisit this decision when the product requires:

- User accounts and private per-user state
- Server-side secrets or heavy computation per request
- Real-time collaboration or writes that cannot be delegated to a third party

---

## Related

- [`../05-decisions-and-rationale.md`](../05-decisions-and-rationale.md)
- [`../00-overview.md`](../00-overview.md)
