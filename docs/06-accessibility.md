# Accessibility

Baseline expectations for `<project-name>`. Optimise for real users, not checkbox compliance.

---

## Principles

- Primary flows should be **keyboard reachable** where the UI allows.
- **Screen reader** users should understand structure, state, and errors.
- Do not overclaim WCAG level in public copy without audit evidence.

---

## Semantic HTML

- Use appropriate landmarks (`main`, `nav`, `header`, `footer`) where applicable.
- Prefer native interactive elements (`button`, `a`, `input`) over div-only controls.
- One logical **`h1`** per view where document outline matters.

---

## Keyboard

- All primary actions reachable without a pointer.
- No keyboard traps unless modal focus management is implemented.
- Document known gaps (e.g. third-party canvas widgets) and workarounds.

---

## Focus management

- Visible `:focus-visible` styles on interactive controls.
- When opening dialogs/sheets: move focus in; on close: return focus to trigger where possible.
- Consider focus trap + inert background for true modals.

---

## Colour and contrast

- Text and controls meet contrast needs for chosen theme(s).
- Do not rely on colour alone for state (selected, error, required).

---

## Motion

- Respect `prefers-reduced-motion` for CSS animations.
- Document if motion-heavy UI (maps, carousels) does not yet honour reduced motion.

---

## Testing checklist

Before a public release:

- [ ] Tab through primary flows — no unreachable dead ends
- [ ] Screen reader spot-check on critical paths
- [ ] Zoom to 200% — content still usable
- [ ] Reduced motion preference — no essential information lost
- [ ] Forms/errors announced or visible

Save lengthy findings under [`audits/ux/`](audits/README.md).

---

## Related

- [`.cursor/rules/04-accessibility-performance.mdc`](../.cursor/rules/04-accessibility-performance.mdc)
- [`07-performance.md`](07-performance.md)
