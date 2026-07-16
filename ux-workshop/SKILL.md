---
name: ux-workshop
description: >
  Brainstorming facilitation, workshop design, and design-process synthesis using
  best-practice UX methods. Use when the user wants to brainstorm or generate ideas
  ("brainstorm", "ideasi", "cari ide", "bantu mikir fitur/solusi", "aku mentok");
  design or plan a team workshop/session ("rancang workshop", "bikin agenda sesi",
  "fasilitasi design sprint", "lightning decision jam", "kickoff/discovery session");
  synthesize and prioritize a pile of ideas or sticky notes into themes and decisions
  ("kelompokkan ide-ide ini", "affinity mapping", "bantu milih/prioritas", "sintesis
  hasil workshop", termasuk membaca stickies dari board FigJam); or pick the right
  method for a situation ("metode apa yang cocok untuk…"). Modes: ideate, workshop,
  converge, method-finder. Not for synthesizing research transcripts (use ux-research
  synthesize) or designing the chosen solution's screens (use ux-design flow).
user-invocable: true
argument-hint: "[ideate|workshop|converge|method-finder] <topik/URL FigJam>"
---

# ux-workshop

Facilitation and decision-making with UX methods: diverge, converge, and document — in chat and on FigJam boards.

## Routing

Read `reference/methods.md` BEFORE any mode work — method choices must come from its selection table (§6), justified by goal × time × group size. If the user passed a mode argument, use it; otherwise infer (need ideas → ideate; plan a session → workshop; pile of ideas/stickies → converge; "metode apa" → method-finder).

| Mode | When | Reference |
|---|---|---|
| `ideate` | Generate ideas: facilitated brainstorming, solo or team | `reference/ideate.md` |
| `workshop` | Design a session package: agenda, facilitator script, FigJam template | `reference/workshop.md` |
| `converge` | Ideas/stickies → themes → priorities → documented decisions | `reference/converge.md` |
| `method-finder` | "Which method fits my situation?" — answer directly from `methods.md` §6 with 1 primary + 1 alternative, each with a one-line why and mini-recipe | (no separate file) |

## Cross-mode rules

1. **Diverge before converge, never mixed in one block.** Idea generation happens without judgment; evaluation gets its own explicitly separate block. Every activity gets an explicit timebox.
2. **Anti-dominance defaults.** Group activities start silent (write first, talk later). When Claude contributes ideas, each is labeled `[Claude]`, capped at roughly a third of the pool, and builds on the user's ideas ("yes, and") rather than replacing them.
3. **Synthesis integrity.** Affinity grouping is transparent — show why items cluster, never silently drop ideas (leftovers go to a visible "Parkir" group). Votes are NEVER fabricated: if no one voted, use explicit criteria (2×2 with a one-line justification per item) and say plainly that the placement is Claude's judgment for the team to challenge.
4. **FigJam is the workshop medium.** Before writing to a board, load `figma-use` AND `figma-use-figjam`; for a brand-new board load `figma-create-new-file` first. Read stickies back with `get_figjam`. FigJam URLs contain `/board/`. Technical patterns: `reference/figjam-board.md`.
5. **Defer, don't duplicate.** Research transcripts → `ux-research synthesize`. Turning a chosen idea into screens → `ux-design flow`. Persona/journey artifacts → `ux-research artifacts`. Communicating outcomes upward → `ux-voice`.
6. **Respond in the user's language**; method names stay English. Deliverable documents go to the project folder (same output conventions as the other skills: visual → FigJam, dokumen → folder proyek, ringkasan → chat).
