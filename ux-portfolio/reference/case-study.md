# Mode: case-study — Raw Material into Narrative

Turn one project's raw material into a layered case-study narrative. The material comes from the user — missing pieces are excavated by interview, never invented.

## Intake

- Bahan mentah apa pun yang ada: brief, file/URL Figma, laporan riset, metric, foto proses, thread keputusan. Tidak harus rapi.
- Peran persis user di proyek itu (dan siapa mengerjakan apa — untuk atribusi jujur).
- Hasil & bukti yang tersedia (petakan ke hierarki `impact.md`).
- Apa yang boleh/tidak boleh tampil (NDA) — tanyakan SEBELUM menulis, bukan sesudah.
- Target pembaca & bahasa (ID/EN/keduanya) — dari kerangka `structure` bila ada.

**Bahan kurang → wawancara terstruktur**, per section arc: "Bagaimana kamu tahu ini masalah?", "Keputusan apa yang paling diperdebatkan? Apa opsi lainnya?", "Apa yang kamu korbankan?", "Apa yang berubah setelah rilis?". Gali sampai ada 2–3 keputusan kunci yang nyata; jangan menambal dengan karangan.

## Process

1. Pilih **2–3 keputusan kunci** sebagai tulang cerita (kriteria: ada opsi nyata, ada alasan berbasis bukti, ada trade-off).
2. Draft mengikuti arc `storytelling.md` — default outcome-first untuk portfolio situs.
3. Tulis dampak per `impact.md` — sebutkan level buktinya; tanpa data → framing jujur, bukan angka kira-kira.
4. Terapkan **3 lapis**: cek bahwa headline saja sudah bercerita, lalu subjudul+bold+caption merangkai cerita, baru paragraf penuh.
5. Tandai visual sebagai placeholder eksplisit: `[gambar: before/after alur checkout — ambil dari file Figma X]` — user yang menyiapkan asetnya.
6. Versi bahasa sesuai target; bila diminta keduanya, tulis penuh dua-duanya (bukan terjemahan mentah — sesuaikan idiom).

## Output

Case study .md di folder proyek (source of truth). Lalu tawarkan:
- **HTML artifact** — preview visual satu halaman (layout, hirarki, placeholder gambar) untuk merasakan hasil jadinya;
- **Draft layout di Figma** — via `figma-use` (load dulu, konfirmasi sebelum menulis ke file user) untuk dipoles manual;
- atau keduanya.

## Quality bar sebelum diserahkan

- [ ] Headline + 1 kalimat outcome bercerita sendiri
- [ ] 2–3 keputusan dengan opsi→pilihan→alasan→trade-off
- [ ] Dampak berlabel level bukti, angka punya baseline+periode+sumber
- [ ] Atribusi saya/kami jujur; ada ≥1 refleksi/trade-off jujur
- [ ] Tidak ada item anti-cliché (`storytelling.md`); tidak ada data NDA

## Scale

Banyak proyek sekaligus → kerjakan satu per satu (kualitas > kecepatan); mulai dari proyek urutan pertama hasil `structure`.
