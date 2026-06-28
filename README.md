# <project-name>

One-paragraph description of what the project does and who it is for.

**Production:** `<production-domain>`

---

## Quick start

**Prerequisites:** {e.g. Node.js ≥ 22, Python ≥ 3.12}

```bash
# Install — adjust for your stack
npm install

# Local development — replace with your commands
npm run dev
```

Open `http://localhost:<port>`.

Common commands: see [`<docs-dir>/02-local-development.md`](docs/02-local-development.md).

---

## Documentation

Operational reference lives in [`docs/`](docs/) (customise `<docs-dir>` if renamed).

| Doc | What it covers |
| --- | -------------- |
| [`docs/00-overview.md`](docs/00-overview.md) | Current project state |
| [`docs/01-how-it-works.md`](docs/01-how-it-works.md) | Runtime behaviour and user flows |
| [`docs/03-deployment.md`](docs/03-deployment.md) | Build targets and hosting |
| [`docs/04-git-workflow.md`](docs/04-git-workflow.md) | Branch promotion and environments |
| [`docs/ai/00-ai-memory-core.md`](docs/ai/00-ai-memory-core.md) | Working with AI assistants |
| [`docs/ai/01-ai-project-memory.md`](docs/ai/01-ai-project-memory.md) | **Auto-generated** — run `node scripts/generate-ai-project-memory.mjs` |

---

## AI-assisted development

- **Cursor rules:** [`.cursor/rules/`](.cursor/rules/) — agent behaviour for this project
- **Prompt library:** [`docs/ai/10-prompt-library.md`](docs/ai/10-prompt-library.md)
- **Generated memory:** concatenates `<docs-dir>/` for ChatGPT handoff — see [`TEMPLATE_NOTES.md`](TEMPLATE_NOTES.md)

---

## Repository hygiene

Do not commit secrets, raw source dumps, or unintended local files. Review `git diff --staged` before pushing. See [`.cursor/rules/05-repository-hygiene.mdc`](.cursor/rules/05-repository-hygiene.mdc).
