# How it works

Plain-language guide to runtime behaviour — for future-you and contributors.

---

## User-facing summary

What a visitor or user can do, in one or two paragraphs.

---

## Main flows

### Flow 1 — {e.g. landing → browse → detail}

1. 
2. 
3. 

### Flow 2 — {e.g. search / filter / settings}

1. 
2. 

---

## Important states

| State | What the user sees | What happens technically |
| ----- | ------------------ | ------------------------ |
| Initial load | | |
| Loading | | |
| Ready | | |
| Error / empty | | |

---

## Data and content flow (overview)

```text
{Source data or CMS}
        │
        ▼
{Build step — if any}
        │
        ▼
{Static assets / runtime fetches}
        │
        ▼
{Browser / client}
```

Describe where content is prepared (build time vs request time vs client).

---

## Routing (if applicable)

- Public routes:
- Deep links:
- Fallback behaviour:

---

## Known limitations

Honest list of MVP gaps, platform caveats, or intentional deferrals.

- 
- 

---

## Related

- [`00-overview.md`](00-overview.md)
- [`05-decisions-and-rationale.md`](05-decisions-and-rationale.md)
