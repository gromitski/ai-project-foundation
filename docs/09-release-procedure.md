# Release procedure

Checklist for promoting a tested milestone to `<production-domain>`.

Use with [`04-git-workflow.md`](04-git-workflow.md) and [`03-deployment.md`](03-deployment.md).

---

## Release readiness

- [ ] Scope complete; acceptance criteria met
- [ ] No known accessibility release blockers (if applicable)
- [ ] Living docs updated (`00-overview`, roadmap, deploy notes as needed)
- [ ] Release notes drafted (if public milestone)
- [ ] Verification commands passed (see project scripts)

---

## Version update

| What | Where |
| ---- | ----- |
| Public app version | `<app-version-file>` |
| Package version | `package.json` (internal — optional) |
| Data / cache schema version | {separate from app version if applicable} |

**Rule:** Distinguish internal deploy slices from public version bumps. Document your convention here.

Bump public version only for milestones you intend to communicate to users.

---

## Staging checks

- [ ] Promoted to `<staging-branch>` and deployed
- [ ] Smoke-test `<staging-domain>`
- [ ] Indexing still blocked on non-production (if policy requires)
- [ ] Critical flows tested on staging-shaped build

---

## Production promotion

**Requires explicit approval.**

- [ ] User confirmed production deploy
- [ ] Fast-forward `<primary-branch>` to tested commit
- [ ] Push `<primary-branch>`
- [ ] Wait for host deploy
- [ ] Smoke-test `<production-domain>`
- [ ] Verify version label if shown

---

## Release notes

- User-facing notes at repo root or GitHub Release — honest scope; no overclaims (accessibility, performance).
- Link to milestone or tag if used.

---

## Post-release

- [ ] Regenerate AI memory if docs changed: `node scripts/generate-ai-project-memory.mjs`
- [ ] Update `00-overview.md` current status
- [ ] **Branch equalisation:** ensure `<development-branch>` is not left in a confusing state vs production (ff-only promotion preferred)
- [ ] Optional: GitHub Release / tag

---

## Rollback

1. Redeploy previous known-good commit on host or revert on `<primary-branch>` (explicit approval).
2. Run production smoke checks.
3. Document incident if user-facing.

---

## Related

- [`04-git-workflow.md`](04-git-workflow.md)
- [`03-deployment.md`](03-deployment.md)
