# AI Project Foundation

A small, reusable foundation for starting and resuming AI-assisted projects without repeatedly explaining the project or maintaining a large documentation system.

## The problem

Ideas often lose momentum during setup. You spend time on folders and process before useful work. When you return after a week or a year, AI assistants need re-education because conversational memory is gone. Long documentation systems become a burden.

This foundation provides a **small durable memory spine** rather than a large process. Begin with rough intent, interpret it once into canonical memory, and grow specialist depth only when a real need appears.

## What it gives you

Day zero, six files:

```text
README.md
START.md
LICENSE
.gitignore
memory/agreements.md
.cursor/rules/00-project-foundation.mdc
```

After initialisation:

```text
memory/intent.md
memory/now.md
evidence/origin/YYYY-MM-DD-origin.md
```

No stack is chosen. No hosting is assumed. No deployment docs are invented. No documentation tier is required. Deeper files appear only when your project genuinely needs them.

## Quick start

1. Create a repository from this foundation or copy the six day-zero files.
2. Replace the body of [`START.md`](START.md) with rough project intent.
3. Copy the initialisation instruction below into an AI assistant.
4. Review the interpreted memory and proposed first slice.
5. Begin the first useful slice if practical.

Uncertainty is acceptable. Record unknowns honestly rather than inventing decisions.

### Initialisation instruction

Copy everything in the block below to an AI assistant:

```markdown
Initialise this AI Project Foundation repository.

1. Inspect repository and Git state.
2. Read local Git identity with `git config user.name` and `git config user.email`.
   - Determine whether identity appears configured and privacy-safe.
   - Continue initialisation even if identity is missing or appears unsafe.
   - Do not copy Git name or email into project files, README project content, archived origin or chat logs in full.
   - If name or email is missing, record a concise warning in the response.
   - If email appears personal rather than privacy-safe, record a concise warning without echoing the full value.
   - Do not commit or push during initialisation.
   - If a commit is later requested, pause until Git identity is privacy-safe or explicitly approved by the maintainer.
3. Read `START.md` and `memory/agreements.md`.
4. Confirm whether the project is already initialised (`memory/intent.md` and `memory/now.md` present with real content).

If already initialised:
- Do not overwrite project memory blindly.
- Report current state from canonical memory.
- Complete only genuinely missing initialisation steps.
- Preserve existing approved project memory.

If not initialised:
5. Interpret the rough intent without inventing decisions.
6. Create:
   - `memory/intent.md`
   - `memory/now.md`
   - `evidence/origin/YYYY-MM-DD-origin.md` (archive the user's words from START.md; remove the instructional template text; redact accidental PII or local-system information and note any redaction)
7. Replace `START.md` with the initialised-project pointer (see foundation template).
8. Update this README with only:
   - project name
   - one-line stable description
   - links to `memory/intent.md` and `memory/now.md`
   Do not add lifecycle state, active slice details, version history, deployment status or Git identity to the README.
9. Record unknowns explicitly.
10. Propose one small, interesting first slice.
11. Do not create architecture docs, deployment docs, roadmaps, `memory/decisions/`, specialist docs, work files, generated context or identity configuration files unless the rough intent and existing repository already genuinely require them.
12. Scan intended changes for PII, local-system information, secrets and private values.
13. Do not commit or push unless explicitly asked.
14. Return:
    - interpreted purpose
    - uncertainties
    - proposed first slice
    - Git identity status (configured / missing / may be privacy-unsafe) without printing unsafe values in full
    - exact files changed
    - next prompt to begin work

### Output contracts

**memory/intent.md** headings: Purpose; Audience and value; Principles; Non-goals; Assumptions and uncertainties. Synthesise intent — do not copy verbatim. No current status, active tasks, invented architecture, deployment or Git identity.

**memory/now.md** headings: Purpose; Lifecycle; What exists now; Active focus; Active slice; Blockers; Uncertainties; Next safe action; Last meaningful update; Pointers. Purpose is one line. Use `none` where meaningful. List only real artefacts. No fictional infrastructure. Pointers only to files that exist. Roughly one screen.

**START.md** after initialisation:

# Project initialised

Current project memory:

- [Product intent](memory/intent.md)
- [Current project truth](memory/now.md)

The original project idea is archived under `evidence/origin/`.
```

## How memory works

- **`memory/intent.md`** — why the project exists.
- **`memory/now.md`** — what is true now and what happens next.
- **`memory/agreements.md`** — safe working expectations.

Specialist depth is added only when needed. Evidence lives under `evidence/`. Decisions are recorded only when they justify a permanent home. Generated AI context is **not** part of the foundation — canonical memory is small enough to read directly.

## Designed for multiple AIs

Project truth is vendor-neutral Markdown. Cursor gets one thin rule pointing to canonical memory. Other repository-aware assistants read the same files. No AI needs retained conversational memory or a permanent exclusive role. Different models will behave differently; the foundation gives them the same evidence.

## Engineering baseline

[`memory/agreements.md`](memory/agreements.md) covers repository truth, accessibility (WCAG AA aim), maintainable code, proportionate testing, secrets discipline, data separation, privacy-safe Git identity, and no AI co-author metadata. The Cursor rule points to agreements — it does not duplicate them.

## Growing a project

Add specialist memory when real needs appear: architecture, development setup, deployment, data models, security, accessibility depth, testing, incidents. Trigger-based, not a mandatory day-zero tree.

## Existing projects

Do not copy the whole foundation over an established repository. Add the `memory/` spine, point to useful existing docs, remove duplicates only after review, keep historical evidence outside default context, and rewrite Git history only when privacy or attribution debt justifies it.

## Current status

Early but usable — **v0.3**. Validated on a fictional concept project and a real concept-stage migration trial. Mature-project migration remains future validation. Not yet v1.0.

## Licence and reuse

AI Project Foundation is available under the [MIT License](LICENSE).

You may use, copy, modify and distribute it under the terms of that licence.
