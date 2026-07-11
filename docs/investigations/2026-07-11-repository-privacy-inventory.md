# Repository privacy inventory

**Date:** 2026-07-11  
**Slice:** 0.2.1 — Correct privacy policy and repository identity  
**Branch inspected:** `audit/foundation-repository` (also commits reachable from `main`)  
**Method:** Tracked-content search, Git metadata inspection, local/global Git config review  
**Scope:** Evidence only for privacy exposure; no rewrite of `main` in this slice  

Sensitive values are **redacted**. No full personal emails, secrets or tokens are reproduced below.

---

## 1. Verdict

The repository has **durable privacy debt in Git history** (personal email on every commit; AI co-author trailers on two commits) and **personal-name language in tracked content** (nickname `Stu` in several living docs and the Slice 0.1 audit). Slice 0.2.1 corrects the authoritative product specification, configures a privacy-safe **local** repository identity, and replaces the unmerged Slice 0.2 tip commit with privacy-safe author/committer metadata.

Cleaning **only** the latest commit is **not** sufficient for a privacy-safe repository before v1.0. A **full history rewrite or clean-root rebuild** will eventually be required. `main` was not altered in this slice.

---

## 2. Approved identity

| Use | Approved value |
| --- | -------------- |
| Public GitHub handle | `gromitski` |
| Commit author/committer name | `gromitski` |
| Commit email | GitHub no-reply address (local Git config / commit metadata only — not written into project docs) |

Neutral role language (`the maintainer`, `the project owner`, `the user`) is preferred in documentation unless the public handle is genuinely required.

---

## 3. Current tracked content

Searched tracked files for personal names, emails, local paths, hostnames, private IPs, credentials and related patterns.

### 3.1 Findings (redacted)

| Category | Result | Notes |
| -------- | ------ | ----- |
| Nickname / personal first name `Stu` | **Present** | In `FOUNDATION-SPEC.md` (pre-correction), `docs/ai/00-ai-memory-core.md`, `docs/04-git-workflow.md`, `docs/audits/README.md`, Slice 0.1 audit. Spec corrected in this slice; other files remain for a later content-cleanup slice unless rebuilt. |
| Full legal name | **Not found** in tracked content | |
| Personal email addresses in tracked files | **Not found** | Placeholder `hello@example.com` in maintainer notes only. |
| Approved handle `gromitski` | **Present (appropriate)** | Remote URL in Slice 0.1 audit evidence table. |
| `cursoragent` in tracked file bodies | **Not found** | Appears only in historical commit trailers (see §4). |
| `Co-authored-by` in tracked file bodies | **Not found** | |
| Private filesystem paths (`/Users/`, `/home/`) | **Not found** | |
| Private IP ranges | **Not found** | |
| Obvious credentials / tokens (`ghp_`, `sk-`, PEM keys, etc.) | **Not found** | Policy text about secrets only. |
| Localhost placeholders | **Present (benign)** | `http://localhost:<port>` in local-dev docs. |
| Hardware / device / hostname details | **Not found** | |
| Untracked `.obsidian/` | **Present locally, untracked** | Must remain untracked; not staged. |

### 3.2 Content risk summary

- Highest content risk before this slice: personal nickname throughout product language, especially the authoritative specification.  
- Specification corrected in Slice 0.2.1.  
- Residual content risk: nickname `Stu` remains in older foundation docs and the Slice 0.1 audit file (historical evidence; not rewritten here).  
- No secrets or private paths found in tracked trees.

---

## 4. Git history (`main` ∪ `audit/foundation-repository`)

Four commits reachable from both tips of interest:

| Commit (short) | Subject | Author name | Author email (redacted) | AI trailer |
| -------------- | ------- | ----------- | ----------------------- | ---------- |
| `1830ddc` | Initial reusable AI project foundation | `gromitski` | `s***@gmail.com` | No |
| `2640c19` (`main` tip) | Polish foundation README… | `gromitski` | `s***@gmail.com` | **Yes** — `Co-authored-by: Cursor <cursoragent@cursor.com>` |
| `ed34e75` (Slice 0.1) | Add foundation repository audit | `gromitski` | `s***@gmail.com` | **Yes** — `Co-authored-by: Cursor <cursoragent@cursor.com>` |
| `979afb7` (Slice 0.2 tip, pre-correction) | v0.1.2 define AI Project Foundation… | `gromitski` | `s***@gmail.com` | No |

### 4.1 Counts

| Exposure | Commit count |
| -------- | ------------ |
| Personal email in author or committer metadata | **4** |
| Personal real-name (non-approved) in author or committer name fields | **0** (names already `gromitski`) |
| AI co-author trailers (`Co-authored-by` / `cursoragent`) | **2** |

### 4.2 Historical filenames

No historical filenames contained personal names, emails or local-system identifiers. Paths are generic project/docs names.

### 4.3 Is tip-only cleanup enough?

**No.**

- Replacing only the Slice 0.2 tip removes personal email from the **current branch tip** and prevents stacking another exposed tip.  
- Slice 0.1 (`ed34e75`) still carries personal email **and** an AI co-author trailer.  
- `main` history still carries personal email on all commits and an AI trailer on `2640c19`.  
- Tracked content outside the specification still contains the nickname `Stu`.

### 4.4 Slice 0.1 rewrite recommendation

Slice 0.1 metadata **does** require eventual correction (personal email + AI trailer). This inventory **recommends** correcting it as part of a later dedicated history-sanitisation / clean-root step, **not** by casually rewriting it in the same narrow tip replacement unless a deliberate force-push of both audit commits is planned and reviewed.

**This slice:** preserve Slice 0.1 content and commit object; replace only the Slice 0.2 tip with a privacy-safe combined specification commit. **Do not rewrite `main`.**

### 4.5 Before v1.0

**A full history rewrite or clean-root rebuild will eventually be required** so that:

1. No personal email remains in author/committer metadata.  
2. No AI co-author trailers remain where clean human authorship is required.  
3. Product documentation uses neutral role language (or the approved handle only where needed).  

Open design questions in the specification already note clean-root and historical co-authorship as unresolved delivery choices; this inventory treats privacy-safe history as a **v1.0 acceptance condition**, not optional polish.

---

## 5. Local Git configuration

Inspected without committing values.

| Setting | State after Slice 0.2.1 |
| ------- | ------------------------ |
| `user.name` (local) | `gromitski` — **privacy-safe** |
| `user.email` (local) | GitHub no-reply address — **privacy-safe** (config / commits only; not in docs) |
| Local repo identity overall | **Privacy-safe for new commits** |
| `user.name` (global) | `gromitski` |
| `user.email` (global) | Personal mailbox still set — redacted as `s***@gmail.com` |
| Global identity risk | **May expose PII in other repositories** that inherit global config and lack a local override |
| `.git/config` tracked? | **No** (must never be committed) |

Global configuration was **not** changed in this slice.

---

## 6. Actions taken in Slice 0.2.1

1. Added principle 23 and related success / anti-pattern / v1.0 / capability language to `FOUNDATION-SPEC.md`.  
2. Replaced personal-name references in the specification with neutral role language; retained `gromitski` only where public identity is relevant.  
3. Set local repository `user.name` / `user.email` to the approved identity.  
4. Replaced the unmerged Slice 0.2 tip commit with a privacy-safe commit containing the corrected specification and this inventory.  
5. Force-pushed `audit/foundation-repository` with `--force-with-lease` only.

---

## 7. Confirmation

- No full personal email address is written in this report.  
- No secret, token or credential value was copied into this report.  
- Sensitive findings are redacted (for example `s***@gmail.com`).  
- `.obsidian/` remains untracked and must not be staged.

---

## Document control

| Item | Value |
| ---- | ----- |
| Inventory role | Evidence for privacy correction and future history sanitisation |
| Non-goals | Rewriting `main`; Slice 0.3 architecture; content rewrite of all legacy `Stu` docs |
