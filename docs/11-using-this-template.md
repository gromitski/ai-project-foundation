# Using this template

How to create a new private GitHub project from the **ai-project-foundation** template.

Commands below assume macOS or Linux Terminal. Replace placeholders before running.

---

## Overview

The foundation provides Cursor rules, operational docs, and an optional AI memory generator. It is **not** an application — you copy it, customise placeholders, trim unused sections, then add your own code.

---

## Recommended use

1. Start with **Standard** tier (all six Cursor rules + core docs) unless the project is tiny.
2. Replace placeholders in one pass before the first real commit.
3. Update `docs/00-overview.md` early — agents are instructed to read it first.
4. Default to **gitignoring** generated AI memory; regenerate when needed.
5. Delete doc sections that do not apply rather than leaving misleading template text.

See tiered setup in the [root README](../README.md#minimal--standard--full-setup).

---

## Creating a new private GitHub repo

1. On GitHub: **New repository**
2. Name: `<new-project-name>` (or your chosen `<project-slug>`)
3. Visibility: **Private** (recommended for new work)
4. Do **not** add a README, `.gitignore`, or licence — the foundation already includes them
5. Copy the repository URL — referred to here as `<new-repo-url>`

Example URL shape: `git@github.com:<github-username>/<new-project-name>.git`

---

## Copying the template locally

Choose one approach.

### Option A — Clone the foundation, then re-point Git

Useful when the foundation lives in a known location:

```bash
cd <projects-folder>
git clone <foundation-repo-url> <new-project-name>
cd <new-project-name>
```

You will replace the remote in a later step.

### Option B — Copy files without history

Useful when you want a clean Git history in the new project:

```bash
cd <projects-folder>
mkdir <new-project-name>
cd <new-project-name>

# Adjust the source path to where you keep ai-project-foundation
cp -R /path/to/ai-project-foundation/. .
rm -rf .git
```

### Option C — GitHub “Use this template”

If you publish **ai-project-foundation** as a GitHub template repository, use GitHub’s **Use this template** button, then clone the new repo:

```bash
cd <projects-folder>
git clone <new-repo-url>
cd <new-project-name>
```

---

## Initialising Git

If you used Option B (copy without `.git`):

```bash
cd <projects-folder>/<new-project-name>
git init
git branch -M <primary-branch>
```

If you cloned the foundation (Option A), remove the old remote before adding yours:

```bash
git remote remove origin
```

Verify status:

```bash
git status
```

---

## Adding the GitHub remote

```bash
git remote add origin <new-repo-url>
git remote -v
```

---

## Replacing placeholders

Search and replace across the repo:

```bash
cd <projects-folder>/<new-project-name>
rg '<' --glob '*.md' --glob '*.mdc'
```

Minimum replacements:

| Placeholder | Set to |
| ----------- | ------ |
| `<project-name>` | Human-readable project name |
| `<project-slug>` | Folder and repo slug |
| `<production-domain>` | Production URL |
| `<staging-domain>` | Staging URL (or remove staging rows) |
| `<hosting-provider>` | e.g. Cloudflare Pages, Netlify, Vercel |
| `<development-branch>` | e.g. `dev` |
| `<staging-branch>` | e.g. `staging` (or remove if unused) |
| `<primary-branch>` | e.g. `main` |
| `<docs-dir>` | Usually `docs` |

Also update `README.md` for your product (the foundation README describes the template; replace it with your project entry point).

Files that commonly need attention:

- `README.md`
- `docs/00-overview.md`
- `docs/03-deployment.md`
- `docs/04-git-workflow.md`
- `.cursor/rules/02-git-and-release.mdc`

---

## First commit

Review what will be committed:

```bash
git status
git diff
```

Stage and commit:

```bash
git add .
git commit -m "Initial project from ai-project-foundation template"
git push -u origin <primary-branch>
```

Do not commit `.env`, local secrets, or `docs/ai/01-ai-project-memory.md` unless you intentionally track generated memory (see below).

---

## Opening the new project in Cursor

1. **File → Open Folder** (or `cursor <projects-folder>/<new-project-name>` from Terminal)
2. Confirm [`.cursor/rules/`](../.cursor/rules/) is present
3. Start a chat and ask the agent to read `docs/00-overview.md` before substantial work — the rules already instruct this

Decide whether `.cursor/rules/` stays committed or is gitignored per project. If gitignored, document that in `docs/10-folder-guide.md`.

---

## Checking `.cursor/rules/`

Six rules should be present:

| File | Purpose |
| ---- | ------- |
| `00-project-behaviour.mdc` | Scope, safety, commits only when asked |
| `01-code-quality.mdc` | Focused diffs, conventions |
| `02-git-and-release.mdc` | Branches and production approval |
| `03-documentation.mdc` | Docs workflow and audits |
| `04-accessibility-performance.mdc` | Evidence-first a11y and performance |
| `05-repository-hygiene.mdc` | Secrets and generated file policy |

For **Minimal** tier, you may delete or disable rules you do not need — keep at least hygiene and documentation guidance.

---

## Generated AI memory — keep or ignore?

**Default (recommended):** ignore `docs/ai/01-ai-project-memory.md` — already listed in [`.gitignore`](../.gitignore). Regenerate locally when you need a single file for ChatGPT.

**Commit the file** only if you want the concatenated bundle in Git without regenerating on every machine. To track it:

1. Remove or comment out the `docs/ai/01-ai-project-memory.md` line in `.gitignore`
2. Document the choice in `docs/10-folder-guide.md`
3. Regenerate and commit when asked

---

## Running the AI memory generator

From the project root (Node.js required — no npm dependencies for the script itself):

```bash
node scripts/generate-ai-project-memory.mjs
```

Optional environment variables:

```bash
DOCS_DIR=docs \
OUTPUT_FILE=docs/ai/01-ai-project-memory.md \
PROJECT_NAME="My Project" \
node scripts/generate-ai-project-memory.mjs
```

Optional: wire in `package.json`:

```json
"scripts": {
  "generate:ai-memory": "node scripts/generate-ai-project-memory.mjs"
}
```

Edit source files under `docs/`, not the generated output. See [`docs/ai/00-ai-memory-core.md`](ai/00-ai-memory-core.md).

---

## Trimming the template for small projects

**Minimal** checklist:

- [ ] Keep `05-repository-hygiene.mdc` and `03-documentation.mdc`
- [ ] Simplify or shorten `02-git-and-release.mdc` if you use a single branch
- [ ] Keep `docs/00-overview.md` and `docs/04-git-workflow.md`
- [ ] Remove `docs/09-release-procedure.md` if you do not use formal releases
- [ ] Remove `docs/audits/` subtree if you will not store audits in-repo
- [ ] Remove `docs/ai/10-prompt-library.md` if unused
- [ ] Delete [`MAINTAINER_NOTES.md`](../MAINTAINER_NOTES.md) from product repos (optional — it is for foundation maintainers)

**Standard** — keep all six rules and `docs/00–04` plus `docs/ai/00-ai-memory-core.md`.

**Full** — keep everything; customise placeholders only.

---

## First-project checklist

- [ ] Private GitHub repo created; remote added
- [ ] Placeholders replaced; product README written
- [ ] `docs/00-overview.md` describes your real project
- [ ] Branch names in docs and `.cursor/rules/02-git-and-release.mdc` match your workflow
- [ ] Staging sections removed or filled in
- [ ] `.gitignore` reviewed (secrets, raw data paths, AI memory policy)
- [ ] Cursor rules reviewed; tier chosen (Minimal / Standard / Full)
- [ ] Application code or existing repo attached
- [ ] First push smoke-tested (clone fresh elsewhere if unsure)

---

## Common mistakes to avoid

| Mistake | Why it hurts | What to do instead |
| ------- | ------------ | ------------------ |
| Pushing without replacing placeholders | Agents and humans follow wrong domains/branches | Run `rg '<'` before first push |
| Leaving the foundation README as the product README | Confusing entry point for collaborators | Rewrite README for your app |
| Committing `.env` or secrets | Security incident | Use `.env.example` with placeholders only |
| Committing large raw data dumps | Bloated repo, accidental publication | Extend `.gitignore`; document in `docs/10-folder-guide.md` |
| Editing `01-ai-project-memory.md` by hand | Changes lost on regenerate | Edit `docs/` sources, then rerun the script |
| Three-branch docs with a one-branch workflow | Agents ask for staging promotion that does not exist | Trim git docs and rules to match reality |
| Stale `project-status.mdc` | Agents trust wrong version/state | Prefer `docs/00-overview.md` or keep snapshot in sync |
| Copying `MAINTAINER_NOTES.md` confusion | Product repo references BlooPlax extraction | Delete maintainer notes from product repos |

---

## Destructive commands — avoid unless you mean it

These are **not** required for normal setup:

| Command | Risk |
| ------- | ---- |
| `git push --force` | Overwrites remote history |
| `git reset --hard` | Discards uncommitted work |
| `rm -rf` on project paths | Permanent file loss |

Prefer `git status`, `git diff`, and fresh clones to recover from mistakes.

---

## Related

- [Root README](../README.md)
- [`MAINTAINER_NOTES.md`](../MAINTAINER_NOTES.md) — foundation maintainer only
- [`docs/10-folder-guide.md`](10-folder-guide.md) — folder layout and generated file policy
- [`docs/ai/00-ai-memory-core.md`](ai/00-ai-memory-core.md) — AI workflow
