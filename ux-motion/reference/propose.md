# Mode: propose — Motion Proposals for a Static Design

From a static design (Figma URL, screenshot, or described flow) to concrete motion: spec always, Figma authoring when the flag allows, HTML demo on offer. All three deliverables share ONE source of values — the spec table.

Prerequisites: `motion-principles.md` loaded. For Figma authoring: `figma-use` + `figma-use-motion` loaded, probe passed (SKILL.md rule 2).

## 1. Intake (short)

Product context + platform (web/mobile — affects durations & patterns), whether a design system with motion tokens exists (reuse them; propose tokens if absent — principles §7), and which flows/screens are in scope.

## 2. Opportunity scan — restraint first

Walk the design once per purpose category (§1), collecting CANDIDATES:

- **Feedback**: every tappable/submittable thing — which ones lack confirmation?
- **Orientation**: screen-to-screen transitions, expanding cards, drawers — where does spatial continuity help comprehension?
- **Status**: loading, async saves, live data — where does the user wait blind?
- **Delight**: pick AT MOST ONE signature-moment candidate per flow, tied to the product's world (not generic confetti).

Then CUT: anything without a clear purpose, anything duplicating another item's job, staggers beyond 5 items. The final list is typically 4–8 items, not 20. State what you deliberately did NOT animate and why — restraint is part of the proposal.

## 3. Deliverable 1 — Motion spec (always)

`motion-spec.md` in the project folder:

```
| Elemen | Trigger | Properti | Durasi | Easing | Purpose — alasan | prefers-reduced-motion |
|---|---|---|---|---|---|---|
| Kartu resep → detail | tap | position+size (shared element) | 350ms | ease-out | Orientation — kartu adalah sumber layar detail | cross-fade 120ms |
```

Values follow the duration scale (§2) and easing rules (§3). If tokens exist/were proposed, reference token names alongside raw values.

## 4. Deliverable 2 — Author in Figma (flag-gated)

Only after the probe passes (else skip with a one-line note and rely on deliverables 1+3):

- Element-level motion (entrances, micro-interactions, status) → manual keyframes / first-party animation styles per `figma-use-motion` patterns; timeline durations in SECONDS; `EASE_IN_AND_OUT` spelling; never animate a top-level page child — animate descendants.
- Screen-to-screen items from the spec → prototype transitions via the `prototype.md` pattern (Smart Animate pre-check included).
- Verify by readback (`manualKeyframeTracks` / `animationStyles` / `reactions`); offer `export_video` for the one or two frames where feel matters most, if ffmpeg is available and the user accepts ~minutes of wait.

## 5. Deliverable 3 — Interactive HTML demo (offer it)

One self-contained HTML file in the project folder (share as artifact on request):

- One section per spec row: the element mocked minimally, a trigger button ("Play" / actual hover/click), the values displayed next to it (duration/easing/props).
- Implementation rules: animate transform+opacity only; easing via the spec's cubic-bezier/spring approximation; include a working `prefers-reduced-motion` variant AND a toggle to preview it; respect the user's design tokens/taste profile for the demo's own styling.
- The demo is a communication tool for feel-checking and stakeholder buy-in — label it as such, not production code (production path: `figma-implement-motion`).

## 6. Close

Recap: N proposals by purpose, the one signature moment, what was left unanimated. Next steps: wire it (`prototype`), implement it (`figma-implement-motion` via dev), or hand off (`ux-handoff spec` referencing motion-spec.md).
