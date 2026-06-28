# Prompt library

Copy-paste prompts for `<project-name>`. Replace placeholders before use.

Each prompt assumes investigation or implementation in Cursor unless noted for ChatGPT-only review.

---

## 1. Repository investigation

**Goal:** Understand current project state before planning work.

**Inspect:**

- `<docs-dir>/00-overview.md`
- `<docs-dir>/01-how-it-works.md`
- `<docs-dir>/05-decisions-and-rationale.md`
- Git: branch, status, recent commits
- Relevant source paths for the topic

**Constraints:**

- Read-only — **do not change code or docs**
- Do not guess; cite file paths for claims
- Do not commit

**Expected output:**

- Short summary of current state
- What is documented vs unclear
- Recommended next step (investigation audit vs scoped implementation)

**Verification:**

- Every factual claim traceable to a file or command output

---

## 2. Bug investigation

**Goal:** Find root cause of `<describe symptom>` without fixing yet.

**Inspect:**

- Reproduction steps and environment (local / staging / production)
- Console, network, and relevant source files
- `<docs-dir>/08-troubleshooting.md`
- Recent Git changes touching the area

**Constraints:**

- **Do not change code** unless explicitly asked to fix in the same task
- Do not commit
- Prefer smallest diagnostic steps

**Expected output:**

- Likely cause with evidence
- Ruled-out causes
- Proposed fix scope (files, risk)
- Optional: save lengthy findings to `<docs-dir>/audits/code/YYYY-MM-DD-<topic>-audit.md`

**Verification:**

- Explain how to reproduce and how fix would be verified

---

## 3. Scoped implementation

**Goal:** Implement `<single focused outcome>`.

**Inspect:**

- `<docs-dir>/` guides for constraints
- Existing patterns in the files you will edit
- Related tests or scripts

**Constraints:**

- **Minimal diff** — no unrelated refactors
- Do not change docs unless this task includes documentation
- Do not commit or push unless asked
- Run relevant verify command (build / test / lint)

**Expected output:**

- What changed and why
- What was verified
- Intentional follow-ups left out of scope

**Verification:**

- State command(s) run and result

---

## 4. Documentation update

**Goal:** Update `<docs-dir>/` to reflect `<documented behaviour change>`.

**Inspect:**

- Current doc sections affected
- Code or config that is now source of truth
- Cross-links from README and overview

**Constraints:**

- Edit **only** docs requested or clearly implied
- Do not rewrite unrelated sections
- Do not regenerate AI memory unless asked

**Expected output:**

- List of files updated
- Brief summary of changes

**Verification:**

- Links valid; no contradiction with code or deploy docs

---

## 5. Release preparation

**Goal:** Prepare `<milestone>` for promotion toward production.

**Inspect:**

- `<docs-dir>/09-release-procedure.md`
- `<docs-dir>/04-git-workflow.md`
- `<docs-dir>/00-overview.md`
- `<app-version-file>` if public version bump needed
- Staging deployment state

**Constraints:**

- **Do not push production** without explicit approval
- Do not bump public version unless this release includes it
- Checklist format preferred

**Expected output:**

- Release readiness checklist with pass/fail/unknown
- Blockers before staging or production
- Suggested Git promotion steps (no execution unless asked)

**Verification:**

- Smoke-test URLs documented for staging/production

---

## 6. Accessibility audit

**Goal:** Accessibility findings for `<scope>` — report only.

**Inspect:**

- `<docs-dir>/06-accessibility.md`
- Relevant components, CSS, and static content
- Keyboard tab order and focus behaviour on primary flows

**Constraints:**

- **Audit only — no code, CSS, or copy changes**
- Do not overclaim WCAG level
- Save report to `<docs-dir>/audits/ux/YYYY-MM-DD-<topic>-accessibility-audit.md`

**Expected output:**

- Executive summary table (area / verdict)
- Launch-blocking vs post-launch issues
- Evidence (file paths, behaviour observed)

**Verification:**

- Distinguish code review from manual testing gaps

---

## 7. Performance investigation

**Goal:** Evidence-based performance assessment for `<scope>`.

**Inspect:**

- `<docs-dir>/07-performance.md`
- Network payload and bundle sizes (build output or Network tab)
- Critical user path timing

**Constraints:**

- **Do not implement optimisations** unless explicitly asked
- State resource, size, user benefit, trade-off for any recommendation
- Do not chase Lighthouse score alone

**Expected output:**

- Measured bottlenecks ranked by user impact
- Recommendations with trade-offs
- Optional audit file under `<docs-dir>/audits/performance/`

**Verification:**

- Numbers cited or marked “not measured — needs X”

---

## 8. Code review

**Goal:** Review `<branch / diff / files>` for correctness, risk, and maintainability.

**Inspect:**

- Stated diff or files
- `<docs-dir>/05-decisions-and-rationale.md`
- Security, accessibility, and performance implications

**Constraints:**

- **Do not change code** unless asked to apply fixes
- Flag blockers vs nits
- Do not commit

**Expected output:**

- Summary verdict (approve / approve with notes / block)
- Issues by severity with file references
- Suggested follow-up prompts (scoped, one concern each)

**Verification:**

- Each issue references specific location or behaviour

---

## Usage notes

- Split large work into multiple prompts from this library.
- Add project-specific prompts under `<docs-dir>/ai/` as patterns emerge.
- For ChatGPT-only sessions, attach `<docs-dir>/ai/01-ai-project-memory.md` after regenerating.
