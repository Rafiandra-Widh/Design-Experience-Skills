# Mode: annotate — Redlines & Annotations Inside Figma

Write measurement redlines, interaction notes, edge-case markers, and audit findings back into the Figma file, next to the design.

## Prerequisites

1. **Load the `figma-use` skill first** — mandatory before any `use_figma` call.
2. Gather real values exactly as in spec mode (`get_design_context`, `get_variable_defs`) — annotations carry token names and true values, never eyeballed numbers.
3. Ask which frames to annotate and what the dev team most often asks about (prioritize those notes).
4. **Confirm before writing** — this mode modifies the user's file. Propose the plan (which frames, which output form) and wait for a yes.

## Output forms (offer both; user picks)

1. **Native Dev Mode annotations** — attach via the Plugin API `node.annotations` property (array of `{label, labelMarkdown, properties}`) directly on the affected layers. Cleanest for developers inspecting in Dev Mode; invisible in normal design view. Verify the property is writable in the file context first (it can be unavailable on some plans/file types) — if it throws, fall back to form 2 and say so.
   - **Pin node properties** with the `properties` field: `[{type: 'fills'}, {type: 'cornerRadius'}, ...]` — Figma renders the live values in the annotation, so devs see the spec without clicking through. Valid `type` values (verify against `plugin-api-standalone.d.ts` if unsure): `width height maxWidth minWidth maxHeight minHeight fills strokes effects strokeWeight cornerRadius textStyleId textAlignHorizontal fontFamily fontStyle fontSize fontWeight lineHeight letterSpacing itemSpacing padding layoutMode alignItems opacity mainComponent` (+ grid variants).
   - Property picks by node role: **container/card/button** → `fills strokes cornerRadius width height`; **text** → `fontFamily fontSize fontWeight lineHeight fills`; **auto-layout frame** → add `itemSpacing padding layoutMode`; **instance** → add `mainComponent`.
   - Assigning `node.annotations` REPLACES the whole array — read the existing annotations first and include them (or their merged content) in the new array, never silently overwrite. Multiple annotations per node are allowed and SHOULD be used for the UX/Development category split (see Annotation categories below).
   - Component candidates deserve this treatment by default: annotate each repeated-but-uncomponentized element with a suggested component name, its repeat count/node IDs, suggested props, and pinned visual properties.
2. **Visual marker section** — annotation graphics beside the frame (see Placement rules below). Visible to everyone without Dev Mode; use for audit findings and designer-facing notes.

**Figma comments are NOT possible from this toolchain.** Comments are REST-API-only (needs a personal access token); the Figma MCP / Plugin API cannot create them. If the user wants comment-style notifications for teammates, say so and offer the REST route as a separate, out-of-MCP step — never silently substitute.

## Annotation categories (UX vs Development)

Split every logic note into TWO annotations with Figma's native categories, so Dev Mode groups them:

1. Ensure categories exist once per file: `figma.annotations.getAnnotationCategoriesAsync()` → reuse by label; else `addAnnotationCategoryAsync({label: "UX", color: "violet"})` and `({label: "Development", color: "blue"})`.
2. Attach both to the node: `node.annotations = [{labelMarkdown: uxNote, categoryId: uxCat.id}, {labelMarkdown: devNote, properties, categoryId: devCat.id}]` — pinned `properties` ride on the Development annotation.
3. If a node type rejects multiple annotations, put the UX note on the container and the Development note on its functional child — never merge them back into one wall of text.

## Plain language (wajib)

Annotations are read by people in a hurry, standing in a meeting or mid-implementation. Rules:
- Short sentences (± ≤ 12 words). Everyday words. One idea per sentence.
- No research jargon in UX notes: never "Insight #4", "token pair", "kontras 4.5:1" — say what it means: "teks harus tetap terbaca di atas video terang".
- Technical terms, formulas, formats, token names live ONLY in the Development annotation.
- Test: could a new teammate act on it without asking questions?

```
❌ Sulit:  "Durasi = format N′ total dan HARUS durasi jujur (aktif + pasif — lihat Insight 4);
           badge durasi memakai accent (satu-satunya badge beraksen)."
✅ UX:     "Tampilkan lama masak yang jujur. Waktu menunggu ikut dihitung.
           Kalau tidak, pengguna merasa dibohongi."
✅ Dev:    "Format: `N′ total`. durasi = aktif + pasif. Badge durasi pakai token accent/default;
           badge lain pakai scrim."
```

Detection table — when you see the pattern on the left, document the rule on the right:

| Pattern in the design | Rule to document |
|---|---|
| Truncated list + "see all" link | Item limit, sort order, overflow destination, empty state |
| Date/time text | Explicit format string (`EEEE, d MMMM yyyy`, `HH:MM:SS`) + locale; computed fields (day name) must never be hardcoded |
| Currency/number | Locale, thousands/decimal separators, decimal count, rounding; totals that must reconcile (Σ parts = whole) |
| Progress bar / percentage | Formula (`spent/limit`), color thresholds, cap behavior at >100%, what the label shows when capped |
| Chart | Data source, period, aggregation granularity, which filters/chips control it |
| Stepper / tabs / filter chips | What state they control, scope of effect, bounds (e.g., can't step past current month), default value |
| Status color / badge | Complete state→color mapping, incl. states not shown in this frame |
| ± signed values | Sign/color rules per transaction type, incl. ambiguous cases (transfers) |

Honesty rules:
- A rule read directly from the design → state it plainly. A rule you inferred → prefix `⚠️ asumsi:` and say what to confirm. A rule that isn't decidable from the design → `⚠️ keputusan terbuka:` — never invent thresholds, limits, or formats silently.
- Rules that change implementation (thresholds, limits, formats, routes) deserve a short user interview BEFORE annotating when the user is available; batch the questions, don't drip them.
- Inconsistencies found while deriving rules (e.g., a date whose weekday is wrong, totals that don't reconcile) go INTO the annotation as bugs — devs copy design values verbatim.
- Write labels in the user's language; keep format strings/pseudocode verbatim.

## Feeding from other modes

When the input is `readiness` or critique findings (rather than a spec), map each finding to: severity emoji (🔴/🟡) + short label + target node ID from the audit. One marker per finding, legend card carries the full text. Findings without a concrete node (e.g., "states not designed") go on the legend card only, marked "frame-level".

## Placement rules (never damage the design)

- All annotation nodes live in a dedicated top-level SECTION named `📐 Annotations — [screen name]` placed beside the frame (find a clear spot from page metadata — never at 0,0, never overlapping existing nodes) — NEVER inside the original design frame, never reparenting or moving design nodes.
- Numbered markers that must point at specific spots go in a non-auto-layout overlay frame sized to the target frame, positioned exactly over a COPY of it or beside it with leader lines — the original stays untouched.
- Lock annotation containers after creating them (`locked = true`) so designers don't move them accidentally.
- Build incrementally per figma-use rules: ≤10 operations per call, `screenshot()` to verify placement after each frame, return all created node IDs so cleanup/undo is possible.
- Keep a consistent visual language so annotations are obviously not-design:
  - Spacing/size redlines: 1px lines + label chips
  - Interaction notes: numbered marker dots + a legend list beside the frame
  - Edge-case flags: ⚠️ chips pointing at the element
  - One accent color for all annotation graphics (pick one NOT used by the design's palette — check variables first), small mono/label type.

## What to annotate

- **Measurements**: spacing between regions, key dimensions, min/max widths — token name first (`space-6 · 24px`). Skip what auto-layout already communicates to a dev inspecting the file; annotate what inspection does NOT reveal.
- **Interaction notes**: numbered markers on interactive elements → legend describing trigger, behavior, destination, and transition.
- **Conditional/edge cases**: what appears when data is empty/long/error; role-based visibility; loading behavior.
- **Token callouts**: places where the right token is ambiguous or recently changed.

## Workflow

1. Propose the annotation plan (which frames, which notes) — confirm before writing.
2. Create the annotation section; build incrementally (one frame at a time), screenshot to verify placement, then continue.
3. Report back with a link/screenshot of the annotated result and a list of anything you flagged as unclear for the designer to resolve.
