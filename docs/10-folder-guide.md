# Folder guide

Where things live — for orientation after time away from the project.

---

## Top level

```text
<project-slug>/
  .cursor/rules/     Agent behaviour (may be committed or gitignored)
  .github/workflows/ CI (if used)
  docs/              Operational documentation (<docs-dir>)
  public/            Static assets served as-is
  scripts/           Build-time and maintenance scripts
  src/               Application source (customise name)
  dist/ or build/    Generated site output (not committed)
  node_modules/      Dependencies (not committed)
```

Adjust for your stack (e.g. `app/`, `lib/`, `content/`).

---

## Source code

| Path | Purpose |
| ---- | ------- |
| `src/` | Components, pages, utilities |
| | |

---

## Public / static assets

| Path | Purpose |
| ---- | ------- |
| `public/` | Images, fonts, files copied to output root |
| | Generated runtime data (if committed) |

---

## Scripts

| Path | Purpose |
| ---- | ------- |
| `scripts/generate-ai-project-memory.mjs` | Concatenate docs for AI handoff |
| | Build / data pipeline scripts |

---

## Documentation

| Path | Purpose |
| ---- | ------- |
| `docs/00–10*.md` | Numbered operational guides |
| `docs/ai/` | AI collaboration docs |
| `docs/audits/` | Investigation and audit reports |
| `docs/decisions/` | ADRs |

---

## Generated files

| File | Committed? | Regenerate |
| ---- | ---------- | ---------- |
| `dist/` | No | `npm run build` |
| `docs/ai/01-ai-project-memory.md` | Project choice (default: gitignore) | `generate-ai-project-memory.mjs` |
| | | |

Document policy clearly — agents depend on it.

---

## Local-only files

Typically gitignored:

- `.env`
- `data/raw/` or other upstream dumps
- Local logs and exports
- `.cursor/` — **unless** this project commits rules intentionally

See [`.gitignore`](../.gitignore) and [`TEMPLATE_NOTES.md`](../TEMPLATE_NOTES.md).

---

## Related

- [`02-local-development.md`](02-local-development.md)
- [`03-deployment.md`](03-deployment.md)
