# Mode: spec — Figma Frame → Developer Spec

Turn a Figma frame/screen into a spec a developer can build from without opening Figma.

## Data gathering (in order)

1. `get_metadata` on the frame URL — node inventory, sizes, positions.
2. `get_design_context` — structure, auto-layout, component instances, bound variables.
3. `get_variable_defs` — token names + resolved values for everything bound.
4. `get_screenshot` — visual reference to embed/attach.
5. If the file has Code Connect: `get_code_connect_map` — reference the real code component names.

If any call fails, list the affected values as "tidak tersedia dari Figma" — never fill in by eye.

## Spec template

```
# Spec: [nama screen] — [link Figma]
**Platform target** | **Breakpoint yang dispesifikasikan** | **Tanggal & versi frame**

## 1. Ringkasan
Apa screen ini, kapan muncul, aksi utama user.

## 2. Layout
- Dimensi frame, grid (kolom/margin/gutter), perilaku scroll
- Struktur region (header/sidebar/content...) dengan ukuran fix vs fluid
- Perilaku responsive per breakpoint; min/max width elemen kunci

## 3. Komponen
Tabel: elemen → komponen DS (nama library / nama code bila ada Code Connect) → varian/props → catatan override.
Elemen non-DS ditandai ⚠️ custom (perlu dibangun).

## 4. Spacing & dimensi
Nilai antar-region dan dalam-komponen — token dulu: `space-4 (16px)`.
Hanya cantumkan yang developer tidak dapat dari komponen DS-nya sendiri.

## 5. Warna & tipografi
Tabel: pemakaian → token → nilai resolved. Raw value tanpa token ditandai ⚠️.

## 6. States
Per elemen interaktif: default / hover / focus / pressed / disabled / loading / error / empty.
State yang TIDAK didesain ditulis "belum didesain" — bukan dihilangkan.

## 7. Interaksi & behavior
Apa yang terjadi saat klik/submit/scroll; validasi form (aturan + pesan error);
transisi/animasi (durasi, easing — dari get_motion_context bila ada); keyboard behavior.

## 8. Konten & data
Sumber data tiap teks/angka; format (tanggal, mata uang, pluralisasi); truncation & overflow;
batas karakter; konten fallback.

## 9. Aksesibilitas
Kontras terverifikasi, urutan fokus yang diharapkan, alt/label untuk elemen non-teks, target size.

## 10. Aset
Daftar ikon/gambar untuk diekspor (nama, format, ukuran) — tawarkan `download_assets`.

## 11. Pertanyaan terbuka
Keputusan yang belum diambil desainer — jangan disembunyikan di dalam spec.
```

## Quality bar

- A developer should never need to ask "what happens when…" for the main flows.
- Don't restate what the DS component already defines — link to the component doc instead (or offer `component-doc` mode to create it).
- Offer output as markdown file, or an HTML artifact for shareable specs.
