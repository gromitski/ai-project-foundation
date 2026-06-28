# AI project foundation

Reusable documentation and Cursor rules for starting new projects with consistent AI-assisted development.

**This is not an application.** Copy or clone this repo into a new private GitHub repository, replace placeholders, trim what you do not need, then add your app code.

---

## What this is

A lightweight template for:

- **Operational docs** — numbered guides under `docs/` for overview, local dev, deployment, git workflow, and more
- **Cursor rules** — six focused `.mdc` files in `.cursor/rules/` (behaviour, code quality, git, documentation, a11y/performance, hygiene)
- **AI collaboration** — handoff docs, a prompt library, and a script that concatenates docs into one file for ChatGPT

It was distilled from patterns used on a real static-first web project. See [`MAINTAINER_NOTES.md`](MAINTAINER_NOTES.md) for extraction provenance and what not to copy blindly.

---

## What problem it solves

New projects often reinvent the same scaffolding: how agents should behave, where docs live, how branches map to environments, and how to avoid committing secrets. This foundation gives you a sane default so you can start building instead of writing process docs from scratch.

---

## Who it is for

Developers using **Cursor** (and optionally ChatGPT) who want:

- Consistent agent behaviour across projects
- Human-readable operational docs that agents are instructed to read first
- Optional tiered adoption — use the full set or a minimal subset for small repos

---

## What is included

| Area | Location |
| ---- | -------- |
| Cursor rules (6 files) | [`.cursor/rules/`](.cursor/rules/) |
| Operational docs | [`docs/`](docs/) |
| AI collaboration | [`docs/ai/`](docs/ai/) |
| Audit report layout | [`docs/audits/`](docs/audits/) |
| ADR example | [`docs/decisions/`](docs/decisions/) |
| Doc concatenation script | [`scripts/generate-ai-project-memory.mjs`](scripts/generate-ai-project-memory.mjs) |
| Maintainer notes | [`MAINTAINER_NOTES.md`](MAINTAINER_NOTES.md) |

---

## Quick start — create a new project

Full step-by-step instructions: **[`docs/11-using-this-template.md`](docs/11-using-this-template.md)**

Short version:

1. Create a new **private** GitHub repository (empty, no README).
2. Copy this foundation into a local folder (clone, copy, or “Use this template” if you publish it on GitHub).
3. Initialise Git if needed, add the GitHub remote, replace placeholders (`<project-name>`, `<production-domain>`, branch names, etc.).
4. Open the folder in Cursor and review [`.cursor/rules/`](.cursor/rules/).
5. Trim docs and rules you do not need (see tiered setup below).
6. Add your application code and update `docs/00-overview.md`.

---

## Minimal / Standard / Full setup

| Tier | Use when | Keep |
| ---- | -------- | ---- |
| **Minimal** | Small scripts, experiments, single-branch repos | `05-repository-hygiene`, `03-documentation`, simplified git rule; `docs/00-overview.md` + `docs/04-git-workflow.md` |
| **Standard** | Most new apps | All six Cursor rules + `docs/00–04` + `docs/ai/00-ai-memory-core.md` |
| **Full** | Teams wanting audits, release checklists, prompt library | Entire template including `docs/05–10`, audits layout, release procedure, prompt library, memory script |

Details and trimming checklist: [`docs/11-using-this-template.md`](docs/11-using-this-template.md#trimming-the-template-for-small-projects).

---

## Cursor rules

Agent behaviour lives in [`.cursor/rules/`](.cursor/rules/):

| File | Purpose |
| ---- | ------- |
| `00-project-behaviour.mdc` | Read docs first, minimal scope, ask before production actions |
| `01-code-quality.mdc` | Focused diffs, reuse conventions, verify changes |
| `02-git-and-release.mdc` | Branch promotion and explicit production approval |
| `03-documentation.mdc` | Do not auto-rewrite docs; audit file conventions |
| `04-accessibility-performance.mdc` | Evidence-first performance and a11y priorities |
| `05-repository-hygiene.mdc` | Never commit secrets or raw dumps |

This foundation **commits** `.cursor/rules/` so guidance travels with the repo. Individual product repos may gitignore `.cursor/` instead — document the choice in `docs/10-folder-guide.md`.

Replace branch and domain placeholders in `02-git-and-release.mdc` when you adopt the template.

---

## Generated AI memory

[`scripts/generate-ai-project-memory.mjs`](scripts/generate-ai-project-memory.mjs) concatenates markdown under `docs/` into a single handoff file:

```bash
node scripts/generate-ai-project-memory.mjs
```

Default output: `docs/ai/01-ai-project-memory.md`.

**Default policy:** that file is **gitignored** (see [`.gitignore`](.gitignore)). Regenerate locally when you need a ChatGPT handoff. Commit it only if you intentionally want the bundle tracked in Git.

See [`docs/ai/00-ai-memory-core.md`](docs/ai/00-ai-memory-core.md) for roles, workflow, and when to regenerate.

---

## Detailed setup guide

**[`docs/11-using-this-template.md`](docs/11-using-this-template.md)** — creating a GitHub repo, copying the template, placeholders, first commit, opening in Cursor, AI memory, trimming, checklist, and common mistakes.

---

## Maintainer

If you maintain this foundation repo itself (not a project created from it), read [`MAINTAINER_NOTES.md`](MAINTAINER_NOTES.md).
