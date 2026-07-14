---
name: ux-research
description: >
  UX research workflows for any product. Use when the user wants to plan research —
  research plan, screener, interview guide, usability test protocol ("riset", "wawancara",
  "uji kegunaan"); synthesize raw data — interview notes/transcripts into themes, insights,
  affinity maps, recommendations ("sintesis", "olah transkrip", "analisis hasil interview");
  produce research artifacts — persona, journey map, JTBD, service blueprint; run desk
  research — competitor analysis, benchmark, heuristic evaluation ("benchmark",
  "riset kompetitor"); or audit accessibility against WCAG ("audit aksesibilitas", "cek WCAG",
  "a11y"). Modes: plan, synthesize, artifacts, benchmark, a11y.
  Not for designing screens (use ux-design) or market/business research unrelated to users.
user-invocable: true
argument-hint: "[plan|synthesize|artifacts|benchmark|a11y]"
---

# ux-research

Research workflows: planning, synthesis, artifacts, desk research/benchmarking, and accessibility audits.

## Routing

Read the mode's reference file BEFORE producing anything. If the user passed a mode argument, use it; otherwise infer, and ask if ambiguous.

| Mode | When | Reference |
|---|---|---|
| `plan` | Design a study: research plan, screener, interview guide, usability test protocol | `reference/plan.md` |
| `synthesize` | Turn notes/transcripts/observations into themes, insights, recommendations | `reference/synthesize.md` |
| `artifacts` | Build persona, journey map, JTBD, service blueprint from existing data | `reference/artifacts.md` |
| `benchmark` | Desk research: competitor analysis, pattern review, heuristic evaluation | `reference/benchmark.md` |
| `a11y` | Audit a design or live page against WCAG 2.2 AA | `reference/a11y.md` |

## Cross-mode rules

1. **Decision first.** Before producing any deliverable, establish: what decision will this research inform, and who will consume it? A study without a decision is a fishing trip — push back gently and sharpen it.
2. **Never fabricate data.** Findings must trace to supplied data (transcripts, notes, analytics) or cited sources (web research). If the user asks for a persona/journey without data, deliver it clearly labeled **"proto-persona / asumsi — perlu divalidasi"** and list the assumptions to test.
3. **Evidence discipline.** Every insight carries its supporting evidence (quote, observation, source URL). Separate *observation* (what happened) from *interpretation* (what it means) from *recommendation* (what to do).
4. **Use real tools for facts.** Desk research uses WebSearch/WebFetch with sources cited; live-page audits use Chrome tools; Figma audits use `get_screenshot` + `get_variable_defs`. Never present recalled knowledge as verified research.
5. **Respond in the user's language**; keep participant-facing materials (screeners, interview questions) in the participants' language.
6. **Dual-output deliverables.** Research deliverables ship as BOTH a markdown file (archive/source of truth) AND a visual board in the project's Figma page — insight boards, persona cards, journey maps (see each mode's "Figma output" section). Load `figma-use` before writing to Figma. Skip the Figma half only when the user asks for file-only, or no Figma file is in play.
