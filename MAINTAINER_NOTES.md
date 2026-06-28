# Maintainer notes

Notes for keeping the **ai-project-foundation** repository itself healthy — not instructions for day-to-day work on a product created from the template.

For adopting this foundation into a new project, see [`docs/11-using-this-template.md`](docs/11-using-this-template.md).

---

## What was extracted from BlooPlax

This foundation was distilled from working patterns in **BlooPlax**, a static-first web project. The extraction preserved process and documentation structure, not product code.

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

BlooPlax-specific names should appear **only in this file** when describing provenance.

---

## What should not be copied into new projects blindly

- **Every doc section** — delete PWA, edge functions, three-branch promotion, or release procedure sections if they do not apply
- **Full prompt library** — start with generic prompts; add project-specific ones when they prove useful
- **Stale snapshots** — do not add a `project-status.mdc` with version tables unless you commit to keeping it aligned with `docs/00-overview.md`
- **Generated AI memory** — default is gitignore + regenerate; only commit the bundle if you want it in repo without regenerating
- **Placeholder branch names** — replace `<development-branch>`, `<staging-branch>`, `<primary-branch>` in Cursor rules and docs together
- **BlooPlax extraction context** — do not copy this file into product repos unless you want maintainer history there

Deliberately **not** included in the foundation:

- Product design system rules (tokens, component naming)
- Domain data pipeline details (upstream dataset names, shard filenames)
- Map/canvas-specific behaviour
- Production domains, contact emails, analytics IDs from the source project
- Application source, CI workflows, `package.json` (wire on adoption)
- The source project’s full generated AI memory blob

---

## How to keep this foundation lightweight

- Resist adding framework-specific or hosting-specific config — those belong in product repos
- Resist CI workflows, example app code, and deep folder nesting
- Keep Cursor rules as **shorthand**; put canonical detail in `docs/`
- Prefer one new numbered doc over scattering notes in README
- When a pattern proves useful on a real project, generalise it here with placeholders — not product names

Tiered adoption (for reference):

| Tier | Include |
| ---- | ------- |
| **Minimal** | `05-repository-hygiene`, `03-documentation`, simplified `02-git-and-release` |
| **Standard** | All six Cursor rules + `docs/00–04` + `docs/ai/00-ai-memory-core.md` |
| **Full** | Entire template including audits, release procedure, prompt library, memory script |

---

## What to review after using this on a real project

After shipping something built from this template, ask:

- Did any Cursor rule encode a one-off decision that should be generalised or removed from the foundation?
- Did any doc section confuse agents because it was too product-specific?
- Did the tiered adoption table match how the project actually worked?
- Should the memory script’s `SKIP_DIRS` / `SKIP_FILES` defaults change for common cases?
- Were placeholders consistent, or did mixed styles cause friction?

Feed improvements back into this repo rather than letting each product fork diverge silently.

---

## When to update the foundation repo

Update **ai-project-foundation** when:

- A reusable pattern emerged from a real project (generalised, not copied verbatim)
- Placeholders or docs were confusing during adoption
- Cursor rule behaviour should change for all future projects
- A section is clearly obsolete and safe to quarantine or remove

Do **not** update the foundation for product-only changes (features, domains, analytics, design tokens).

---

## Placeholder reference

| Placeholder | Example |
| ----------- | ------- |
| `<project-name>` | MyApp |
| `<project-slug>` | my-app |
| `<github-username>` | your-github-handle |
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

Search the repo for `<` to find remaining placeholders before publishing a product repo.

---

## Quality check before publishing foundation changes

Confirm no product-specific names leaked outside this file:

```bash
rg -i 'blooplax|open plaques|maplibre|heritage brass|bp-' . \
  --glob '!MAINTAINER_NOTES.md'
```

Expect zero matches outside `MAINTAINER_NOTES.md`.
