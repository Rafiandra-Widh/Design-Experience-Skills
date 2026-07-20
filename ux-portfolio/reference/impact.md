# Shared guide: impact framing & evidence

How to write project impact honestly — including when there is no data. Used by every ux-portfolio mode.

## Hierarki bukti dampak

Selalu naik ke level tertinggi yang *jujur* tersedia; sebutkan levelnya apa adanya.

1. **Metric terukur before→after** (emas) — "setup completion 40%→68% dalam 2 bulan setelah rilis (analytics internal)". Metric didefinisikan dengan benar via `ux-metrics identify`/`measure`.
2. **Proxy metric** — dampak tidak langsung yang tercatat: tiket support topik X turun, waktu training pengguna baru turun, adopsi fitur oleh N kantor/tim.
3. **Kualitatif terverifikasi** — hasil uji usability (5/6 partisipan menyelesaikan tugas yang sebelumnya gagal), kutipan pengguna, testimoni stakeholder yang bisa dikonfirmasi.
4. **Output signifikan yang diadopsi** — design system dipakai N tim, standar yang jadi acuan, komponen di-reuse. Ini outcome adopsi, bukan sekadar "selesai dibuat".

## Framing jujur tanpa data — kasus paling umum

Banyak proyek nyata tidak diukur. Jangan mengarang; pakai salah satu framing ini:

- **Metric thinking tanpa angka** — "Keberhasilannya seharusnya diukur dari X; instrumentasinya belum sempat dipasang, tapi indikasi awal Y." Menunjukkan cara berpikir metric — yang sebenarnya dicari hiring manager — tanpa angka palsu.
- **Dampak proses** — "Keputusan memangkas alur dari 7 jadi 3 langkah menghilangkan 2 sprint pekerjaan dev" — dampak nyata yang tidak butuh analytics.
- **Dampak keputusan** — "Temuan riset ini membatalkan rencana fitur X, menghemat satu kuartal roadmap."
- **Belajar dari nihil** — kalau proyek gagal/dibatalkan: ceritakan sebagai studi pengambilan keputusan. Satu cerita gagal yang jujur sering lebih kuat dari tiga cerita sukses generik.

**Larangan keras**: angka karangan atau "kira-kira"; klaim kausal tanpa dasar ("revenue naik karena redesign saya" saat banyak faktor lain); mengambil kredit metric milik tim/faktor lain.

## Cara menulis angka

- Selalu: **baseline → hasil + periode + sumber**. "68%" tanpa baseline tidak bercerita; "naik 70%" dari basis 40%→68% menyesatkan (sebut keduanya).
- **NDA/sensitif**: angka absolut → relatif ("transaksi harian naik 40%" tanpa nilai absolut), atau kategori ("dipakai jutaan pengguna" bila itu pun boleh). Konfirmasi dulu apa yang boleh tampil (cross-mode rule 4).
- Median > mean untuk waktu; sebutkan segmen kalau dampaknya tidak merata.

## Sambungan ke ux-metrics

- Case study proyek *berjalan* yang belum punya metric → sarankan jalankan `ux-metrics identify` + `measure` sekarang, supaya portfolio 6 bulan lagi punya bukti level-1. Ini saran standar di mode `review`.
- Rantai UX metric → dampak bisnis di case study mengikuti aturan `ux-metrics connect`: tulis sebagai hipotesis berlabel bukti, bukan klaim kausal mutlak.
