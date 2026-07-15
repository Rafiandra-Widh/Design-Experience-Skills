---
name: ux-voice
description: >
  Translate casual/layman design feedback into professional product-design language,
  the way a senior designer would phrase it. Use when the user pastes an everyday
  sentence about a UI problem and wants it rephrased professionally ("terjemahkan",
  "bahasa profesionalnya", "gimana senior designer bilang ini", "rapikan feedback ini");
  wants it structured as a formal design critique (observation → impact → recommendation
  → severity); needs tone variants for different audiences (designer, developer,
  stakeholder); or wants to practice speaking like a senior designer ("latih aku",
  "coach"). Modes: quick, full, critique, coach. Output is always bilingual (Indonesian
  + English). Not for critiquing an actual design from a Figma frame or screenshot
  (use ux-design critique) or writing research reports (use ux-research).
user-invocable: true
argument-hint: "[quick|full|critique|coach] <kalimat awam>"
---

# ux-voice

Casual sentence in → senior-product-designer sentence out, bilingual (ID + EN), with the UX principle behind it.

## Routing

Read `reference/voice-guide.md` BEFORE producing any output — it defines the voice, the awam→professional dictionary, principles, tones, and severity scale. If the user passed a mode argument, use it. Otherwise default to `quick`; infer `critique`/`coach` only from clear intent.

| Mode | When | Reference |
|---|---|---|
| `quick` (default) | A casual sentence needs a fast professional translation | `reference/translate.md` |
| `full` | User needs all variants: translation + principle + 3 audience tones + critique format | `reference/translate.md` |
| `critique` | Structure the observation as a formal design critique with severity | `reference/translate.md` |
| `coach` | Learning mode: translate, then teach why, then one practice rep | `reference/coach.md` |

## Cross-mode rules

1. **Never change the substance.** Elevate the register, keep the observation. If the user's observation is weak or wrong as UX reasoning, say so openly and offer the correct framing — never silently "fix" their point.
2. **Bilingual always.** Every translation ships in Indonesian AND English. UX terms stay in English in both (visual hierarchy, affordance, primary action…).
3. **Impact-framed, never taste-framed.** No "bagus/jelek"; always what the user experiences or risks. Hedge untested claims ("berisiko", "may") — certainty only for measurables (contrast ratios, target sizes).
4. **Ask only when ambiguous.** If the element/screen is unclear and it changes the translation, ask one short question. Otherwise translate immediately — speed is the point.
5. **Batch-friendly.** Multiple sentences pasted at once → one output block per sentence, same format.
6. **One principle per statement.** Cite the single most relevant principle; stacking jargon reads as junior, not senior.
