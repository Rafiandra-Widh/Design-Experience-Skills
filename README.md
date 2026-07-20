# Panduan Skill UX — ux-design · ux-research · ux-handoff · ux-voice · ux-motion · ux-workshop · ux-metrics

Tujuh skill Claude Code untuk alur kerja UI/UX lengkap: riset → ideasi & keputusan → desain → motion & prototype → komunikasi → serah terima ke developer → pengukuran & OKR. Generik — bisa dipakai di proyek dan design system apa pun.

## Instalasi (untuk mesin baru)

1. **Pasang Claude Code** (CLI, desktop app, atau claude.ai/code) dan login.
2. **Hubungkan Figma** (untuk mode yang membaca/menulis Figma): pasang plugin resmi `figma@claude-plugins-official` dari marketplace plugin Claude Code, lalu login akun Figma saat diminta.
3. **Ambil skill-nya** — clone dari GitHub lalu salin ke `~/.claude/skills/`:
   ```
   git clone https://github.com/Rafiandra-Widh/Design-Experience-Skills.git
   cp -R Design-Experience-Skills/ux-* ~/.claude/skills/
   ```
   (Atau salin manual 7 folder `ux-design/ ux-research/ ux-handoff/ ux-voice/ ux-motion/ ux-workshop/ ux-metrics/`.) Tidak ada setting lain — skill terdeteksi otomatis di sesi berikutnya.
4. Cek: ketik `/ux-` di Claude Code — ketujuh skill muncul di autocomplete.
5. *(Opsional tapi sangat disarankan)* **Isi taste profile** — salin `design-taste.template.md` ke `~/.claude/design-taste.md`, lalu minta Claude mengisinya dari screenshot UI favorit / moodboard Figma / daftar produk yang Anda kagumi. Mode desain membacanya setiap kali bekerja — inilah yang membuat hasilnya terasa seperti selera Anda, bukan rata-rata AI.

## Dua cara memakai

**A. Perintah eksplisit** — paling pasti:
```
/ux-handoff spec https://figma.com/design/<fileKey>/Nama-File?node-id=12-345
/ux-research plan
/ux-design critique
```

**B. Bahasa natural** — skill terpicu otomatis dari kalimat biasa. Tidak perlu hafal nama skill atau mode; cukup tulis niatnya. Daftar lengkap kata kunci pemicu per skill ada di bagian berikutnya.

## Kata kunci pemicu & contoh pemakaian per skill

Claude mencocokkan *niat* kalimatmu, bukan kata persis — kata-kata di bawah adalah contoh yang paling andal memicu skill yang benar. Kalau ragu skill mana yang terpicu, pakai perintah eksplisit `/nama-skill mode`.

### 🎨 ux-design — mendesain & mengkritik visual

- **Kata pemicu**: "desain…", "rancang…", "bikin screen/halaman…", "review desain", "kritik tampilan", "audit visual", "eksplorasi arah visual", "moodboard", "alternatif desain", "buat design token", "fondasi visual", "type scale"
- **Contoh kalimat** → mode yang terpicu:
  - "rancang halaman onboarding untuk app kasir, mobile" → `flow` (intake → user flow → wireframe → hi-fi, ada checkpoint persetujuan di tiap tahap)
  - "review desain ini dong" + URL frame/screenshot → `critique`
  - "kasih 3 arah visual buat landing page kopi ini" → `explore`
  - "rapikan token warna & spacing file ini" → `foundation`
- **Siapkan**: brief singkat (siapa user, platform) untuk flow; URL frame ber-`node-id` untuk critique (klik kanan frame di Figma → Copy link).

### 🔍 ux-research — riset pengguna

- **Kata pemicu**: "riset…", "wawancara / interview guide", "usability test / uji kegunaan", "screener", "sintesis", "olah transkrip", "analisis hasil interview", "persona", "journey map", "JTBD", "benchmark", "riset kompetitor", "audit aksesibilitas", "cek WCAG", "a11y"
- **Contoh kalimat** → mode:
  - "buatkan interview guide untuk riset app kasir" → `plan`
  - "ini 5 transkrip interview, tarik insight-nya" → `synthesize`
  - "bikin persona dan journey map dari hasil sintesis kemarin" → `artifacts`
  - "bandingkan pola checkout Tokopedia vs Shopee" → `benchmark`
  - "audit aksesibilitas halaman ini" + URL → `a11y`
- **Siapkan**: konteks produk + keputusan yang mau didukung (plan); paste transkrip atau path foldernya (synthesize).

### 📦 ux-handoff — serah terima ke developer

- **Kata pemicu**: "handoff", "serah terima", "spek untuk dev", "spesifikasi frame ini", "dokumentasi komponen", "anotasi", "redline", "catatan interaksi", "cek kesiapan frame", "audit sebelum handoff"
- **Contoh kalimat** → mode:
  - "siapkan spek developer dari frame ini" + URL → `spec`
  - "cek dulu frame ini siap di-handoff atau belum" + URL → `readiness`
  - "tulis anotasi untuk dev di frame checkout" + URL → `annotate` (menulis ke Figma Dev Mode, selalu konfirmasi dulu)
  - "buat dokumentasi komponen Button ini" + URL → `component-doc`
- **Siapkan**: URL frame ber-`node-id` — semua angka diambil dari data Figma asli, bukan tebakan visual.

### 🗣️ ux-voice — bahasa profesional product design

- **Kata pemicu**: "terjemahkan ke bahasa profesional", "gimana bahasa profesionalnya…", "rapikan feedback ini", "gimana senior designer bilang ini", "jadikan design critique", "latih aku ngomong kayak senior"
- **Contoh kalimat** → mode:
  - "gimana bahasa profesionalnya: 'tombolnya gak keliatan jadi gak tau itu primary'" → `quick` (terjemahan 🇮🇩+🇬🇧 + prinsip)
  - "rapikan feedback ini untuk 3 audiens: designer, dev, stakeholder" → `full`
  - "jadikan kalimat ini design critique formal" → `critique`
  - "latih aku menyampaikan temuan kayak senior" → `coach`
- **Siapkan**: cukup kalimat awamnya — boleh beberapa sekaligus (di-batch per kalimat). Substansi observasimu tidak pernah diubah, hanya registernya.

### 🎬 ux-motion — prototype & motion interaction

- **Kata pemicu**: "prototype", "sambungkan frame", "bikin bisa diklik", "smart animate", "cek motion", "audit animasi/transisi", "transisinya kok aneh", "usulkan motion", "animasi apa yang cocok", "biar terasa hidup"
- **Contoh kalimat** → mode:
  - "sambungkan frame-frame ini jadi prototype yang bisa diklik" → `prototype` (reactions ditulis ke Figma; kamu verifikasi rasa lewat tombol ▶ Play)
  - "cek animasi di app ini, kok terasa aneh" + URL Figma/web/path video → `audit`
  - "usulkan motion buat layar feed ini biar terasa hidup" + URL → `propose` (spec + keyframes di Figma + demo HTML)
- **Siapkan**: daftar koneksi frame A → frame B (prototype); URL Figma / URL web live / path rekaman (audit). Catatan jujur: Claude memverifikasi wiring & nilai animasi lewat data, tapi *rasa* motion tetap kamu cek dengan menekan Play — screenshot tidak menampilkan gerakan.

### 🧠 ux-workshop — brainstorming, workshop & sintesis keputusan

- **Kata pemicu**: "brainstorm / ideasi / cari ide", "aku mentok", "rancang workshop", "bikin agenda sesi", "lightning decision jam", "kelompokkan ide-ide ini", "affinity mapping", "bantu milih / prioritas", "sintesis hasil workshop", "metode apa yang cocok untuk…"
- **Contoh kalimat** → mode:
  - "bantu aku brainstorm fitur untuk halaman simpanan" → `ideate` (HMW dulu, lalu metode yang pas; solo pun bisa — Claude jadi sparring partner, idenya berlabel)
  - "rancang workshop 90 menit supaya tim sepakat prioritas Q3" → `workshop` (agenda menit-per-menit + facilitator script + board FigJam template)
  - "ini stickies hasil sesi kemarin, kelompokkan dan bantu pilih" + URL FigJam → `converge` (affinity → 2×2 → keputusan, ditulis balik ke board)
  - "tim ku suka debat muter-muter, metode apa yang cocok?" → `method-finder`
- **Siapkan**: topik/masalah (ideate); tujuan sesi + durasi + jumlah peserta (workshop); URL board FigJam atau paste ide (converge).

### 📊 ux-metrics — UX metric, dampak bisnis & KPI/OKR

- **Kata pemicu**: "metric apa yang cocok", "ukuran keberhasilan", "success metrics", "HEART", "hubungkan ke business metric", "dampak bisnis", "metric tree", "north star", "cara ngukur", "measurement plan", "instrumentasi", "baseline", "turunkan OKR", "KPI tim desain", "key result"
- **Contoh kalimat** → mode:
  - "metric apa yang cocok buat fitur onboarding app kasir?" → `identify` (HEART + Goals-Signals-Metrics → 1 metric primer + sekunder + guardrail)
  - "hubungkan task success checkout ke revenue dong" → `connect` (metric tree dengan rantai hipotesis berlabel bukti + narasi stakeholder)
  - "gimana cara ngukur adoption rate fitur ini?" → `measure` (formula operasional + event/survey yang dibutuhkan + baseline & target)
  - "turunkan OKR tim desain dari OKR perusahaan Q3 ini" → `okr` (level lead: Objective + KR berbasis metric + guardrail + KPI berkelanjutan)
- **Siapkan**: goal produk/fitur & keputusan yang mau didukung (identify); business metric yang penting bagi stakeholder (connect); akses data yang ada — analytics/survey (measure); OKR perusahaan/departemen di atasnya, disalin persis (okr). Catatan jujur: baseline & benchmark tidak pernah dikarang — kalau datanya belum ada, langkah pertamanya "ukur baseline dulu".

## Peta 28 mode — kapan pakai apa, dapat apa, di mana

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
| `/ux-motion prototype` | Merangkai alur klik antar frame Figma | Daftar koneksi (frame A → frame B) atau user flow .md | **Reactions di Figma** — di komponen spesifik (via invisible hotspot bila tombol ada di dalam instance) atau klik-di-mana-pun untuk walkthrough + tabel koneksi → chat |
| `/ux-motion audit` | Mengecek motion/interaksi yang sudah ada | URL Figma / URL web live / path video-GIF | Temuan berperingkat severity + nilai perbaikan konkret → chat/.md |
| `/ux-motion propose` | Desain statis → usulan motion interaction | URL frame Figma / screenshot + konteks produk | Motion spec .md + **keyframes/prototype di Figma** + demo HTML |
| `/ux-workshop ideate` | Brainstorming difasilitasi (solo/tim) | Masalah/topik (diubah jadi HMW dulu) | Daftar ide → **stickies FigJam** dan/atau .md |
| `/ux-workshop workshop` | Merancang paket sesi tim | Tujuan + durasi + peserta | Agenda + facilitator script .md + **board FigJam template** |
| `/ux-workshop converge` | Tumpukan ide/stickies → tema & keputusan | URL board FigJam / paste ide | Affinity + prioritas + keputusan → .md + **section Hasil Sintesis di board** |
| `/ux-workshop method-finder` | "Metode apa yang cocok untuk situasiku?" | Deskripsi situasi | Rekomendasi metode + alasan + resep singkat → chat |
| `/ux-metrics identify` | Menentukan UX metric untuk produk/fitur | Goal produk/fitur + keputusan yang mau didukung | Tabel GSM + metric primer/sekunder/guardrail → chat/.md |
| `/ux-metrics connect` | Memetakan UX metric → business metric | Business metric stakeholder + metric hasil identify | Metric tree (mermaid) berlabel bukti + narasi stakeholder → .md + **FigJam** (opsional) |
| `/ux-metrics measure` | Rencana pengukuran metric | Metric yang mau diukur + akses data yang ada | Measurement plan: formula, event/survey, baseline, target, cadence → file .md |
| `/ux-metrics okr` | Lead: turunkan KPI/OKR tim desain | OKR perusahaan/departemen + metric tim | Objective + KR (baseline→target) + guardrail + tabel KPI → file .md |

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
- ux-motion: setiap animasi wajib punya purpose (feedback/orientation/status/delight, delight maksimal 1 signature moment per flow), selalu menyertakan perilaku `prefers-reduced-motion`, dan nilai durasi/easing selalu konkret — screenshot tidak pernah dipakai sebagai bukti motion (verifikasi via readback data + kamu menekan Play).
- ux-workshop: divergen dan konvergen tidak pernah dicampur dalam satu blok; ide Claude selalu berlabel `[Claude]` dan maksimal ±sepertiga; affinity transparan (ide tak terkelompok masuk "Parkir", tidak dibuang); **vote tidak pernah dikarang** — penempatan tanpa vote dinyatakan sebagai penilaian Claude yang boleh dibantah.
- ux-metrics: **angka tidak pernah dikarang** — baseline diukur, bukan ditebak; target awal & benchmark tanpa sumber dilabeli "asumsi — perlu divalidasi"; hubungan UX→business selalu ditulis sebagai hipotesis berlabel bukti (terbukti/hipotesis/asumsi), bukan fakta; metric & KR wajib outcome (perubahan perilaku/hasil), bukan output (deliverable).

---
*Dibangun & diuji penuh 14 Jul 2026 (demo: proyek Masakmemasak). Untuk menambah mode: tambah file di `reference/` + satu baris routing di `SKILL.md` skill terkait.*
