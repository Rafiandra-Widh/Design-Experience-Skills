# UX Methods Catalog — Knowledge Base

Read before any ux-workshop work. Method recommendations always come from the selection table (§6), justified by goal × time × group size — never by habit.

Format per method: **Tujuan · Kapan · Durasi · Grup · Langkah · Output · Jebakan**. "Grup: solo ✓" means it works with one person (+ Claude as sparring partner).

## 1. Kerangka proses (orientasi, bukan resep sesi)

- **Design Thinking** — Empathize → Define → Ideate → Prototype → Test. Gunakan sebagai peta: mode ideate hidup di "Ideate", converge di "Define/Decide".
- **Double Diamond** — Discover ↔ Define, Develop ↔ Deliver. Kuncinya: dua kali divergen-konvergen; jangan konvergen di diamond pertama dengan metode diamond kedua.
- **Lean UX** — asumsi → hipotesis → eksperimen terkecil. Pasangan alami assumption mapping.
- **Google Design Sprint (5 hari)** — Map / Sketch / Decide / Prototype / Test; Design Sprint 2.0 memadatkan jadi 4 hari. Ambil bloknya (mis. decide-day) tanpa harus 5 hari penuh.
- **Jobs-to-be-Done** — "orang menyewa produk untuk menyelesaikan job"; framing intake yang bagus sebelum ideasi fitur.

## 2. Metode divergen (memperbanyak ide)

| Metode | Tujuan · Kapan | Durasi | Grup | Langkah inti | Jebakan |
|---|---|---|---|---|---|
| **How Might We (HMW)** | Reframe masalah jadi pertanyaan peluang; SELALU langkah pertama sebelum ideasi | 10–15′ | solo ✓ | Ambil masalah/insight → tulis "Bagaimana kita bisa…" → uji lebar: terlalu sempit (sudah berisi solusi) / terlalu lebar (tak bisa dieksekusi) → pilih 1–3 HMW | HMW yang menyelundupkan solusi ("HMW menambah tombol X") |
| **Crazy 8s** | Kuantitas sketsa cepat, memaksa lewat ide pertama yang obvious | 8′ + share 10′ | 1–8, solo ✓ | Lipat kertas jadi 8 / 8 area FigJam → 1 ide per kotak per menit → presentasi 30 detik/ide | Berhenti di 3–4 karena "sudah bagus"; sisanya justru yang menarik |
| **Brainwriting 6-3-5** | Ide tertulis senyap, anti-dominasi vokal | ~30′ | 4–6; solo: 3 ronde × 3 ide dgn Claude | 6 orang × 3 ide × 5 menit → geser kertas → build on ide orang sebelumnya | Peserta menulis variasi idenya sendiri, bukan membangun ide orang lain |
| **SCAMPER** | Membongkar kebuntuan pada solusi/produk EXISTING | 20–30′ | solo ✓ | Jalankan 7 lensa satu per satu: Substitute, Combine, Adapt, Modify/Magnify, Put to other use, Eliminate, Reverse | Melewati lensa yang "tidak relevan" — justru di situ ide non-obvious |
| **Reverse Brainstorm / Worst Idea** | Membuka grup yang takut salah; menemukan asumsi tersembunyi | 15–20′ | 2+, solo ✓ | "Bagaimana membuat pengalaman ini SEBURUK mungkin?" → banjir ide buruk → balikkan tiap ide buruk jadi arah perbaikan | Berhenti di lucu-lucuan tanpa langkah pembalikan |
| **Mind Mapping** | Memetakan ruang masalah/asosiasi sebelum menyempit | 15–20′ | solo ✓ | Topik di tengah → cabang aspek → sub-cabang; tanpa sensor | Rapi-terstruktur terlalu dini; biarkan liar dulu |
| **Starbursting** | Menghasilkan PERTANYAAN, bukan jawaban — bagus saat brief kabur | 15′ | solo ✓ | Bintang 6 sudut: Who/What/When/Where/Why/How → ≥3 pertanyaan per sudut | Menjawab pertanyaan saat masih fase bertanya |
| **Analogous Inspiration** | Ide segar dari domain lain | 20–30′ | solo ✓ | Abstraksikan masalah ("antrian → distribusi beban") → cari domain lain dengan masalah sama (restoran, ATC, game) → curi polanya | Analogi dangkal pada fitur, bukan pada mekanisme |
| **Design Studio / Charrette** | Sketsa paralel + kritik terstruktur, konvergen bertahap | 45–90′ | 3–8 | Ronde: sketch 8′ → present 2′/orang → critique berbasis tujuan → ronde 2 menggabung ide terbaik | Kritik selera ("aku kurang suka") alih-alih berbasis tujuan |
| **Storyboarding** | Menguji ide dalam konteks pengalaman ujung-ke-ujung | 30′ | solo ✓ | 6–8 panel: situasi → trigger → interaksi → hasil; gambar buruk tidak apa-apa | Menggambar UI detail; fokusnya alur cerita |

## 3. Metode konvergen (menyempitkan & memutuskan)

| Metode | Tujuan · Kapan | Durasi | Grup | Langkah inti | Jebakan |
|---|---|---|---|---|---|
| **Affinity Mapping (KJ)** | Tumpukan ide/stickies → tema | 20–45′ | solo ✓ | Senyap: kelompokkan yang "terasa sekeluarga" → BARU beri label tema deskriptif → hitung isi | Membuat kategori dulu baru mengisi (harusnya bottom-up); label generik ("UI", "Lain-lain") |
| **Dot Voting** | Menyaring cepat dengan suara setara | 5–10′ | 3+ | 3–5 dot/orang → tempel senyap → tanpa kampanye; heatmap = varian bebas jumlah | Anchor: orang menempel di yang sudah ramai — tutup nama/urutan acak |
| **Note-and-Vote** | Keputusan cepat tanpa diskusi berputar | 10–15′ | 2+ | Tulis senyap → tempel → vote senyap → decider memutuskan dari top vote | Membuka diskusi sebelum vote |
| **Impact × Effort (2×2)** | Prioritisasi default saat tak ada data kuantitatif | 15–30′ | solo ✓ | Sumbu dampak × usaha → tempatkan per item DENGAN justifikasi 1 baris → kuadran quick-win dulu | Semua ditaruh "high impact low effort" — paksa relatif, bukan absolut |
| **MoSCoW** | Scope release/proyek | 15–30′ | solo ✓ | Must/Should/Could/Won't (eksplisit Won't!) | Won't kosong = belum memutuskan apa-apa |
| **RICE / ICE** | Prioritisasi dengan data (jangkauan/keyakinan) | 30′+ | solo ✓ | Reach × Impact × Confidence ÷ Effort; ICE tanpa reach | Angka presisi palsu — pakai skala kasar (1/2/4/8) |
| **$100 Test** | Memaksa trade-off nyata | 10′ | 2+ | Tiap orang membagi $100 ke opsi; jumlah dibandingkan | Pembagian rata ($10 ke semua) = menolak memilih |
| **Kano** | Memilah fitur wajib vs pembeda vs delighter | riset | tim | Survey functional/dysfunctional per fitur → klasifikasi basic/performance/exciter | Butuh data user asli — tanpa itu jadi tebakan berlabel Kano |

## 4. Format workshop siap pakai

| Format | Tujuan | Durasi | Struktur blok |
|---|---|---|---|
| **Lightning Decision Jam (LDJ)** | Dari "ada banyak masalah" → solusi terprioritas, nyaris tanpa diskusi terbuka | 60–90′ | Yang jalan baik 5′ → masalah senyap 7′ → pilih masalah (vote 5′) → reframe HMW 5′ → solusi senyap 7′ → vote solusi 5′ → 2×2 effort/impact 10′ → komit next steps 5′ |
| **Discovery / Kickoff** | Menyamakan pemahaman awal proyek | 2–4 jam | Hopes & fears → konteks/brief → proto-persona → success metrics → assumption mapping → HMW awal → next steps |
| **Assumption Mapping** | Memilih asumsi yang diuji dulu | 45–60′ | Dump asumsi (desirability/viability/feasibility) → plot penting × bukti → kuadran "penting & tanpa bukti" = eksperimen berikutnya |
| **Journey Mapping session** | Menyamakan gambaran pengalaman user | 2–3 jam | Persona & skenario → tahapan → doing/thinking/feeling per tahap → pain & peluang → vote fokus |
| **Empathy Map workshop** | Cepat menyamakan gambaran user (proto) | 30–45′ | Says/Thinks/Does/Feels dari data yang ada → gap pengetahuan → pertanyaan riset |
| **Retro** | Perbaikan proses tim | 45–60′ | Start-Stop-Continue atau 4Ls (Liked/Learned/Lacked/Longed for) → vote → action items ber-owner |
| **World Café** | Grup besar (>12) membahas beberapa topik | 60–90′ | Meja per topik, ronde 15–20′, host meja tetap, peserta berpindah; panen antar-ronde |

## 5. Sintesis proses desain (rantai bahan mentah → keputusan)

- **Rantai baku**: data/stickies → *affinity* → **insight statement** (temuan + kenapa penting, bukan observasi mentah) → **POV/problem statement** ("[User] butuh [kebutuhan] karena [insight]") → **HMW** → ideasi.
- **Opportunity Solution Tree** (Teresa Torres) — outcome bisnis di puncak → peluang (dari riset) → solusi per peluang → eksperimen per solusi. Bagus untuk menautkan ide-ide liar ke outcome.
- **Assumption → Hypothesis** — "Kami percaya [X]; kami tahu benar bila [sinyal terukur]" — jembatan dari ide terpilih ke eksperimen (Lean UX).
- **Design Principles** — 3–5 prinsip produk yang lahir dari tema riset ("Jujur soal durasi" ala Masakmemasak); dipakai sebagai kriteria kurasi ide.

## 6. Tabel pemilihan — gejala situasi → metode

| Situasi | Mulai dengan | Lalu |
|---|---|---|
| Masalah belum terdefinisi / brief kabur | Starbursting atau Empathy Map | HMW |
| Kickoff proyek, tim belum sepakat arah | Discovery workshop | Assumption Mapping |
| Butuh banyak ide cepat (tim) | HMW → Crazy 8s | Dot voting |
| Butuh ide tapi peserta pendiam / ada yang dominan | Brainwriting 6-3-5 | Note-and-Vote |
| Ide mentok / itu-itu saja pada produk existing | SCAMPER atau Reverse Brainstorm | Analogous Inspiration |
| Solo, butuh sparring partner | HMW → brainwriting bergantian dengan Claude | 2×2 |
| Banyak ide, buntu memilih | Affinity Mapping | Dot voting / 2×2 |
| Diskusi tim berputar-putar tanpa keputusan | Lightning Decision Jam | — |
| Harus memilih fitur untuk release | MoSCoW (ada deadline) / RICE (ada data) | — |
| Banyak asumsi belum teruji | Assumption Mapping | Hypothesis + eksperimen |
| Ide terpilih, mau divalidasi konteksnya | Storyboarding | ux-design flow |
| Grup > 12 orang | World Café | Panen → affinity |

**Timebox adalah alat, bukan hiasan** — sebut durasi setiap blok, tepati, dan ingatkan sisa waktu di tengah blok.
