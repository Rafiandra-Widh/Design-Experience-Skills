# Mode: artifacts — Persona, Journey Map, JTBD, Service Blueprint

Build research artifacts from existing data. Artifact choice follows the question the team is asking.

## Data-grounding rule (applies to all artifacts)

Ask for the underlying data first (synthesis output, transcripts, analytics). If none exists, you may still build the artifact but it MUST be titled **"Proto-[artifact] — berbasis asumsi, perlu divalidasi"**, with an explicit list of the assumptions and a suggestion to validate via `plan` mode. Never present an assumed artifact as researched.

## Persona

- Segment by **behavior and goals**, not demographics. Two users with the same age/job but different workflows are different personas; the reverse are one.
- 2–4 personas max; more means segmentation is too thin to be actionable.
- Template per persona: name + role tagline / goal utama (1–2) / perilaku kunci (bagaimana mereka bekerja sekarang, tools, workaround) / pain points (dengan bukti) / kebutuhan terhadap produk / kutipan khas / tingkat kepercayaan data (tinggi = dari riset, rendah = asumsi).
- Skip filler: no invented hobbies, stock-photo vibes, or "tech-savviness: 7/10" meters unless they change a design decision.

## Journey map

- One journey = one persona attempting one goal, end to end (including before/after using the product).
- Columns = tahapan; rows = **aksi / pikiran / emosi (kurva) / pain point / peluang / titik kontak (channel)**.
- Pain points carry evidence refs (P3, analytics, quote). Opportunities phrased as "How might we…".
- Mark the **moment of truth** — the stage where the journey most often fails or is won.
- Output: markdown table by default; offer FigJam version (load `figma-use-figjam`) or HTML artifact for a shareable visual.

## JTBD

- Format: **Ketika** [situasi], **saya ingin** [motivasi/progress], **sehingga** [hasil yang diharapkan].
- Jobs are solution-free: "menyimpan uang tanpa tergoda memakainya" ✅, "punya fitur kunci tabungan" ❌.
- For each main job list: functional / emotional / social dimensions, current workaround, and hiring criteria (what makes them switch).

## Service blueprint

- Rows: **bukti fisik/digital → aksi pengguna → frontstage (yang dilihat user) → backstage (staf/sistem di belakang) → proses pendukung**, aligned per journey stage.
- Mark failure points and waiting lines (delays between layers).
- Use when the pain lives in operations/handoffs, not in a single screen — say so if a journey map would serve better.

## Figma output (dual-output rule — SKILL.md rule 6)

Artifacts also get rendered as Figma boards (load `figma-use` first), neutral board styling like exploration boards:
- **Persona** → one card frame per persona: name + tagline header, then rows for goals / key behaviors / pain points (with evidence refs) / needs / signature quote / data-confidence chip (🔴 asumsi · 🟡 sebagian · 🟢 riset). Proto-personas carry the "perlu divalidasi" label ON the card.
- **Journey map** → grid frame: columns = stages, rows = aksi / pikiran / emosi / pain / peluang; mark the moment-of-truth column with an accent border or ⚡ chip. Auto-layout row-of-columns so cells stay aligned.
- **JTBD / blueprint** → stacked statement cards / swimlane rows.
- Place in the research area of the project's Figma page, never overlapping design frames.

## Choosing (guide the user if they picked the wrong artifact)

- "Siapa user kita?" → persona
- "Di mana pengalaman rusak?" → journey map
- "Kenapa orang memakai/meninggalkan produk?" → JTBD
- "Kenapa layanan gagal walau UI-nya baik?" → service blueprint
