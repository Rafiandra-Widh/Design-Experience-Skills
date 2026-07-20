# Mode: identify — Pick the Right UX Metrics

Choose a small, defensible set of UX metrics for a product or feature, derived from goals — not grabbed from a list.

## Intake

- What product/feature, and what is the design goal? (What should change in user behavior if the design works?)
- Stage: baru rilis / mature / sedang redesign? (Baru → Adoption & Task success dulu; mature → Engagement/Retention; redesign → before-after pada metric yang sama.)
- What decision will these metrics inform? (Prioritas roadmap? Menilai redesign? Laporan ke leadership?) No decision → sharpen it first, same rule as `ux-research`.
- What data already exists (analytics events, past surveys, support tickets)? Prefer metrics that can start from existing data.

## Process

1. Map the goal to HEART categories — pick only the 2–3 relevant categories, say why the others are skipped (see `frameworks.md`).
2. Run Goals → Signals → Metrics per chosen category. Show the GSM steps, not just the result — the signal step is where bad metrics get caught.
3. Select **1 primary metric** (the one the design is accountable for), **2–3 secondary**, and **≥1 guardrail**. Reject vanity metrics explicitly if the user proposes one — explain with the anti-pattern list.
4. For each metric note the data source honestly: sudah ada / perlu instrumentasi / perlu survey. Measurement details belong to mode `measure` — offer it as the next step.

## Output template

```
# UX Metrics: [produk/fitur]

**Goal desain** — [1 kalimat]
**Keputusan yang didukung** — [1 kalimat]

## Goals → Signals → Metrics
| Kategori HEART | Goal | Signal | Metric |
|---|---|---|---|

## Metric terpilih
| Metric | Peran | Definisi | Kenapa relevan | Tipe | Sumber data |
|---|---|---|---|---|---|
| ... | primer | ... | ... | leading | perlu instrumentasi |
| ... | sekunder | ... | ... | leading | sudah ada |
| ... | guardrail | ... | tidak boleh memburuk karena ... | lagging | sudah ada |

**Kategori HEART yang dilewati & alasannya** — ...
**Langkah berikutnya** — `/ux-metrics measure` untuk rencana pengukuran, `/ux-metrics connect` untuk memetakan ke business metric.
```

## Scale

Output default ke chat; simpan sebagai .md di folder proyek jika akan dipakai lintas mode (connect/measure/okr membacanya sebagai input). Untuk menyepakati metric bersama tim dalam sesi, arahkan ke `ux-workshop`.
