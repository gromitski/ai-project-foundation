# Project overview

**Public version:** `<current-public-version>` on `<production-domain>`  
**Next milestone:** `<next-milestone>`  
**Owner / maintainer:** `<owner-notes>`

Authoritative detail for agents and future-you — keep this file current.

---

## Purpose

What the project is, who it is for, and what problem it solves in plain language.

---

## Current status

| Area | Current reality |
| ---- | ---------------- |
| **Production** | `<production-domain>` on `<hosting-provider>` |
| **Staging** | `<staging-domain>` (if used) |
| **Development** | `<development-domain-or-local>` |
| **Public version** | `<current-public-version>` (source: `<app-version-file>`) |
| **Indexing / SEO** | {allowed / blocked on non-production — document env gate} |
| **Analytics** | `<analytics-provider>` — {staging vs production IDs if applicable} |

---

## Environments

| Environment | Branch | URL | Notes |
| ----------- | ------ | --- | ----- |
| Local | — | `http://localhost:<port>` | |
| Development | `<development-branch>` | | |
| Staging | `<staging-branch>` | `<staging-domain>` | Optional |
| Production | `<primary-branch>` | `<production-domain>` | |

---

## Tech stack

| Layer | Choice |
| ----- | ------ |
| Framework | |
| Language | |
| Hosting | `<hosting-provider>` |
| Edge / serverless | {if any} |
| Data | {static files / API / none} |

---

## Key constraints

Document deliberate limits — e.g. static-first, no backend, no user accounts, build-time data generation, mobile-first UX.

- 
- 

---

## Contacts

| Role | Value |
| ---- | ----- |
| Public contact | `<contact-email>` |
| Support / admin | |

---

## Related docs

- [`01-how-it-works.md`](01-how-it-works.md)
- [`04-git-workflow.md`](04-git-workflow.md)
- [`decisions/0001-project-shape.md`](decisions/0001-project-shape.md)
- [`roadmap.md`](roadmap.md) — optional living roadmap
