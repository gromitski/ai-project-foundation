# Performance

How to approach performance work on `<project-name>`. Measure first; user experience over audit scores.

---

## Priority order

1. User-perceived responsiveness
2. Accessibility (slow or broken UX is a performance problem for many users)
3. Network payload size
4. Bundle size
5. Lighthouse or similar audit scores

---

## Measurement approach

Before optimising, identify:

| Question | Answer |
| -------- | ------ |
| **Resource** | Exact file, request, or chunk |
| **Size** | Raw and compressed |
| **When loaded** | First paint / interaction / lazy |
| **User benefit** | What feels faster or more reliable |

Use Network tab, build output, and host metrics — not guesses.

---

## First useful interaction

Optimise for when the user can **start their task**, not only when everything has finished loading.

Document loading states and recovery paths.

---

## Payload awareness

Maintain a table of heavy resources (customise per project):

| Resource | ~size | When loaded |
| -------- | ----- | ----------- |
| Main app bundle | | Startup |
| Primary data file | | Startup / lazy |
| Fonts / images | | |

Update after pipeline or routing changes.

---

## Caching

Document:

- CDN / host cache behaviour
- Service worker policy (if any)
- Cache-busting strategy for generated data

---

## Trade-off logging

When accepting a trade-off, record:

- What was optimised
- What was deferred
- Why the trade-off is acceptable

Use audits or decision log for non-obvious choices.

---

## Related

- [`.cursor/rules/04-accessibility-performance.mdc`](../.cursor/rules/04-accessibility-performance.mdc)
- [`06-accessibility.md`](06-accessibility.md)
