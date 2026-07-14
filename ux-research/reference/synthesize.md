# Mode: synthesize — From Raw Data to Insights

Turn interview notes, transcripts, usability observations, or open survey answers into themes, insights, and recommendations.

## Intake

- Get ALL the raw data (paste, files, or folder path — read every file before synthesizing).
- The original research questions/hypotheses (synthesis answers *those*, not everything interesting).
- How many participants, which segments — needed for honest counting.

## Process (show your work)

1. **Open coding** — pass through each source, tag meaningful fragments with short codes (e.g., `trust-barrier`, `workaround-excel`). Keep participant IDs attached (P1, P2…).
2. **Affinity grouping** — cluster codes into candidate themes. A theme needs evidence from **≥ 2 participants**; single-participant signals go into a separate "sinyal lemah / perlu validasi" list, never silently promoted.
3. **Theme → insight** — an insight is a *statement about the user world with a consequence*, not a topic. "Peserta tidak percaya angka dashboard karena pernah menemukan selisih dengan laporan manual (P2, P4, P5) — sehingga mereka selalu re-check di Excel" ✅. "Tema: kepercayaan data" ❌.
4. **Recommendations** — each insight gets 1–3 design recommendations, tagged by effort (quick win / needs design / needs strategy). Recommendations are suggestions to the design process, not decrees.

## Evidence discipline

- Every insight lists supporting participants and ≥ 1 verbatim quote or concrete observation.
- Count honestly: "4 dari 6 peserta", never "sebagian besar pengguna".
- Contradicting evidence is reported, not dropped — note where participants split and by what segment.
- Separate clearly: **Observasi** (what happened) / **Interpretasi** (what we think it means) / **Rekomendasi** (what to do).

## Output format

```
# Sintesis Riset: [judul]
**Ringkasan eksekutif** — 3–5 insight terpenting, satu kalimat masing-masing

## Insight 1: [pernyataan insight]
- Bukti: P2 "kutipan...", P4 (observasi: ...), P5 "..."
- Kekuatan bukti: 4/6 peserta, konsisten di kedua segmen
- Interpretasi: ...
- Rekomendasi: [quick win] ..., [needs design] ...

## Insight 2: ...

## Sinyal lemah (1 peserta — perlu validasi)
## Jawaban atas pertanyaan riset awal   ← map each original question → answered/partial/unanswered
## Pertanyaan riset berikutnya
```

## Figma output (dual-output rule — SKILL.md rule 6)

Also render the synthesis as an **insight board** in the project's Figma page (load `figma-use` first):
- One board frame (auto-layout V, ~720 wide, padded) titled `Riset — Insight: [judul]`, with the data-source label ([DATA SIMULASI] if applicable) visible on the board.
- One card per insight (auto-layout V, surface fill, radius, padding): insight statement (bold) → evidence quote + participant IDs (smaller, secondary color) → recommendation chips tagged quick-win/needs-design/needs-strategy.
- Weak signals get a visually distinct muted card. Use neutral board styling (like exploration boards), NOT the product's design system — this is research communication, not product UI.
- Place in the page's research area; never overlapping design frames.

Offer follow-ups: turn insights into `artifacts` mode inputs (persona/journey), or an affinity map in FigJam (load `figma-use-figjam` first).
