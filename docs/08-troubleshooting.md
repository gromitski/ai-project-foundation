# Troubleshooting

Common problems and smallest-safe fixes — mainly for future-you during tired debugging.

---

## First rule

Do not panic-reinstall everything.

1. Read the actual error.
2. Identify which layer failed (tooling, app, data, host, cache).
3. Fix the **smallest** thing that could explain the symptom.

---

## Debug by layer

| Layer | Checks |
| ----- | ------ |
| **Local tooling** | Node version, dependencies installed, env vars |
| **Application** | Console errors, route, component state |
| **Build** | Build command output, missing assets in `dist/` |
| **Data / content** | Generated files present, schema version, cache buster |
| **Deployment** | Correct branch, env vars on host, CI success |
| **CDN / cache** | Hard refresh, incognito, purge if applicable |

---

## Local development

| Symptom | Likely cause | Try |
| ------- | -------------- | --- |
| Won’t start | Port / Node / deps | See [`02-local-development.md`](02-local-development.md) |
| Blank page | JS error / wrong base path | Console, network tab |
| Old behaviour | Stale build | Clean output dir, rebuild |

---

## Deployment

| Symptom | Likely cause | Try |
| ------- | -------------- | --- |
| 404 on assets | Wrong base path or deploy root | Compare dev vs prod build target |
| Wrong site version | Old deployment active | Host rollback or redeploy |
| Env behaviour wrong | Missing host env var | Check dashboard vs docs |

---

## Caching

| Symptom | Likely cause | Try |
| ------- | -------------- | --- |
| Old JS/CSS after deploy | CDN or service worker | Hard refresh; SW update policy |
| Stale data | Cached JSON | Cache-bust query or version bump |

---

## Data / content

| Symptom | Likely cause | Try |
| ------- | -------------- | --- |
| Missing records | Build not run | Regenerate data pipeline |
| Wrong shape | Schema change | Rebuild; check types |

---

## When to create an investigation report

If the issue is:

- multi-system (host + build + data)
- recurring without clear cause
- risky to fix without evidence

→ Write an audit under [`audits/`](audits/README.md) **before** large code changes.

---

## Related

- [`02-local-development.md`](02-local-development.md)
- [`03-deployment.md`](03-deployment.md)
