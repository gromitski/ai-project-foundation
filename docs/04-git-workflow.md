# Git workflow

How changes move from local development to staging and production.

For day-to-day agent shorthand (“commit to dev”, “commit to staging”), see `.cursor/rules/02-git-and-release.mdc`.

---

## Branch model

| Branch | Shorthand | Host / URL | Role |
| ------ | --------- | ---------- | ---- |
| `<development-branch>` | **dev** | | Day-to-day development |
| `<staging-branch>` | **staging** | `<staging-domain>` | Pre-production QA (optional) |
| `<primary-branch>` | **main** / **production** | `<production-domain>` | Production |

Delete the staging row if the project uses a two-branch model.

---

## What Stu means by…

| Phrase | Meaning |
| ------ | ------- |
| **commit to dev** | Commit intended changes on `<development-branch>` and `git push origin <development-branch>` only |
| **commit to staging** | Promote tested dev to `<staging-branch>` and push |
| **commit to main** | Promote tested work to `<primary-branch>` and push **only after explicit approval** |

Agents must not push production because dev or staging passed.

---

## Preferred promotion flow

1. Work on `<development-branch>`
2. Commit and push when asked
3. Test development deployment
4. Fast-forward `<staging-branch>` to match tested dev (if used)
5. Test `<staging-domain>`
6. **Only after explicit approval**, fast-forward `<primary-branch>` and push

Use **fast-forward or direct ref push**. Avoid merge commits on promotion branches unless documented otherwise.

```bash
# Example: promote dev → staging
git checkout <development-branch>
git pull --ff-only origin <development-branch>
git push origin <development-branch>:<staging-branch>

# Example: promote to production (explicit approval only)
git push origin <development-branch>:<primary-branch>
```

If `--ff-only` fails, branches diverged — investigate; do not force-push without explicit approval.

---

## Commit rules

- Only commit when explicitly asked.
- Imperative commit subject; body explains why when useful.
- Review `git status` and staged diff before commit.
- Never commit secrets or raw dumps (see `05-repository-hygiene.mdc`).

---

## Release branch handling

If the project uses release branches or tags:

- Document naming here
- Document when tags are created vs footer version bumps

---

## Post-change verification

After push, smoke-test the environment documented in [`03-deployment.md`](03-deployment.md).

---

## Related

- [`09-release-procedure.md`](09-release-procedure.md)
- [`03-deployment.md`](03-deployment.md)
