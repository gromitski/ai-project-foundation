# AI Project Foundation — Product Specification

**Status:** Authoritative product definition for rebuild
**Version:** 0.1.2 (specification slice)
**Date:** 2026-07-11
**Branch:** `audit/foundation-repository`
**Evidence:** `docs/investigations/2026-07-11-foundation-repository-audit.md` (Slice 0.1); `docs/investigations/2026-07-11-repository-privacy-inventory.md` (Slice 0.2.1)
**Scope of this document:** Product definition only — not repository structure, templates, scripts or automation design

British English. Vendor-neutral where project truth is concerned.

---

## 1. Executive summary

**AI Project Foundation** is a reusable operating system for the maintainer’s AI-assisted projects. It exists so that a rough idea can become useful investigation, experimentation or implementation with minimal friction, and so that work can pause, resume and move between AI systems without reconstructing the project from memory.

It is not a documentation template, Cursor configuration pack, static-website starter, software framework, technology stack or mandatory methodology. Those may appear later as *expressions* of the foundation; they are not the product.

The current repository (pre-rebuild) fails the governing tests defined below: it forces tier choice, placeholder labour and file deletion before useful work; it ships empty shells as if they were current truth; it dumps documentation indiscriminately into AI context; and it assumes a mature multi-environment web product. Slice 0.1 recommended clean structural replacement. This specification accepts that verdict as the direction of travel and defines what the replacement must *be* and *prove*, without prescribing filenames or folder trees.

v1.0 succeeds when the foundation can initialise a concept quickly, support growth without structural replacement, preserve resumable current memory, keep multiple AIs consistent, generate selective context, activate specialist capability without tiers, uphold proportionate quality expectations, keep unnecessary personal and local-system information out of repositories, and demonstrate materially lower setup friction and context weight than today’s baseline — after real use on a tiny experiment, a concept-stage project, and a mature project.

---

## 2. Problem statement

### What goes wrong today

Starting or resuming an AI-assisted project repeatedly costs attention that should go to the idea:

- The maintainer must explain the same project facts to different AIs.
- Setup and “process documentation” expand before there is anything to operate.
- After months away, reconstructing state from chat history or Git archaeology is unreliable and expensive.
- Agents invent missing context or load irrelevant historical and operational text.
- Mature-project scaffolding (deployment, staging, SEO, release checklists) arrives before it is earned.
- Documentation tiers and template trimming turn adoption into administrative work.

### What the foundation must solve

Provide a stable, progressive operating system that:

1. Accepts rough human intent.
2. Turns that intent into minimum useful project memory with AI help.
3. Keeps a concise, authoritative picture of *now*.
4. Preserves decisions, uncertainty and history without flooding default context.
5. Lets ChatGPT, Cursor and other capable systems reach consistent conclusions from the repository alone.
6. Supports concept through production — and pause — without structural migration.
7. Protects secrets, personal and local-system information, production actions and repository hygiene.
8. Favours momentum and satisfaction over ceremony.

### What failure looks like

If using the foundation consistently delays the first useful slice, forces the user through forms, requires deleting half the clone, or grows context until every session reloads the past, the product has failed — regardless of how complete the documentation tree appears.

---

## 3. Primary user and working pattern

### Primary user

**The maintainer** — the person who owns intent, priorities and approval for a project built with this foundation. Where a public GitHub identity is required, the approved handle is `gromitski`. Use that handle only when the public identity itself is relevant; otherwise prefer neutral role language (`the maintainer`, `the project owner`, `the user`).

### Working characteristics the product must respect

| Characteristic | Product implication |
| -------------- | ------------------- |
| Sessions may last one hour or years | Structure must not assume continuous engagement |
| Many ideas; frequent switching | Low start cost; honest pause/resume |
| Concepts, experiments and public services all valid | Lifecycle describes reality; does not gate progress |
| Early momentum matters | First slice should produce evidence or progress, not a docs marathon |
| Long setup causes loss of interest | Adoption must fit in minutes of intent plus one initialise step |
| Prefers AI for structural documentation and maintenance | Humans decide; agents organise and keep memory tidy |
| Wants product decisions, not administrative forms | No questionnaires or placeholder scavenger hunts |
| Values honest challenge | Agents must inspect and contradict false certainty |
| Values progress, maintainability, low cost, practical outcomes | Cost, cleanliness and visible results are product requirements |
| May return after complete memory wipe | Repository must be sufficient |
| Wants strong technical foundation without speculative over-engineering | Discipline without premature architecture |

### Modes that must not force structural replacement

- One-hour experiment
- Paused after one session
- Resumed after months or years
- Sustained development over a year or more
- Indefinite concept stage
- Mature production service

---

## 4. Product vision

### Central product claim

**AI Project Foundation is the smallest durable operating system that lets the maintainer and multiple AIs share current project truth, grow capability only when reality demands it, and start useful work in the same session as initialisation.**

### Intended experience

1. Create a project repository from the foundation.
2. Write or dictate a few minutes of rough project intent.
3. Ask an AI to initialise the project (instruction supplied by the foundation).
4. Review the AI’s interpretation.
5. Begin a useful first slice in the same session where practical.
6. Expand memory and process only when reality requires it.
7. Pause for hours, months or years.
8. Resume without manually reconstructing the project.
9. Move work between ChatGPT, Cursor and other capable AIs without repeatedly explaining the project.

### What the product is not

- A documentation template to fill in
- A Cursor-only rule pack
- A static website or stack starter
- A software framework
- A predefined technology stack
- A mandatory gated methodology
- A project-management or issue-tracking replacement
- An archive of every conversation

---

## 5. Partnership and multi-AI model

The system must not depend on any vendor retaining conversational memory. **Core project truth is vendor-neutral and lives in the repository.**

Vendor-specific rules may enforce behaviour or provide shorthand. They must not be the sole home of critical project instructions.

### The maintainer

Responsible for intent, priorities, taste, product judgement, significant trade-off approval, approval of commits/pushes/production actions where required, and deciding whether a project continues, pauses or stops.

### ChatGPT

May be used for product and technical architecture, planning, repository examination, review (code, QA, accessibility, performance), strategy, copy, documentation design, cross-document consistency, independent verification, and preparing scoped work for implementation.

### Cursor

May be used for local inspection, implementation, commands, builds and tests, focused changes, debugging, authorised Git operations, and investigation reports.

### Other AI systems

May be used for independent or specialist review (including security, accessibility, performance), alternative approaches, and covering gaps in tool or model capability.

### Consistency expectation

Given the same repository, capable AIs should independently reach materially consistent conclusions about current state, priorities, scope, accepted decisions, unresolved questions, constraints and safe next actions. Disagreement should stem from judgement, not from missing or contradictory memory surfaces.

---

## 6. Governing tests

These tests judge all later design and implementation. Failing a test is a product defect.

### 6.1 Complete memory wipe test

Given only the repository, a capable AI (and the maintainer) must determine:

- what the project is
- why it exists
- lifecycle stage
- what currently exists
- what is being worked on
- what has been completed
- accepted decisions
- remaining uncertainty
- how to work safely
- the next sensible action

The maintainer must not need to read the entire Git history to regain that understanding.

### 6.2 Variable-engagement test

The system must support one-hour experiments, long pauses, multi-year development, indefinite concepts and mature production services **without structural migration merely because the project grew or shrank in intensity.**

### 6.3 Low-friction test

Starting should approximate: create repository → express rough intent → one initialise instruction → review interpretation → start useful work.

It must **not** require the user to:

- choose a documentation tier
- complete a setup questionnaire
- resolve architecture before experimentation
- manually populate multiple empty documents
- remove irrelevant template files
- replace placeholders across the repository
- repeat the same fact in several places
- re-educate different AI systems
- understand the entire foundation before using it

### 6.4 Multi-AI consistency test

ChatGPT, Cursor and another capable AI, given the same repository, reach materially consistent conclusions about state, priorities, scope, decisions, uncertainties, constraints and safe next actions.

### 6.5 Cost test

The system must reduce total AI cost over a project’s life by:

- minimising default context
- minimising always-loaded vendor instructions
- excluding historical reports unless needed
- avoiding duplicated facts
- avoiding irrelevant operational guidance in default load
- supporting targeted retrieval
- keeping generated handoff concise
- exposing context growth
- avoiding documentation whose maintenance costs more than the confusion it prevents

Large context is not automatically better context.

### 6.6 Momentum test

The first meaningful slice should normally produce useful evidence, a prototype, a visible result, a decision-enabling experiment, or a practical implementation step — **not** a lengthy documentation exercise.

### 6.7 Engineering foundation test

Even a small or temporary project should begin with enough technical discipline to grow without a complete rebuild. This must not become speculative architecture. Prefer simple, clean, extensible implementation over disposable shortcuts — without forcing production architecture onto a prototype.

---

## 7. Core principles

### 1. Current truth over historical volume

Default AI context prioritises present state. History remains retrievable; it does not load automatically.

### 2. One memory, one home

Each durable project fact has one canonical home. Other material may link; it should not restate unnecessarily.

### 3. Human intent can be rough

Incomplete, informal or unstructured intent is valid input. AI organises it without pretending unresolved questions are settled.

### 4. Uncertainty is valid project state

Use explicit states such as: unknown, assumed, proposed, investigating, accepted, rejected, superseded, deferred. Do not force decisions to make documentation look complete.

### 5. Stable core, progressive capability

The canonical core remains valid from concept to mature project. Specialist documentation and capabilities appear when a real trigger exists. Adding them must not reorganise or replace the core. Do not stub every future concern on day one.

### 6. Documentation must earn its maintenance cost

Every maintained file must preserve a distinct useful form of memory. If two files preserve the same memory, one should normally be removed, narrowed or generated.

### 7. Historical evidence must remain retrievable

Investigations, experiments, audits and rejected approaches stay available where useful, outside normal context.

### 8. AI must inspect, not assume

Agents verify repository, branch, configuration and implementation state before claims. Conversation memory is useful context, not authoritative project truth.

### 9. Project truth must be vendor-neutral

Critical state, principles and constraints must be accessible without Cursor. Vendor rules may enforce behaviour; they must not duplicate project truth unnecessarily or hide critical rules.

### 10. Smallest useful change

Work is normally small, testable slices with clear acceptance criteria. Avoid broad refactors and process expansion without demonstrated need.

### 11. Safety requires explicit authority

Commits, pushes, destructive operations, production changes, secrets handling and cost-incurring infrastructure actions require explicit rules and approval where appropriate.

### 12. Generated context must be selective

Generated AI context uses deliberate inclusion rules. It must not recursively concatenate all documentation by default.

### 13. Default agent instructions must also be selective

Cost control applies to vendor rules and automatic instructions. A small script must not automatically load detailed guidance about production deployment, analytics, routing or other irrelevant domains.

### 14. Accessibility is a baseline requirement

Projects with a user interface should aim for WCAG AA. Even in prototypes, fundamentals apply where relevant: semantic structure, keyboard access, visible focus, labels and accessible names, sensible contrast, readable content, usable error handling, and progressive enhancement where appropriate. Temporary limitations may be documented; accessibility is not bolted on later.

### 15. Usability includes performance

For interactive or user-facing systems, performance is part of usability. Encourage fast startup, responsive interaction, proportionate payloads, avoidance of unnecessary dependencies, evidence-based decisions, and realistic-device testing where relevant — proportionate to project scale.

### 16. Clean code is continuous work

Code should be clear, maintainable and appropriately structured from the start. Agents should remove dead code, avoid unnecessary duplication, use clear names and boundaries, refactor while context is fresh, and avoid knowingly leaving avoidable structural debt — without speculative abstraction or unrelated refactoring.

### 17. Small projects may grow

A one-hour experiment may later matter. Avoid disposable patterns that make growth unnecessarily painful. Provide sensible structure and hygiene without forcing production architecture onto a prototype.

### 18. Separate data from presentation and application logic

Where practical, maintainable data and content should be separated from presentation and executable logic (for example JSON, YAML, Markdown, text, APIs, databases or generated artefacts). Mechanism depends on needs. Do not hard-code significant maintainable data into presentation code without good reason.

### 19. Security is never optional

Proportionate security from the beginning: never commit secrets; validate untrusted input; use safe dependency and configuration practices; avoid unnecessary exposure; apply least privilege where relevant; handle authentication and authorisation deliberately; consider privacy and retention; document significant security assumptions. Match the actual threat and shape; do not postpone security as a generic later task.

### 20. Testing must have a natural home

Projects begin with a clear path for consistent verification: simple repeatable checks; automated tests where valuable; fixtures where appropriate; build/lint verification; accessibility checks for interfaces; integration or end-to-end tests when justified; documented manual checks when automation is not proportionate. A large suite is not required on day one; redesigning later for testing must not be required either.

### 21. Foundation metadata and project truth must be separate

Foundation maintenance history, provenance and adoption instructions must not become inherited project truth. A project created from the foundation should contain only what that project and its AIs need.

### 22. The system should create satisfaction

The foundation succeeds only if it helps the maintainer enjoy making progress. Process that repeatedly delays visible or useful progress is a product failure.

### 23. Personal and local information stays out of repositories

Repositories must not contain unnecessary personally identifiable information, sensitive personal context or local-system details.

The only approved personal identifier for this maintainer on GitHub is the public handle `gromitski`.

Agents must inspect proposed files, logs, reports, screenshots, configuration and commit metadata for accidental disclosure before committing or pushing.

Protected information includes, but is not limited to:

- real names
- personal email addresses
- postal addresses
- telephone numbers
- dates of birth
- family details
- private employment information
- local usernames
- computer or device names
- hardware identifiers
- private filesystem paths
- private IP addresses and local network information
- private service or repository URLs
- authentication material, credentials and secrets
- logs, screenshots or diagnostic output containing any of these

Use neutral role descriptions such as `the maintainer`, `the project owner` or `the user` unless an approved public handle is genuinely required.

Private repositories are not an exemption. Repository content and Git history must be treated as durable and potentially exposed.

Sensitive information required for local operation belongs in ignored local configuration, secret stores or documented placeholders — never committed values.

---

## 8. Required capabilities

For each capability: problem solved, minimum acceptable behaviour, what must remain flexible, what must not happen. **No filenames or directories.**

### 8.1 Rough-intent capture

| | |
| - | - |
| **Problem** | Useful work cannot wait for polished documentation. |
| **Minimum** | Accept short informal intent (typed or dictated) without prior structure. Preserve it as identifiable project input. |
| **Flexible** | Medium, length and formality of the raw input. |
| **Must not** | Require questionnaires, multiple empty documents, or architecture decisions first. |

### 8.2 Project initialisation

| | |
| - | - |
| **Problem** | Manual structuring and placeholder filling kill momentum. |
| **Minimum** | From rough intent, an AI produces minimum useful project memory, states uncertainties honestly, and proposes a sensible first slice. Foundation supplies the initialise instruction. |
| **Flexible** | Which AI performs initialisation; depth of first interpretation. |
| **Must not** | Pretend unknowns are decided; invent stack/hosting/branch model as required truth; leave the user to populate many shells manually. |

### 8.3 Current project state

| | |
| - | - |
| **Problem** | Memory wipe and multi-AI consistency need one authoritative “now”. |
| **Minimum** | One concise view of where the project stands: purpose summary, lifecycle stage, what exists, active focus pointer, major uncertainties, safe next action. |
| **Flexible** | Presentation format. |
| **Must not** | Duplicate status across many maintained surfaces; mix historical narrative into the default “now” view; present empty template text as reality. |

### 8.4 Durable product intent

| | |
| - | - |
| **Problem** | Why the project exists is lost when chats end. |
| **Minimum** | Preserve why it exists, who it serves, intended value, product principles, non-goals and major assumptions. |
| **Flexible** | How intent evolves from rough capture into durable form. |
| **Must not** | Force completeness; silently overwrite unresolved points as facts. |

### 8.5 Current work

| | |
| - | - |
| **Problem** | Without an active slice signal, AIs invent scope or resume the wrong work. |
| **Minimum** | Identify the active slice: goal, scope, exclusions, completion criteria, status. |
| **Flexible** | Slice size and naming. |
| **Must not** | Turn every thought into permanent work items; conflate roadmap with active work. |

### 8.6 Roadmap

| | |
| - | - |
| **Problem** | Direction is needed without project-management theatre. |
| **Minimum** | Retain near-term direction and meaningful milestones lightly. |
| **Flexible** | Horizon and density. |
| **Must not** | Become an exhaustive backlog or issue tracker substitute. |

### 8.7 Decisions

| | |
| - | - |
| **Problem** | Accepted choices and rationale die with conversation. |
| **Minimum** | Durable record of accepted decisions with enough rationale to prevent re-litigation. Uncertainty states remain visible where relevant. |
| **Flexible** | Granularity; when a dedicated record is warranted. |
| **Must not** | Record trivial or easily reversible implementation noise; treat investigation findings as accepted decisions. |

### 8.8 Technical reality

| | |
| - | - |
| **Problem** | Agents must know how the project works — or that it does not yet. |
| **Minimum** | When implementation exists, explain current behaviour and structure honestly. Before implementation, say so explicitly. |
| **Flexible** | Depth and medium. |
| **Must not** | Describe fictional architecture; assume a web stack. |

### 8.9 Development and operation

| | |
| - | - |
| **Problem** | Commands, environments, deploy and troubleshooting matter only when relevant. |
| **Minimum** | Become available when the project has something to run, deploy or maintain. |
| **Flexible** | Hosting, branch model, tooling. |
| **Must not** | Pollute concept-stage default context with fictional production infrastructure. |

### 8.10 Quality expectations

| | |
| - | - |
| **Problem** | Accessibility, usability, performance, maintainability, code quality, security, privacy, reliability, data accuracy and testing need a home without early ceremony. |
| **Minimum** | Proportionate baseline expectations always apply where relevant (especially a11y for UI, security always, verification path for implementation). Specialist depth appears when complexity justifies it. |
| **Flexible** | Depth and tooling per domain. |
| **Must not** | Defer fundamentals with “it’s only a prototype”; load specialist manuals into every tiny project’s default context. |

### 8.11 Historical investigations

| | |
| - | - |
| **Problem** | Long or risky investigations must survive without becoming current truth. |
| **Minimum** | Preserve decision-heavy investigations retrievably; exclude them from default context. |
| **Flexible** | When an investigation earns a permanent record. |
| **Must not** | Dump all investigations into generated default context; confuse findings with decisions. |

### 8.12 Resumption

| | |
| - | - |
| **Problem** | After long absence, next useful action is obscure. |
| **Minimum** | Repository makes next sensible action discoverable from current state and current work, within about ten minutes of focused reading. |
| **Flexible** | How pointers are expressed. |
| **Must not** | Require chat archaeology or full history review as the normal path. |

### 8.13 Multi-AI handoff

| | |
| - | - |
| **Problem** | Work stuck in one vendor’s conversation cannot continue elsewhere. |
| **Minimum** | After meaningful work, repository state alone is enough for another AI to continue without a bespoke verbal handoff. |
| **Flexible** | Whether a generated handoff artefact is used as an aid. |
| **Must not** | Make critical truth local-only (for example editor-only state) if it is claimed as shared project memory. |

### 8.14 Context generation

| | |
| - | - |
| **Problem** | Unselective concatenation is expensive and misleading. |
| **Minimum** | Produce concise, reproducible AI context from deliberately selected sources, with clear inclusion rules. Prefer current truth; exclude history and foundation meta by default. |
| **Flexible** | Whether committed, generated on demand, or both; task-selective variants. |
| **Must not** | Recursively concatenate all documentation by default; treat generated context as the place to edit permanent truth. |

### 8.15 Context-cost observability

| | |
| - | - |
| **Problem** | Context inflation is invisible until sessions become expensive and confused. |
| **Minimum** | Make it possible to inspect included files, excluded files, generated context size, always-loaded vendor instruction size, and growth over time. |
| **Flexible** | Tooling and reporting format. |
| **Must not** | Optimise for scoreboards instead of usable sessions; hide always-on rule weight. |

### 8.16 Freshness and contradiction control

| | |
| - | - |
| **Problem** | Stale or contradictory memory misleads every AI equally. |
| **Minimum** | Make staleness and contradiction easier to detect (for example conflicting status, duplicate facts, decisions that disagree with implementation notes). Perfect automatic code-to-document verification is not assumed. |
| **Flexible** | Detection method. |
| **Must not** | Claim guaranteed sync with code; rely on duplicate restatements “just in case”. |

### 8.17 Version-based development

| | |
| - | - |
| **Problem** | Work needs milestones and slices without treating every change as a public release. |
| **Minimum** | Support broad milestones, small implementation slices, internal development versions, and public releases where relevant. |
| **Flexible** | Version scheme per project. |
| **Must not** | Force public release ceremony on every slice; invent version theatre at concept stage. |

### 8.18 Progressive capability activation

| | |
| - | - |
| **Problem** | Specialist areas (deploy, analytics, data governance, production ops, deep a11y/security docs, etc.) appear at different times. |
| **Minimum** | Activate when triggered by real needs. Core structure remains. |
| **Flexible** | Triggers and depth. |
| **Must not** | Require tier selection; require replacing the core; pre-create every specialist document. |

### 8.19 Foundation / project separation

| | |
| - | - |
| **Problem** | Provenance and adoption material pollute product AI context (Slice 0.1 evidence). |
| **Minimum** | Foundation maintainer material and project truth occupy separate planes. New projects inherit only what they need. |
| **Flexible** | Distribution mechanism (design later). |
| **Must not** | Ship BlooPlax extraction notes or long foundation manuals into product default context. |

### 8.20 Archiving

| | |
| - | - |
| **Problem** | Completed or superseded material must leave active context without being lost. |
| **Minimum** | Clear destination outside active context for completed, superseded or retired material. |
| **Flexible** | Archive medium and retention. |
| **Must not** | Delete useful history by default; leave retired material in default AI load. |

### 8.21 Repository safety

| | |
| - | - |
| **Problem** | Secrets, dumps, personal identifiers, local-system details and destructive operations create irreversible harm. |
| **Minimum** | Protect secrets and credentials; keep personal and local-system information out of tracked content and commit metadata (principle 23); keep local editor state out of shared truth unless intentional; avoid generated waste and large raw dumps in the repo; constrain destructive operations; avoid inappropriate AI authorship metadata in commits when the maintainer requires clean human authorship. Agents must inspect files and metadata before commit or push. |
| **Flexible** | Ignore rules per stack; local secret-store tooling. |
| **Must not** | Treat hygiene or privacy as optional after “just this once”; commit `.env` or equivalent; commit real names, personal emails, private paths, hostnames, hardware identifiers or similar; leave AI co-author trailers when clean authorship is required. |

---

## 9. Lifecycle model

Lifecycle vocabulary exists to **describe** reality, not to control it.

Suggested labels (non-exhaustive, non-mandatory sequence):

| State | Meaning (plain) |
| ----- | --------------- |
| **concept** | Idea and intent; little or no implementation |
| **feasibility** | Checking whether the idea is worth pursuing |
| **prototype** | Disposable-tolerant exploration with basic hygiene still applying |
| **active development** | Building toward a usable result |
| **private testing** | Real use by a limited audience |
| **public** | Exposed beyond private testing |
| **maintenance** | Stable; changes are corrective or small |
| **paused** | Intentionally inactive; should be resumable |
| **archived** | No longer active; retained for reference |

A project may skip states, return to earlier states, remain in one state indefinitely, or stop at any point. Lifecycle must not become a gated methodology.

---

## 10. Scope boundaries

The foundation does **not** aim to:

- choose a technology stack
- impose a framework
- mandate a hosting provider
- require a particular branch model
- replace issue trackers or project-management tools
- require pull requests for solo work
- retain every conversation transcript
- generate documentation for its own sake
- guarantee documentation always matches code
- make every project production-ready
- force abandoned ideas through formal closure
- prescribe which AI must perform each task
- automate production actions without approval
- optimise for hypothetical teams at the expense of the maintainer’s workflow
- pre-create every specialist document
- require speculative abstractions
- require comprehensive test coverage before experimentation
- treat temporary prototypes as exempt from basic accessibility, security or code hygiene

---

## 11. Adoption experience

### Target path

1. Create a repository from the foundation.
2. Write or dictate rough intent.
3. Ask an AI to initialise (foundation-supplied instruction).
4. Review the interpretation.
5. Begin the first useful slice.

Normal use must not require reading a long adoption manual or choosing a tier.

### Concept-stage freedom

A concept project must **not** need to customise before useful work begins:

- deployment
- branch strategy
- technology stack
- analytics
- production infrastructure
- specialist quality documentation

### Relation to Slice 0.1 findings

This adoption path **rejects** the current foundation’s tiered Minimal/Standard/Full model, placeholder replacement ritual, and “delete what you don’t need” adoption (audit §4 items 1–3, §11). The *need* for an onboarding path is retained; the *form* must invert from subtractive template labour to initialise-from-intent.

---

## 12. Success measures

### Observable targets

| Target | Intent |
| ------ | ------ |
| Initial intent capturable in under ten minutes | Protect momentum |
| Initialisation does not require the user to populate multiple documents manually | AI does structural work |
| First useful slice normally begins in the same session | Momentum test |
| Dormant project understandable from the repository in under ten minutes | Memory wipe / resumption |
| Default generated AI context excludes historical investigations | Cost test |
| Core facts not deliberately duplicated across maintained files | One memory, one home |
| Another AI can continue active work without bespoke verbal handoff | Multi-AI |
| Structure remains valid from concept through production | Variable engagement |
| Setup does not require choosing a tier | Low friction |
| Normal use does not require a long adoption manual | Low friction |
| Small project not burdened by fictional production infrastructure | Progressive capability |
| Mature project can add operational depth without reorganising the core | Stable core |
| Context size and included sources can be measured | Observability |
| Accessibility basics not deferred on user-facing work | Principle 14 |
| Security and secret-handling apply from the start | Principle 19 |
| Personal and local-system information stays out of repositories and commit metadata | Principle 23 |
| Clear verification path from first implementation slice | Principle 20 |
| Code quality can improve continuously without emergency refactors | Principle 16 |
| Maintained data separable from presentation/logic where practical | Principle 18 |

### Current foundation baseline (comparison evidence from Slice 0.1)

Later design must improve **materially** on:

| Baseline | Approximate value |
| -------- | ----------------- |
| Prose weight | ~9,590 words |
| Files in generated AI memory | 16 |
| Generated context size | ~47 KB |
| Always-applied Cursor rules | 6 |
| Adoption model | Long, tiered, placeholder-heavy |

This specification does **not** set arbitrary final numeric caps. Design slices must show clear reduction in setup friction and default context weight relative to this baseline, without sacrificing the governing tests.

---

## 13. Anti-patterns

Warning signs that the foundation is drifting:

- Adding documents because another methodology includes them
- Copying BlooPlax structures without proving they are universal
- Making agents read the full documentation tree by default
- Making all vendor rules always apply
- Treating empty template text as project truth
- Repeating current version, branch or status in several places
- Adding process before a real problem exists
- Creating permanent files for every slice
- Recording trivial decisions
- Confusing investigation findings with accepted decisions
- Hiding critical rules only in Cursor configuration
- Requiring the user to understand the foundation before using it
- Optimising for hypothetical collaborators instead of actual use
- Adding automation whose maintenance exceeds its benefit
- Allowing this specification itself to become ceremony
- Using “prototype” to justify inaccessible or insecure implementation
- Writing throwaway code where a simple clean solution would take similar effort
- Performing speculative refactors unrelated to the active slice
- Hard-coding maintainable project data into UI code without reason
- Bolting testing, security or accessibility onto a mature project after avoidable early neglect
- Shipping foundation provenance into product repositories as if it were project truth
- Subtractive tiers as the answer to progressive needs
- Committing unnecessary personally identifiable information, local-system details or private operational data
- Using real personal names or personal email addresses in repository content or commit metadata when an approved public handle or neutral role language suffices
- Treating private repositories as safe for durable personal or local-system disclosure

---

## 14. Open design questions

Do **not** resolve final repository architecture here. Unresolved questions include:

1. What is the smallest permanent project memory spine?
2. Which capabilities need permanent homes?
3. Which capabilities should appear only when triggered?
4. Where does rough human intent live initially?
5. Does rough intent remain permanently, or get absorbed into durable product memory?
6. What is the exact canonical current-state model?
7. How is active work represented?
8. Should generated AI context be committed?
9. Is one generated context enough?
10. Should context be task-selective?
11. How should inclusion and exclusion rules be declared?
12. How small should default generated context be?
13. How small should always-loaded vendor guidance be?
14. What belongs in vendor-neutral guidance vs Cursor-specific enforcement?
15. How should accessibility, performance, security, testing and clean-code rules be enforced without excessive default context?
16. How should stale documentation be detected?
17. When does an investigation earn a permanent file?
18. When does a decision earn a dedicated decision record?
19. Should completed slice specifications be archived or left to Git history?
20. How much project initialisation can be automated safely?
21. What version model suits concept-stage projects?
22. How can the foundation generate a clean project without copying foundation provenance?
23. Should foundation-maintainer material live in a separate branch, directory or distribution process?
24. Should historical AI co-authorship remain in Git history?
25. Should v1.0 begin from a clean root commit?
26. How should existing mature projects migrate without losing useful history?
27. How should separation of data from application logic be expressed across different stacks?
28. What minimum testing foundation is universal without becoming framework-specific?
29. How is lifecycle stage recorded so it stays honest and cheap to update?
30. What is the trigger taxonomy for progressive capability activation?
31. How should multi-AI handoff work when some tools lack direct repository access?
32. How will satisfaction and token cost be measured in practice so dump culture does not return?
33. What is the relationship between investigation paths used in practice and any default archive convention (Slice 0.1 already saw path rigidity conflict with real work)?

### Audit conclusions: accepted, refined, challenged

| Audit conclusion | Spec stance |
| ---------------- | ----------- |
| Clean structural replacement over incremental trim | **Accepted** as rebuild direction for the product; implementation timing remains a design/delivery question. |
| Retain behavioural principles (inspect, investigate-first, explicit Git approval, hygiene, selective memory intent) | **Accepted** and expanded into principles 8–13, 19–21, 23 and quality principles 14–20. |
| Accessibility/performance should not be always-on Cursor load for every project type | **Refined:** fundamentals remain baseline *requirements* for UI work (principle 14–15); *delivery* into default agent context must stay selective (principle 13). Not a licence to ignore a11y in prototypes. |
| Evidence-first performance framework is valuable | **Accepted** as method when performance work occurs; not as mandatory furniture for concept repos. |
| Gitignored full memory dump hurts multi-AI | **Accepted** as a problem statement. Whether selective context is committed is **open** (questions 8–11); the dump approach itself remains rejected. |
| Numbered empty `docs/00–11` set should not be mandatory | **Accepted.** |
| Tiers must go | **Accepted.** |
| Prompt library “unknown/change” | **Refined:** scoped-prompt discipline is valuable; a mature-web prompt pack is not a v1 requirement. Design later. |
| “Docs win over rules for deployment truth” | **Accepted** in spirit as vendor-neutral truth wins; exact split remains open (question 14). |
| Audit listed a11y/perf always-on as mainly a cost/bias problem | **Challenged in emphasis:** cost control stands, but this specification elevates accessibility and security to non-optional quality floors for relevant work — selective loading must not become selective *neglect*. |

---

## 15. Definition of v1.0 success

v1.0 of AI Project Foundation is achieved when the product:

1. **Initialises** a new concept quickly from rough intent using a foundation-supplied instruction.
2. **Supports real development** without structural replacement of the core.
3. **Preserves enough current memory** for complete resumption after memory wipe.
4. **Supports multiple AIs** reaching consistent conclusions from the repository.
5. **Generates selective context** with observable inclusion/exclusion and size.
6. **Adds specialist capability** without tiers or core restructuring.
7. **Maintains** proportionate expectations for accessibility, usability, performance, code quality, security, privacy, data separation and testing.
8. **Keeps** unnecessary personally identifiable information and local-system details out of repository content and Git metadata (principle 23), using only approved public handles where identity is required.
9. **Has been tested** on at least:
   - a tiny experiment
   - Wye Trains or another concept-stage project
   - BlooPlax or another mature project
10. **Demonstrates** materially lower setup friction and default context weight than the Slice 0.1 baseline (~9.6k words prose, 16-file / ~47 KB dump, six always-applied Cursor rules, long tiered adoption).

v1.0 is **not** achieved by finishing a folder tree, renaming documents, or writing more process. It is achieved when the governing tests pass in real use.

---

## Document control

| Item | Value |
| ---- | ----- |
| Product name | AI Project Foundation |
| Spec role | Authoritative product definition for rebuild |
| Non-goals of this slice | Final structure, filenames, templates, scripts, automation design, merge to `main` |
| Next work | Design slices constrained by this specification and the Slice 0.1 audit evidence |
