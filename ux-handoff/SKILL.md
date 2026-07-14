---
name: ux-handoff
description: >
  Design-to-developer handoff workflows for any project. Use when the user wants to
  hand a design to developers ("handoff", "serah terima"); generate a developer spec
  from a Figma frame — sizes, spacing, tokens, states, behavior ("spek", "spesifikasi
  untuk dev"); write design-system component documentation — anatomy, variants, props,
  do/don't ("dokumentasi komponen"); add annotations or redlines back into a Figma file
  ("anotasi", "redline", "catatan interaksi"); or audit a frame's readiness before
  handoff — naming, auto-layout, token coverage, states ("cek kesiapan", "audit frame").
  Modes: spec, component-doc, annotate, readiness.
  Not for implementing the design as code (use figma-design-to-code) or reviewing
  visual quality (use ux-design critique).
user-invocable: true
argument-hint: "[spec|component-doc|annotate|readiness]"
---

# ux-handoff

Everything between "the design is done" and "developers build it": specs, component docs, redlines, and readiness audits.

## Routing

Read the mode's reference file BEFORE producing anything. If the user passed a mode argument, use it; otherwise infer, and ask if ambiguous.

| Mode | When | Reference |
|---|---|---|
| `spec` | Figma frame/screen → structured developer spec | `reference/spec.md` |
| `component-doc` | Document a design-system component (anatomy, variants, usage rules) | `reference/component-doc.md` |
| `annotate` | Write redlines/annotations back INTO the Figma file | `reference/annotate.md` |
| `readiness` | Audit a frame before handoff: naming, auto-layout, tokens, states | `reference/readiness.md` |

## Cross-mode rules

1. **Real values only.** Every number and color comes from the source of truth: `get_design_context` for structure/dimensions, `get_variable_defs` for tokens, `get_metadata` for node inventory. NEVER estimate values from a screenshot — if data can't be fetched, say which values are missing rather than guessing.
2. **Tokens over raw values.** When a value is bound to a variable/style, the deliverable names the token (`color-bg-surface`, `space-4`), with the resolved value in parentheses. Raw hex/px appears alone only when no token exists — and that itself is flagged as a finding.
3. **Figma writes require `figma-use`.** `annotate` mode (and any other write into Figma) must load the `figma-use` skill before calling `use_figma`.
4. **States are part of the design.** A spec or doc without hover/focus/disabled/error/empty/loading states is incomplete — list missing states explicitly instead of silently covering only the default.
5. **Audience check.** Ask what the receiving team uses (web/mobile, framework, token pipeline) so units and naming match their world; note Code Connect mappings when they exist (`get_code_connect_map`).
6. **Respond in the user's language** for narrative; keep token names, property names, and code snippets verbatim.
