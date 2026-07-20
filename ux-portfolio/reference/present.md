# Mode: present — Portfolio Deck & Delivery

Build the presentation deck, speaker notes, and panel-question prep for a portfolio session.

## Intake

- Konteks sesi: interview panel / portfolio review internal (promosi) / sharing komunitas? Durasi (default asumsi 20–30 menit + Q&A)? Presentasi live atau deck dikirim dulu?
- Sumber cerita: case study hasil mode `case-study`, atau bahan langsung (→ jalankan intake case-study ringkas dulu).
- Audiens panel: designer? PM/eng? leadership? — menentukan berat cerita (craft vs dampak vs kepemimpinan).
- Bahasa presentasi (ID/EN).

## Process

1. **Pilih 1–3 proyek** — 30 menit realistis untuk 2 proyek dalam; 3 hanya jika salah satunya singkat. Lebih baik dalam daripada lebar.
2. **Struktur deck** (interview 20–30 menit):
   - Opening 1–2 slide: positioning + peta apa yang akan diceritakan.
   - Per proyek ±8–12 slide mengikuti arc `storytelling.md`, berat di keputusan kunci & outcome — bukan tur proses. Satu ide per slide; slide adalah visual + headline, bukan dokumen.
   - Closing 1 slide: benang merah cara kerja + apa yang dicari.
3. **Speaker notes per slide** — apa yang *diucapkan* (cerita, transisi, penekanan), bukan pengulangan teks slide. Tandai slide yang boleh dilewati kalau waktu menipis.
4. **Antisipasi pertanyaan panel** per proyek + draft jawaban jujur: "Kenapa tidak [alternatif]?", "Apa yang gagal / akan kamu ubah?", "Apa peranmu persisnya vs tim?", "Bagaimana kamu tahu ini berhasil?" (→ jawaban memakai `impact.md`; kalau tidak diukur, jawab dengan framing jujur — panel lebih menghargai itu daripada angka mendadak).
5. **Latihan Q&A opsional** — Claude berperan sebagai panel (tanya satu-satu, lalu feedback per jawaban: substansi dulu, cara menyampaikan kedua — gaya `ux-voice coach`). Latihan penyampaian verbal mendalam → arahkan ke `ux-voice coach`.

## Output template

```
# Deck Portfolio: [nama] — [konteks sesi, durasi]

## Struktur
| # | Slide | Isi visual | Speaker notes | Boleh dilewati? |
|---|---|---|---|---|

## Antisipasi pertanyaan panel
| Proyek | Pertanyaan | Jawaban jujur (poin) |
|---|---|---|

**Timing** — [pembagian menit per bagian + buffer Q&A]
```

Ships as .md; slide visual → HTML artifact (satu halaman per slide) atau layout Figma (via `figma-use`, konfirmasi dulu).

## Scale

Deck dikirim tanpa presentasi live ("silent deck") → speaker notes dilebur jadi teks pendamping di slide; aturan 3 lapis `storytelling.md` berlaku penuh.
