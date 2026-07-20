# Shared guide: metric frameworks & catalog

Read this before any ux-metrics mode. It is the shared vocabulary; mode files only reference it.

## HEART (Google)

Framework untuk memilih *kategori* UX metric per produk/fitur. Tidak semua kategori dipakai — pilih yang relevan dengan goal.

| Kategori | Mengukur | Contoh metric |
|---|---|---|
| **H**appiness | Sikap/persepsi pengguna | SUS, CSAT, NPS, rating app store |
| **E**ngagement | Tingkat keterlibatan sukarela | Frekuensi pakai per minggu, depth of use, fitur dipakai per sesi |
| **A**doption | Pengguna baru mulai memakai | % pengguna baru yang mencoba fitur dalam N hari, aktivasi |
| **R**etention | Pengguna kembali | Retention D7/D30, churn rate, resurrection |
| **T**ask success | Efektivitas & efisiensi tugas | Task success rate, time on task, error rate, funnel completion |

Catatan: untuk tool internal/enterprise, Engagement sering tidak relevan (pemakaian diwajibkan) — utamakan Task success + Happiness.

## Goals → Signals → Metrics (GSM)

Proses menurunkan metric dari goal, dipakai bersama HEART. Jangan lompat langsung ke metric.

1. **Goal** — apa yang ingin dicapai pengguna/bisnis di kategori itu ("pengguna baru berhasil setup tanpa bantuan").
2. **Signal** — perilaku/sikap yang menandakan goal tercapai atau gagal ("menyelesaikan wizard", "menghubungi CS saat setup").
3. **Metric** — signal yang dikuantifikasi, bisa dilacak dari waktu ke waktu ("% pengguna baru menyelesaikan setup < 10 menit dalam sesi pertama").

## North Star Metric & input metrics

- **North Star** = satu metric level produk yang paling mewakili nilai yang diterima pengguna (bukan revenue langsung). Contoh: "transaksi tercatat per warung aktif per minggu" — bukan "jumlah download".
- **Input metrics** = 3–5 metric yang secara kausal mendorong North Star; di sinilah UX metric biasanya duduk. Tim desain jarang memegang North Star sendirian, tapi memegang input metric.

## AARRR (pirate metrics) — konteks funnel

Acquisition → Activation → Retention → Referral → Revenue. Berguna untuk memetakan *di tahap funnel mana* sebuah UX metric bekerja — mis. perbaikan onboarding menyerang Activation, bukan Acquisition.

## Leading vs lagging

- **Lagging** — hasil akhir, lambat bergerak, sering di level bisnis (revenue, churn, NPS). Bagus untuk menilai, buruk untuk mengarahkan kerja mingguan.
- **Leading** — perilaku yang mendahului hasil, cepat bergerak, bisa dipengaruhi desain (task success, aktivasi, error rate). UX metric yang baik hampir selalu leading terhadap business metric.

## Metric tree

Pohon: business outcome di puncak → product metric → UX metric sebagai driver di daun. Setiap panah adalah klaim kausal yang harus dilabeli kekuatan buktinya (terbukti / hipotesis / asumsi). Dipakai penuh di mode `connect`.

## Katalog UX metric umum

**Behavioral (dari analytics/log):**

| Metric | Definisi singkat | Tipe |
|---|---|---|
| Task success rate | % sesi/pengguna yang mencapai goal tugas yang terdefinisi | leading |
| Time on task | Waktu median menyelesaikan tugas (median, bukan mean — outlier) | leading |
| Error rate | % tugas dengan error/validasi gagal/salah jalur | leading |
| Funnel conversion per step | % lolos tiap langkah funnel (bukan hanya ujung) | leading |
| Adoption rate | % pengguna yang memakai fitur ≥1× dalam N hari sejak eligible | leading |
| Feature usage / depth | Frekuensi & kedalaman pemakaian fitur | leading |
| Retention (D7/D30) / churn | % pengguna kembali pada hari ke-N / berhenti | lagging |
| Support ticket rate | Tiket bantuan per 1.000 pengguna aktif untuk area tertentu | lagging |

**Attitudinal (dari survey):**

| Metric | Skala & kapan | Catatan |
|---|---|---|
| SUS | 10 pertanyaan, skor 0–100; setelah pemakaian menyeluruh | Standar industri; rata-rata benchmark publik ≈ 68 |
| SEQ | 1 pertanyaan, 1–7; langsung setelah satu tugas | Per tugas — protokolnya milik `ux-research plan` |
| UMUX-Lite | 2 pertanyaan; alternatif ringkas SUS | Berkorelasi dengan SUS |
| CSAT | 1–5, setelah interaksi/transaksi spesifik | Momen, bukan keseluruhan |
| CES | 1–7 "seberapa mudah…", setelah menyelesaikan urusan | Bagus untuk support & servis |
| NPS | 0–10 kemungkinan merekomendasikan; berkala (kuartalan) | Lagging & kasar — jangan jadikan satu-satunya UX metric |

## Guardrail / health metrics

Metric yang **tidak boleh memburuk** saat mengejar target. Contoh: mengejar kecepatan checkout → guardrail error rate & refund rate; mengejar adoption fitur → guardrail retention & support tickets. Setiap set metric dan setiap OKR wajib punya minimal satu guardrail.

## Anti-pattern

- **Vanity metrics** — angka yang selalu naik dan tidak menginformasikan keputusan (total download kumulatif, page views, jumlah pengguna terdaftar).
- **Metric tanpa definisi operasional** — "engagement naik" tanpa formula, populasi, dan time window bukan metric, tapi slogan.
- **Terlalu banyak metric** — pilih 1 primer + 2–3 sekunder + guardrail. Lebih dari itu, tidak ada yang benar-benar dipantau.
- **Mengukur yang mudah, bukan yang penting** — clicks mudah diukur; keberhasilan tugas yang penting.
- **Deliverable disamarkan jadi metric** — "redesign selesai Q3" adalah output, bukan outcome.
