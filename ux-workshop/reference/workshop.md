# Mode: workshop — Session Package Designer

Designs a complete, runnable workshop package for a human facilitator (usually the user). Prerequisite: `methods.md` loaded.

## 1. Intake

1. **Tujuan & keputusan**: what must EXIST when the session ends (a chosen problem? 3 prioritized solutions? aligned scope?). No decision → no workshop; suggest an async doc instead.
2. **Durasi** yang tersedia (be honest: LDJ needs 60–90′, discovery needs half a day — don't compress a discovery into 45′; cut scope instead).
3. **Peserta**: jumlah, peran (ada decider? ada yang dominan?), remote/onsite, medium (FigJam?).
4. **Preset match**: if the situation matches a ready format (methods §4 — LDJ, discovery, assumption mapping, retro…), start from the preset and adapt; don't design from scratch for solved problems.

## 2. Assemble the agenda

Block sequence (adapt, don't skip the shape): **opening/icebreaker → framing → divergen → konvergen → commitment**.

Rules of assembly:
- Every block: nama metode + timebox + output blok. Menit-per-menit timeline with real clock times when start time is known.
- Diverge and converge never share a block (cross-mode rule 1); silent starts for group input (rule 2).
- One decider named for tie-breaks (Sprint-style) when the group is ≥5 or political.
- Buffer: 10% of total duration, placed before the commitment block, never at the end.
- Icebreaker relates to the topic (hopes & fears about THIS project), not generic trivia.

## 3. Deliverables

1. **Agenda .md** (project folder): tujuan & keputusan target → peserta & peran (fasilitator, timekeeper, notulen, decider) → timeline tabel (waktu · blok · metode · instruksi 1 baris · output) → daftar materi.
2. **Facilitator script** (same file, per block): kalimat pembuka verbatim, aturan 2 kalimat, apa yang dilakukan saat macet, transisi ke blok berikut. Plus **risiko & mitigasi** (peserta dominan → silent start + round robin; waktu molor → potong share-out, bukan potong konvergen; ide sensitif politik → anonim).
3. **FigJam board template** (if medium includes FigJam — patterns in `figjam-board.md`): one section per block in agenda order, instruction text inside each, pre-made sticky grids/voting areas. Verify by readback (`get_figjam`) and report the board link area names.

## 4. Handback

Walk the user through the agenda in chat (short), flag the 1–2 blocks that most often fail and why, and offer: dry-run the facilitation live with Claude (`ideate`/`converge` as rehearsal), or adjust timing.
