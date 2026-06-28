# Decisions and rationale

Why major technical and product choices were made — so future-you can answer “was this deliberate?”

For dated entries, see also [`decisions/`](decisions/) ADRs.

---

## Decision summary

| Topic | Decision | Doc |
| ----- | -------- | --- |
| Project shape | Static-first MVP | [`decisions/0001-project-shape.md`](decisions/0001-project-shape.md) |
| Stack | | |
| Hosting | `<hosting-provider>` | |
| Branch strategy | dev → staging → main | [`04-git-workflow.md`](04-git-workflow.md) |

---

## Static-first (example — customise)

**Decision:** Build as static-first where possible; defer backend until a real problem requires it.

**Reasoning:** simpler deployment, lower cost, easier rollback, fewer moving parts at MVP.

**Review trigger:** Need for user accounts, private data, or server-side logic that cannot run at the edge.

---

## Stack choice (template)

**Decision:**

**Reasoning:**

**Rejected alternatives:**

| Option | Why not |
| ------ | ------- |
| | |

---

## Rejected alternatives (general)

Record options considered and why they were not chosen — not to defend forever, but to preserve context.

---

## Review triggers

Revisit documented decisions when:

- Traffic or data size grows significantly
- A new platform requirement appears (auth, payments, realtime)
- Maintenance cost of the current approach exceeds benefit
- Security or compliance requirements change

---

## Related

- [`decisions/0001-project-shape.md`](decisions/0001-project-shape.md)
- [`00-overview.md`](00-overview.md)
