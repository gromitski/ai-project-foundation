# Project memory model — Slice 0.3

**Date:** 2026-07-11
**Branch:** `audit/foundation-repository`
**Status:** Architecture decision — information responsibilities and relationships only
**Authority:** `FOUNDATION-SPEC.md` (product direction)
**Evidence:** Slice 0.1 foundation repository audit; Slice 0.2.1 privacy inventory
**Non-goals:** Final folder tree; filenames; scripts; Cursor rules; automation; replacing the current foundation tree; merge to `main`

British English. Neutral role language (`the maintainer`, `the user`). Approved public handle `gromitski` only where GitHub identity is genuinely required. No personal emails, no-reply addresses, local paths, hostnames, hardware details or secrets in this report.

---

## 1. Executive recommendation

Adopt a **four-plane memory model**:

1. **Durable identity** — slow-changing why/who/boundaries plus thin working agreements and durable decisions.
2. **Current truth** — one authoritative “now”, including active-work summary or pointer.
3. **Historical evidence** — retrievable, normally excluded from default AI context.
4. **Generated views** — selective AI context and handoff artefacts; **never** canonical memory.

Plus a separate **foundation-maintainer plane** that must not become inherited project truth.

### Hard recommendations

| Question | Recommendation |
| -------- | -------------- |
| Minimum permanent memory responsibilities | **Four:** durable product intent; current project truth; working agreements (thin safety/quality/Git authority); accepted-decision memory (as a responsibility — artefact may appear only when the first durable decision exists) |
| Active work vs current state | **Hybrid:** always summarised or pointed from current truth; separate detail only when a multi-step or handoff-heavy slice needs it |
| Rough intent after initialisation | **Promote into durable intent; retain original as archived origin material outside default context** (not deleted immediately; not treated as current product truth) |
| Accepted decisions | **Permanent core responsibility**; no empty decision file on day zero |
| Architecture and operations | **Triggered**, not permanent |
| Generated AI context | **A view**, not canonical memory |
| Committing generated context | **Both:** generate on demand; optionally commit a **selective** default snapshot for remote multi-AI use — subject to a later freshness test |
| Completed slices | **Usually no archival document**; update current truth (and decisions if needed); keep Git history; archive only when decision-heavy or investigation-like |
| Foundation-maintainer material | **Separate plane**; never enters product default context or new-project inheritance |

The provisional three-layer model (A/B/C) is **accepted as the core**, with two refinements: working agreements and decisions sit in durable identity; generated context is explicitly **not** a fifth memory layer.

---

## 2. Design criteria

Derived from the specification’s governing tests and principles.

A memory responsibility is justified only if:

1. Something important is forgotten without it.
2. A clear audience needs it (maintainer, any capable AI, or both).
3. Change frequency matches its role (slow vs frequent vs rare).
4. Its type is clear: current truth, durable rationale, active work, historical evidence, generated view, or foundation-only.
5. Permanence is earned (day-zero vs triggered).
6. Default AI load is justified by frequent use.
7. No other responsibility answers the same question better.
8. Maintenance cost is lower than the confusion or re-education it prevents.

Additional hard constraints:

- No tier selection; no deletion as growth path.
- No empty authoritative forms.
- No fictional operational content.
- Vendor-neutral project truth.
- Personal and local-system information stays out of repositories (principle 23).
- One memory, one home.

---

## 3. Proposed memory layers

### Accepted core layers

| Layer | Name | Role |
| ----- | ---- | ---- |
| **A** | Durable project identity | Slow-changing identity, principles, working agreements, accepted decisions |
| **B** | Current project truth | Authoritative “now”, including active focus |
| **C** | Historical evidence | Retrievable past; excluded from default context |

### Explicit non-layers

| Plane | Role |
| ----- | ---- |
| **Generated views** | Selective projections over A+B (+ conditional specialist memory); not editable truth |
| **Foundation-maintainer plane** | How the foundation itself is maintained and distributed; never product truth |

### Challenges to the provisional three-layer model

| Challenge | Verdict |
| --------- | ------- |
| Are three layers sufficient? | **Yes for product memory**, if generated views and foundation plane are named separately and not mistaken for layers A–C |
| Distinct technical/operational layer? | **No as permanent layer.** Technical reality and operations are **triggered specialist memory** that may temporarily join default context when relevant |
| Decisions with identity or separate? | **Belong in Layer A** as durable rationale; may use a dedicated artefact when volume or importance warrants |
| Active work inside current truth or separate? | **Hybrid** — summary/pointer always in Layer B; detail only when needed |
| Generated AI context a layer? | **No** — it is a view |
| Rough human intent permanent? | **Initialisation input + archived origin**, not Layer B truth |

---

## 4. Memory responsibility inventory

Classification key: **D0** day zero · **T** triggered · **O** optional · **V** generated view · **H** historical only · **F** foundation-maintainer only · **X** reject/duplicative

| Candidate | Class | Unique question | Notes |
| --------- | ----- | --------------- | ----- |
| Rough human intent | **D0 input → H origin** | What did the maintainer originally say? | Not current truth after approval |
| Durable product intent | **D0** | Why does this project exist and for whom? | Layer A |
| Current project truth | **D0** | Where is the project *now*? | Layer B; single authoritative now |
| Active slice (detail) | **T / hybrid** | What exact work is in flight and how does it finish? | Summary always in current truth |
| Near-term direction / roadmap | **O / light in B** | What milestones matter next? | Tiny projects: a few lines in current truth; separate only when multi-milestone pressure appears |
| Accepted decisions | **D0 responsibility / T artefact** | Which important choices are settled and why? | No empty shell; first record creates the home |
| Uncertainties and assumptions | **D0 (inside A/B)** | What is unknown, assumed or proposed? | Prefer fields in intent + current truth over a separate register |
| Working agreements | **D0** | How must agents and humans work safely here? | Thin: privacy, secrets, Git authority, quality floor |
| Technical architecture / reality | **T** | How does the implementation actually work? | Appears when code/structure exists |
| Development instructions | **T** | How do I run, build and verify locally? | When there is something to run |
| Deployment and operations | **T** | How is it hosted, promoted and recovered? | When deploy/environments exist |
| Quality expectations (baseline) | **D0 (thin in working agreements)** | What quality floors always apply? | Specialist depth triggered (UI a11y, perf evidence, deep security) |
| Quality specialist manuals | **T** | What deep guidance applies for this domain? | Not default load for tiny projects |
| Investigations / experiments | **H** | What was examined and what was found? | Exclude from default context |
| Incidents | **T → H** | What went wrong in production and what changed? | Only when production failure is possible/real |
| Changelog / release history | **T / H** | What shipped publicly or as named releases? | Not required at concept stage |
| Completed slice reports | **Usually X / rare H** | How was this slice executed? | Prefer Git + current-truth update; archive only if decision-heavy |
| Generated AI context | **V** | What concise package should an AI load by default? | Never canonical |
| Task-specific AI views | **V / O** | What package suits this task? | Later design; not required for spine |
| Foundation adoption instructions | **F / distribution** | How do I create a project from the foundation? | Not product memory |
| Foundation maintenance provenance | **F** | How is the foundation itself maintained? | Must not inherit into projects |
| Prompt libraries | **O / on demand** | What scoped prompt helps this task? | Not permanent spine; not default context |
| Issue-tracker substitutes / exhaustive backlog | **X** | — | Spec non-goal |
| Conversation transcripts | **X** | — | Spec non-goal |
| Empty numbered ops manuals | **X** | — | Slice 0.1 failure mode |

---

## 5. Minimum permanent spine

### The spine (four responsibilities)

| # | Responsibility | Layer | Must exist from concept? | Default AI context? |
| - | -------------- | ----- | ------------------------ | ------------------- |
| 1 | **Durable product intent** | A | Yes (created at initialisation from rough intent) | Yes |
| 2 | **Current project truth** | B | Yes | Yes |
| 3 | **Working agreements** | A | Yes (thin, universal) | Yes |
| 4 | **Accepted-decision memory** | A | Responsibility yes; dedicated artefact only after first durable decision | Yes when present; until then current truth states “none yet” |

### Why each survives the ruthlessness test

| Responsibility | Forgotten without it | Why not merge elsewhere |
| -------------- | -------------------- | ----------------------- |
| Durable product intent | Why/who/boundaries drift or vanish after chat ends | Current truth is too volatile; history is too late |
| Current project truth | Resumption and multi-AI consistency fail | Intent is too slow-changing; history floods cost |
| Working agreements | Unsafe commits, privacy leaks, secret commits, missing quality floor | Must remain available without Cursor; too important to bury only in vendor rules |
| Accepted decisions | Important choices are re-litigated or silently reopened | Intent holds principles, not settled trade-offs; current truth should not accumulate rationale essays |

### Explicitly **not** in the permanent spine

- Technical architecture documents
- Local development manuals
- Deployment / multi-environment / release procedure docs
- Specialist a11y/perf/security manuals
- Roadmap as a mandatory separate surface
- Investigation folders as mandatory day-zero content
- Generated AI memory as source of truth
- Foundation adoption or provenance material

### Spine properties

- Passes memory-wipe when filled with honest content (including honest “unknown”).
- Works for one-hour projects: intent + current truth can be short; working agreements stay thin; decisions may be absent.
- Grows to mature services by **adding triggered memory**, not replacing the spine.
- No tiers; no deletion path for growth.
- No fictional ops rows.
- No empty authoritative tables pretending to be filled.
- Understandable from the repository without Cursor.

---

## 6. Triggered specialist memory

Triggers activate responsibilities; they do **not** change the permanent spine.

| Trigger (real need) | Memory that becomes necessary | Join default context? | Spine changes? | How another AI discovers it |
| ------------------- | ----------------------------- | --------------------- | -------------- | --------------------------- |
| Application code exists | Technical reality (“how it works”) | Conditionally yes when implementing | No | Pointer from current truth |
| Runnable project exists | Development instructions (run/build/verify) | Conditionally when developing | No | Pointer from current truth |
| User interface exists | UI accessibility expectations (beyond thin floor) | Conditionally for UI work | No | Pointer + working agreements note |
| Performance-sensitive interaction / large payloads | Evidence-first performance notes | Conditionally for perf work | No | Pointer when relevant |
| Maintained datasets / pipelines | Data shape, pipeline and accuracy notes | Conditionally for data work | No | Pointer from current truth |
| External services / APIs | Integration and failure-mode notes | Conditionally | No | Pointer |
| Deployment exists | Deploy/ops memory | Conditionally for release/ops tasks | No | Pointer; absent at concept |
| Multiple environments | Environment map and promotion rules | Conditionally | No | Pointer |
| Public users / indexing / analytics | Public-exposure and measurement notes | Conditionally | No | Pointer |
| Personal data processed | Privacy/retention specialist notes | Yes when that work is active; always respect working agreements | No | Pointer + agreements |
| Authentication exists | Authz/authn threat and flow notes | Conditionally | No | Pointer |
| Scheduled jobs / automation | Job inventory and failure handling | Conditionally | No | Pointer |
| Production incidents possible or real | Incident process / incident records | Process may be thin ops; records are historical | No | Ops pointer; incidents stay historical |
| Multi-milestone sustained work | Separate near-term roadmap surface | Light inclusion or pointer only | No | Pointer from current truth |
| Decision-heavy investigation | Historical investigation record | **No** by default | No | Index/pointer from current truth or decisions |
| Named public releases | Changelog / release history | **No** by default | No | Pointer when releasing |

Rules:

- Absence of a specialist area means “not yet needed”, not “delete a stub”.
- Do not pre-create a catalogue of empty specialist files.
- Discovery mechanism for Slice 0.4 structure design: current truth holds an explicit **pointers** section listing only memories that exist.

---

## 7. Canonical current-state contract

One authoritative Layer B surface answers “where is the project now?”

### Must include

| Field | Purpose |
| ----- | ------- |
| One-line purpose | Concise “what this is” |
| Lifecycle state | Honest label (concept, paused, public, …) |
| What exists now | Concrete inventory of real artefacts (code, data, docs) — or “none yet” |
| Milestone / version | Only when useful; omit rather than invent |
| Active focus | Current theme or “none” |
| Active slice | Summary or pointer (goal, status, completion criteria) — or “none” |
| Major blockers | Only real blockers |
| Important uncertainties | Open questions that affect next work |
| Next safe action | Single sensible next step |
| Branch / environment | Only when they exist and matter |
| Last meaningful update | Date + short note |
| Pointers | Links/names of deeper technical, operational, decision or historical memory that exists |

### Must not include

- Full historical narrative
- Lengthy investigation findings
- Duplicated architecture essays
- Complete roadmap or backlog
- Fictional infrastructure, staging rows or SEO gates
- Private or local-system information
- Foundation adoption/provenance text
- Secrets, tokens, personal emails, private paths

### Freshness

Stale when: lifecycle, what-exists, active slice or next action disagree with the repository or with an active-work detail surface. Agents must inspect the repo, not trust this surface blindly (spec principle 8).

---

## 8. Active-work model

### Recommendation: hybrid

| Situation | Representation |
| --------- | -------------- |
| No active slice | Current truth: “none” |
| Tiny one-session task | Current truth summary only |
| Multi-step implementation slice | Current truth pointer + separate active-work detail |
| Investigation-only work | Current truth pointer + historical investigation file as the working evidence surface |
| Paused work | Current truth status `paused` + enough detail to resume |
| Abandoned work | Close in current truth; optional short historical note if lessons matter; do not keep forever as “active” |
| Handoff between AIs | Prefer committed current truth + active detail; generated view may package them |
| Completion | Update current truth; promote durable outcomes into intent/decisions/tech memory; do **not** auto-archive a permanent report for every slice |

### Active-work detail contract (when separate)

Must state: goal, in-scope, out-of-scope, completion criteria, status, risks/blockers, and links to relevant evidence.

Must not become: issue tracker, permanent archive of every thought, or duplicate of current truth’s entire project status.

### Anti-pattern

Creating a permanent file for every small task. Default is **update current truth**; escalate to a dedicated active-work surface only when ambiguity or handoff cost is real.

---

## 9. Decision-memory model

### States

| State | Meaning | Default context? |
| ----- | ------- | ---------------- |
| Proposed | Under consideration | Mention in current truth if it blocks work |
| Temporary assumption | Working hypothesis; reversible | Current truth / intent assumptions |
| Accepted durable decision | Settled choice with rationale | Yes (index + records as needed) |
| Reversible implementation choice | Local engineering detail | Usually no dedicated decision record |
| Rejected approach | Considered and declined | Historical; link from decision if useful |
| Superseded decision | Was accepted; no longer current | Historical; keep out of default context |

### When a dedicated decision record is justified

Create one when **all** of the following tend to hold:

1. Reversal would be costly or confusing.
2. Future AIs would otherwise re-open the debate.
3. Rationale is not obvious from code alone.
4. The choice is product/architecture/process significant — not a one-line implementation tweak.

### Prevent

- Trivial decision logging
- Investigation findings auto-promoting to “accepted”
- Superseded decisions remaining in default context
- Empty decision templates on day zero

Until the first durable decision exists, current truth simply states that none are recorded yet. That is honest memory, not an empty form.

---

## 10. Historical evidence model

### Included kinds

Investigations, experiments, audit evidence, rejected options, incidents, retired documentation, superseded decisions, rare decision-heavy completed-slice reports.

### Default policy

| Rule | Policy |
| ---- | ------ |
| Discoverability | Dated records + pointers from current truth or decisions when still relevant |
| Default AI context | **Excluded** |
| Retention | Keep when they prevent re-work or record irreversible lessons; otherwise Git history may suffice |
| Completed slice specs | **Usually do not need permanent archive copies.** Update current truth; commit the work; add a historical file only if the slice produced decisions, rejected major options, or lengthy evidence worth re-reading |
| Path rigidity | Do not hard-force a single taxonomy that blocks real work (Slice 0.1 lesson: audits-only vs investigations) |

### Relation to Layer C

Historical evidence is Layer C. It must remain cheap to ignore and possible to retrieve.

---

## 11. Rough-intent lifecycle

### Recommended lifecycle

1. **Capture** — unstructured intent (typed or dictated) as identifiable initialisation input.
2. **Initialise** — AI proposes durable product intent, current truth, and first uncertainties; maintainer reviews.
3. **Promote** — approved durable intent becomes Layer A authority.
4. **Retain origin** — keep the original rough intent as **archived origin material** outside default AI context.
5. **Do not treat origin as current truth** — reinterpretation is allowed by reading origin + updating durable intent deliberately.
6. **Do not delete immediately** — preserves creative nuance and supports memory-wipe understanding of how the project began.
7. **Optional later disposal** — if origin adds only contradiction and no value, archive further or drop with explicit note; prefer deliberate removal over silent loss.

### Rejected options

| Option | Why rejected |
| ------ | ------------ |
| Remain permanently in default context | Duplicates and contradicts durable intent; fails cost test |
| Transform and delete immediately | Loses creative source; weakens reinterpretation |
| Keep as only product truth | Never becomes structured enough for multi-AI consistency |

---

## 12. AI-context model

### Recommendation

Generated AI context is a **view over canonical memory**, optionally materialised as:

- on-demand generation for local tools, and
- a **committed selective default snapshot** when remote/GitHub-based AIs need a reproducible package.

It is **not** canonical. Edits belong in source memories (A/B and triggered specialist), then regenerate the view.

### Default context must answer

Enough to pass memory-wipe and start safe next work:

- what/why (intent)
- now (current truth)
- how to work safely (working agreements)
- settled important decisions (if any)
- pointers to specialist memory that currently matters

### Eligible sources (default)

- Durable product intent
- Current project truth
- Working agreements
- Accepted decisions that are current (not superseded)
- Conditionally: technical/ops/quality specialist memory **only when current truth marks them relevant** or a task profile includes them

### Excluded by default

- Historical investigations, audits, incidents
- Superseded decisions
- Rough-intent origin archive
- Foundation-maintainer plane
- Prompt libraries
- Full specialist manuals unrelated to current work
- Raw logs, dumps, screenshots with sensitive data

### Active work

Always include the current-truth active summary/pointer. Include separate active-work detail when it exists.

### Inclusion declaration

A machine-readable or clearly human-declared inclusion list must name:

- included sources
- excluded classes
- generation timestamp
- content hash or equivalent freshness marker

### Size and staleness

- Measure bytes and source count (Slice 0.1 baseline ~47 KB / 16 files must be beaten materially for default selective context).
- Stale when source hashes/dates disagree or current truth’s last update is newer than the generated view.
- Never hand-edit the generated view as if it were truth.

### Multi-AI

| Consumer | Path |
| -------- | ---- |
| Local Cursor | Can read canonical sources directly; generated view optional |
| Remote GitHub AI | Needs committed selective snapshot **or** ability to read the same small spine files directly |
| ChatGPT upload workflows | Prefer the selective snapshot; forbid full-docs dump |

### Open test (do not invent certainty)

Whether “commit always” or “commit when sharing remotely” is better should be tested in a later slice with a dormant-concept and a mature-project handoff. Recommendation for design: **support both; default to committing a selective snapshot once generator exists**, because Slice 0.1 showed gitignored dumps fail multi-AI.

---

## 13. Vendor-neutral and vendor-specific boundary

| Kind | Home | Examples |
| ---- | ---- | -------- |
| Vendor-neutral project truth | Layers A/B + triggered specialist | Intent, current truth, decisions, architecture-when-real |
| Universal engineering principles | Working agreements (thin) + specialist when triggered | Privacy, secrets, inspect-don’t-assume, Git approval, a11y/security floors |
| Cursor-specific enforcement | Cursor rules only | Always-apply hooks, editor shorthand, local command habits |
| ChatGPT working guidance | Optional prompts / session instructions | Scoped review prompts |
| Temporary task prompts | Ephemeral | One-off implementation prompts |

### Critical instructions that must survive without Cursor

Privacy and personal/local-information rules; secrets hygiene; explicit authority for commit/push/production; accessibility and security floors where relevant; “inspect repository, don’t invent”; investigation-before-risky-change.

Cursor rules may **point to** working agreements and enforce behaviour; they must not be the only copy of those laws, and must not duplicate full project status or architecture.

---

## 14. Foundation-maintainer separation

| Material | Plane | May enter new project? |
| -------- | ----- | ---------------------- |
| Foundation maintenance provenance | Foundation-only | **No** |
| Historical extraction commentary / BlooPlax assumptions | Foundation-only / archive | **No** |
| Foundation design investigations (this series) | Foundation-only evidence | **No** as product truth |
| Adoption instructions for creating projects | Distribution / foundation UX | **Instruction during create**, not inherited living product memory |
| Templates that become project spine | Distribution → becomes project A/B | **Yes**, but only the spine + initialise outcome |
| Examples and test fixtures | Foundation-only or optional samples | Only if explicitly copied as samples, never as pretended project truth |
| Migration guidance for existing projects | Foundation-only | Reference during migration; not product default context |

Conceptual rule: **initialisation generates project memory; it does not copy foundation autobiography.**

Distribution mechanism (branch vs package vs clean root) is deferred to later slices; the memory-plane separation is decided now.

---

## 15. Privacy and repository-safety implications

Every memory responsibility inherits principle 23 and repository-safety capability 8.21.

| Risk | Rule |
| ---- | ---- |
| Personal identity | Neutral roles; `gromitski` only when public GitHub identity is required |
| Personal or no-reply emails | Commit metadata/local Git config only; **never** documentation |
| Local paths, hostnames, hardware, private IPs/URLs | Forbidden in committed memory; use placeholders |
| Secrets / tokens | Ignored local config or secret stores; placeholders in docs |
| Raw logs / diagnostic dumps | Redact or keep out of repo; historical reports must not paste secrets |
| AI authorship metadata | Do not add co-author trailers when clean authorship is required |
| Current truth / investigations | Especially high risk for accidental path and screenshot leakage — inspect before commit |

### Placement guide

| Information kind | Placement |
| ---------------- | --------- |
| Public project facts | Canonical memory |
| Neutral placeholders | Docs examples |
| Local secrets | Ignored local configuration / secret stores |
| Sensitive diagnostics | Redacted reports or external private systems |
| Foundation private ops | Foundation-maintainer plane only |

---

## 16. Stress-test results

If any test required altering the permanent spine, the model would fail. None did.

### A. Tiny experiment (one-file script, one hour, abandoned)

| Aspect | Result |
| ------ | ------ |
| Permanent memory | Short intent; short current truth (“abandoned/paused”); thin working agreements; no decisions |
| Triggered memory | None, or minimal “how to run” if needed |
| Default AI context | Spine only |
| Active work | “None” or closed note in current truth |
| Overhead | Low — no ops/a11y manuals |
| Structural change | None |

### B. Dormant concept (ten minutes, one year later)

| Aspect | Result |
| ------ | ------ |
| Permanent memory | Intent + current truth with lifecycle `paused` + next action + uncertainties |
| Triggered memory | None |
| Default AI context | Spine; origin rough intent available only if retrieved |
| Active work | None |
| Overhead | Minimal |
| Structural change | None |

### C. Wye Trains (concept-stage, data-dependent, feasibility unresolved)

| Aspect | Result |
| ------ | ------ |
| Permanent memory | Intent emphasises uncertainty; current truth lifecycle `feasibility`/`concept`; working agreements |
| Triggered memory | Data notes when datasets appear; no fake deploy docs |
| Default AI context | Spine + data notes only if marked relevant |
| Active work | Investigation slice pointing at a historical investigation file |
| Overhead | Avoids web-ops furniture (Slice 0.1 failure) |
| Structural change | None |

### D. BlooPlax (mature public web app)

| Aspect | Result |
| ------ | ------ |
| Permanent memory | Full spine; many accepted decisions |
| Triggered memory | Technical reality, dev, deploy/envs, a11y/perf specialist, data pipeline, release history, rich Layer C audits |
| Default AI context | Spine + currently relevant specialist pointers; **not** full audit tree |
| Active work | Versioned slice detail + current-truth pointer |
| Overhead | Historical debt stays in Layer C; must not re-enter dump culture |
| Structural change | None — specialist memory attaches around the same spine |

### E. Non-web project (CLI / automation / analysis / desktop)

| Aspect | Result |
| ------ | ------ |
| Permanent memory | Same spine |
| Triggered memory | Dev/run notes; no UI a11y manual unless UI exists |
| Default AI context | Spine; no web deploy assumptions |
| Active work | Hybrid as usual |
| Overhead | None forced by web inheritance |
| Structural change | None |

---

## 17. Rejected alternatives

| Alternative | Why rejected |
| ----------- | ------------ |
| Keep current numbered `docs/00–11` as spine | Empty shells, web-mature bias, deletion/tiers (Slice 0.1) |
| Two-layer only (intent + history) | Fails “now”, active work and safe next action |
| Four permanent content layers including Tech/Ops | Forces fictional or empty ops memory onto concepts |
| Active work always a separate mandatory file | Overhead for tiny tasks; ceremony risk |
| Active work only inside chat | Fails multi-AI and memory-wipe |
| Decisions always mandatory empty ADR set | Empty authoritative forms |
| Decisions only in Git messages | Poor multi-AI retrieval; weak rationale home |
| Rough intent as permanent default context | Duplication and contradiction |
| Generated dump as canonical memory | Spec anti-pattern; Slice 0.1 cost failure |
| Gitignore-only generated handoff | Fails remote multi-AI (Slice 0.1) |
| Archive every completed slice | Permanent-file inflation; anti-pattern in spec |
| Foundation provenance shipped into projects | Principle 21 / capability 8.19 failure |
| Subtractive tiers for progressive needs | Explicitly rejected by specification |

---

## 18. Risks and trade-offs

### Largest trade-off

**Resumability and multi-AI consistency require a small amount of always-maintained memory** (the spine). That is real overhead versus “just chat”. The bet is that four thin responsibilities cost less than repeated re-education, unsafe guesses and dump culture — but the spine must stay ruthlessly short or the product fails the satisfaction and cost tests.

### Other risks

| Risk | Mitigation |
| ---- | ---------- |
| Current truth becomes a junk drawer | Strict must-not list; pointers instead of essays |
| Decision logging becomes theatre | High bar for dedicated records |
| Triggered memory quietly becomes mandatory stubs | Forbid empty specialist files; create on real trigger |
| Committed generated context goes stale | Timestamp/hash; regenerate on memory updates; never hand-edit |
| Working agreements grow into a second foundation manual | Keep thin; push depth into triggered specialist |
| Hybrid active work confuses agents | Current truth always states whether detail exists |
| Historical nickname/PII debt in older files | Privacy inventory; clean-root before v1.0 |

---

## 19. Open questions for repository-structure design (Slice 0.4+)

These are structure/expression questions, **not** unresolved memory responsibilities:

1. How are the four spine responsibilities expressed as files or surfaces without empty shells?
2. Where does archived rough intent live so it is excluded from default context?
3. Exact pointer syntax from current truth to triggered memory.
4. Naming and placement conventions for investigations vs audits vs incidents without path rigidity.
5. How inclusion rules for generated views are declared (manifest, script config, or header).
6. Whether one committed default view is enough or task profiles are needed at v1.
7. How Cursor rules reference working agreements without duplicating them.
8. How initialisation writes the spine in one step from rough intent.
9. How foundation distribution creates a clean project without provenance leakage.
10. Migration path for BlooPlax-like mature repos onto the spine without losing Layer C.
11. Freshness checks that are good enough without promising perfect doc–code sync.
12. Whether decision index and decision records are one surface or two once volume grows.

---

## 20. Clear recommendation for Slice 0.4

Slice 0.4 should design the **repository expression** of this memory model — still without implementing generators or replacing `main` — specifically:

1. Map the four permanent responsibilities to concrete surfaces (still avoiding premature filename lock-in where alternatives remain).
2. Define discovery/pointer conventions for triggered specialist memory.
3. Define Layer C placement principles that stay flexible.
4. Define the generated-view contract (inclusion manifest, staleness markers, commit policy experiment).
5. Define the foundation-maintainer plane boundary in distribution terms (conceptual, not necessarily final packaging).
6. Produce stress-test sketches for tiny / Wye Trains / BlooPlax shapes against the proposed surfaces.
7. List acceptance checks proving no empty authoritative forms and no fictional ops content on day zero.

**Do not** in Slice 0.4: implement scripts, rewrite the live foundation tree into production use, or merge to `main`.

---

## Decision summary (quick reference)

| Decision | Choice |
| -------- | ------ |
| Permanent responsibilities | **4** — intent, current truth, working agreements, accepted decisions (artefact when needed) |
| Layers | **A/B/C** + generated views + foundation plane |
| Active work | **Hybrid** |
| Rough intent | **Promote + archive origin outside default context** |
| Decisions | **Core responsibility; no empty day-zero file** |
| Architecture / operations | **Triggered** |
| Generated context | **View** |
| Commit generated context | **Both on-demand and optional/preferred selective commit** (test freshness in later slice) |
| Completed slices | **Usually no archive doc** |
| Foundation material | **Separate plane; never inherited as product truth** |

---

## Document control

| Item | Value |
| ---- | ----- |
| Slice | 0.3 — Design project memory model |
| Output type | Investigation / architecture decision record (evidence path) |
| Spec questions advanced | Especially open questions 1–11, 14, 17–19, 22–23, 30 |
| Unchanged by this slice | `FOUNDATION-SPEC.md`; prior investigation files; current foundation tree |
