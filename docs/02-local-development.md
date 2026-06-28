# Local development

---

## Prerequisites

| Tool | Version |
| ---- | ------- |
| Node.js | {e.g. ≥ 22} |
| Package manager | npm / pnpm / yarn |
| Other | |

Optional: `.nvmrc` or `engines` in `package.json` for version pinning.

---

## First-time setup

```bash
git clone <repository-url>
cd <project-slug>
npm install
```

---

## Run locally

```bash
npm run dev
```

Open `http://localhost:<port>`.

Notes:

- Hot reload: {yes/no}
- Service worker / PWA in dev: {usually off — document if different}
- Env vars: copy `.env.example` to `.env` if the project uses local secrets

---

## Common commands

| Command | Purpose |
| ------- | ------- |
| `npm run dev` | Local development server |
| `npm run build` | Production-shaped build |
| `npm run preview` | Preview production build locally |
| `npm test` | Tests (if configured) |
| `npm run lint` | Lint (if configured) |
| `node scripts/generate-ai-project-memory.mjs` | Regenerate AI handoff doc |

Add project-specific scripts here as they stabilise.

---

## Verify a change

Minimum checklist before asking for review or commit:

- [ ] App loads locally
- [ ] Changed flow manually tested
- [ ] Relevant test/lint/build command passed
- [ ] No secrets or raw dumps staged

---

## Common local issues

| Symptom | Likely cause | Fix |
| ------- | -------------- | --- |
| Port already in use | Previous dev server | Kill process or change port |
| Stale assets | Cached build | Clean `dist/` and rebuild |
| Wrong Node version | Version mismatch | Use version from `.nvmrc` |
| Missing env | `.env` not created | Copy from `.env.example` |

More: [`08-troubleshooting.md`](08-troubleshooting.md).
