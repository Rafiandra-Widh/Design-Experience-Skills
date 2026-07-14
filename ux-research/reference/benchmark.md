# Mode: benchmark — Desk Research, Competitor Analysis, Heuristic Evaluation

Structured secondary research. Everything cited; nothing from memory presented as current fact.

## Intake

- Goal: inspiration for a pattern? feature-gap analysis? positioning? Pick the lens before searching.
- Which competitors/products? If unknown, propose a list (direct, indirect, best-in-class from other industries) and confirm.
- Which flows/patterns matter (onboarding, checkout, dashboard, empty states…)?

## Tooling rules

- Facts about products (features, pricing, recent changes) → **WebSearch/WebFetch**, cite every claim with its source URL and access date.
- Actual UI flows → walk the product with Chrome tools (load `claude-in-chrome` skill) when accessible; screenshot key steps. Secondary sources (Mobbin-style galleries, reviews, blog teardowns) are acceptable but must be labeled as secondary.
- If something can't be verified, write "tidak terverifikasi" — never fill the gap with plausible guesses.

## Competitor analysis output

```
# Benchmark: [topik]
**Tujuan & lensa** | **Produk yang dianalisis & alasan**

## Per produk
- Ringkasan posisi
- Bagaimana mereka menangani [flow yang diteliti] — langkah per langkah
- Pola UI yang menonjol (+screenshot bila ada)
- Kekuatan / kelemahan relatif terhadap tujuan kita
- Sumber

## Matriks perbandingan   ← fitur/pola × produk, ✓/✗/parsial
## Pola yang layak diadopsi (dengan adaptasi apa)
## Pola yang sengaja TIDAK diadopsi (dan alasannya)   ← as valuable as the adopt list
## Peluang diferensiasi
```

## Heuristic evaluation (Nielsen 10)

Evaluate against: (1) visibility of system status, (2) match with the real world, (3) user control & freedom, (4) consistency & standards, (5) error prevention, (6) recognition over recall, (7) flexibility & efficiency, (8) aesthetic & minimalist design, (9) help users recognize/recover from errors, (10) help & documentation.

- Walk defined tasks, not random browsing. Evaluate the product per heuristic per task.
- Each finding: **lokasi → heuristik yang dilanggar → deskripsi masalah → severity 0–4** (0 bukan masalah, 1 kosmetik, 2 minor, 3 major, 4 katastrofik) → rekomendasi.
- Sort by severity; include a count summary per heuristic to show where the product is systematically weak.
- Note the method's limits: 1 evaluator ≈ 35% of issues — recommend usability testing (`plan` mode) for the critical flows.

## Scale

For a broad sweep (many competitors × many flows) suggest the `deep-research` skill or a Workflow fan-out; for 2–4 competitors, do it inline.
