# Mode: measure — Measurement Plan (Tool-Agnostic)

Turn chosen metrics into an operational measurement plan: exact formulas, what to instrument or ask, baseline & target, cadence. Method first — tools (GA4, Mixpanel, Amplitude, Hotjar) are only examples, never requirements.

## Intake

- Which metrics (from `identify`/`connect`, or stated directly)?
- What access exists: analytics terpasang? bisa pasang survey in-product? ada tim data yang bisa dimintai query/event baru?
- Is there any historical data that can serve as baseline?

## Process — per metric

1. **Definisi operasional.** Explicit formula: numerator / denominator, unit, populasi (siapa yang dihitung — semua user? user baru? per sesi?), dan time window. "Adoption rate" becomes: *jumlah pengguna eligible yang memakai fitur ≥1× dalam 14 hari sejak rilis ÷ jumlah pengguna eligible*. A metric without all four is sent back to definition.
2. **Metode.** Choose and justify:
   - **Analytics event** — list the exact events + properties needed, generic taxonomy (`checkout_step_completed {step, duration_ms, error_count}`). Flag which events already exist vs need engineering work — instrumentasi baru adalah request ke developer, tuliskan sebagai spec singkat.
   - **Survey in-product** — pick the instrument from the attitudinal catalog in `frameworks.md` (SUS/UMUX-Lite untuk keseluruhan produk, CSAT/CES untuk momen, NPS berkala). Define trigger timing (setelah menyelesaikan apa), sampling (jangan tanya orang yang sama < 90 hari), and target respons minimum — di bawah ~30 respons per segmen, laporkan sebagai indikasi, bukan skor.
   - **Moderated testing** — task-level protocol & metrics (SEQ per task, completion, errors) are owned by `ux-research plan`; defer, don't rewrite.
3. **Baseline & target.** Baseline is measured, never guessed — no historical data → the plan's first milestone is "ukur baseline selama N minggu". Targets tanpa dasar dilabeli **"asumsi — perlu divalidasi"**; industry benchmarks only with a cited source (URL + tanggal akses).
4. **Cadence & segmen.** Review rhythm (mingguan untuk leading, bulanan/kuartalan untuk lagging) and the segments that matter (platform, kohort baru vs lama, tier) — an average across segments hides the problem.

## Output template

```
# Measurement Plan: [produk/fitur]

| Metric | Formula (numerator/denominator, populasi, window) | Metode & instrumentasi | Baseline | Target | Cadence & segmen | Owner |
|---|---|---|---|---|---|---|

## Event yang perlu diinstrumentasi (request ke dev)
| Event | Properties | Dipakai oleh metric | Status |
|---|---|---|---|

## Survey
[Instrumen, pertanyaan persis, trigger, sampling, minimum respons]

**Catatan** — target bertanda ⚠️ = asumsi, perlu divalidasi setelah baseline terukur.
```

Ships as .md in the project folder; ringkasan singkat di chat.

## Scale

Instrumentation requests going to developers can be packaged via `ux-handoff annotate`/`spec` if they attach to specific screens.
