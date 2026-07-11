# Repository expression design — Slice 0.4

**Date:** 2026-07-11
**Branch:** `audit/foundation-repository`
**Status:** Repository-architecture design — concrete expression of the approved memory model
**Authority:** `FOUNDATION-SPEC.md`; `docs/investigations/2026-07-11-project-memory-model.md`
**Evidence:** Slice 0.1 audit; Slice 0.2.1 privacy inventory
**Non-goals:** Rebuild the current repository; implement generator; create final templates; replace Cursor rules; merge to `main`

British English. Neutral role language. Approved public handle `gromitski` only where GitHub identity is genuinely required. No personal emails, no-reply addresses, local paths, hostnames, hardware details, secrets or AI authorship metadata in this report.

---

## 1. Executive recommendation

Adopt a **compact root-and-memory spine** with on-demand directories:

```text
README.md
START.md
.gitignore
memory/
  agreements.md
  intent.md          ← after initialisation
  now.md             ← after initialisation
  decisions/         ← only after first durable decision
context/             ← generated views; manifest sidecar
evidence/            ← historical; origin archive; flat dated files
specialist/          ← triggered files only when created
work/                ← optional active-slice detail
.cursor/rules/       ← thin vendor enforcement (future slice)
```

### Leading decisions

| Topic | Recommendation |
| ----- | -------------- |
| Day-zero distributable files | `README.md`, `START.md`, `.gitignore`, `memory/agreements.md` |
| Post-initialisation minimum | above + `memory/intent.md`, `memory/now.md`, archived origin under `evidence/origin/` |
| Four responsibilities → surfaces | **Three permanent files** + **conditional `memory/decisions/`** |
| Rough intent | User overwrites `START.md`; initialisation promotes to `memory/intent.md` and archives origin |
| Generated context | **View** at `context/default.md` + `context/manifest.json`; **prefer committed** after init (configurable) |
| Foundation separation | **Clean-root distributable branch/artefact**; maintainer repo keeps design history |
| Clean-root v1.0 | **New orphan root** with privacy-safe history; current repo preserved as design archive |
| Universal `.gitignore` | Minimal cross-stack baseline; stack paths added at trigger time |

This rejects the current numbered `docs/00–11` catalogue, empty operational shells, and subtractive tiers.

---

## 2. Candidate structures

Three materially different options were evaluated.

### Option A — Root memory spine (recommended)

```text
README.md
START.md
memory/{agreements,intent,now}.md
memory/decisions/          (conditional)
evidence/
specialist/
work/
context/
.cursor/rules/
```

| Aspect | Assessment |
| ------ | ---------- |
| Canonical memory | `memory/` |
| Generated views | `context/` |
| Historical | `evidence/` |
| Vendor-specific | `.cursor/rules/` |
| Foundation-only | Not in distributable artefact |
| Rough intent | `START.md` → archive → `memory/intent.md` |
| Triggered memory | `specialist/<topic>.md` created on demand |

**Trade-off:** Slightly more root files, but maximum discoverability for humans and GitHub browsers without implying “read all docs”.

### Option B — Single structured project-memory document

```text
README.md
START.md
PROJECT.md                 (sections: Intent, Now, Agreements, Pointers)
memory/decisions/          (conditional)
evidence/
specialist/
context/
.cursor/rules/
```

All permanent responsibilities live in one file with fixed headings.

| Aspect | Assessment |
| ------ | ---------- |
| Pros | Fewest files; trivial default context generation; easy memory-wipe |
| Cons | Merge contention; grows into a junk drawer; harder to enforce “one question per surface”; agreements and intent edits collide |

**Verdict:** Rejected — fails stale-information and duplication controls at maturity.

### Option C — Compact `docs/` spine (legacy-shaped)

```text
README.md
START.md
docs/
  intent.md
  now.md
  agreements.md
  decisions/               (conditional)
docs/evidence/
docs/specialist/
context/
.cursor/rules/
```

| Aspect | Assessment |
| ------ | ---------- |
| Pros | Familiar to developers; keeps root clean |
| Cons | `docs/` gravity pulls “document everything here”; risks re-growing numbered catalogue; remote AIs may over-fetch `docs/**` |

**Verdict:** Rejected — too easy to recreate Slice 0.1 dump culture and web-manual assumptions.

---

## 3. Comparative assessment

Scoring: **Strong / Adequate / Weak**

| Criterion | A Root spine | B Single doc | C docs/ spine |
| --------- | ------------ | ------------ | ------------- |
| Memory-wipe recovery | Strong | Strong | Adequate |
| One-hour overhead | Strong | Strong | Adequate |
| Multi-AI discoverability | Strong | Adequate | Weak |
| Human readability | Strong | Adequate | Adequate |
| Context efficiency | Strong | Strong | Weak |
| Initialisation ease | Strong | Strong | Adequate |
| Resumption ease | Strong | Adequate | Adequate |
| Duplication risk | Strong | Weak | Adequate |
| Stale-info risk | Strong | Weak | Adequate |
| Triggering specialist memory | Strong | Strong | Strong |
| Wye Trains migration | Strong | Adequate | Adequate |
| BlooPlax migration | Strong | Weak | Adequate |
| Vendor neutrality | Strong | Strong | Strong |
| Privacy safety | Strong | Strong | Strong |
| Explainability without long manual | Strong | Strong | Weak |

All options reject tiers, placeholder replacement, empty ops shells, structural migration, full-tree loading, Cursor-only truth, and foundation provenance in distributions.

**Winner:** Option A.

---

## 4. Recommended day-zero structure

What a **distributable new project** contains **before** the user writes intent or initialises:

```text
README.md
START.md
.gitignore
memory/
  agreements.md
```

Optional in distribution packaging (future slice, not required day-zero files):

```text
.cursor/rules/             ← thin enforcement stubs when Cursor is used
context/
  README.md                ← explains generated views; not a generated view itself
```

### Day-zero file purposes

| Path | Role | Default AI context |
| ---- | ---- | ------------------ |
| `README.md` | Project entry; one-screen orientation; initialisation instruction | Yes (short) |
| `START.md` | Rough-intent capture surface | No after initialisation |
| `.gitignore` | Universal hygiene | No |
| `memory/agreements.md` | Thin working agreements (pre-filled universal baseline) | Yes |

**Not present day zero:** `memory/intent.md`, `memory/now.md`, `memory/decisions/`, `evidence/`, `specialist/`, `work/`, generated context, stack-specific ignores, deployment docs, architecture docs.

---

## 5. Recommended post-initialisation structure

Minimum after successful initialisation:

```text
README.md                  ← project one-liner added
.gitignore
memory/
  agreements.md            ← unchanged or lightly extended
  intent.md                ← created
  now.md                   ← created
evidence/
  origin/
    YYYY-MM-DD-origin.md   ← archived START.md content
context/
  manifest.json            ← created when generator first runs (may be manual stub in early tests)
  default.md               ← generated selective snapshot (preferred committed)
```

`START.md` after initialisation: **removed or replaced** with a three-line pointer (“intent captured; see `memory/intent.md` and `evidence/origin/`”).

Conditional additions (only when triggers fire):

```text
memory/decisions/
  index.md
  YYYY-MM-DD-<slug>.md
specialist/
  <topic>.md
work/
  YYYY-MM-DD-<slug>.md
evidence/
  YYYY-MM-DD-<topic>.md
```

---

## 6. Permanent memory surfaces

### Mapping: four responsibilities → concrete surfaces

| Responsibility | Surface | Files |
| -------------- | ------- | ----- |
| Durable product intent | `memory/intent.md` | 1 file |
| Current project truth | `memory/now.md` | 1 file |
| Working agreements | `memory/agreements.md` | 1 file (pre-filled at distribution) |
| Accepted decisions | `memory/decisions/` | **Conditional directory** — created with first durable decision |

**Not four files by default** — three files plus a conditional directory. Decisions do not get an empty day-zero artefact.

### 6.1 `memory/intent.md`

| Attribute | Value |
| --------- | ----- |
| Unique question | Why does this project exist, for whom, and what is out of scope? |
| Canonical content | Purpose, audience/value, principles, non-goals, major assumptions (with uncertainty states) |
| Max scope | ~1–2 screens; slow-changing |
| Change frequency | Low |
| Default AI context | Yes |
| Initialisation | AI creates from approved rough intent |
| Stale when | Contradicts maintainer direction or accepted decisions without update |
| Must not contain | Current status, active slice detail, architecture essays, ops fiction, personal/local info |

### 6.2 `memory/now.md`

| Attribute | Value |
| --------- | ----- |
| Unique question | Where is the project *now*? |
| Canonical content | See §8 current-truth contract |
| Max scope | ~1 screen target; mature projects may reach ~2 with pointers only |
| Change frequency | High |
| Default AI context | Yes |
| Initialisation | AI creates honest first state |
| Stale when | Disagrees with repository facts, active work detail, or last meaningful update is old while repo changed |
| Must not contain | History, investigations, full roadmap, duplicated specialist depth |

### 6.3 `memory/agreements.md`

| Attribute | Value |
| --------- | ----- |
| Unique question | How must humans and agents work safely on this project? |
| Canonical content | See §9 |
| Max scope | **Hard limit ~120 lines / ~800 words** in v1 guidance |
| Change frequency | Low |
| Default AI context | Yes |
| Initialisation | Pre-filled; project may append short project-specific notes |
| Stale when | Conflicts with specialist security/deploy docs — specialist wins for domain detail, agreements win for authority law |
| Must not contain | Architecture, current status, long handbooks |

### 6.4 `memory/decisions/` (conditional)

| Attribute | Value |
| --------- | ----- |
| Unique question | Which important choices are settled and why? |
| Creation trigger | First **accepted durable decision** meeting Slice 0.3 bar |
| Structure | `index.md` (current decisions only) + `YYYY-MM-DD-<slug>.md` per record |
| Default AI context | Index + current records; superseded records excluded |
| Must not contain | Empty template on day zero; trivial choices; raw investigation dumps |

---

## 7. Rough-intent lifecycle

### Capture mechanism

| Step | Behaviour |
| ---- | --------- |
| Where written | `START.md` at repository root |
| Distributable? | Yes — ships as a short instruction header the user **replaces entirely** with free text |
| Forms? | **None** — no questionnaire; overwrite the starter text |
| Voice/dictation | User may paste transcript into `START.md` |

Starter content of `START.md` (distribution template):

```markdown
# Start here

Replace everything below this heading with a few minutes of rough project intent.
Write or paste freely — incomplete thoughts are fine.

---

```

### Initialisation transform

1. AI reads `START.md` and repository state.
2. AI drafts `memory/intent.md` and `memory/now.md`.
3. AI copies raw `START.md` body to `evidence/origin/YYYY-MM-DD-origin.md`.
4. AI replaces `START.md` with a brief pointer (or removes file — **prefer pointer** for discoverability).
5. Maintainer reviews before first useful slice.

### Duplication prevention

- Origin is **historical** — excluded from default context manifest.
- `memory/intent.md` is the **only** current product-truth source for why/who/boundaries.
- Generator and manifest must list `evidence/origin/**` under excluded classes.
- Agents must not restate origin verbatim in `intent.md`; synthesise and mark uncertainties.

### Default-context exclusion

Archived origin excluded via:

- manifest `excluded: ["evidence/origin/**"]`
- no pointer from `memory/now.md` unless maintainer explicitly wants reinterpretation from source

---

## 8. Current-truth contract (`memory/now.md`)

### Format

- **Markdown with fixed H2 headings** (simple structure, no mandatory YAML front matter).
- Human-readable first; optional lightweight front matter later if tooling needs it.

### Required sections (in order)

```markdown
## Purpose (one line)

## Lifecycle

## What exists now

## Milestone or version

## Active focus

## Active slice

## Blockers

## Uncertainties

## Next safe action

## Last meaningful update

## Pointers
```

### Field rules

| Section | Rule |
| ------- | ---- |
| Purpose (one line) | Echo intent briefly; not a copy of full intent doc |
| Lifecycle | One label from spec vocabulary; honest |
| What exists now | Bulleted inventory of real artefacts or “none yet” |
| Milestone or version | Omit section entirely if not useful |
| Active focus | Theme or “none” |
| Active slice | Summary **or** link to `work/…` **or** “none” |
| Blockers | Real blockers only; omit if none |
| Uncertainties | Open questions affecting next work |
| Next safe action | One step |
| Last meaningful update | ISO date + short note |
| Pointers | Only paths that **exist** — specialist, decisions, evidence |

### Maintenance model

- **Both** human and AI may update; AI updates after meaningful slices.
- **Not a change diary** — replace outdated lines; do not append session logs.
- Staleness signal: `Last meaningful update` older than latest commit touching product artefacts, or contradictions found on inspect.

### Mature-project discipline

When pointers grow, **add pointers only** — do not paste specialist content into `now.md`.

---

## 9. Working-agreements contract (`memory/agreements.md`)

### Scope limit

Pre-filled universal baseline (~80–120 lines max). Project-specific additions append under `## Project-specific notes` (keep short).

### Universal baseline must include

1. Inspect repository state before assumptions.
2. Personal and local-system information stay out of repositories.
3. Never commit secrets; use env examples and secret stores.
4. Commits/pushes/production actions only when the maintainer explicitly asks.
5. No AI co-author metadata in commits when clean authorship is required.
6. Accessibility fundamentals for user interfaces (WCAG AA aim; prototypes still respect basics).
7. Usability includes proportionate performance; measure before optimising.
8. Clean, maintainable code; refactor while context is fresh; smallest useful change.
9. Separate maintained data from presentation/logic where practical.
10. Proportionate security from the start.
11. Natural path for repeatable testing from first implementation.
12. Investigate before risky or ambiguous implementation.

### Delegated to triggered specialist memory

Deep accessibility manuals, performance evidence frameworks, deployment runbooks, threat models, testing catalogues, data-governance detail.

### Vendor rules relationship

`.cursor/rules/` **must point to** `memory/agreements.md` and **must not** duplicate the full baseline. Cursor enforces behaviour; agreements remain canonical.

### Extension rule

Projects may append short notes; if additions exceed ~40 lines, move depth to `specialist/` and leave a pointer.

---

## 10. Decision-memory contract

### Before first durable decision

- `memory/now.md` includes under pointers or uncertainties: **“Accepted decisions: none recorded yet.”**
- No `memory/decisions/` directory.

### First artefact creation trigger

Create `memory/decisions/` when a choice meets all of:

1. Costly or confusing to reverse.
2. Would be re-litigated without a record.
3. Rationale not obvious from code alone.
4. Product/architecture/process significant.

### Structure after creation

```text
memory/decisions/
  index.md                 ← table of current accepted decisions only
  YYYY-MM-DD-<slug>.md     ← one decision per file when justified
```

`index.md` lists: date, title, status (accepted), link to record.

### Superseded decisions

- Move record to `evidence/decisions/` **or** keep in place with status `superseded` and **remove from index**.
- Default context includes **index only** (current decisions).
- Rejected alternatives: mention in decision record; link to `evidence/…` investigation if exists.

### Trivial logging prevention

No decision file for: naming bikesheds, reversible one-line edits, investigation findings not yet accepted.

---

## 11. Triggered specialist-memory convention

### Principles

- **No pre-created folders or empty files** in distribution.
- First specialist file creation **may** create `specialist/` directory.
- Flat topic files preferred over deep taxonomies.

### Naming

```text
specialist/<topic>.md
```

Examples: `technical.md`, `develop.md`, `deploy.md`, `data.md`, `accessibility.md`, `security.md`, `performance.md`, `testing.md`, `integrations.md`, `analytics.md`, `operations.md`

Use separate files when topics are independently maintained; merge when tightly coupled (e.g. `develop.md` includes run/build/test until volume forces split).

### Trigger → file (illustrative, not mandatory catalogue)

| Trigger | First file |
| ------- | ---------- |
| Application code exists | `specialist/technical.md` |
| Runnable locally | `specialist/develop.md` |
| Deployment exists | `specialist/deploy.md` |
| Maintained datasets | `specialist/data.md` |
| Public UI | `specialist/accessibility.md` |
| Auth / PII processing | `specialist/security.md` |
| Performance work | `specialist/performance.md` |
| Named releases | `specialist/releases.md` or changelog section inside deploy |

### Discovery

`memory/now.md` → `## Pointers`:

```markdown
- specialist/technical.md — implementation structure (created 2026-…)
```

Only list files that exist.

### Generated context

Specialist files join default generated view **only when** listed in `memory/now.md` pointers **or** named in manifest conditional include list for active task profile.

### Retirement

When specialist doc superseded: move to `evidence/retired/` or mark retired at top; remove from pointers and manifest includes.

---

## 12. Historical-evidence convention

### Placement

```text
evidence/
  origin/                  ← archived rough intent only
  YYYY-MM-DD-<topic>.md      ← flat default for investigations, audits, experiments
  decisions/                 ← optional superseded decision archives
  retired/                 ← retired specialist docs
```

### Naming

- Dated prefix mandatory: `YYYY-MM-DD-`
- Slug describes topic: `feasibility-api-sources`, `incident-cache-miss`, `audit-accessibility-baseline`
- **Do not** force subdirectory taxonomies (`audits/` vs `investigations/`) unless volume makes flat search painful

### Index

**No global evidence index required** at v1. Search + pointers suffice.

Optional: brief “Recent evidence” list in `memory/now.md` only while investigations are active; remove when complete.

### Default context

**Excluded** except when explicitly pulled for a task.

### Sensitive material

Reports must redact secrets, tokens, personal data, local paths. Raw logs belong outside the repo or in redacted form.

---

## 13. Active-work-detail convention

### Path

```text
work/YYYY-MM-DD-<slug>.md
```

### Creation trigger

Create when **any** of:

- Multi-step slice with handoff risk
- Ambiguous scope needing explicit in/out
- Investigation implementing across sessions (otherwise use `evidence/…` as working surface)

### Contents

Goal, in-scope, out-of-scope, completion criteria, status, blockers, links to evidence.

### Lifecycle

| Event | Action |
| ----- | ------ |
| Complete | Update `memory/now.md`; extract decisions if needed; **delete or archive** work file — default **archive to `evidence/` only if decision-heavy**, else delete |
| Pause | Status `paused` in work file + `memory/now.md` |
| Abandon | Close in `memory/now.md`; delete work file or short note in evidence if lesson worth keeping |

### Tiny tasks

One-line update in `memory/now.md` only — **no** `work/` file.

### Investigation-only work

Use `evidence/YYYY-MM-DD-<topic>.md` as the working surface; pointer from `memory/now.md`.

---

## 14. Generated-view contract

### Location

```text
context/default.md          ← selective generated snapshot
context/manifest.json       ← inclusion declaration
```

Optional later: `context/profiles/<task>.md`

### `context/manifest.json` schema (v1 minimal)

```json
{
  "generated_at": "ISO-8601",
  "generator": "name-or-version",
  "output": "context/default.md",
  "included": ["memory/intent.md", "memory/now.md", "memory/agreements.md"],
  "conditional": ["specialist/technical.md"],
  "excluded_classes": ["evidence/**", "evidence/origin/**", "work/**"],
  "source_hashes": {"memory/now.md": "sha256:…"},
  "byte_size": 0,
  "stale_if": "any source hash differs or memory/now.md Last meaningful update is newer"
}
```

### `context/default.md` header

Markdown comment or YAML front matter repeating manifest summary and **DO NOT EDIT** warning.

### Commit policy (leading recommendation)

| Mode | Policy |
| ---- | ------ |
| Default for distributable projects | **Commit** `context/default.md` + `context/manifest.json` after initialisation and after memory updates |
| Local override | `.gitignore` entry for `context/default.md` documented in README if maintainer opts out |
| Before generator exists | Canonical spine files alone are small enough for remote AIs to read directly |

**Unresolved test:** whether always-commit vs commit-when-remote-handoff is better — Slice 0.5 should measure stale rates.

### Stale detection

- Compare manifest hashes to sources.
- Compare `generated_at` to `Last meaningful update` in `memory/now.md`.
- Warn in README or generator output when stale; never silently trust stale view.

### Hand editing

**Forbidden** as canonical edits. Changes go to source memories, then regenerate.

### Consumer suitability

| Consumer | Approach |
| -------- | -------- |
| Cursor | Read `memory/*` directly; generated view optional |
| GitHub remote AI | Read spine or committed `context/default.md` |
| ChatGPT upload | Prefer `context/default.md` |
| Other repo AIs | Same as GitHub |

### No generator yet

README instructs: load `memory/intent.md`, `memory/now.md`, `memory/agreements.md`, and current decision index if present.

---

## 15. Vendor-specific rule model (future)

### Distribution stance

| Question | Recommendation |
| -------- | -------------- |
| Ship `.cursor/rules/`? | **Yes**, but minimal |
| Committed? | **Yes** in Cursor-using projects |
| Always-applied count | **Maximum three** at v1: behaviour, hygiene, git authority |
| Never duplicate | Full agreements, intent, now, architecture, deploy checklists |
| Pattern-specific rules | Allowed later (`*.tsx`, `**/deploy/**`) for a11y/perf depth |
| Point to canonical | Each rule links `memory/agreements.md` and `memory/now.md` |
| Without Cursor | Project fully usable via `memory/` spine |

### Co-author prevention

Distribution README and agreements remind: use clean commit metadata; avoid AI co-author trailers when required. Implementation in Slice 0.5+ (hooks or commit helper) — not this slice.

### Accessibility/security/testing enforcement

Floors live in `memory/agreements.md`. Cursor rules **enforce** (“before UI work, read specialist/accessibility.md if present”) — not restate WCAG manuals.

---

## 16. Foundation-maintainer plane

### What stays out of project distributions

- `FOUNDATION-SPEC.md`
- `docs/investigations/**` (design evidence)
- Privacy inventory and audit history
- BlooPlax extraction commentary
- Foundation maintenance instructions
- Historical commits with personal email or AI co-author trailers

### Options compared

| Option | Pros | Cons |
| ------ | ---- | ---- |
| Separate branch (`template/main` orphan) | Clean history; single repo | Branch discipline required |
| Top-level `foundation/` directory | Easy access | Risk of accidental inheritance; pollutes clone |
| Build/distribution output | Clean artefact | Needs script |
| Separate repository | Clearest separation | Two repos to manage |
| Clean-root release tag | Simple consumer story | Still need generation step |

### Leading recommendation

**Orphan clean-root branch + generation script (Slice 0.5):**

1. **Maintainer repo** (`audit/foundation-repository`, later `main`) keeps design history, spec, investigations.
2. **`template/main` orphan branch** (or tagged release tarball) contains **only** distributable day-zero spine.
3. Generation script copies: `README`, `START`, `.gitignore`, `memory/agreements.md`, minimal `.cursor/rules/`, `context/README.md`.
4. New projects fork/copy template — **not** the maintainer audit tree.

**Requires later implementation test:** script proves zero foundation autobiography bytes in output.

---

## 17. Clean-root / history recommendation

### Problem (from privacy inventory)

Existing history contains personal email metadata, AI co-author trailers, and legacy personal-name content in old docs.

### Options

| Strategy | Verdict |
| -------- | ------- |
| Rewrite existing history in place | High risk; rewrites audit evidence |
| Orphan clean-root distributable branch | **Recommended** |
| New repository for v1.0 releases | Strong alternative; same orphan idea |
| Preserve messy repo + filter on export | **Recommended combo** — messy repo as archive, clean export for users |
| Do nothing | Fails v1.0 privacy acceptance |

### Recommendation

1. **Preserve** current repository as design/archive history (no forced rewrite in Slice 0.4).
2. **Publish v1.0** from a **new orphan root** with privacy-safe commit metadata only.
3. **Projects** inherit from clean template, never from maintainer investigation commits.
4. **Migrate** BlooPlax/Wye Trains onto new spine in dedicated migration slice — do not rewrite their histories in 0.4.

---

## 18. Universal `.gitignore` baseline

### Recommended distributable minimum

```gitignore
# Local editor state
.obsidian/

# Secrets and local env
.env
.env.*
!.env.example

# OS metadata
.DS_Store
Thumbs.db

# Logs and scratch
*.log

# Local overrides
*.local
```

### Explicitly **not** in universal baseline

- `node_modules/`, `dist/`, framework build dirs — add when stack trigger fires (document in `specialist/develop.md` or init script)
- `data/raw/` — project-specific; add when data pipeline exists
- Generated context — **committed by default**; optional ignore documented per project

### Foundation maintainer repo

May keep additional entries for legacy tree until rebuild; distributable template uses minimal baseline only.

---

## 19. Initialisation flow

### Steps

| # | Actor | Action |
| - | ----- | ------ |
| 1 | Maintainer | Create repository from clean template |
| 2 | Maintainer | Overwrite `START.md` with rough intent |
| 3 | Maintainer | Ask AI with **one supplied initialisation prompt** (in README) |
| 4 | AI | Inspect repository; confirm not yet initialised |
| 5 | AI | Draft `memory/intent.md`, `memory/now.md` |
| 6 | AI | Archive origin → `evidence/origin/YYYY-MM-DD-origin.md` |
| 7 | AI | Replace `START.md` with pointer |
| 8 | AI | State uncertainties honestly; propose one first slice |
| 9 | Maintainer | Review; adjust |
| 10 | Both | Begin useful work; commit spine before or with first slice |

### If never initialised

Repository remains valid but incomplete — README shows initialisation prompt; no fictional `memory/intent.md`.

### Half-initialised resume

If only `START.md` filled: run initialisation.

If intent without now: AI completes missing spine file from repo inspection.

### Privacy / Git checks (lightweight)

Initialisation prompt includes: scan for personal/local info before commit; confirm local Git identity uses approved handle/no-reply — **not** a blocking questionnaire.

### Pre-init distributable files

`README.md`, `START.md`, `.gitignore`, `memory/agreements.md`

### Post-init generated

`memory/intent.md`, `memory/now.md`, `evidence/origin/…`, optional `context/*` after generator

---

## 20. Stress-test results

Structural migration required: **none** for all tests.

### A. One-hour script

| | |
| - | - |
| Before init | README, START, .gitignore, memory/agreements.md |
| After init | + intent, now, origin archive |
| Triggered | optional specialist/develop.md if script needs run instructions |
| Generated | context/default.md optional |
| Default AI load | 3 memory files |
| Overhead | Minimal |

### B. Dormant concept (one year)

| | |
| - | - |
| Canonical | intent, now (lifecycle `paused`), agreements |
| Triggered | none |
| Generated | stale marker likely — regenerate on resume |
| Default AI load | spine only |
| Overhead | Minimal |

### C. Wye Trains

| | |
| - | - |
| Day-zero spine | standard |
| Investigation | evidence/2026-…-feasibility-data-sources.md |
| Triggered | specialist/data.md when datasets appear |
| No fiction | no deploy/architecture files until earned |
| Active work | pointer to evidence file during feasibility slice |
| Default AI load | spine + data specialist if pointer active |

### D. BlooPlax (migration sketch)

| Old surface | New surface |
| ----------- | ----------- |
| docs/00-overview | memory/now.md |
| Product principles scattered | memory/intent.md |
| Cursor rules behaviour | memory/agreements.md + thin .cursor/rules |
| docs/decisions/* | memory/decisions/* |
| docs/01–03 ops | specialist/technical.md, develop.md, deploy.md |
| docs/06–07 depth | specialist/accessibility.md, performance.md |
| docs/audits/* | evidence/YYYY-MM-DD-*.md |
| Active slice | memory/now.md + work/2026-…-slice.md |
| Generated dump | context/default.md selective |

Historical audits excluded from default context. Maintainership knowledge preserved in specialist + decisions + evidence — not lost.

### E. Non-web CLI tool

| | |
| - | - |
| Canonical | same spine |
| Triggered | specialist/develop.md, maybe technical.md |
| Absent | accessibility/deploy until relevant |
| Default AI load | spine only |
| Overhead | no web assumptions |

---

## 21. Rejected alternatives

- Numbered `docs/00–11` mandatory set
- Single `PROJECT.md` for all spine responsibilities
- Pre-created `specialist/` folder tree
- Pre-created `evidence/audits/` taxonomy
- Empty `memory/decisions/index.md` on day zero
- Gitignored-only default context (Slice 0.1 failure for remote AI)
- Copying foundation investigations into new projects
- Stack-heavy universal `.gitignore`
- Mandatory `work/` file per slice
- Keeping rough intent in `START.md` as live truth after init

---

## 22. Risks and trade-offs

| Risk | Mitigation |
| ---- | ---------- |
| Three memory files still feel like “docs” | README emphasises short spine; strict size limits |
| Pointer discipline fails | Manifest + initialisation training; reviews |
| Committed generated view goes stale | manifest hashes; regen after memory edits |
| `specialist/` becomes new numbered catalogue | flat files; create on trigger only |
| Clean-root/template drift from design | generation script with inclusion tests |
| Migration from BlooPlax is labour-intensive | dedicated migration slice; mapping table above |

**Largest trade-off:** A visible `memory/` directory trades minimal file count for **clarity of canonical truth** — slightly more structure upfront to prevent the ambiguous `docs/` gravity that caused dump culture.

---

## 23. Open implementation questions (Slice 0.5+)

1. Exact initialisation prompt wording and idempotency rules.
2. Generation script: implement manifest hashing and stale warnings.
3. Template branch creation automation and CI check for zero foundation leakage.
4. Cursor rule file contents (three always-applied stubs).
5. Commit policy A/B test: always commit context vs opt-in ignore.
6. Decision index UX when >10 decisions — split index or search-only.
7. Migration tooling for BlooPlax and Wye Trains.
8. Git hook or helper for co-author prevention.
9. Stack-triggered `.gitignore` fragments — manual vs init-appended.
10. Whether `START.md` pointer or deletion after init is better — user test.

---

## 24. Recommendation for Slice 0.5

Slice 0.5 should **implement the distributable clean template** on an orphan branch:

1. Create day-zero files exactly as specified (README, START, .gitignore, memory/agreements.md, context/README.md).
2. Write the initialisation prompt and a manual initialisation dry-run on a fictional project.
3. Implement minimal `context/manifest.json` schema (manual or script).
4. Draft three thin `.cursor/rules/` stubs pointing to agreements.
5. Build the template-generation script with **zero foundation-autobiography** verification.
6. Prove `.obsidian/` and secrets patterns stay ignored.
7. Do **not** replace the legacy foundation tree on `main` yet.

---

## Appendix A — Fictional post-initialisation example (not created in repo)

Project: **Shelf Ledger** — a concept for tracking household consumables.

### `memory/intent.md` (excerpt)

```markdown
# Product intent

## Purpose
Help the maintainer notice when everyday household consumables are running low before they run out.

## Audience
The maintainer only — personal utility, not a commercial product.

## Value
Less mental load and fewer emergency shop trips.

## Principles
- Manual entry is acceptable early; automation only if it stays simple.
- Prefer boring, maintainable tooling.

## Non-goals
- Multi-user accounts
- Retail integrations in v1
- Mobile app

## Assumptions
- **Unknown:** whether barcode scanning is worth the complexity.
- **Assumed:** a simple list with quantities is enough for a first experiment.
```

### `memory/now.md` (excerpt)

```markdown
## Purpose (one line)
Personal household consumable tracker — concept only.

## Lifecycle
concept

## What exists now
- memory spine initialised
- no application code

## Active focus
Decide whether a spreadsheet, script or small app is the right first experiment.

## Active slice
None — propose a one-hour feasibility spike comparing manual CSV vs tiny script.

## Blockers
None

## Uncertainties
- Preferred interface (CLI vs spreadsheet)
- Whether shared household use is needed later

## Next safe action
Run a one-hour spike: create a CSV template and use it for one week manually.

## Last meaningful update
2026-07-11 — project initialised from rough intent.

## Pointers
- evidence/origin/2026-07-11-origin.md — original rough intent (historical)
```

No `memory/decisions/`. No `specialist/`. No deployment fiction.

---

## Appendix B — Day-zero vs post-init file matrix

| File | Day zero | Post init |
| ---- | -------- | --------- |
| README.md | yes | yes (updated) |
| START.md | yes | pointer or removed |
| .gitignore | yes | yes |
| memory/agreements.md | yes | yes |
| memory/intent.md | no | yes |
| memory/now.md | no | yes |
| memory/decisions/ | no | when triggered |
| evidence/origin/ | no | yes |
| evidence/other | no | when needed |
| specialist/* | no | when triggered |
| work/* | no | when needed |
| context/default.md | no | generated (preferred committed) |
| context/manifest.json | no | generated |

---

## Document control

| Item | Value |
| ---- | ----- |
| Slice | 0.4 — Repository expression design |
| Resolves | Memory-model open questions 1–12 (structure expression) |
| Changed in implementation slice | `.gitignore` only (+ this report) |
