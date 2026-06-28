# Template notes

Draft reusable AI/project foundation extracted from working patterns in a static-first web project (source: private audit in `_ai-project-foundation/01-audit/`).

**This is not a runnable application.** Copy into a new private repo and replace placeholders.

---

## What was extracted from the source project

| Pattern | Template location |
| ------- | ----------------- |
| Six focused Cursor rules (not one mega-file) | `.cursor/rules/00–05*.mdc` |
| Numbered operational docs | `docs/00–10*.md` |
| AI collaboration guide | `docs/ai/00-ai-memory-core.md` |
| Starter prompt library (8 prompts) | `docs/ai/10-prompt-library.md` |
| Audit/report taxonomy | `docs/audits/README.md` |
| ADR-style first decision | `docs/decisions/0001-project-shape.md` |
| Doc concatenation for ChatGPT handoff | `scripts/generate-ai-project-memory.mjs` |
| Three-tier git promotion + user shorthands | `02-git-and-release.mdc`, `docs/04-git-workflow.md` |
| Evidence-first performance framework | `04-accessibility-performance.mdc`, `docs/07-performance.md` |
| Repository hygiene gate | `05-repository-hygiene.mdc` |
| Internal vs public release procedure skeleton | `docs/09-release-procedure.md` |

Source audit: [`../01-audit/reusable-foundation-audit.md`](../01-audit/reusable-foundation-audit.md)

---

## What was deliberately not extracted

- Product-specific design system rules (tokens, component naming)
- **Stale `project-status.mdc` snapshot** — the source project’s version table was out of date; this template uses `00-overview.md` instead and warns about optional snapshots
- Domain data pipeline details (upstream dataset names, categorisation, shard filenames)
- Map/canvas-specific behaviour and accessibility workarounds
- Production domains, contact emails, analytics measurement IDs
- Raw Lighthouse trace storage (optional `lighthouse/` skip in generator)
- Application source, CI workflows, `package.json` scripts (wire on adoption)
- Entire generated AI memory blob from the source repo (~40k+ lines)

---

## BlooPlax-specific content in this template

**None in template files.** This draft uses generic placeholders (`<project-name>`, `<production-domain>`, etc.).

The source project name appears **only in this file** when describing extraction provenance.

---

## Known assumptions

1. **Static-first or mostly static** web project — ADR 0001 reflects that; change if wrong.
2. **Optional three-branch flow** (dev → staging → production) — delete staging rows if unused.
3. **Cursor rules committed** in the foundation template — some teams prefer gitignored `.cursor/` (documented in `.gitignore` comment).
4. **Generated AI memory gitignored by default** — commit it if you want ChatGPT handoff in repo without regenerating.
5. **Node-based script** for memory generation — adapt if docs live elsewhere.
6. **Tiered adoption** — small projects may use only hygiene + git + docs rules (see below).

---

## Placeholders to replace on adoption

| Placeholder | Example |
| ----------- | ------- |
| `<project-name>` | MyApp |
| `<project-slug>` | my-app |
| `<production-domain>` | `https://example.com` |
| `<staging-domain>` | `https://staging.example.com` |
| `<hosting-provider>` | Cloudflare Pages |
| `<development-branch>` | `dev` |
| `<staging-branch>` | `staging` |
| `<primary-branch>` | `main` |
| `<docs-dir>` | `docs` |
| `<app-version-file>` | `src/lib/appVersion.ts` |
| `<analytics-provider>` | Umami / none |
| `<contact-email>` | `hello@example.com` |
| `<current-public-version>` | `1.0` |
| `<next-milestone>` | `1.1` |

Search the template folder for `<` to find remaining placeholders.

---

## What Stu should review before moving to a private repo

- [ ] Branch model matches how you actually ship (two vs three environments)
- [ ] Whether `.cursor/rules/` should be committed or gitignored per project
- [ ] Whether `01-ai-project-memory.md` should be committed or generated on demand
- [ ] `SKIP_DIRS` / `SKIP_FILES` in memory script (exclude heavy audit artefacts?)
- [ ] Prompt library — add project-specific prompts as they prove useful
- [ ] Delete doc sections that do not apply (PWA, edge functions, data pipeline)
- [ ] Wire `generate:ai-memory` in new project `package.json`
- [ ] Confirm no product-specific names leaked (grep below)

---

## Tiered adoption

| Tier | Include |
| ---- | ------- |
| **Minimal** | `05-repository-hygiene`, `03-documentation`, simplified `02-git-and-release` |
| **Standard** | All six Cursor rules + `docs/00–04` + `docs/ai/00-ai-memory-core.md` |
| **Full** | Entire template including audits, release procedure, prompt library, memory script |

---

## Suggested next step after review

1. Copy `_ai-project-foundation/03-template-draft/` to a new private repository (e.g. `project-template` or `ai-project-foundation`).
2. Replace placeholders; trim unused sections.
3. Initialise a real app or attach to an existing repo’s docs layout.
4. Run from the new repo root (after docs exist):

   ```bash
   node scripts/generate-ai-project-memory.mjs
   ```

5. **Do not commit `_ai-project-foundation/` to the source product repo** unless you intentionally want extraction scratch space tracked in Git.

---

## Quality check reference

Before publishing the private template repo, run:

```bash
rg -i 'blooplax|open plaques|maplibre|heritage brass|bp-|plaque|gromitski' _ai-project-foundation/03-template-draft/ --glob '!TEMPLATE_NOTES.md'
```

Expect zero matches outside `TEMPLATE_NOTES.md`.
