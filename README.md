# Panduan Skill UX — ux-design · ux-research · ux-handoff · ux-voice

Empat skill Claude Code untuk alur kerja UI/UX lengkap: riset → desain → komunikasi → serah terima ke developer. Generik — bisa dipakai di proyek dan design system apa pun.

## Instalasi (untuk mesin baru)

1. **Pasang Claude Code** (CLI, desktop app, atau claude.ai/code) dan login.
2. **Hubungkan Figma** (untuk mode yang membaca/menulis Figma): pasang plugin resmi `figma@claude-plugins-official` dari marketplace plugin Claude Code, lalu login akun Figma saat diminta.
3. **Ambil skill-nya** — clone dari GitHub lalu salin ke `~/.claude/skills/`:
   ```
   git clone https://github.com/Rafiandra-Widh/Design-Experience-Skills.git
   cp -R Design-Experience-Skills/ux-* ~/.claude/skills/
   ```
   (Atau salin manual 4 folder `ux-design/ ux-research/ ux-handoff/ ux-voice/`.) Tidak ada setting lain — skill terdeteksi otomatis di sesi berikutnya.
4. Cek: ketik `/ux-` di Claude Code — keempat skill muncul di autocomplete.
5. *(Opsional tapi sangat disarankan)* **Isi taste profile** — salin `design-taste.template.md` ke `~/.claude/design-taste.md`, lalu minta Claude mengisinya dari screenshot UI favorit / moodboard Figma / daftar produk yang Anda kagumi. Mode desain membacanya setiap kali bekerja — inilah yang membuat hasilnya terasa seperti selera Anda, bukan rata-rata AI.

## Dua cara memakai

**A. Perintah eksplisit** — paling pasti:
```
/ux-handoff spec https://figma.com/design/<fileKey>/Nama-File?node-id=12-345
/ux-research plan
/ux-design critique
```

**B. Bahasa natural** — skill terpicu otomatis dari kalimat biasa:
- "review desain ini dong" → ux-design (critique)
- "buatkan interview guide untuk riset app kasir" → ux-research (plan)
- "siapkan spek developer dari frame ini" → ux-handoff (spec)
- "gimana bahasa profesionalnya: 'tombolnya gak keliatan jadi gak tau itu primary'" → ux-voice (quick)

## Peta 17 mode — kapan pakai apa, dapat apa, di mana

| Perintah | Kapan dipakai | Siapkan | Output & lokasi |
|---|---|---|---|
| `/ux-research plan` | Mau mulai riset: interview/usability test | Konteks produk & keputusan yang mau didukung | Research plan + screener + guide → file .md |
| `/ux-research benchmark` | Riset kompetitor / pola desain | Nama kompetitor (atau minta diusulkan) | Analisis bersumber URL → file .md |
| `/ux-research synthesize` | Sudah punya catatan/transkrip riset | Paste transkrip atau path file/foldernya | Insight berbukti → file .md + **insight board di Figma** |
| `/ux-research artifacts` | Butuh persona / journey map / JTBD | Hasil sintesis (atau tanpa data → dilabeli asumsi) | File .md + **kartu persona & journey map di Figma** |
| `/ux-research a11y` | Audit aksesibilitas WCAG | URL frame Figma ber-`node-id` ATAU URL halaman live | Laporan audit → file .md |
| `/ux-design flow` | Mendesain screen/fitur baru dari nol | Brief singkat (siapa usernya, platform, batasan) | User flow + wireframe + hi-fi → **Figma** (flow juga .md) |
| `/ux-design critique` | Minta review desain | URL frame / screenshot / halaman live | Temuan berperingkat + rekomendasi → chat/.md |
| `/ux-design explore` | Butuh beberapa arah visual | Brief + rasa yang diinginkan | 3 board arah + rekomendasi → **Figma** |
| `/ux-design foundation` | Menyusun/merapikan design token | Warna brand (bila ada), format target | **Figma variables** + tokens.css |
| `/ux-handoff readiness` | Cek frame sebelum diserahkan ke dev | URL frame ber-`node-id` | Skor + daftar perbaikan → chat + kartu di Figma |
| `/ux-handoff annotate` | Menulis catatan untuk dev di Figma | URL frame (idealnya sudah lolos readiness) | **Anotasi Dev Mode** kategori UX & Development + marker |
| `/ux-handoff spec` | Spek developer dari desain | URL frame ber-`node-id` | Spek lengkap → file .md |
| `/ux-handoff component-doc` | Dokumentasi komponen design system | URL komponen di Figma | Dokumentasi → file .md |
| `/ux-voice` (quick) | Kalimat awam soal masalah UI → kalimat profesional | Kalimat awamnya saja | Terjemahan 🇮🇩+🇬🇧 + prinsip UX → chat |
| `/ux-voice full` | Butuh semua varian untuk beberapa channel | Kalimat awam | + 3 tone (designer/dev/stakeholder) + format critique → chat |
| `/ux-voice critique` | Observasi mau jadi design critique formal | Kalimat awam (+ konteks screen bila ada) | Observasi → Dampak → Rekomendasi → Severity → chat |
| `/ux-voice coach` | Latihan bicara seperti senior designer | Kalimat awam | Terjemahan + bedah kenapa + 1 latihan → chat |

**Konvensi lokasi output**: visual → Figma (page proyek) · dokumen → folder proyek (mis. `~/nama-proyek-ux/`) · ringkasan → chat · halaman review → artifact (link bisa dibagikan).

## Yang akan Claude tanyakan (jangan kaget — skill ini interaktif)

- **Intake di awal**: target user, platform, batasan — jawab singkat saja.
- **Checkpoint** di mode `flow`: persetujuan user flow → wireframe → baru hi-fi. Di mode `explore`: kamu memilih 1 dari 3 arah.
- **Konfirmasi sebelum menulis ke file Figma-mu** (annotate, perbaikan otomatis) — tidak pernah menulis diam-diam.
- Aturan yang tidak bisa dibaca dari desain (batas item, format angka, threshold warna) **ditanyakan, bukan dikarang** — jawaban "tergantung desain" membuat aturan ditandai ⚠️ asumsi.

## Tiga contoh sesi

**1. Cek kesiapan handoff** — salin URL frame dari Figma (klik kanan frame → Copy link):
```
/ux-handoff readiness https://figma.com/design/<fileKey>/File?node-id=33-2
```
Claude membaca metadata/token/komponen frame → laporan skor (mis. 17/21) + daftar 🔴/🟡. Lanjutan umum: "tulis temuannya sebagai anotasi" → masuk Dev Mode dengan kategori UX/Development.

**2. Sintesis riset** — punya 5 transkrip interview:
```
/ux-research synthesize
(paste transkrip, atau: "filenya di ~/riset-kasir/transkrip/")
```
Claude mengkode → tema → insight (tiap insight ada kutipan bukti + kekuatan bukti "4/6 peserta") → rekomendasi. Output .md + insight board di Figma.

**3. Desain dari nol**:
```
/ux-design flow — app pencatat stok untuk warung, mobile, user = pemilik warung usia 30–55
```
Claude bertanya intake → user flow (disetujui dulu) → wireframe (disetujui) → hi-fi dengan token & komponen + garis alur antar-screen.

## Aturan tetap yang dijamin skill

- Angka/warna di spek & audit **selalu dari data Figma asli** — tidak pernah menebak dari screenshot.
- Kontras warna **dihitung**, bukan dikira-kira.
- Data riset tidak pernah dikarang; artefak tanpa data diberi label "proto — perlu divalidasi".
- Anotasi Figma: bahasa sederhana, terpisah kategori **UX** (maksud) dan **Development** (aturan teknis).
- Menulis ke Figma selalu lewat konfirmasi, di container terpisah yang terkunci — desain asli tidak disentuh.
- ux-voice **tidak pernah mengubah substansi observasi** — hanya menaikkan register; kalau observasinya lemah secara UX, dikatakan terang-terangan, bukan dikoreksi diam-diam.

---
*Dibangun & diuji penuh 14 Jul 2026 (demo: proyek Masakmemasak). Untuk menambah mode: tambah file di `reference/` + satu baris routing di `SKILL.md` skill terkait.*
