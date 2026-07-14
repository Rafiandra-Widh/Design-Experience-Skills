# Mode: readiness — Pre-Handoff Frame Audit

Audit frames BEFORE handoff so developers receive clean, unambiguous files. Output: pass/fail per check + a fix list.

## Data gathering

- `get_metadata` for the node tree (names, types), `get_design_context` for layout mode/instances/bindings, `get_variable_defs` for token coverage.
- Ask which frames are in scope (a page URL is fine — enumerate its frames) and whether the team has its own definition-of-done to merge with this checklist.

## Checklist

**1. Struktur & penamaan**
- [ ] Frame diberi nama bermakna (`02 Login / Error`), bukan `Frame 4212`
- [ ] Layer penting diberi nama; tidak ada `Rectangle 12` pada elemen yang akan direferensikan
- [ ] Tidak ada layer tersembunyi sisa eksplorasi di dalam frame handoff
- [ ] Draft/eksplorasi terpisah dari frame final (halaman atau section berbeda)

**2. Auto-layout & responsivitas**
- [ ] Semua container pakai auto-layout (bukan posisi absolut manual), kecuali yang memang perlu
- [ ] Sizing masuk akal: fill/hug sesuai perilaku yang diinginkan, bukan fixed semua
- [ ] Constraint/perilaku resize benar saat frame dilebarkan-disempitkan
- [ ] Breakpoint lain yang dijanjikan benar-benar ada framenya

**3. Token & style**
- [ ] Semua warna terikat variable/style — deteksi raw hex dari design context
- [ ] Semua teks pakai text style / typography variable
- [ ] Spacing utama pakai token spacing (bila sistemnya mendukung)
- [ ] Radius & efek pakai token/style, bukan nilai lepas

**4. Komponen**
- [ ] Elemen UI adalah instance dari library, bukan rekaan lokal dari primitif
- [ ] Tidak ada instance detached tanpa alasan; override tidak mengubah anatomi komponen
- [ ] Komponen lokal baru diberi tanda: kandidat untuk diangkat ke library?

**5. Kelengkapan states & alur**
- [ ] Elemen interaktif punya state: hover/focus/disabled minimal untuk web
- [ ] Ada desain untuk: empty, loading, error, dan konten ekstrem (teks panjang, angka besar, list kosong vs 1000 item)
- [ ] Alur tidak buntu: setiap aksi utama punya layar hasil/umpan balik

**6. Konten**
- [ ] Tidak ada lorem ipsum atau placeholder `Label`
- [ ] Data realistis dan konsisten antar-frame (nama, angka, tanggal masuk akal)
- [ ] Bahasa konten konsisten dan sesuai produk

## Output format

```
# Audit Kesiapan Handoff: [file/halaman] — [tanggal]
**Skor**: X/Y checks lolos

## 🔴 Harus dibereskan sebelum handoff
1. [check] — lokasi spesifik (nama frame/layer) — cara memperbaiki

## 🟡 Sebaiknya dibereskan
## ✅ Lolos
(daftar check yang bersih — bukti audit menyeluruh)

## Langkah selanjutnya
Setelah bersih: lanjut `spec` untuk spek dev, atau `annotate` untuk redline.
```

Findings name the exact frame/layer (from metadata), so the designer can fix without hunting. Offer to fix mechanical issues (renaming, binding obvious tokens) directly via `figma-use` — with the user's confirmation, since it modifies their file.
