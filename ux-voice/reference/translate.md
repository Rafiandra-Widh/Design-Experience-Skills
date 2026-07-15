# Modes: quick / full / critique — Translation Workflows

Prerequisite: `voice-guide.md` is loaded. All output follows its register rules (§1), dictionary (§2), principles (§3), tones (§4), severity (§5).

## Workflow (all three modes)

1. **Parse** the casual sentence: what element, what screen/context, what symptom. If element/screen is missing AND the translation would differ meaningfully, ask ONE short question; otherwise use a neutral placeholder ("elemen ini", "this element") and proceed.
2. **Map** the symptom to the dictionary (§2) → professional terminology + principle. If no dictionary entry fits, construct from the anatomy (§1): observation → impact → recommendation.
3. **Sanity-check the substance.** If the observation is UX-weak or wrong (e.g. complaining that a destructive action HAS a confirmation), keep the translation but add a short honest note: "Catatan: secara prinsip UX, …" and offer the stronger framing.
4. **Render** in the mode's format below.

## Format: `quick` (default)

```
📝 Asli: <kalimat user>

🇮🇩 <kalimat profesional Indonesia>
🇬🇧 <professional English sentence>

💡 Prinsip: <nama prinsip> — <1 baris kenapa relevan>
```

Keep it tight — no preamble, no extra commentary unless step 3 triggered a note.

## Format: `full`

Quick format, plus:

```
🎯 Varian tone
- Sesama designer : <ID version — full terminology, token-level fix>
- Developer       : <ID version — concrete change + acceptance criteria + 1-line rationale>
- Stakeholder     : <ID version — impact-first, no jargon, one clear ask>

📋 Format critique
Observasi   : …
Dampak      : …
Rekomendasi : …
Severity    : <emoji + level + 1 clause why this level>
```

Tone variants are Indonesian by default; add English on request. The three variants must differ in framing, not just word swaps (see voice-guide §4).

## Format: `critique`

Only the critique block (plus the bilingual headline sentence on top):

```
🇮🇩 <kalimat profesional Indonesia>
🇬🇧 <professional English sentence>

Observasi   : <elemen + konteks + apa yang terjadi>
Dampak      : <konsekuensi ke user/bisnis, hedged bila belum teruji>
Rekomendasi : <perubahan konkret, dengan nilai/token bila tersedia>
Severity    : 🔴/🟡/🟢/⚪ <level> — <why this level>
```

Severity must follow voice-guide §5 definitions. If the user's sentence gives no basis for severity, pick the most likely level and mark it "(perkiraan — perlu dicek di desainnya)".

## Batch input

Multiple sentences → repeat the mode's format per sentence, numbered, separated by `---`. At the end, if ≥ 3 sentences share one principle, add one line: "Pola: <n> temuan berakar di <prinsip> — layak diangkat sebagai tema di review."
