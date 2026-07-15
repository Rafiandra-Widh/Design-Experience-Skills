# Motion Principles — Knowledge Base

Read before any ux-motion work. Every proposal, audit finding, and prototype default derives from here.

## 1. Purpose taxonomy — motion must earn its place

Every animation must serve exactly one of these purposes. If none fits, the finding/recommendation is "remove it".

| Purpose | What it does | Examples |
|---|---|---|
| **Feedback** | Confirms the user's input registered | Button press state, ripple, toggle flip, form error shake (small!) |
| **Orientation** | Shows where things come from / go to; preserves spatial continuity | Screen transitions, shared-element (Smart Animate), drawer slide, expanding card |
| **Status** | Communicates ongoing system work or change | Skeleton shimmer, progress bar, pull-to-refresh, live-updating number |
| **Delight** | Personality, brand moment | Success confetti, playful empty state, signature onboarding moment |

**Delight budget: maximum ONE signature moment per flow.** More than one competes and reads as noise. Feedback/orientation/status motion should be so quick and expected it's barely noticed.

## 2. Duration scale

| Class | Range | Use for |
|---|---|---|
| Micro | 100–150 ms | State changes: hover, press, toggle, checkbox |
| Small | 150–250 ms | Local element: dropdown, tooltip, chip, small fade |
| Medium | 250–400 ms | Component-level: modal, drawer, card expand, tab content |
| Large | 400–600 ms | Full-screen transitions, complex choreography |

- **> 600 ms needs a written justification** (usually only onboarding/signature moments qualify).
- Distance–duration link: farther travel / bigger element → longer duration, within the class range. Same duration for a 24px icon and a full-screen panel is a finding.
- **Doherty threshold**: interface response < 400 ms keeps users in flow. Feedback motion must never delay the actual response (animate alongside, not before, the result).
- Exits ~20–30% faster than entrances (users are done with the element).

## 3. Easing rules

| Situation | Easing | Figma value | CSS reference |
|---|---|---|---|
| Enter (appear, slide in) | ease-out | `EASE_OUT` | `cubic-bezier(0, 0, 0.2, 1)` |
| Exit (dismiss, slide out) | ease-in | `EASE_IN` | `cubic-bezier(0.4, 0, 1, 1)` |
| Move / morph on screen | ease-in-out | `EASE_IN_AND_OUT` (the alias `EASE_IN_OUT` is INVALID in Figma) | `cubic-bezier(0.4, 0, 0.2, 1)` |
| Physical / draggable / playful | spring | `easingFunctionSpring` or `GENTLE`/`QUICK` presets | motion.dev spring |
| Constant-rate only (spinners, marquee) | linear | — | `linear` |

- `linear` on entrance/exit movement is a finding (feels mechanical).
- **Stagger**: list/grid entrances 20–50 ms apart, cap at ±5 items then bring the rest in together — a 20-item full stagger takes seconds and punishes the user.

## 4. Prototype transitions (Figma)

- **SMART_ANIMATE** — when the two frames share elements: layer names must be IDENTICAL between frames (Figma matches by name+hierarchy; mismatch silently degrades to dissolve). Best for shared-element continuity (orientation purpose). Default 300 ms `EASE_OUT`.
- **DISSOLVE** — unrelated content, quick context switch. Default 200 ms `EASE_OUT`. An entire prototype of only dissolves = monotony finding (no spatial model).
- **PUSH / MOVE_IN / SLIDE_IN** — directional hierarchy: forward = push left (LTR), back = push right; sheet/drawer = MOVE_IN from edge. Direction must be consistent across the whole flow.
- **Instant (no transition)** — tab switches within the same screen level can be instant; not everything needs motion.
- OVERLAY for modals/sheets (keeps the underlying frame), BACK action for returns — don't wire an explicit reverse NAVIGATE when BACK is semantically correct.

## 5. Accessibility & performance

- **Every spec includes `prefers-reduced-motion` behavior**: replacement is usually a fast opacity fade (≤150 ms) or nothing — never just "remove the animation" without stating the replacement.
- **Vestibular triggers = high-severity findings**: large parallax, full-screen zoom/scale > ~1.2×, rotation of large surfaces, auto-playing background motion.
- Web performance: animate **transform and opacity only**; animating layout properties (width/height/top/left/margin) is a 🟡 finding with the transform equivalent as the fix.
- Flashing > 3×/second = 🔴 (WCAG 2.3.1).
- Auto-playing motion longer than 5 s needs pause/stop/hide (WCAG 2.2.2).

## 6. Severity scale (same ladder as ux-design critique / ux-voice)

| Level | Motion examples |
|---|---|
| 🔴 Blocker | Vestibular-trigger motion with no reduced-motion path; flashing > 3×/s; animation that blocks task completion (unskippable, delays input response beyond ~400 ms) |
| 🟡 Major | Feedback missing where users need confirmation; transition > 600 ms on a frequent path; layout-property animation causing jank; direction/spatial model inconsistent across the flow |
| 🟢 Minor | Duration outside scale by < 100 ms; linear easing on a movement; stagger too slow; all-dissolve monotony |
| ⚪ Polish | Easing curve refinement; exit not faster than entrance; micro-timing alignment between paired elements |

## 7. Motion tokens

If the project has a design system, propose values AS TOKENS (e.g. `duration/fast = 150ms`, `easing/enter = cubic-bezier(0,0,0.2,1)`) so dev handoff inherits them. Suggested minimal set: `duration/instant|fast|base|slow` + `easing/enter|exit|move|spring`.
