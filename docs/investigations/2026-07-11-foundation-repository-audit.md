# Foundation repository audit — Slice 0.1

**Date:** 2026-07-11  
**Scope:** Entire `ai-project-foundation` repository (docs, Cursor rules, scripts, Git state, adoption surface)  
**Method:** Full file read, Git history (`1830ddc`, `2640c19`), placeholder and inheritance scans, dry-run of `scripts/generate-ai-project-memory.mjs` (output deleted after measurement; not retained)  
**Status:** Audit only — no redesign; no commits; only this report and `docs/investigations/` created  

**Governing tests applied:** complete memory wipe, variable engagement, low-friction, multi-AI, cost  

---

## 1. Executive summary

The repository is a **well-intentioned extraction of mature-product process** from a static-first web project (BlooPlax), not yet an operating system for projects that start as vague ideas.

What works: clear investigation-before-implementation discipline; commit/push safety; secrets hygiene; evidence-first performance thinking; separation of human docs from Cursor shorthand; honest maintainer provenance.

What fails the governing tests: adoption requires **tier choice, placeholder replacement, and file deletion** before useful work; “current truth” is empty template shells that still load into AI context; the memory script is a **full recursive dump** of `docs/` (gitignored by default, so remote AIs cannot use it); structure and always-on rules assume a **deployed multi-environment web app**.

**Verdict:** Retain principles and a few behavioural patterns as design evidence. Do **not** treat the current file set as the permanent foundation. Prefer a **clean structural replacement** informed by this evidence over incremental trimming of the existing template.

---

## 2. Current repository inventory

### Git and workspace state (evidence)

| Fact | Evidence |
| ---- | -------- |
| Single branch | `main` only; tracks `origin/main` |
| Commits | `1830ddc` initial foundation (25 files); `2640c19` README/adoption/maintainer polish (`TEMPLATE_NOTES.md` → `MAINTAINER_NOTES.md` + `docs/11-using-this-template.md`) |
| Remote | `git@github.com:gromitski/ai-project-foundation.git` |
| Untracked local | `.obsidian/` (not part of foundation; local-only) |
| No app code | No `package.json`, `src/`, CI, or env examples |

The foundation **documents** a three-branch promotion model but **does not use it itself**.

### Root

| Path | Purpose | Audience | Neutral vs inherited | Overlap |
| ---- | ------- | -------- | -------------------- | ------- |
| `README.md` | Template pitch, tiers, quick start | Human + AI entry | Neutral intent; assumes Cursor + optional ChatGPT | Duplicates tiers/setup with `docs/11`, maintainer themes with `MAINTAINER_NOTES` |
| `MAINTAINER_NOTES.md` | Provenance (BlooPlax), what not to copy, foundation maintenance | Human (foundation maintainers) | Explicitly BlooPlax-aware | Tier table again; placeholder table overlaps `docs/11` |
| `.gitignore` | Secrets, build dirs, `data/raw/`, generated memory | Operational | Stack-biased (`node_modules`, Astro/Next); `data/raw/` is product-pipeline smell | Policy restated in hygiene rule + folder guide |
| `.obsidian/` | Local Obsidian config | Local only | N/A | Invisible to remote/multi-AI |

### `.cursor/rules/` (all `alwaysApply: true`)

| Path | Purpose | Audience | Neutral vs inherited | Overlap |
| ---- | ------- | -------- | -------------------- | ------- |
| `00-project-behaviour.mdc` | Read docs, small scope, investigate first, explicit commit/push | AI (Cursor) | Largely universal | Mirrors `docs/ai/00-ai-memory-core.md` workflows |
| `01-code-quality.mdc` | Focused diffs, conventions, verify | AI (Cursor) | Universal for code work; weak for non-code projects | Partial overlap with prompt library “scoped implementation” |
| `02-git-and-release.mdc` | Three-branch model + Stu shorthands | AI (Cursor) | **Inherited maturity assumption** | Near-duplicate of `docs/04-git-workflow.md` |
| `03-documentation.mdc` | Don’t auto-rewrite docs; audits under `docs/audits/` | AI (Cursor) | Useful discipline; audit path is rigid | Overlaps audits README + AI memory core |
| `04-accessibility-performance.mdc` | Evidence-first a11y/perf priorities | AI (Cursor) | Universal *as principles*; **always-on for every project type is inherited** | Near-duplicate of `docs/06` + `docs/07` |
| `05-repository-hygiene.mdc` | No secrets/dumps | AI (Cursor) | Universal | Overlaps `.gitignore` commentary + folder guide |

### `docs/` numbered guides

| Path | Purpose | Audience | Neutral vs inherited | Overlap |
| ---- | ------- | -------- | -------------------- | ------- |
| `00-overview.md` | Intended single source of project status | Human + AI | Shell assumes production/staging/SEO/analytics | Referenced everywhere; links missing `roadmap.md` |
| `01-how-it-works.md` | Runtime/user flows | Human + AI | Assumes interactive product with routing | Overlaps overview purpose for “what exists” |
| `02-local-development.md` | Clone, npm, verify | Human + AI | Assumes Node web app | Overlaps troubleshooting |
| `03-deployment.md` | Host, env vars, deploy checks | Human + AI | Multi-env + indexing gates | Overlaps release procedure + git workflow |
| `04-git-workflow.md` | Branch promotion detail | Human + AI | Three-branch default | Duplicate of Cursor rule `02` |
| `05-decisions-and-rationale.md` | Decision index + static-first example | Human + AI | **Static-first as default example** | Overlaps ADR `0001` |
| `06-accessibility.md` | A11y baseline | Human + AI | Web UI assumptions | Duplicate of rule `04` |
| `07-performance.md` | Perf measurement framework | Human + AI | Web payload/SW assumptions | Duplicate of rule `04` |
| `08-troubleshooting.md` | Layered debug tables | Human | Web/CDN/data-pipeline flavoured | Overlaps local + deploy docs |
| `09-release-procedure.md` | Milestone → production checklist | Human + AI | Mature product release | Overlaps deploy + git |
| `10-folder-guide.md` | Where things live | Human + AI | Assumes `src/`, `public/`, `dist/`, CI | Conflicts with “empty concept” repos |
| `11-using-this-template.md` | Adoption how-to (~1.3k words) | Human (adopters) | Foundation meta, not product truth | Duplicates README; **included in AI memory dump** |

### `docs/ai/`

| Path | Purpose | Audience | Neutral vs inherited | Overlap |
| ---- | ------- | -------- | -------------------- | ------- |
| `00-ai-memory-core.md` | Roles Stu/ChatGPT/Cursor; workflows | Human + all AIs | Vendor-aware but useful | Overlaps behaviour rule + prompt library |
| `10-prompt-library.md` | Eight copy-paste prompts | Human | Mature web project prompts (release, a11y, perf) | Encodes same workflows as rules/docs |
| `01-ai-project-memory.md` | Generated concatenation | Generated; gitignored | N/A when absent | Would duplicate *all* of the above into one file |

### `docs/audits/`, `docs/decisions/`, `scripts/`

| Path | Purpose | Audience | Neutral vs inherited | Overlap |
| ---- | ------- | -------- | -------------------- | ------- |
| `audits/README.md` | Audit taxonomy + conventions | Human + AI | Categories: code/data/ux/**seo**/analytics/perf/**lighthouse** — web-product taxonomy | Rule `03` hard-codes this path |
| `decisions/0001-project-shape.md` | Example ADR: static-first, no backend | Human + AI | **Strong BlooPlax-shaped default** | Overlaps `05-decisions` |
| `scripts/generate-ai-project-memory.mjs` | Walk all `docs/**/*.md`, concatenate | Operational | Cost-blind dump; skips only named dirs (`lighthouse`, `brand`, `.obsidian`) | Policy described in README, `.gitignore`, AI core, rule `03` |

### Referenced but missing

| Reference | Where | Issue |
| --------- | ----- | ----- |
| `docs/roadmap.md` | `00-overview.md`, `09-release-procedure.md` | Linked optional roadmap does not exist |
| Audit subfolders (`code/`, `ux/`, …) | `audits/README.md` | Documented; not created (OK as stubs, but taxonomy already steers shape) |

---

## 3. Classification table

| Item | Class | Reason |
| ---- | ----- | ------ |
| Investigation-before-implementation discipline | **Keep** (principle) | Passes safety and memory-wipe “resume safely” if findings are written down |
| Explicit commit/push; production needs confirmation | **Keep** (principle) | Universal; low cost |
| Secrets / raw-dump hygiene | **Keep** | Universal; low friction |
| Evidence-first performance questions (resource/size/benefit/trade-off) | **Keep** (principle) | Universal when performance work happens; should not be always-on scaffolding |
| Human-maintained operational docs as source of truth | **Keep** (principle) | Aligns with multi-AI and inspect-repo tests |
| Cursor rules as *shorthand* with docs canonical for deploy truth | **Keep** (principle) | Correct vendor split; current *content* still drifts |
| `00-overview.md` as “current status” role | **Change** | Role is right; content shape assumes mature web product and empty shells fail memory-wipe |
| Focused multi-file Cursor rules vs one mega-rule | **Change** | Structure OK; `alwaysApply` + product assumptions wrong for foundation |
| AI collaboration roles (`00-ai-memory-core.md`) | **Change** | Needed; too Cursor/ChatGPT-specific and assumes generated dump workflow |
| ADR idea (`docs/decisions/`) | **Change** | Useful; seed ADR must not pre-decide static-first |
| Dated investigation/audit files | **Change** | Preserve history-without-pollution intent; path/taxonomy too web-specific and currently forces `audits/` only |
| Git promotion shorthands (“commit to dev/staging/main”) | **Change** | Valuable *when* multi-branch exists; harmful as default for single-branch/experiment repos |
| Numbered `docs/00–10` operational set | **Change** / mostly **Remove** as mandatory set | Real need emerges per project; shipping empty shells creates burden and false context |
| Tiered Minimal/Standard/Full adoption | **Remove** | Directly fails low-friction test (forces choice + trimming) |
| `docs/11-using-this-template.md` as required adoption surface | **Remove** / **Archive** | Longer than many tasks it enables; process should shrink to minutes of intent + AI init |
| Placeholder-heavy template filling ritual | **Remove** as adoption model | Fails low-friction and variable-engagement |
| Memory script as full `docs/` concatenation | **Remove** (implementation) | Fails cost test; keep *selective context* as a future requirement |
| Default gitignore of generated memory | **Change** | Correct that dumps shouldn’t be canonical; wrong if remote multi-AI needs committed selective context |
| `0001` static-first ADR | **Archive** (as seed content) | Lesson (defer backend until needed) can be universal; file as default decision is not |
| Audit taxonomy seo/analytics/lighthouse | **Archive** / **Remove** from foundation defaults | BlooPlax-shaped; recreate when a project needs them |
| `04-accessibility-performance.mdc` always applied | **Change** | Principles keep; always-on Cursor load for non-UI projects is waste and bias |
| `MAINTAINER_NOTES.md` BlooPlax provenance | **Archive** relative to product repos; **Keep** in foundation history | Correct as extraction evidence; must not ship into new projects |
| `.gitignore` Node/Astro/Next/`data/raw/` | **Change** | Hygiene keep; stack and pipeline paths are premature |
| `docs/10-folder-guide.md` assuming `src/public/dist` | **Change** / **Remove** as fixed layout | Forces rename/reorg for non-web or concept-only repos |
| Prompt library (8 prompts) | **Unknown** / lean **Change** | Useful patterns; current set encodes mature web lifecycle |
| Optional `project-status.mdc` | **Remove** as recommended pattern | Docs themselves warn it goes stale; duplicates overview |
| Foundation README describing tiers | **Change** | README should describe the future OS, not trimming rituals |

---

## 4. Friction findings

Ranked largest sources of friction when adopting today:

1. **Tier selection + trimming** — README and `docs/11` require choosing Minimal/Standard/Full and deleting files/sections. Violates: “must not choose documentation tiers” / “must not delete irrelevant files before beginning.”

2. **Placeholder replacement across many files** — Angle-bracket tokens appear in overview, deploy, git, rules, AI docs, prompts, ADR, release (~hundreds of replacement sites across ~20 files). Useful work is gated on a search-replace pass. Violates low-friction and “AI should help turn unstructured intent into structure.”

3. **Empty shells treated as required reading** — Rules say read `docs/` especially `00-overview` before substantial work. After clone, overview is still placeholders. Agents and humans either invent facts or waste tokens on blank tables. Fails memory-wipe and cost tests.

4. **Assumed maturity: three environments + release procedure** — Staging rows, indexing gates, promotion flow, and release checklists appear before any code exists. Experiments must edit or delete process they do not need.

5. **Assumed stack: Node web app** — Local dev, folder guide, `.gitignore`, troubleshooting, and prompts assume npm/`src`/`dist`. Concepts, scripts, and non-JS work start by fighting the template.

6. **Adoption guide length** — `docs/11-using-this-template.md` alone is ~1.3k words; total foundation prose ~9.6k words. Setup documentation exceeds “few minutes of rough intent.”

7. **Duplicated configuration surfaces** — Branch names and domains must stay aligned across `docs/04`, rule `02`, overview, deploy, release. Drift is inevitable; multi-AI consistency fails when surfaces diverge.

8. **Generated memory unavailable via GitHub (default)** — Gitignored `01-ai-project-memory.md` means ChatGPT/remote inspection cannot rely on the handoff file unless someone regenerates and uploads or changes policy. Multi-AI test fails for the advertised ChatGPT path unless extra steps are taken.

9. **Local-only state** — `.obsidian/` (and optionally gitignored `.cursor/`) cannot be seen by another AI on GitHub. Project truth that lives only there is invisible.

10. **Misleading seed decisions** — Static-first ADR and decision summary present a chosen architecture before the project has one. Premature resolution of uncertainty.

11. **Missing roadmap file still linked** — Small but real: broken optional link trains agents to trust incomplete indexes.

---

## 5. AI context findings

### What the generator includes today

Dry-run (11 Jul 2026): **16 markdown sources**, **~47 KB**, all under `docs/`:

1. `00`–`11` numbered guides (including **template adoption guide `11`**)
2. `ai/00-ai-memory-core.md`, `ai/10-prompt-library.md`
3. `audits/README.md`
4. `decisions/0001-project-shape.md`

Skipped by default: output basename; dirs named `.obsidian`, `lighthouse`, `brand` (env-overridable).

### As the repository grows

- Every new `docs/**/*.md` is included unless basename/dir is skipped.
- Dated audits under `docs/audits/**` **will enter the default dump** (only `lighthouse` dir name is skipped — not `audits/` itself).
- Historical investigations, completed checklists, and rejected options therefore pollute default ChatGPT context over time.
- Cursor already loads all six `alwaysApply` rules on every chat (~1.6k words), independent of the dump.

### Current vs historical

**No distinction.** Numbered “current” stubs, adoption meta-docs, prompt library, audit instructions, and seed ADR are concatenated equally.

### Duplication and contradiction risks

| Risk | Example |
| ---- | ------- |
| Duplication | Git promotion in rule `02` + `docs/04` + release + prompts; a11y/perf in rule `04` + `docs/06`/`07`; tiers in README + `11` + maintainer notes |
| Contradiction | Docs win for deploy truth (stated) vs always-on rules that still encode branch/domain placeholders; empty overview vs filled ADR “static-first chosen”; foundation repo uses only `main` while docs assume three branches |
| Meta pollution | Product AI memory includes `11-using-this-template.md` and audits README — foundation instructions, not project truth |
| Stale optional snapshot | `project-status.mdc` warned against, still documented as option |

### Multi-AI suitability

| Consumer | Fit |
| -------- | --- |
| Cursor | Rules always applied; instructed to read `docs/` — works locally if docs are filled; poor if shells empty |
| ChatGPT | Relies on regenerated dump or manual uploads; dump is unselective and gitignored by default |
| Other AI via GitHub | Sees committed docs + rules; **does not** see generated memory; **does not** see `.obsidian`; gets empty placeholders + static-first seed |

### Committed / gitignored policy

Default: regenerate locally, do not commit. Supports “don’t treat dump as editable truth” but **hurts** remote multi-AI examination. Committing the full dump would fix availability while worsening cost and staleness.

### What should never load by default (requirements for a future generator — not a design)

- Template/adoption/maintainer meta-docs
- Historical audits and superseded decisions (unless task requests them)
- Prompt libraries (on-demand)
- Empty or stub sections that are not yet project-filled
- Duplicate restatements of the same policy
- Large raw data, Lighthouse traces, brand assets
- Anything gitignored that another AI cannot fetch from the remote repo *if* that content is claimed to be shared truth

**Generator requirements (problem statements only):** select current truth; exclude history by default; remain usable without Cursor; be explainable (what was included/excluded); avoid recursive “all markdown”; support handoff between AIs from **committed** selective context where needed.

---

## 6. Cursor rule findings

| Rule | Universal? | Duplicates docs? | Assumptions elsewhere? | Verbosity | Stay Cursor-specific? | Principle → vendor-neutral? |
| ---- | ---------- | ---------------- | ---------------------- | --------- | --------------------- | --------------------------- |
| `00` behaviour | Mostly yes | Partially (`ai/00`) | Optional `project-status.mdc` | OK | Behavioural enforcement can stay Cursor | “Inspect repo; don’t guess; investigate before risky work” → yes |
| `01` code quality | For code yes | Prompt library | Assumes codebase exists | OK | Yes as Cursor shorthand | Diff discipline → yes |
| `02` git/release | Only if multi-branch deploy | **Heavy** (`04`, `09`) | Domains, staging | Verbose for experiments | Shorthands Cursor-specific | “No prod push without approval” → yes; branch table → project config |
| `03` documentation | Partially | Audits README, AI core | Hard-codes `docs/audits/` path | Verbose | Path conventions could be docs | “Don’t rewrite docs unprompted; write long investigations to files” → yes |
| `04` a11y/perf | Principles yes; always-on no | **Heavy** (`06`, `07`) | UI/web product | Medium | Enforcement Cursor-specific | Priority order → docs when relevant |
| `05` hygiene | Yes | `.gitignore`, folder guide | `data/raw` flavour | OK | Yes | Secrets policy → yes |

### Drift / contradiction risks

- Rules say read `<docs-dir>/` but placeholders leave nothing trustworthy.
- Rule `03` forbids ad-hoc audit paths; this slice explicitly required `docs/investigations/` — template rigidity already conflicts with real workflows.
- “Docs win over rules for deployment truth” is stated, but both contain parallel branch tables with placeholders — easy permanent drift.
- All rules `alwaysApply: true` → cost test failure as projects grow unrelated concerns (a11y rule on a one-file script).

---

## 7. Structural findings

### Stability across project shapes

| Shape | Fit today |
| ----- | --------- |
| Undeveloped concept | Poor — empty web/deploy shells dominate; no first-class “intent / uncertainty” home |
| One-hour experiment | Poor — tiers/placeholders/rules overhead exceeds experiment |
| Small script | Poor — Node web assumptions; a11y/perf/release noise |
| Static website | Good — closest to extraction source |
| Data-heavy web app | Partial — `data/raw`, sharding hints, audit data category present but pipeline not real |
| Mature production service | Partial — release/git/deploy helpful; still static-first biased; no backend/service stubs |
| Paused / abandoned | Partial — overview *could* hold resume truth but is not designed as a resume brief; history lands in audits that later pollute memory |

### Forced churn the current structure encourages

| Forced action | Why |
| ------------- | --- |
| Delete files | Tier trimming; remove staging/release/a11y/audits for small projects |
| Add documentation layers | Mature projects outgrow empty shells; audits taxonomy; optional roadmap; optional status rule |
| Rename core documents | `<docs-dir>` placeholder; folder guide’s `src/public` may not match stack |
| Change context strategy | Growing audits break dump usefulness; pressure to commit memory or invent skips |
| Reorganise historical work | Audits README implies category folders; investigations path not first-class |

**Conclusion:** The permanent structure is **not** stable from concept to mature project. It is optimised for a mid-to-late static web product and requires subtraction to go smaller and addition to go elsewhere.

---

## 8. Missing capabilities

Problems the foundation does not solve (capabilities, not filenames):

1. **Accepting rough human intent** — no first-class place for unstructured “why this exists” before docs are “proper.”
2. **Recording current project state** — overview is a status table for deployed products, not “what exists in the repo now.”
3. **Identifying current work** — no active focus / in-flight work signal distinct from roadmap or audits.
4. **Resuming after long inactivity** — no short resume protocol that points only at current truth.
5. **Selective AI context generation** — only all-or-nothing concatenation.
6. **Handing work between AI systems** — roles described; shared committed context weak; Cursor-local assumptions strong.
7. **Preserving history without loading it** — audits exist, but generator and rules do not keep them out of default context.
8. **Validating documentation freshness** — no check that overview/decisions match repo reality.
9. **Supporting version-based slices / progressive hardening** — tiers are subtractive, not progressive growth from one stable spine.
10. **Distinguishing concept / prototype / production** — maturity is implied by which files you deleted, not by an explicit honest state.
11. **Recording uncertainty without resolving it** — ADR seed resolves static-first; no uncertainty register.
12. **AI-initialise-from-intent** — adoption is manual clone + replace + trim; opposite of desired steps 2–4.
13. **Vendor-neutral project truth** — too much essential behaviour lives only in `.cursor/rules/`.
14. **Non-web project shapes** — first-class support absent.

---

## 9. BlooPlax inheritance

Evidence from this repo only (primarily `MAINTAINER_NOTES.md`, seed ADR, audit taxonomy, deploy/SEO language). **Inference labeled.**

| Element | Assessment |
| ------- | ---------- |
| Six focused Cursor rules | **Underlying lesson universal** (modular agent guidance). Implementation should not always-on every product concern. |
| Numbered operational docs 00–10 | **Lesson partially universal** (orient after time away). **Implementation BlooPlax/web-mature** — too many mandatory shells. |
| Three-branch promotion + shorthands | **Lesson universal** when multiple deploy targets exist. **Implementation not universal** as default. |
| Evidence-first a11y/perf | **Lesson universal.** Always-on docs/rules for every foundation clone are **implementation-specific**. |
| Audit taxonomy (seo, analytics, lighthouse) | **Mostly BlooPlax-shaped.** Recreate when needed; not foundation spine. |
| Static-first ADR + decision summary | **Defer-complexity lesson universal.** **Default decision should be removed** from foundation. |
| `data/raw/` gitignore + shard catalogue language | **Pipeline-specific.** Remove from defaults; keep “don’t commit huge dumps” lesson. |
| PWA / service worker notes | **Product-specific.** Optional later. |
| Indexing blocked on non-production | **SEO-site-specific.** Universal only as “know your public exposure.” |
| Cloudflare / Umami examples | **Hosting/analytics-specific** examples; fine as examples, harmful if read as defaults. |
| Doc concatenation for ChatGPT | **Handoff need universal.** **Dump implementation should not survive.** |
| Prompt library oriented to release/a11y/perf | **Underlying “scoped prompts” lesson universal.** Current set is mature-web. |
| Extraction hygiene (`rg` for BlooPlax names) | **Maintainer process** — keep for foundation repo only. |

---

## 10. Risks and contradictions

1. **Advertised problem vs actual design** — README claims “start building instead of writing process docs”; reality is writing/replacing/trimming process docs first.
2. **Current truth vs empty templates** — Agents are ordered to trust docs that contain no project facts.
3. **Cost vs completeness** — Memory generator maximises inclusion; governing cost test maximises exclusion of history/meta.
4. **Multi-AI vs gitignored handoff** — ChatGPT path depends on a file GitHub consumers don’t have.
5. **Vendor-neutral vs Cursor-centred** — Critical behavioural law lives in `.mdc`; other AIs only get softer docs copies.
6. **Stable spine vs tier deletion** — Tiers admit the structure is wrong for small projects, then push labour onto Stu.
7. **Uncertainty vs seed ADR** — Template resolves architecture before intent exists.
8. **Rule path rigidity vs real investigations** — `docs/audits/` only vs need for `docs/investigations/` (this file).
9. **Self-inconsistency** — Foundation uses single `main`; documents three-branch flow as default.
10. **Broken optional links** — `roadmap.md` referenced, absent.
11. **Duplication as drift engine** — Same facts in README, `11`, maintainer notes, rules, and numbered docs.

---

## 11. Initial verdict

### Already strong

- Safety culture: investigate vs implement; explicit Git approval; secrets hygiene.
- Principle that agents must inspect repository state, not invent it.
- Principle that long findings become files, chat stays short.
- Honest provenance documentation for the foundation itself.
- Recognition that generated memory must not be hand-edited as source of truth.
- Evidence-first performance questioning (as a method, not as mandatory furniture).

### Fundamentally misguided

- **Subtractive tiered templates** as the adoption model.
- Treating a **mature static-web operations manual** as the default spine for all project ages.
- **Unselective doc concatenation** as the AI memory strategy.
- Shipping **empty authoritative shells** that burn tokens and fail memory-wipe until filled.
- Encoding **product architecture defaults** (static-first, three envs, SEO gates) into the foundation.

### Retain as design evidence

- Behavioural principles listed under “Already strong.”
- The *problem statements* behind overview, decisions, audits, hygiene, and AI roles — not their current filenames or fullness.
- Maintainer notes as historical extraction record for rebuilding.
- This audit and Git history of what was tried.

### Should not survive into the rebuilt foundation (as mandatory defaults)

- Minimal/Standard/Full trimming ritual.
- Full `docs/00–11` empty web-ops set as required clone payload.
- Always-on a11y/perf and three-branch Cursor rules for every project.
- Seed static-first ADR.
- SEO/lighthouse/analytics audit taxonomy as default folders.
- Full-docs memory dump script behaviour.
- Adoption guide longer than the initialise path it should enable.
- `project-status.mdc` pattern.

### Incremental refactor vs clean replacement

**Recommend clean structural replacement**, using this repository’s principles and failures as evidence.

Incremental refactor would mean months of deleting shells, retuning skips, and still carrying BlooPlax-shaped gravity. The adoption model and context model are wrong at the root; rearranging numbered files will not pass the governing tests.

Replacement does **not** mean discarding lessons — it means not treating the current tree as sacred.

---

## 12. Questions that must be answered before designing the replacement

1. What is the **minimum committed spine** that every project keeps from concept through production (zero deletion required)?
2. Where does **rough human intent** live on day zero, and how does AI promote it into structured truth without forcing forms?
3. What is the single **current-truth** artefact for memory-wipe resume, and what is explicitly *out of scope* for it?
4. How are **uncertainty** and **rejected options** recorded so they are findable but not default context?
5. How is **active work** signalled distinctly from backlog, audits, and decisions?
6. What is the **selective context** contract for Cursor vs ChatGPT vs GitHub-only AIs (committed vs generated vs on-demand)?
7. Which behavioural laws are **vendor-neutral musts** vs Cursor enforcement hooks?
8. How does the foundation express **maturity** (concept / experiment / build / production / paused) without tier menus?
9. When do deploy/git/release/a11y docs **appear** — triggers, not upfront shells?
10. Should the foundation include **any** stack assumptions (Node, web, static), or remain shape-agnostic until the project chooses?
11. What is the initialise UX: human minutes of intent → **one AI command** → ready to investigate — what does success look like?
12. How will **Stu’s satisfaction and token cost** be measured so the foundation does not re-accumulate dump culture?
13. Should foundation meta-docs (adoption, maintainer provenance) exist in a **separate** plane from product truth so they never enter project AI context?
14. What is the policy for **historical investigations** paths (`audits/` vs `investigations/` vs archive) so rules and reality agree?

---

## Appendix A — Measurement notes

| Measurement | Result |
| ----------- | ------ |
| Tracked files | 26 paths under Git |
| Approx. prose weight | ~9,590 words across README, maintainer notes, docs, rules |
| Memory dry-run | 16 sources, ~46,736 bytes; includes `docs/11` and audits README |
| Branches | `main` only |
| BlooPlax name outside maintainer notes | `docs/11` common-mistakes row only (plus maintainer file) |
| Memory file after audit | Not retained (deleted post dry-run) |

## Appendix B — Verification of this slice

Intended filesystem delta:

- Created: `docs/investigations/`
- Created: `docs/investigations/2026-07-11-foundation-repository-audit.md`
- No other foundation files modified, renamed, moved, or deleted (untracked `.obsidian/` untouched; temporary memory file created then deleted during measurement)
