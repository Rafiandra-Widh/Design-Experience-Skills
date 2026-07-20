# Shared guide: storytelling, structure & language

Read this before any ux-portfolio mode. Every structural and language decision traces back to how portfolios are actually read.

## Perilaku pembaca — dasar semua keputusan

| Pembaca | Cara membaca | Yang dicari |
|---|---|---|
| Recruiter / screening | Skim 2–5 menit, visual & headline dulu, jarang baca paragraf | Positioning jelas, outcome kelihatan tanpa membaca, kecocokan kasar dengan role |
| Hiring manager / design lead | Baca dalam 1–2 case study yang paling relevan | Cara berpikir: keputusan, alasan, trade-off; bukti dampak; peran yang jujur |
| Leadership internal (promosi) | Menilai terhadap rubric level | Scope, outcome bisnis, bukti kepemimpinan & pengaruh lintas tim |
| Panel interview | Sudah baca sekilas; portfolio jadi bahan menggali | Konsistensi cerita saat ditanya "kenapa", kejujuran soal kegagalan & peran |

**Implikasi inti — tulis 3 lapis.** Setiap case study harus bisa dibaca tiga cara: (1) *headline saja* — judul + 1 kalimat outcome per proyek sudah bercerita; (2) *skim* — subjudul, bold, caption gambar, dan angka merangkai cerita utuh; (3) *baca penuh* — paragraf memberi kedalaman keputusan. Kalau lapis 1–2 tidak jalan, mayoritas pembaca tidak pernah sampai lapis 3.

## Arc naratif case study

Kerangka default (urutan bisa digeser, isinya tidak boleh hilang):

1. **Context** — produk apa, untuk siapa, 2–3 kalimat. Plus satu baris meta: peran, tim, durasi, tahun.
2. **Problem** — masalahnya apa, kenapa penting (bagi pengguna DAN bisnis), bagaimana tahu itu masalah (data/riset, bukan asumsi).
3. **Constraints & role** — batasan nyata (waktu, tech, regulasi, politik organisasi) dan peran persis penulis. Constraints membuat keputusan bisa dinilai.
4. **Keputusan kunci** — INTI CERITA. Pilih 2–3 decision point: apa opsinya, apa yang dipilih, kenapa, apa trade-off-nya, bukti apa yang mendasari. BUKAN kronologi lengkap proses.
5. **Outcome** — apa yang berubah, dengan bukti (pakai hierarki di `impact.md`).
6. **Reflection** — apa yang dipelajari, apa yang akan dilakukan berbeda. Satu kegagalan/trade-off jujur membuat seluruh cerita lebih dipercaya.

**Variasi outcome-first**: untuk pembaca skim, buka case study dengan ringkasan outcome ("Redesign onboarding — setup completion 40%→68% dalam 2 bulan"), baru cerita lengkapnya. Aman jadi default untuk portfolio situs.

## TOC template

**Level portfolio** (situs/PDF):
```
Homepage — positioning 1 kalimat (siapa + spesialisasi + bukti singkat) + 3–5 kartu proyek (judul + outcome headline + visual)
Case studies — 3–5, terkuat & paling relevan pertama
About — cerita singkat, cara kerja, di luar kerja; BUKAN daftar tools
Kontak / CV
```

**Level case study** (mengikuti arc):
```
Judul + outcome headline
Meta: peran · tim · durasi · tahun
Context & Problem
Constraints & peran saya
Keputusan 1..3 (masing-masing: opsi → pilihan → alasan → trade-off, dengan visual)
Outcome & bukti
Refleksi
```

## Aturan bahasa

- **Aktif, orang pertama.** "Saya memutuskan X karena Y" — bukan "diputuskanlah X" atau "the team decided" saat itu keputusanmu.
- **Spesifik, bukan generik.** "Menaikkan setup completion dari 40% ke 68%" — bukan "meningkatkan UX secara signifikan". Klaim generik = tidak ada klaim.
- **Atribusi jujur.** "Saya" untuk kerjamu, "kami — bagian saya: …" untuk kerja tim. Panel akan menggali ini; cerita yang menggelembung runtuh di interview.
- **Tanpa jargon internal.** Nama squad, istilah proyek internal, singkatan instansi — ganti dengan bahasa yang dipahami orang luar.
- **Kalimat pendek.** Satu ide per kalimat; paragraf ≤4 kalimat. Pembaca sedang skim.

## Anti-cliché / anti-slop

Pola yang membuat reviewer senior berhenti membaca — tolak secara eksplisit saat muncul di draft:

- **Dump proses** — diagram Double Diamond / empathize-define-ideate-prototype-test dipajang tanpa cerita. Proses standar bukan diferensiasi; keputusanmu yang membedakan.
- **Galeri screenshot** — deretan visual tanpa narasi keputusan. Portfolio bukan Dribbble.
- **Bio slop** — "passionate about crafting delightful user experiences". Ganti dengan positioning spesifik + bukti.
- **Artefak tanpa konsekuensi** — persona/journey map dipajang tanpa menjelaskan keputusan apa yang berubah karenanya.
- **Semua sukses sempurna** — tanpa trade-off, kegagalan, atau constraint. Terbaca sebagai cerita yang disanitasi; tidak dipercaya.
- **Metric tanpa konteks** — "naik 200%!" tanpa baseline, periode, atau sumber (lihat `impact.md`).
