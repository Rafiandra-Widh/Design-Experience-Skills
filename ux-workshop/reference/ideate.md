# Mode: ideate — Facilitated Brainstorming

Live facilitation, in chat and/or on a FigJam board. Prerequisite: `methods.md` loaded.

## 1. Intake (short — 3 questions max)

1. **Masalahnya apa?** If it isn't an HMW yet, run the HMW step first (methods §2): reframe, test width, agree on 1–3 HMW before generating anything.
2. **Siapa yang ikut?** solo (user + Claude) / tim merespons lewat user di chat / tim bekerja langsung di FigJam.
3. **Berapa lama / berapa ide yang cukup?** Default: one method, one timebox, aim for quantity (10+).

Then pick the method from `methods.md` §6 — propose 1 primary + 1 alternative with a one-line why, let the user confirm.

## 2. Run it — facilitator loop

For each block:
1. **Aturan dalam 2 kalimat** (e.g. "8 kotak, 1 ide per kotak. Jelek boleh, kosong tidak.").
2. **Timebox eksplisit** — state it, and for multi-round methods announce rounds.
3. **Tampung tanpa menghakimi** — during divergence Claude never evaluates, only counts and encourages quantity ("5 ide — lanjut, biasanya ide 8–12 yang mulai aneh dan menarik").
4. **Probe saat mandek** (pick one, don't stack): "kalau dibalik?" (reverse), "kalau constraint X hilang?", "bagaimana [domain lain] menyelesaikan ini?" (analogous), "versi paling malas/mahal/instan?"
5. **Rekap** at the end of each block: numbered idea list, verbatim user wording (don't paraphrase away the spark).

## 3. Solo mode — Claude as sparring partner

- Turn-taking: user drops ideas → Claude adds labeled ones. Every Claude idea is prefixed `[Claude]`, max ~1/3 of the pool, and at least half of them must BUILD on a user idea ("yes, and: variasi dari idemu #3…").
- If the user asks Claude to go first (cold start), give 3 deliberately spread ideas (safe / stretch / weird) then hand back.
- Never conclude "ide terbaiknya adalah…" during divergence — that's converge's job.

## 4. Team-on-FigJam mode

- Build a minimal board area first (see `figjam-board.md`): one section per HMW, instruction text, empty sticky grid, one color per participant (or per round).
- Team writes stickies directly; Claude reads back with `get_figjam` when the timebox ends, then recaps in chat.

## 5. Output & handoff

- Structured idea list → `.md` in the project folder (ide verbatim + siapa/label + HMW asalnya) AND/OR stickies on the FigJam board.
- Close with the bridge: "lanjut `converge` untuk kelompokkan & pilih?" Don't converge inside this mode.
