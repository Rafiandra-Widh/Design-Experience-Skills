# Mode: critique — Design Review

Structured critique of an existing design: Figma frame, screenshot, or live page.

## Input handling

- **Figma URL** → `get_screenshot` for the visual + `get_design_context` / `get_variable_defs` to check real token usage. Never judge token consistency from pixels alone.
- **Screenshot/image** → visual-only review; state explicitly that token/spec-level checks were not possible.
- **Live page** → use Chrome tools (load `claude-in-chrome` skill) to view at desktop AND mobile widths.

Ask for the design's intent first if not obvious: who is it for, what is the primary action, any known constraints. Critique against intent, not personal taste.

## Review dimensions (go through all six)

1. **Visual hierarchy** — Is the primary action/content unmistakable in a 5-second glance? Does size/weight/color/position match importance? One primary CTA per view.
2. **Layout & spacing** — Consistent spacing scale (multiples of 4/8)? Aligned to a grid? Related items grouped, unrelated items separated (proximity)? Adequate breathing room vs cramped clusters?
3. **Consistency & tokens** — Same element styled the same way everywhere? Values from the design system's tokens, or rogue hex/px? Components from the library or hand-rebuilt?
4. **Typography & content** — Clear type scale (not 7 near-identical sizes)? Line length 45–75ch? Labels action-oriented and unambiguous? Realistic content?
5. **Accessibility** — Text contrast ≥ 4.5:1 (3:1 for large text), non-text contrast ≥ 3:1, touch targets ≥ 44px, color never the only signal, visible focus states.
6. **UX heuristics** (Nielsen) — visibility of status, match with real world, user control/undo, error prevention, recognition over recall, flexibility, minimalist design, good error messages, help.
7. **AI-slop test** (see `anti-slop.md`) — does any hard ban appear (side-stripe, gradient text, identical card grids, eyebrow/numbered scaffolding, cream default…)? Could the theme+palette be guessed from the category alone? Is there a nameable signature element, or is it template-average? If a taste profile exists, does the design contradict its hard-nos?

## Output format

Ranked findings, most severe first:

```
## Temuan

### 🔴 Blocker (harus diperbaiki)
1. [Lokasi/elemen] — masalah. → Rekomendasi konkret (nilai/token spesifik, bukan "perbaiki spacing").

### 🟡 Major (sangat disarankan)
...

### 🟢 Minor / polish
...

## Yang sudah bagus
- (2–3 hal — kritik yang kredibel mengakui kekuatan desain)
```

Every finding must name its location and give a concrete fix. If ≤ 3 findings total, say the design is solid — do not pad with invented issues.
