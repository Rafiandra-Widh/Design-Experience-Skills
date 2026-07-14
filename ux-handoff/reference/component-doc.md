# Mode: component-doc — Design System Component Documentation

Document a component for a design-system site or internal wiki: what it is, its parts, its variants, and how to use it correctly.

## Data gathering

- From the component's Figma URL: `get_metadata` (variant set inventory), `get_design_context` (structure, properties, bound tokens), `get_variable_defs`, `get_screenshot` per key variant.
- `get_code_connect_map` if available — document the code name and props alongside the design name so both audiences share one page.
- Ask: who reads this doc (designers, developers, both)? Existing doc template to match?

## Doc template

```
# [Nama Komponen]
Satu kalimat: apa komponen ini dan kapan dipakai.

## Kapan digunakan / Kapan TIDAK
- Gunakan untuk: ...
- Jangan gunakan untuk: ... → pakai [komponen lain] (tautkan)

## Anatomi
Screenshot dengan bagian bernomor + tabel: # → nama bagian → wajib/opsional → catatan.
Nama bagian harus konsisten dengan nama layer di Figma dan prop di kode.

## Varian & properti
Tabel per property: nama → nilai yang tersedia → default → kapan memakai masing-masing.
(Figma: component properties. Kode: props dari Code Connect bila ada.)

## States
default / hover / focus / active / disabled / loading / error — screenshot atau deskripsi + token yang berubah per state. State yang belum ada di library ditandai.

## Konten
Aturan teks: panjang maksimal, kapitalisasi, nada; perilaku truncation; pluralisasi; ikon apa yang boleh.

## Do / Don't
3–5 pasang, masing-masing dengan visual atau contoh konkret dan SATU alasan singkat.
Ambil dari kesalahan yang benar-benar terjadi bila user bisa menyebutkan.

## Aksesibilitas
Peran semantik (button vs link!), label yang dibutuhkan, perilaku keyboard, kontras minimal antarstate.

## Token yang dipakai
Tabel: bagian → properti → token → nilai resolved.

## Terkait
Komponen serupa + kapan memilih yang mana.
```

## Quality bar

- The "when NOT to use" section is mandatory — it's the part people actually need.
- Every claim about the component must match the actual Figma component (verified via the tools), not the ideal version in someone's head; discrepancies between design intent and the built component are listed as maintenance notes.
- For a batch of components, do one fully, confirm the format, then proceed (or suggest a Workflow fan-out for 10+).
