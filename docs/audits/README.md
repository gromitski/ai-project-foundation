# Audit and report files

Human-written audits, investigations, and checklists live here. Operational docs (how to run, deploy, release) stay in the numbered guides at `<docs-dir>/00–10*.md`.

**For AI assistants:** When asked to create a report or audit, default to `<docs-dir>/audits/{appropriate-subfolder}/` unless explicitly instructed otherwise.

---

## When to create an audit

Create a dated audit when work is:

- lengthy (multi-section findings, inventories, readiness reviews)
- risky (architecture, production, security, performance)
- ambiguous (needs evidence before implementation)
- explicitly requested as investigation-only

Small bugfixes and obvious one-file changes do not need a formal audit.

---

## Audit categories

| Folder | Use for |
| ------ | ------- |
| **`code/`** | Hosting, CI, routing, deployment, build architecture |
| **`data/`** | Source fields, pipelines, generated data, loading architecture |
| **`ux/`** | Layout, accessibility, interaction, typography |
| **`seo/`** | Indexing, metadata, sitemap, crawlability |
| **`analytics/`** | Event inventories, verification checklists, tracking issues |
| **`performance/`** | Runtime performance, Lighthouse interpretation, CSS/rendering |
| **`lighthouse/`** | Raw Lighthouse HTML/JSON traces (optional — can gitignore) |

When a topic spans folders, pick the **primary** subject and link to related audits elsewhere.

---

## Filename convention

Prefer dated names tied to a point in time:

`YYYY-MM-DD-short-topic-audit.md`

Descriptive names without dates are fine for living checklists, e.g. `event-verification-checklist.md`.

---

## Report structure

Recommended header:

```markdown
# Title

**Date:** YYYY-MM-DD
**Scope:** …
**Method:** …
**Status:** Audit only — no code changes (when applicable)
```

Include executive summary, findings table, recommendations, and suggested next steps.

---

## Code changes during audits

**Do not change code during an audit unless explicitly asked.**

Investigation tasks produce files and concise chat summaries — not drive-by fixes.

---

## Summarising back to Stu

In chat:

- Keep the reply concise
- Point to the saved file path
- State verdict / blockers / recommended next step

---

## Related

- [`.cursor/rules/03-documentation.mdc`](../../.cursor/rules/03-documentation.mdc)
- [`../10-folder-guide.md`](../10-folder-guide.md)
- [`../ai/10-prompt-library.md`](../ai/10-prompt-library.md)
