# Mode: explore — Concept Exploration

Generate genuinely distinct design directions for one brief — different souls, not one design with three coats of paint.

## Intake

- What is being designed (product/screen), for whom, and what feeling should it evoke?
- Brand constraints: existing logo, mandatory colors, tone of voice?
- How many directions? Default **3**.
- Output medium: Figma frames, HTML artifact (side-by-side), or written concept board?

## Anti-slop gate (before presenting directions)

- Read `anti-slop.md` + taste profile (`~/.claude/design-taste.md` if present) BEFORE generating directions.
- Every direction must pass the **category-reflex test** (both altitudes) — state the result per direction ("bukan jawaban refleks kategori karena…").
- If a taste profile exists, each direction states its relationship: *mengikuti profil* or *sengaja menantang profil* + alasan. At least one direction should follow, at least one should challenge.

## Rules for distinctness

Each direction must differ on at least 3 of these axes — otherwise it's a variation, not a direction:
- **Layout structure** (e.g., dense dashboard vs editorial single-column vs card bento)
- **Type personality** (geometric sans vs humanist vs serif display; scale contrast high vs low)
- **Color strategy** (monochrome + one accent vs full palette vs dark-first)
- **Shape language** (sharp/technical vs rounded/friendly vs organic)
- **Density & motion attitude** (calm and sparse vs energetic and layered)

Use `ui-ux-pro-max` for palette/font-pairing/style vocabulary when helpful.

## Per-direction spec

For each direction deliver:

1. **Name** — evocative, 2–3 words (e.g., "Civic Clarity", "Night Market").
2. **One-line soul** — the feeling it delivers and who it's for.
3. **Palette** — 4–6 colors with hex + role (bg, surface, text, primary, accent); AA-checked pairs.
4. **Typography** — heading + body font (available on Google Fonts unless brand dictates), scale ratio.
5. **Layout sketch** — the signature structural move, shown not just described.
6. **Shape & detail language** — radius, borders, shadows, iconography style.
7. **Trade-offs** — where this direction is strong, where it is risky (honestly: dev cost, a11y tension, brand fit).

## Presentation

- Side-by-side comparison so directions can be judged against each other.
- End with a comparison table (axis × direction) and **a recommendation with reasoning** — do not leave the user with an unweighted menu.
- Offer to develop the chosen direction into a full screen via `flow` mode.
