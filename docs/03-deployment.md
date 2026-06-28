# Deployment

How builds reach `<hosting-provider>` and what to verify after deploy.

---

## Hosting

| Item | Value |
| ---- | ----- |
| **Provider** | `<hosting-provider>` |
| **Production URL** | `<production-domain>` |
| **Staging URL** | `<staging-domain>` |
| **CI** | {GitHub Actions / Cloudflare / manual} |

---

## Environments

| Environment | Branch | Build command | Base path | Indexing |
| ----------- | ------ | ------------- | --------- | -------- |
| Development | `<development-branch>` | | | blocked |
| Staging | `<staging-branch>` | | | blocked |
| Production | `<primary-branch>` | | `/` | allowed |

Adjust columns for your project.

---

## Build commands

```bash
# Production-shaped build
npm run build

# Preview locally
npm run preview
```

Document separate build targets here if the project builds differently per host (e.g. GitHub Pages base path vs root).

---

## Environment variables

| Name | Environments | Purpose |
| ---- | ------------ | ------- |
| | Production | |
| | Staging | |
| | Development CI | |

Never commit real values. Document where they are set (host dashboard, workflow secrets).

---

## Deployment checks

After each deploy to staging or production:

- [ ] Site loads over HTTPS
- [ ] Assets resolve (no 404 on JS/CSS)
- [ ] Correct version or build label visible (if applicable)
- [ ] Staging still blocked from indexing (if policy requires)
- [ ] Production canonical URLs correct
- [ ] Critical user flow smoke-tested

---

## Rollback

1. Identify last known-good commit on `<primary-branch>`.
2. Revert or redeploy that commit via host UI or Git promotion.
3. Verify production checks above.
4. Record incident in decision log or audit if non-trivial.

Document host-specific rollback steps (Cloudflare rollback, Pages previous deployment, etc.).

---

## Related

- [`04-git-workflow.md`](04-git-workflow.md)
- [`09-release-procedure.md`](09-release-procedure.md)
