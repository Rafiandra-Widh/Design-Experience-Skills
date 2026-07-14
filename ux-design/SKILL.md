---
name: ux-design
description: >
  UI/UX design workflows for any project or design system. Use when the user wants to
  design a screen, page, app, feature, user flow, or wireframe ("desain", "rancang",
  "bikin screen/halaman"); critique or review a design's visual hierarchy, spacing,
  consistency, or usability ("review desain", "kritik", "audit tampilan"); explore
  multiple visual concepts or directions ("eksplorasi", "moodboard", "alternatif desain");
  or build visual foundations — design tokens, type scale, spacing scale, color palette,
  grid ("token", "fondasi visual"). Modes: flow, critique, explore, foundation.
  Not for polishing existing code-based UI (use impeccable), implementing a Figma design
  as code (use figma-design-to-code), or backend/non-UI tasks.
user-invocable: true
argument-hint: "[flow|critique|explore|foundation]"
---

# ux-design

Structured design workflows: from brief to hi-fi, design critique, concept exploration, and visual foundations.

## Routing

Read the mode's reference file BEFORE doing any design work. If the user passed a mode argument, use it. Otherwise infer from intent; if genuinely ambiguous, ask.

| Mode | When | Reference |
|---|---|---|
| `flow` | Design something new: screen, page, feature, user flow, wireframe → hi-fi | `reference/flow.md` |
| `critique` | Review/critique an existing design (Figma frame, screenshot, live page) | `reference/critique.md` |
| `explore` | Generate multiple distinct visual directions for one brief | `reference/explore.md` |
| `foundation` | Create or clean up design tokens: type, spacing, color, grid | `reference/foundation.md` |

## Cross-mode rules

1. **Discovery before creation.** Before designing anything, find the project's active design system: in Figma use `search_design_system` / `get_libraries` / `get_variable_defs`; in code grep for token files (tailwind config, CSS variables, theme files). Reuse existing components and tokens — never rebuild what already exists from primitives.
2. **Figma writes require the figma skills.** If output goes INTO Figma, load `figma-use` (and `figma-generate-design` for full pages) before any `use_figma` call. For a new file, load `figma-create-new-file` first.
3. **Defer, don't duplicate.** Polishing code-based UI → hand off to the `impeccable` skill. Charts/data viz → load `dataviz` first. Style/palette/font-pairing lookups → `ui-ux-pro-max` is available.
4. **Ask before assuming.** Every mode starts with a short intake (see each reference). Never invent target users, brand constraints, or platform.
5. **Respond in the user's language.** Deliverables and explanations follow the language the user writes in (Indonesian ↔ English).
6. **Accessibility is not optional.** Any color/type decision must pass WCAG AA contrast; any interactive element ≥ 44×44 (mobile) / 24×24 (desktop) target size.
