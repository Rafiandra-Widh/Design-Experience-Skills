# Mode: review — Portfolio Audit Through Three Reader Lenses

Audit an existing portfolio or case study by simulating how each real reader actually reads it — with specific, located findings, never general impressions.

## Intake

- Sumber: URL portfolio live / paste teks / path PDF / URL Figma.
- Pemilik: user sendiri, atau anggota tim (siapa + levelnya — mengubah kalibrasi & nada).
- Target role & tujuan (lamar/promosi/branding) — review tanpa target = opini tanpa arah.

## Tooling rules

- Portfolio live → baca via Chrome tools/WebFetch, per halaman; jangan menilai dari ingatan.
- Figma → `get_screenshot` (+ `get_metadata` bila perlu struktur).
- Setiap temuan merujuk lokasi spesifik (halaman/section/kalimat) + kutip contohnya. Tanpa lokasi = bukan temuan.

## Process — simulasi 3 lapis pembaca

**Lapis 1 — Recruiter skim (5 menit).** Baca hanya headline, visual, dan bold — seperti recruiter sungguhan. Nilai: positioning langsung jelas? Outcome tiap proyek kelihatan tanpa membaca paragraf? Proyek pertama yang terkuat? Navigasi & first impression?

**Lapis 2 — Hiring manager deep-read.** Baca penuh 1–2 case study terkuat. Nilai: keputusan & alasan terlihat, atau hanya proses/galeri? Bukti dampak level berapa (`impact.md`)? Peran penulis jelas dan jujur? Ada trade-off/refleksi?

**Lapis 3 — Craft & bahasa.** Sapu seluruh teks: klaim generik, anti-cliché (`storytelling.md`), atribusi saya/kami, angka tanpa baseline/sumber, jargon internal, konsistensi bahasa (campur ID/EN tak disengaja), potensi bocor NDA.

Tiap temuan: severity **🔴** (membuat pembaca berhenti/menolak) / **🟡** (melemahkan) / **🟢** (polesan) + rekomendasi konkret + untuk temuan bahasa: contoh perbaikan **before→after**.

## Output template

```
# Review Portfolio: [nama] — target [role]

## Skor per lapis pembaca
| Lapis | Skor /5 | Ringkasan 1 kalimat |
|---|---|---|

## Temuan
| # | Lokasi | Temuan | Severity | Rekomendasi (+ before→after bila bahasa) |
|---|---|---|---|---|

## 3 prioritas perbaikan
1. ...

**Saran standar** — proyek berjalan yang belum punya bukti dampak: jalankan `ux-metrics identify` + `measure` sekarang supaya portfolio berikutnya punya angka nyata.
```

Ke chat/.md; halaman review yang rapi untuk dibagikan → artifact.

## Mentoring seorang anggota tim

- Mulai dari yang sudah kuat (spesifik, bukan basa-basi), baru temuan.
- Maksimal **3 prioritas** perbaikan — daftar 20 temuan melumpuhkan, bukan membantu.
- Kalibrasi ke level: junior dinilai pada craft & kejelasan cerita, bukan scope kepemimpinan.
- Kritik kualitas desain karyanya sendiri (bukan cara menceritakannya) → `ux-design critique`; cara menyampaikan feedback → `ux-voice`.
