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

### After initialisation

You should now have:

```text
memory/intent.md
memory/now.md
memory/agreements.md
evidence/origin/YYYY-MM-DD-origin.md
```

The AI does **not** commit during initialisation unless you separately authorise it.

Your next steps:

1. Read `memory/intent.md`.
2. Correct any misunderstood purpose, scope or assumptions.
3. Read `memory/now.md`.
4. Check that the next safe action is realistic.
5. Review the Git diff.
6. Commit the initial foundation only when satisfied.
7. Begin the proposed first slice.

## Your first session after initialisation

The foundation is ready. No further setup is necessarily required. You do not need to create architecture, deployment, testing or roadmap files immediately. Begin useful work by asking for one focused slice. The AI should inspect current memory before proposing or implementing changes.

Copy this prompt to any assistant that can access the repository:

```markdown
Read `memory/agreements.md`, `memory/now.md` and `memory/intent.md`.

Briefly tell me:

1. What the project is trying to achieve.
2. What exists right now.
3. What remains uncertain.
4. What the next safe action is.

Then help me complete that next action as one focused slice.

Read additional files only when `memory/now.md` points to them or the task clearly requires them. Do not create new permanent documentation unless the work exposes a real need.
```

## Starting each new AI session

Conversational memory is not project memory. Each fresh session should resume from the repository.

At the beginning of a session, a repository-aware AI should read:

```text
memory/agreements.md
memory/now.md
memory/intent.md
```

It should then follow only relevant pointers from `memory/now.md`.

```markdown
Resume this project from the repository rather than previous chat history.

Read:

- `memory/agreements.md`
- `memory/now.md`
- `memory/intent.md`

Follow only the pointers relevant to the active task.

Summarise the current state and wait for my instruction before making changes.
```

You do not need to paste the full repository into chat. Repository-aware tools can inspect files directly. Review what the AI claims it has read. Assistants should not assume old chat history is current.

## What should the AI read?

Context should match the task.

### Repository-aware agent

Examples: Cursor, Claude Code, repository-connected ChatGPT, agents with local or GitHub access.

Start with `memory/agreements.md`, `memory/now.md` and `memory/intent.md`. Add files linked from `memory/now.md`, task-relevant source code, and relevant specialist files. Do not read every file by default.

### Chat-only assistant

Provide the three canonical memory files plus relevant code, errors, and any specialist document needed. Upload or paste them.

### Small one-off question

The full spine may be unnecessary. A CSS bug may need only the component and stylesheet. Scope questions need `memory/intent.md`. “What next?” questions need `memory/now.md`.

## Keeping token and credit use under control

The foundation does not control vendor pricing, indexing or context windows. Tools charge and load context differently. Repository indexing may happen outside files you explicitly attach to a conversation.

The foundation reduces repeated context by keeping canonical memory small, avoiding generated full-repository bundles, keeping evidence outside normal context, and using `memory/now.md` to route agents to relevant material.

Practical guidance: keep `memory/now.md` concise; avoid “read the entire repository” prompts; ask for targeted inspection; start a new conversation when context has drifted; use cheaper models for mechanical work; review auto-attached context in tools that expose it.

```markdown
Use the minimum context needed for this task.

Start with `memory/agreements.md`, `memory/now.md` and `memory/intent.md`.

Inspect only the files directly relevant to the active work. Do not perform a broad repository review unless you find a concrete dependency or I explicitly ask for one.
```

## Using different AI tools

**Cursor** — the tracked rule directs Cursor to canonical memory. It is short and does not contain full project history. Cursor may inspect additional code when the task requires it.

**Claude Code** — works without conversion. Use ordinary Markdown memory and the session-opening prompt. `CLAUDE.md` is optional; do not duplicate `memory/agreements.md` into it.

**Other repository-aware assistants** — connect repository access where supported, point to canonical memory, use the session-opening prompt. Behaviour varies by product and model.

**Chat-only tools** — upload or paste the three canonical memory files plus task-relevant code and specialist material.

No official vendor integration is implied.

## How project files evolve

The foundation is not a background service. Files change when you instruct an AI to work and it follows the agreements.

- **`memory/intent.md`** — update when durable intent changes. Not every task.
- **`memory/now.md`** — update when current reality or next action changes. Not a daily diary.
- **`memory/agreements.md`** — change rarely.
- **Specialist files** — create when a repeated or complex need appears.
- **Evidence files** — investigations, audits, origin material, migration reports; outside default context.

Git history covers ordinary change. A permanent report is not needed for every task.

The foundation provides canonical locations, reading order, working expectations, update triggers, and privacy safeguards. It does **not** provide autonomous agents, guaranteed model behaviour, automatic commits, automatic memory updates, or protection from incorrect output without human review. Review diffs, memory updates, verification, and commit metadata.

## Example working prompts

### Start a focused slice

```markdown
Read the canonical project memory and help me complete the next safe action as one focused slice.

Before changing anything:

1. Summarise the intended outcome.
2. Identify the files likely to be involved.
3. State any material uncertainty.
4. Propose how the result will be verified.

Keep changes proportionate. Update `memory/now.md` if project reality changes. Do not commit or push unless I explicitly ask.
```

### Ask for investigation before implementation

```markdown
Investigate this problem before implementing a fix.

Read the canonical memory, inspect only relevant files, identify the most likely cause, and report:

- evidence
- risks
- recommended next action
- whether implementation is safe yet

Do not change files during the investigation.
```

### End a slice cleanly

```markdown
Review the completed work against the original objective.

Run proportionate verification, then update `memory/now.md` only if the project's current reality or next safe action has changed.

Report:

- files changed
- verification performed
- remaining uncertainty
- proposed next action

Do not create a separate report unless the findings need durable evidence.
```

### Use a chat-only AI

```markdown
I am providing:

- `memory/agreements.md`
- `memory/now.md`
- `memory/intent.md`
- the files relevant to this task

Treat repository memory as authoritative over assumptions from previous chats.

Answer using only the supplied evidence. Tell me if a missing file materially prevents a reliable answer.
```

## How memory works

- **`memory/intent.md`** — why the project exists.
- **`memory/now.md`** — what is true now and what happens next.
- **`memory/agreements.md`** — safe working expectations.

Specialist depth is added only when needed. Evidence lives under `evidence/`. Decisions are recorded only when they justify a permanent home. Generated AI context is **not** part of the foundation — canonical memory is small enough to read directly.

## Engineering baseline

[`memory/agreements.md`](memory/agreements.md) covers repository truth, accessibility (WCAG AA aim), maintainable code, proportionate testing, secrets discipline, data separation, privacy-safe Git identity, and no AI co-author metadata. The Cursor rule points to agreements — it does not duplicate them.

## Growing a project

Add specialist memory when real needs appear: architecture, development setup, deployment, data models, security, accessibility depth, testing, incidents. Trigger-based, not a mandatory day-zero tree.

## Existing projects

Do not copy the whole foundation over an established repository. Add the `memory/` spine, point to useful existing docs, remove duplicates only after review, keep historical evidence outside default context, and rewrite Git history only when privacy or attribution debt justifies it.

## Common questions

**Do I give every AI the whole repository?** No — begin with canonical memory; inspect task-relevant files only.

**Will memory files consume lots of credits?** Some, like any text — but they are concise. Broad repository reading and long chats cost more.

**Does the foundation update itself?** No — agents update files during instructed work, subject to review.

**Must I use Cursor?** No — Cursor has a convenience rule; memory is vendor-neutral.

**Can I use several AIs?** Yes — same repository truth; avoid concurrent uncoordinated edits.

**Must every task update memory?** No — only meaningful intent, reality or next-action changes.

**Create all specialist folders now?** No — trigger-based only.

**Let an AI commit automatically?** Only when explicitly authorised, after reviewing identity, diff and verification.

**When an AI gets something wrong?** Correct canonical memory and the artefact; do not rely on the old chat.

**Can a team use this?** Yes — treat canonical memory like code and review changes.

## Current status

Early but usable — **v0.3**. Validated on a fictional concept project and a real concept-stage migration trial. Mature-project migration remains future validation. Not yet v1.0.

## Licence and reuse

AI Project Foundation is available under the [MIT License](LICENSE).

You may use, copy, modify and distribute it under the terms of that licence.
