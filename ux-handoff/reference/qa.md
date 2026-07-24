# Mode: qa — Implementation vs Figma (Pixel-Perfect Audit)

Compare implemented UI against its Figma design and report exactly where they diverge — both sides read from real data, never eyeballed.

## Intake

- URL frame Figma ber-`node-id` (source of truth desain).
- Bentuk implementasi (bisa lebih dari satu, saling melengkapi): URL live/localhost (path A — paling akurat), path screenshot (path B), path repo/file komponen (path C).
- Toleransi: default **≤1px = lolos** (tetap dicatat, tidak dihitung pelanggaran); user bisa perketat/perlonggar.
- Breakpoint yang harus dicek (bila desain punya frame per breakpoint) dan scope: screen penuh atau komponen tertentu.

## Ground truth Figma

Sama seperti spec mode: `get_metadata` → `get_design_context` → `get_variable_defs` → `get_screenshot`. Nilai desain SELALU dari data Figma; kalau sebuah nilai gagal diambil, tulis "tidak tersedia dari Figma" — jangan diisi dari render.

## Input path A — Web live/localhost (paling akurat)

1. Load `claude-in-chrome`; buka halaman, samakan viewport dengan lebar frame desain (`resize_window`).
2. Petakan elemen DOM ↔ node Figma, lalu per elemen ambil via `javascript_tool`: `getComputedStyle` (font-family/size/weight/line-height, color, background, border-radius, padding, gap/margin, border) + `getBoundingClientRect` (ukuran & posisi). Normalisasi sebelum membandingkan: rgb→hex, unitless line-height→px.
3. **States**: baca CSS rules `:hover`/`:focus`/`:disabled` dari stylesheet, dan/atau trigger nyata (fokus keyboard, submit form salah untuk error state). State yang ada di desain tapi tidak ditemukan di implementasi = temuan kategori sendiri ("state hilang"), bukan selisih nilai.
4. **Responsive**: `resize_window` ke tiap breakpoint yang punya frame desain → ulangi cek elemen kunci terhadap frame breakpoint itu.

## Input path B — Screenshot implementasi

Perbandingan visual screenshot vs `get_screenshot` frame Figma pada skala sama. Batasannya dikatakan jujur di laporan:
- Selisih dilaporkan sebagai **estimasi visual** ("±2px"), TIDAK masuk skor properti; **path B tidak menghasilkan skor angka**.
- Hanya deviasi jelas yang jadi temuan: ≥3–4px, warna/font family beda kasat mata, elemen hilang/tambah.
- States & responsive tidak bisa dicek dari satu screenshot — tulis "tidak tercakup", jangan dihilangkan diam-diam.

## Input path C — Source code

Baca file komponen/CSS yang ditunjuk user (atau temukan via Grep dari nama komponen/selector). Bandingkan **tiga level** per properti:
1. Nilai akhirnya benar?
2. Pakai token design system atau hardcoded?
3. Tokennya yang BENAR? (nilai kebetulan sama ≠ token benar)

Path C menangkap kelas temuan yang tak terlihat dari path A: "visual benar tapi token salah" (`#1A1A1B` hardcoded vs `var(--color-text)`) — pelanggaran maintainability meski pixel cocok. Path C melengkapi path A, bukan menggantikan.

## Severity rubric

- **🔴** layout rusak / komponen atau state hilang / warna beda peran (warning dipakai untuk error) / font family beda
- **🟡** selisih 2–4px / weight atau line-height beda / warna beda nilai dalam peran sama / token salah meski nilai benar (path C)
- **🟢** selisih ≤2px di atas toleransi / pembulatan / minor
- **✅** cocok — dihitung untuk skor

## Skor kesesuaian

`properti cocok ÷ properti dicek` per screen — denominatornya jujur: hanya properti yang benar-benar dibandingkan, dan cakupannya disebut eksplisit ("48 properti pada 12 elemen; states & breakpoint md tidak dicek karena X"). Skor tanpa pernyataan cakupan menyesatkan.

## Honesty & drift rules

- Dua sisi dari data: implementasi dari computed styles/kode, desain dari data Figma. Estimasi visual hanya di path B, selalu berlabel.
- **Desain juga bisa salah/usang.** Mismatch yang sistematis (seluruh halaman memakai nilai token versi lebih baru, spacing konsisten beda 8px di semua region) → tanyakan mana source of truth sebelum memvonis; labeli "⚠️ kemungkinan design drift". QA yang menyalahkan implementasi padahal desainnya yang belum di-update menghancurkan kepercayaan dev.
- Elemen implementasi tanpa padanan node Figma (atau sebaliknya) = temuan struktural tersendiri.

## Output (urutan produksi)

1. **Laporan diff** — .md di folder proyek:

````
# QA Pixel-Perfect: [screen] — [tanggal]
**Skor**: [N% — X/Y properti cocok] · **Cakupan**: [elemen, states, breakpoint yang dicek & yang tidak + alasannya]
**Toleransi**: ≤[N]px · **3 temuan terpenting**: ...

| Elemen | Properti | Desain (token · nilai) | Implementasi | Selisih | Severity | Fix |
|---|---|---|---|---|---|---|
````

2. **Fix list untuk dev** — temuan dikelompokkan per file/komponen (path C) atau per elemen/selector (path A), nilai benar siap tempel (`padding: 16px → 24px (space-6)`), blok siap di-copy ke ticket.
3. **Anotasi QA di Figma** — tawarkan tulis balik via mekanisme annotate mode (load `figma-use`, konfirmasi dulu; seluruh placement & plain-language rules annotate.md berlaku): marker 🔴/🟡 di node terkait + legend card `🧪 QA — [tanggal]`, temuan dipetakan seperti §Feeding from other modes; catatan teknis pakai kategori Dev Mode "Development".
4. **Halaman side-by-side** — HTML artifact: screenshot Figma vs implementasi berdampingan per screen + tabel temuan + skor — untuk dibahas bareng dev.

Tutup dengan langkah lanjut: fix di sisi kode → serahkan fix list; desainnya yang drift → update desain lalu `readiness`; audit ulang setelah perbaikan untuk skor baru.
