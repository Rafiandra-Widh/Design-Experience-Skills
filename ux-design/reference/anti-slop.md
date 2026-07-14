# Anti-Slop — Rules for Human, Organic Design Output

Read this BEFORE generating any visual (explore boards, hi-fi, foundations). Goal: no one should be able to look at the output and say "AI made that" without doubt. Adapted for Figma work from proven code-side rules (impeccable).

## Taste profile (personal layer)

If `~/.claude/design-taste.md` exists, read it first — it holds the designer's personal preferences (loved references + why, typography leanings, density, color attitudes, hard-nos). It is the strongest anti-slop tool because it replaces "statistically average design" with THIS designer's taste.
- Every explore direction must state its relationship to the profile: *mengikuti* (follows it) or *sengaja menantang* (deliberately challenges it, with a reason).
- Hi-fi decisions default to the profile; the user's explicit brief always wins over the profile.
- If the file doesn't exist, offer once to build it (screenshots, moodboard, favorite products) — don't nag.

## Hard bans (match-and-refuse — rewrite the element, don't soften it)

1. **Side-stripe accent** — colored left/right border >1px on cards, callouts, list items. Use full border, bg tint, leading icon, or nothing.
2. **Gradient text fills.** One solid color; emphasis via weight/size.
3. **Glassmorphism / blur cards as default.** Rare and purposeful, or absent.
4. **Hero-metric template** — big number + small label + delta chip grid as the reflexive dashboard opener.
5. **Identical card grids** — same-size icon+heading+text cards repeated. Vary size, merge, or use a different structure.
6. **Tiny uppercase tracked eyebrow above every section**, and its sibling **01/02/03 numbered scaffolding**. One deliberate instance = voice; on every section = AI grammar. Numbers only when the content truly is a sequence.
7. **Cream/sand/beige body background as the "warm" default** (incl. token names like paper/linen/ivory). Warmth belongs to accent, type, and imagery — pick a chroma-0 off-white, a brand-hued tint, or a committed saturated surface instead.
8. **Near-twin font pairs** (two geometric sans, two humanist sans). Pair across a contrast axis (serif+sans, geometric+humanist) or use one family in weights.
9. **Washed-out gray text on tinted/colored backgrounds.** Use a darker shade of the bg's own hue or verified-contrast ink.

## Category-reflex test (run at two altitudes)

- **Tingkat 1:** could someone guess the theme + palette from the product category alone? (finance → navy/teal + green deltas; food → warm cream + terracotta; kids → pastel rainbow) → rework until the answer isn't obvious.
- **Tingkat 2:** could someone guess the aesthetic family from category + anti-reference? ("recipe app that's not warm-cream → dark TikTok clone" is itself the second reflex) → rework again. Two rounds of "not the obvious answer" minimum.

## The physical-scene sentence (before choosing dark/light and color strategy)

Write one sentence: **who** uses this, **where**, under **what light**, in **what mood**. If it doesn't force the theme/palette decision, add detail until it does. (Real example from this skill's history: "Mode Masak dipakai di dapur terang, layar dilihat dari jauh, tangan kotor" → forced Light mode + big type + huge targets.)

## Signature-element requirement

Every hi-fi screen set must contain **at least one design decision that no template would produce** — a distinctive structural move, a meaningful typographic treatment, a spacing rhythm that carries hierarchy, a shape language tied to the product's world. When presenting the hi-fi, NAME the signature element explicitly. If you can't name one, the design isn't done.

## Texture of the real

- Real content everywhere: plausible names, honest numbers that reconcile, correct language — never lorem, never `1,234`-style filler that contradicts itself.
- Vary spacing rhythm deliberately (grouping carries meaning); uniform 16px-everywhere reads as generated.
- Details humans add: optical alignment over mathematical, one intentionally quiet area per screen, asymmetry where content justifies it.
- Contrast is still law: bold moves must keep AA (compute, don't eyeball) — anti-slop never excuses inaccessibility.
