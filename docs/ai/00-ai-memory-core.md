# AI memory core

How Stu, ChatGPT, and Cursor work together on `<project-name>`.

Keep this file short and stable. Detailed project truth lives in `<docs-dir>/` numbered guides.

---

## Purpose of this document

Define **roles**, **boundaries**, and **workflows** so AI assistants do not contradict each other or guess project state.

This is not a copy of all project docs — it is the operating manual for AI collaboration.

---

## Roles: Stu, ChatGPT, Cursor

| Actor | Best for |
| ----- | -------- |
| **Stu** | Product intent, priorities, approval to ship, final trade-offs |
| **ChatGPT** | Long-context planning, copy, reviewing generated memory file, strategy when away from the repo |
| **Cursor** | In-repo implementation, inspection, scoped diffs, running commands, writing audit files |

Use ChatGPT when uploading one consolidated handoff file is easier than giving repo access. Use Cursor when files, Git, and commands matter.

---

## What lives where

### Committed documentation (`<docs-dir>/`)

Canonical project truth: architecture, deploy, git flow, decisions, troubleshooting.

**Edit source docs** when behaviour or process changes permanently.

### Cursor rules (`.cursor/rules/`)

Agent behaviour shorthand: scope control, git promotion, doc discipline, hygiene.

May be committed (template default) or local-only (some teams gitignore `.cursor/`).

### Generated AI project memory (`<docs-dir>/ai/01-ai-project-memory.md`)

Auto-generated concatenation of markdown under `<docs-dir>/` for ChatGPT handoff.

**Do not hand-edit.** Regenerate after doc changes.

---

## When to use which tool

| Task | Tool |
| ---- | ---- |
| Implement a scoped code change in repo | Cursor |
| Investigate files and Git state | Cursor |
| Review full doc set in one upload | ChatGPT + generated memory |
| Product wording / strategy draft | ChatGPT or Cursor (prefer Stu review) |
| Production push | Cursor only after Stu explicit approval |

---

## Investigation and documentation-first workflow

For risky, ambiguous, or multi-area work:

1. **Investigate** — read docs, code, and Git state; do not guess.
2. **Report** — save lengthy findings to `<docs-dir>/audits/` (see audits README).
3. **Summarise** in chat: verdict, blockers, recommended next step.
4. **Implement** only when Stu asks — scoped prompts from [`10-prompt-library.md`](10-prompt-library.md).

Mark audit headers with **“audit only — no code changes”** when applicable.

---

## Implementation workflow

### Scope control

- Smallest correct change; no unrelated refactors.
- One concern per prompt when possible (matches prompt library).

### Report-first audits

Long investigations become files, not endless chat threads.

### Regenerating AI memory

After meaningful doc updates:

```bash
node scripts/generate-ai-project-memory.mjs
```

Or ask Cursor: “update the documentation memory file”. Commit only when Stu asks.

---

## Git and release interaction with AI assistants

- Cursor may commit or push **only when Stu explicitly asks**.
- Production branch push requires **explicit approval** every time.
- Align with `<docs-dir>/04-git-workflow.md` and `.cursor/rules/02-git-and-release.mdc`.

User shorthands (“commit to dev”, “commit to staging”, “commit to main”) are defined in git workflow docs — customise branch names per project.

---

## Prompt conventions

Use [`10-prompt-library.md`](10-prompt-library.md) for copy-paste templates.

Good prompts include:

- **Goal**
- **Files/docs to inspect**
- **Constraints** (no code changes / no docs / no production push)
- **Expected output**
- **Verification**

---

## What AI must not do

- Push production or change production env vars without explicit approval
- Commit unless explicitly asked
- Rewrite operational docs during unrelated code tasks
- Copy version numbers or domains from memory without verifying source files
- Treat generated AI memory as the place to make permanent doc edits
- Include secrets or raw dumps in commits or chat logs

---

## Keeping instructions in sync

| When | Action |
| ---- | ------ |
| Process change | Update relevant `<docs-dir>/` doc + Cursor rule if shorthand changed |
| Doc batch before ChatGPT session | Regenerate `01-ai-project-memory.md` |
| Optional `project-status.mdc` | Keep aligned with `00-overview.md` — stale snapshots mislead agents |

If Cursor rules and docs disagree, **docs win** for deployment truth; update rules to match.

---

## Related documents

- [`10-prompt-library.md`](10-prompt-library.md)
- [`../00-overview.md`](../00-overview.md)
- [`../04-git-workflow.md`](../04-git-workflow.md)
- [`../audits/README.md`](../audits/README.md)
- [`.cursor/rules/00-project-behaviour.mdc`](../../.cursor/rules/00-project-behaviour.mdc)
