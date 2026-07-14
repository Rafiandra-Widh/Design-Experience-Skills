# Mode: foundation — Visual Foundations & Design Tokens

Create token foundations from scratch, or audit/clean up an existing set.

## Intake

- From scratch or cleanup? If cleanup: pull current values first (Figma `get_variable_defs`, or token files in code) and diff against the rules below.
- Target format: Figma variables, CSS custom properties, Tailwind config, JSON (W3C design tokens)? Default: match what the project already uses.
- Brand seed: existing brand color(s)? Light/dark or single theme?

## Token architecture (two layers minimum)

1. **Primitives** — raw values, named by scale, never used directly in designs: `blue-500`, `space-4`, `font-size-lg`.
2. **Semantic** — meaning-named, alias to primitives, this is what designs consume: `color-bg-surface`, `color-text-primary`, `color-border-danger`, `space-card-padding`.

Theming (light/dark) happens by remapping semantic → primitive, never by swapping primitives.

## Scales

- **Color**: per hue, 10–12 steps (50–950). Generate in a perceptual space (OKLCH) so steps feel even. Required semantic roles: bg (default/subtle/surface), text (primary/secondary/disabled/inverse), border (default/strong), interactive (primary/hover/active/disabled), feedback (success/warning/danger/info, each with bg + text + border).
- **Contrast validation is mandatory**: every semantic text-on-bg pair ≥ 4.5:1 (AA), large text & UI borders ≥ 3:1. Show the checked pairs in a table with actual ratios; fix failures before delivering.
- **Typography**: one scale ratio — 1.2 (dense product UI) / 1.25 (default) / 1.333+ (marketing). Define: family, size, line-height (≈1.5 body, ≈1.2 headings), weight, letter-spacing per step. 6–8 steps is enough.
- **Spacing**: base-4 geometric-ish scale: 2, 4, 8, 12, 16, 24, 32, 48, 64, 96. Name by step (`space-1`…`space-10`), not by px.
- **Radius & elevation**: 3–4 radius steps (sm/md/lg/full); 3–4 shadow levels with defined use (card, dropdown, modal).
- **Grid**: columns/margin/gutter per breakpoint (e.g., 12/8/4 columns for desktop/tablet/mobile).

## Output

- The full token set in the chosen format, ready to paste/import.
- If Figma: load `figma-use` + `figma-generate-library` before creating variables; use proper collections (Primitives / Semantic) and modes for theming.
- A short usage guide: which semantic token to use for the 10 most common cases.
- For cleanup: a before→after mapping table (old rogue value → new token) so existing designs can be migrated.
