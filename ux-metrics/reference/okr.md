# Mode: okr — Cascade Metrics into KPI/OKR (Lead-Level)

Turn company/department goals plus the team's UX metrics into design-team OKRs and standing KPIs. For design leads setting quarterly direction.

## Intake

- The company/department OKR or goal this cascades from (paste it — jangan menebak strategi perusahaan).
- UX metrics available (from `identify`/`connect`/`measure` runs, or stated). No metrics yet → run `identify` first; OKR tanpa metric hanya daftar harapan.
- Period (quarter is the default), team size/scope (satu squad? seluruh design org?).

## KPI vs OKR — keep them separate

- **KPI** = health metric berkelanjutan yang tim jaga terus-menerus (task success checkout ≥ X%, SUS ≥ Y). Tidak berganti tiap kuartal; alarm kalau turun.
- **OKR** = target *perubahan* untuk satu periode (naikkan aktivasi dari A ke B). Ambisius, berganti tiap kuartal.
- Metric yang sama bisa pindah peran: jadi KR saat sedang diperbaiki, turun jadi KPI setelah stabil.

## Process

1. **Cascade, don't copy.** From the company objective, derive the design-team **Objective**: qualitative, inspiring, answers "apa kontribusi desain terhadap goal itu" — bukan menyalin objective perusahaan.
2. **Key Results = metric + baseline → target.** 2–4 KRs per objective, each *is* a UX metric from the tree (mode `connect` shows which UX metrics drive the business goal — pick those). Format: *[metric] dari [baseline] ke [target] pada [akhir periode]*. Baseline unknown → the KR becomes "tetapkan baseline [metric] dan capai [target awal]" — never invent the number.
3. **Good-KR checks** (apply and show them): outcome bukan output; angka baseline & target eksplisit; dalam pengaruh tim (tim desain tidak bisa memegang revenue sendirian — pegang driver-nya); ambisius tapi masuk akal (~70% confidence, bukan sandbag).
4. **Guardrail per objective.** At least one metric that must not degrade while chasing the KRs (see `frameworks.md`).
5. **Standing KPIs.** A short table of health metrics the team watches regardless of quarter, each linked to its measurement plan.

## Anti-patterns to reject explicitly

- KR = daftar deliverable ("ship redesign", "buat design system") — itu milestone proyek, bukan KR.
- Lebih dari ~4 KR per objective, atau lebih dari 2–3 objective per tim — tidak ada yang fokus.
- KR yang 100% pasti tercapai (sandbagging) atau di luar kendali tim sepenuhnya.
- OKR tanpa cara mengukur — every KR must link to a measurement plan row (`/ux-metrics measure`).

## Output template

```
# OKR Tim Desain — [periode]

**Cascade dari** — [objective perusahaan/departemen, disalin persis]

## Objective 1: [kualitatif, inspiratif]
| KR | Metric | Baseline | Target | Confidence | Cara mengukur |
|---|---|---|---|---|---|
**Guardrail** — [metric] tidak turun di bawah [angka]

## KPI tim (berkelanjutan)
| KPI | Ambang sehat | Cadence review | Cara mengukur |
|---|---|---|---|

**Catatan** — target bertanda ⚠️ = asumsi, perlu divalidasi; review confidence tiap [cadence].
```

Ships as .md; offer an artifact page if it will be shared with leadership.

## Scale

Aligning OKRs *across* teams or getting stakeholder buy-in is a facilitation problem — design the session with `ux-workshop workshop`. Presenting the OKR narrative upward → `ux-voice` for stakeholder register.
