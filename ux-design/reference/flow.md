# Mode: flow — Brief → User Flow → Wireframe → Hi-Fi

A staged design workflow with a user checkpoint after every stage. Never jump straight to hi-fi.

## Stage 0 — Intake (always first)

Ask only what's missing; keep it to one round of questions:
- **Who** is the target user, and what task are they trying to complete?
- **Platform**: desktop web / mobile web / native app / responsive? Breakpoints?
- **Context**: new product, or a screen inside an existing product? Which design system?
- **Constraints**: brand rules, tech stack, deadline scope (MVP vs polished), content that already exists.
- **Success**: what does "done" look like for this screen/flow?

Then run design-system discovery (see SKILL.md rule 1) and report what you found before proceeding.

## Stage 1 — User flow

- Map the happy path plus the 2–3 most important edge paths (error, empty, unauthorized).
- Output as a diagram in TWO places: (a) mermaid flowchart in the flow doc (archive), AND (b) a **user-flow board drawn in the project's Figma page** — small labeled frames as nodes, `figma.createLine()` with `strokeCap = 'ARROW_LINES'` as arrows, small label chips on each arrow naming the trigger. Load `figma-use` first. (FigJam `generate_diagram` is an alternative only when the user prefers a separate FigJam file — Connector nodes do NOT work in design files.)
- Each node = one screen or decision, labeled with the user's intent, not the UI element.
- **Checkpoint**: confirm the flow with the user before wireframing.

## Stage 2 — Lo-fi wireframe

- Grayscale only, real content hierarchy, no visual styling decisions yet.
- Every screen in the approved flow gets a wireframe, including empty/error/loading states.
- Annotate each region with its priority (primary action, secondary, supporting info).
- In Figma: simple frames with auto-layout, gray fills, system font. In artifact: HTML grayscale mockup.
- **Checkpoint**: confirm layout and content priority.

## Stage 3 — Hi-fi

- Apply the project's design system: real components (imported via key, instance + override), tokens for every color/spacing/type value.
- Cover all states designed in Stage 2, plus interaction states (hover, focus, pressed, disabled).
- Realistic content — real-sounding names, plausible numbers, correct language. Never lorem ipsum.
- Verify against SKILL.md rule 6 (contrast, target sizes) before presenting.

## Stage 4 — Flow connectors on canvas

After wireframes AND after hi-fi, draw the flow BETWEEN the actual screen frames:
- Arrows: `figma.createLine()`, `strokeCap = 'ARROW_LINES'`, 2px, one distinct non-palette color (same accent as annotations), routed through the gutters between frames.
- Each arrow gets a small label chip naming the trigger in plain words ("tap Lihat Resep", "selesai masak").
- ALL connector nodes live inside one dedicated locked frame `🔀 Flow — [nama]` (transparent, `clipsContent = false`, spanning the screen row) — never inside screen frames, never reparenting screens.
- Update connectors when screens move or new states are added; they are part of the deliverable, not decoration.

## Output conventions

- Name Figma frames by flow position: `01 Login`, `02 Login / Error`, etc.
- End with a short summary: decisions made, open questions, what to hand to `ux-handoff` next.
