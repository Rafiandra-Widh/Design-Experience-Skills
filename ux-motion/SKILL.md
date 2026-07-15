---
name: ux-motion
description: >
  Figma prototyping and motion/interaction design for better UX. Use when the user
  wants to wire a clickable prototype in Figma ("prototype", "sambungkan frame",
  "bikin bisa diklik", "smart animate"); check/audit existing motion or micro-interactions
  in a Figma file, live web page, or screen recording ("cek motion", "audit animasi",
  "transisinya kok aneh"); or get motion-interaction proposals for a static design
  ("usulkan motion", "animasi apa yang cocok", "biar terasa hidup") delivered as a
  motion spec, authored directly in Figma (keyframes/animation styles/prototype), and/or
  an interactive HTML demo. Modes: prototype, audit, propose. Not for implementing
  Figma motion as production code (use figma-implement-motion) or critiquing static
  visuals (use ux-design critique).
user-invocable: true
argument-hint: "[prototype|audit|propose] <URL/konteks>"
---

# ux-motion

Prototype wiring, motion audits, and motion proposals — grounded in motion principles, with honest verification.

## Routing

Read `reference/motion-principles.md` BEFORE any mode work. If the user passed a mode argument, use it; otherwise infer (wire/connect → prototype, check/review → audit, suggest/add → propose); ask only if genuinely ambiguous.

| Mode | When | Reference |
|---|---|---|
| `prototype` | Wire click-through flows between Figma frames (navigate/overlay/back, Smart Animate) | `reference/prototype.md` |
| `audit` | Check existing motion: Figma prototype, live web page, or video/GIF recording | `reference/audit.md` |
| `propose` | Static design → motion proposals (spec + Figma authoring + HTML demo) | `reference/propose.md` |

## Cross-mode rules

1. **Figma writes require the figma skills.** Load `figma-use` before ANY `use_figma` call; additionally load `figma-use-motion` before authoring keyframes/animation styles/timelines.
2. **Probe before authoring motion in Figma.** Keyframe/animation-style APIs are gated by an account feature flag. Once per session, before the first motion write, run a try/catch probe of `figma.motion.figmaAnimationStyles()` via `use_figma`. If it throws "not a supported API": the flag is absent — tell the user, do NOT retry, and fall back to spec + HTML demo + prototype transitions (reactions are NOT gated by this flag).
3. **Verify honestly.** Screenshots show only the resting state — never claim motion "looks right" from a screenshot. State explicitly what was verified by readback (tracks, reactions) versus what the user must check by pressing Play. Offer `export_video` only when ffmpeg is available and the user accepts the wait.
4. **Defer, don't duplicate.** Motion → production code: hand off to `figma-implement-motion`. Static visual critique: `ux-design critique`. Dev handoff of the spec: `ux-handoff`.
5. **Restraint is the default.** Every proposed animation names its purpose (feedback / orientation / status / delight); delight is capped at ONE signature moment per flow; every spec row includes `prefers-reduced-motion` behavior. "Animate everything" is never the answer.
6. **Concrete values only.** Duration in ms + easing (named curve or cubic-bezier/spring params) + animated properties — never "add a smooth animation".
7. **Respond in the user's language**; deliverables follow the user's language, terms stay English.
