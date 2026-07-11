# AI Project Foundation

AI Project Foundation helps you keep an AI-assisted project understandable and organised as it grows. It gives every assistant the same small source of truth, helps fresh sessions resume quickly, and lets durable documentation emerge through real work without filling the repository with placeholders.

An AI-assisted project often starts quickly but loses coherence later. Decisions stay trapped in old chats. A different assistant lacks context. New sessions repeat old explanations. Speculative documentation creates noise. You become the only person who remembers why things are the way they are.

This foundation changes that experience. Project truth lives in the repository. A fresh AI can understand the purpose and current position. You can switch tools. Permanent documentation appears only as needed. Work can pause and resume without reconstructing the project from memory.

You begin with only a few files. You remain in control of decisions, diffs, commits and releases.

## What using it feels like

A normal project follows a short progression:

1. You write or dictate an unfinished idea.
2. You ask an AI to initialise the project.
3. You review the interpreted intent and next safe action.
4. You begin one useful slice.
5. You return later and ask a fresh AI to resume from repository memory.
6. As the project matures, you ask naturally for a roadmap, architecture notes or a deployment guide.
7. The AI creates and links only the durable documentation that is now useful.

You do not need to remember the framework's filing rules during normal work. Repository-aware assistants read the working agreements and use them to keep durable project knowledge organised.

AI behaviour is not guaranteed. You review changes. The foundation supplies structure and instructions rather than autonomous enforcement.

## How a project grows

Each document earns its place through real project work. The repository grows with the project rather than asking the project to fill in a prebuilt documentation system.

### Initialised project

```text
memory/
  agreements.md
  intent.md
  now.md
```

You can begin work here. No architecture, deployment, testing or roadmap documents are created speculatively.

### You ask: "Create a roadmap for the next six months."

The AI should recognise the roadmap as durable project knowledge and create the smallest suitable specialist document, for example:

```text
docs/
  roadmap.md
```

It adds a pointer from `memory/now.md`. It does not also create architecture, deployment or testing documents.

### Later: "Design the application architecture."

The project now earns another durable document:

```text
docs/
  roadmap.md
  architecture.md
```

Again, `memory/now.md` points to it.

### Later still: "Document how this is deployed."

Only when deployment exists and needs preserving:

```text
docs/
  roadmap.md
  architecture.md
  deployment.md
```

What does **not** happen:

- no automatic troubleshooting guide
- no empty testing strategy
- no speculative decision-record tree
- no release manual without releases
- no full documentation suite because one document became useful

`docs/` is an example location, not a mandatory universal directory. Existing projects may already have appropriate places. The durable rules are: create the smallest useful document; avoid duplication; link relevant specialist knowledge from `memory/now.md`; do not generate related documents speculatively.

## Start a new project

The foundation ships six day-zero files:

```text
README.md
START.md
LICENSE
.gitignore
memory/agreements.md
.cursor/rules/00-project-foundation.mdc
```

From your perspective:

- **`START.md`** gives you somewhere informal to think.
- **`memory/agreements.md`** teaches assistants how to work safely.
- **`.cursor/rules/00-project-foundation.mdc`** points Cursor to project memory automatically.
- **`README.md`** helps humans understand and use the foundation.
- **`.gitignore`** provides a basic privacy and local-file baseline.
- **`LICENSE`** permits reuse.

To begin:

1. Create a repository from the foundation or copy the six day-zero files.
2. Replace the body of [`START.md`](START.md) with rough intent.
3. Open the full initialisation prompt below.
4. Paste it into a repository-aware assistant.
5. Review the resulting memory and diff.
6. Commit only when satisfied.

Uncertainty is acceptable. Record unknowns honestly rather than inventing decisions.

<details>
<summary><strong>Copy the full initialisation prompt</strong></summary>

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

</details>

## After initialisation

Initialisation adds three artefacts:

```text
memory/intent.md
memory/now.md
evidence/origin/YYYY-MM-DD-origin.md
```

Together with `memory/agreements.md`, these form the project's working memory. The AI does **not** commit during initialisation unless you separately authorise it.

Your next steps:

1. Read `memory/intent.md` and correct any misunderstood purpose, scope or assumptions.
2. Read `memory/now.md` and check that the next safe action is realistic.
3. Review the Git diff.
4. Commit the initial foundation only when satisfied.
5. Begin the proposed first slice.

No further setup is necessarily required. You do not need architecture, deployment, testing or roadmap files before useful work begins.

## Work on the project

The framework and AI help by preserving shared project truth, restoring context in new sessions, routing assistants to relevant material, distinguishing durable intent from current work, creating specialist documentation when real needs arise, and applying universal quality, privacy and Git safeguards.

You remain responsible for correcting misunderstood intent, accepting or rejecting recommendations, reviewing diffs, deciding whether documentation deserves permanence, authorising commits and pushes, verifying implementation and testing, and resolving disagreements between concurrent agents.

This is your main everyday prompt:

```markdown
Resume this project from the repository.

Read:

- `memory/agreements.md`
- `memory/now.md`
- `memory/intent.md`

Follow only the pointers relevant to the active task.

Summarise the project's current position, then help me complete the next safe action as one focused slice.

Create or update permanent documentation only when this work exposes a durable need. Keep it concise, avoid duplication, and link relevant specialist material from `memory/now.md`.

Do not commit or push unless I explicitly ask.
```

To end a slice cleanly:

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

## Return in a new AI session

Conversational memory is not project memory. After a week or six months, a fresh assistant should resume from the repository, not from an old chat.

It should read `memory/agreements.md`, `memory/now.md` and `memory/intent.md`, then follow pointers in `memory/now.md` to deeper material such as a roadmap or architecture note. Old conversation history is unnecessary when repository memory is current.

You do not need to paste the full repository into chat. Repository-aware tools can inspect files directly. Review what the AI claims it has read.

## Use different AI tools

The project memory is ordinary Markdown, so it is not locked to one AI product.

**Cursor** includes a short convenience rule that points to project memory automatically. It does not contain the full project history.

**Claude Code** can use the same files and the everyday session prompt. A duplicated `CLAUDE.md` is optional and usually unnecessary.

**Other repository-aware assistants** (including repository-connected ChatGPT and similar agents) can inspect files directly when you point them to the three memory files and use the everyday prompt.

**Chat-only assistants** need the three memory files plus task-relevant code and specialist material. Upload or paste them:

```markdown
I am providing:

- `memory/agreements.md`
- `memory/now.md`
- `memory/intent.md`
- the files relevant to this task

Treat repository memory as authoritative over assumptions from previous chats.

Answer using only the supplied evidence. Tell me if a missing file materially prevents a reliable answer.
```

Behaviour varies between products and models. No official vendor integration is implied.

## Keep context and cost under control

The memory spine is intentionally small. An assistant does not need to read the whole repository for each task. `memory/now.md` acts as a route map. Historical evidence stays out of normal context. Specialist files load only when relevant. Generated full-repository handoffs are deliberately absent.

The foundation cannot control vendor pricing, indexing or automatic context attachment. Practical controls still help: keep `memory/now.md` concise; avoid "read the entire repository" prompts; ask for targeted inspection; start a new conversation when context has drifted; use cheaper models for mechanical work; review auto-attached context in tools that expose it.

```markdown
Use the minimum context needed for this task.

Start with `memory/agreements.md`, `memory/now.md` and `memory/intent.md`.

Inspect only the files directly relevant to the active work. Do not perform a broad repository review unless you find a concrete dependency or I explicitly ask for one.
```

## Understand the memory files

These files exist to help you stay organised, not to create paperwork.

- **`memory/intent.md`** prevents purpose and scope drifting between sessions. It holds why the project exists, who it serves, principles and non-goals.
- **`memory/now.md`** tells a new assistant where the project actually is: what exists, what you are working on, blockers, and the next safe action. It links to deeper material when needed.
- **`memory/agreements.md`** prevents each AI from inventing its own working rules. It covers repository truth, privacy, Git authority, quality expectations and proportionate testing.
- **Specialist documents** preserve depth (roadmap, architecture, deployment and similar) without loading everything every time.
- **`evidence/`** retains important history (original intent, investigations, audits) outside everyday context.

Update `memory/intent.md` when durable intent changes. Update `memory/now.md` when current reality or the next action changes. Change `memory/agreements.md` rarely. Generated AI context bundles remain deferred; canonical memory is small enough to read directly.

## Working agreements and engineering quality

[`memory/agreements.md`](memory/agreements.md) travels with the project so a new assistant does not need the same reminders in every prompt. It includes:

- inspect repository state before making claims
- aim for WCAG AA on interfaces
- maintainable code and practical performance
- proportionate testing
- secrets discipline
- privacy-safe repository content and Git identity
- no AI co-author metadata on commits
- maintained data separated from presentation and logic where practical

The Cursor rule points to agreements. It does not duplicate them.

## Use it with an existing project

Do not copy the whole foundation over an established repository. Add the `memory/` spine, point to useful existing docs, remove duplicates only after review, keep historical evidence outside default context, and rewrite Git history only when privacy or attribution debt justifies it.

## Common questions

**Does it organise everything automatically?** No. It provides structure and reading order. You and your assistants maintain the files through instructed work, subject to review.

**Do I give every AI the whole repository?** No. Begin with the three memory files and inspect task-relevant material only.

**Will this consume lots of credits?** The memory files are concise. Broad repository reading and long accumulated chats cost more.

**Must I use Cursor?** No. Cursor has a convenience rule. The memory model is vendor-neutral.

**Can I use several AIs?** Yes. They should share the same repository truth. Avoid concurrent uncoordinated edits to the same files.

**What happens when I ask for a roadmap?** The assistant should create the smallest durable roadmap document in a sensible project location, add a pointer from `memory/now.md`, and leave unrelated documentation alone. Review the proposed location and content like any other change.

**Must every task update project memory?** No. Update only when intent, current reality or the next action meaningfully changes.

**Does it commit automatically?** No. Commits happen only when you explicitly authorise them, after reviewing identity, diff and verification.

**Can a team use it?** Yes. Treat canonical memory like code and review changes together.

**What happens when an AI gets something wrong?** Correct the memory file and the affected artefact. Do not rely on the old conversation.

## Current status

Early but usable, at **v0.3**. Validated on a fictional concept project and a real concept-stage migration trial. Mature-project migration remains future validation. Not yet v1.0.

## Licence and reuse

AI Project Foundation is available under the [MIT License](LICENSE).

You may use, copy, modify and distribute it under the terms of that licence.
