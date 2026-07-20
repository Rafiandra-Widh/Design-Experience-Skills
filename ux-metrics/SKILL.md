---
name: ux-metrics
description: >
  UX measurement workflows: pick the right UX metrics, tie them to business metrics,
  plan how to measure them, and cascade them into KPI/OKR. Use when the user wants to
  identify success metrics for a product/feature ("metric apa yang cocok", "ukuran
  keberhasilan", "success metrics", "HEART"); connect UX metrics to business impact
  ("hubungkan ke business metric", "dampak bisnis", "metric tree", "north star");
  plan how to measure a metric ("cara ngukur", "measurement plan", "instrumentasi",
  "baseline", "target"); or derive team KPI/OKR from those metrics — lead-level
  ("turunkan OKR", "KPI tim desain", "cascade OKR", "key result").
  Modes: identify, connect, measure, okr.
  Not for task-level usability-test metrics/protocol (use ux-research plan), competitor
  benchmarking (use ux-research benchmark), or synthesizing research data (use ux-research synthesize).
user-invocable: true
argument-hint: "[identify|connect|measure|okr]"
---

# ux-metrics

Measurement workflows: identifying UX metrics, linking them to business metrics, planning measurement, and cascading them into KPI/OKR.

## Routing

Read `reference/frameworks.md` first, then the mode's reference file BEFORE producing anything. If the user passed a mode argument, use it; otherwise infer, and ask if ambiguous.

| Mode | When | Reference |
|---|---|---|
| `identify` | Pick the right UX metrics for a product/feature (HEART, Goals-Signals-Metrics) | `reference/identify.md` |
| `connect` | Map UX metrics to business metrics in a metric tree with explicit hypotheses | `reference/connect.md` |
| `measure` | Plan how to measure: formula, instrumentation, survey, baseline & target | `reference/measure.md` |
| `okr` | Cascade company goals into design-team Objectives, Key Results, and KPIs (lead-level) | `reference/okr.md` |

## Cross-mode rules

1. **Respond in the user's language**; keep metric and framework names (HEART, North Star, task success rate, SUS) in English — they are shared vocabulary with data/product teams.
2. **Never fabricate numbers.** Baselines, industry benchmarks, and targets are never invented. No data → write "baseline belum diketahui — ukur dulu", or find a cited source via WebSearch (URL + access date). Every initial target is labeled **"asumsi — perlu divalidasi"**.
3. **Correlation ≠ causation.** Every UX→business link is written as a testable hypothesis with its evidence strength labeled (terbukti / hipotesis / asumsi) — never presented as fact.
4. **Outcome, not output.** A metric or Key Result measures a change in user behavior or business result. A deliverable ("redesign selesai", "10 screen di-ship") is never a metric.
5. **Output medium.** Metric tree/diagram → FigJam (mermaid in chat/doc as fallback); measurement plans & OKR docs → project folder as .md; quick answers → chat; shareable review page → artifact. Load `figma-use` before writing to Figma, and always confirm first.
6. **Defer, don't duplicate.** Task-level usability-test metrics & protocol (SEQ per task, completion, errors) → `ux-research plan`; competitor benchmarking → `ux-research benchmark`; synthesizing research data → `ux-research synthesize`; running a team session to align on metrics → `ux-workshop`.
