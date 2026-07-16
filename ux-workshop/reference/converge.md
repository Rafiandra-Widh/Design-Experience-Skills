# Mode: converge — Synthesis & Decisions

Turns a pile of ideas/stickies into themes, priorities, and documented decisions. Prerequisite: `methods.md` loaded (§3 convergent methods, §5 synthesis chain).

## 1. Gather input

- **FigJam board**: `get_figjam` on the board/section URL → extract sticky texts (+ section & color if meaningful — color often encodes author/round). If structure is unclear, fall back to a `use_figma` read.
- **Paste/chat**: ideas listed in conversation (e.g. straight from `ideate`).
- **File**: `.md` idea list from a previous session.
- Record the total count — it must reconcile at the end (nothing silently dropped).

## 2. Affinity mapping (transparent)

1. Bottom-up: cluster items that answer the same underlying need — do NOT invent categories first and sort into them.
2. Label each theme DESCRIPTIVELY, as a sentence fragment that carries meaning ("User tidak percaya durasi resep" — bukan "Trust" atau "UI").
3. Show every theme WITH its members (verbatim). Unclustered leftovers go to a visible **"Parkir"** group with one line on why they didn't fit — never deleted.
4. Sanity check: a theme with one member is not a theme (move to Parkir or merge); a theme holding >40% of items is too broad (split).

## 3. Prioritize (framework chosen by context, methods §3)

- Default **Impact × Effort 2×2** when there's no quantitative data. Every placement gets a ONE-LINE justification; placements are relative (force spread — not everything is quick-win).
- **RICE/ICE** when reach/confidence data exists; **MoSCoW** when the decision is release scope; **$100 test / dot voting** only when real people actually vote.
- **Integrity rule (hard)**: never fabricate votes or team consensus. If it's Claude's placement, say so: "Ini penilaian saya — bantah penempatannya" and invite corrections before finalizing.

## 4. Decide & document

Output document (`.md`, project folder):

```
## Keputusan — <topik> (<tanggal>)
Input: N ide (sumber) → M tema + Parkir (K)
### Tema
1. <label> (n) — anggota…
### Prioritas (kerangka: …)
Quick wins: … | Big bets: … | Nanti: … | Tidak: …
### Keputusan & next steps
- <keputusan> → langkah, owner, kapan
### Parkir
- …
```

If a FigJam board was the input, also write a **"Hasil Sintesis"** section back onto the board (themes as labeled sticky clusters + the 2×2 — patterns in `figjam-board.md`), then verify by `get_figjam` readback.

## 5. Bridge

Problem themes → offer fresh HMW (loop back to `ideate`). Chosen solutions → `ux-design flow` (build it), assumption mapping (test it first), or `ux-voice` (communicate the decision upward).
