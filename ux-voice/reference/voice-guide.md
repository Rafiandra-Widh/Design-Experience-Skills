# Voice Guide — How a Senior Product Designer Sounds

The knowledge base for all ux-voice modes. Read this before producing any translation.

## 1. Anatomy of a senior designer sentence

Every professional design statement has up to three parts. A quick comment may use only the first two; a critique uses all three.

1. **Specific observation** — name the element AND its context. Not "tombolnya", but "the primary CTA on the checkout screen".
2. **User/business impact** — what happens to the user because of it. Frame as risk or friction, not personal reaction: "users may overlook it", "this adds friction at the highest-intent moment".
3. **Actionable recommendation** — concrete direction, ideally with values/tokens: "increase contrast to meet 3:1 non-text contrast", "move it into the sticky footer".

Register rules:
- Never "saya suka / saya tidak suka" → always impact-framed: "ini berisiko…", "this may cause…".
- Hedge claims that are untested: "may", "risks", "berpotensi" — certainty is only for measurable facts (contrast ratios, target sizes).
- Critique the design, never the designer: "the layout doesn't communicate…" not "kamu lupa…".
- One idea per sentence. Senior ≠ long; senior = precise.
- UX terms stay in English inside Indonesian sentences (visual hierarchy, affordance, primary action) — industry convention.

## 2. Kamus awam → profesional

| Kalimat awam (gejala) | Istilah profesional | Prinsip terkait |
|---|---|---|
| "kurang terlihat / gak keliatan" | insufficient visual prominence, weak visual hierarchy | Visual hierarchy |
| "gak tau itu bisa diklik" | weak affordance, low perceived interactivity | Affordance |
| "gak tau mana yang utama" | unclear primary action, competing CTAs | Visual hierarchy |
| "terlalu rame / penuh" | high visual noise, cluttered layout, cognitive overload | Cognitive load |
| "bingung mulai dari mana" | no clear entry point / focal point | Visual hierarchy, F-pattern |
| "kepencet yang sebelahnya" | insufficient touch target size / spacing | Fitts's law, target size |
| "jauh banget mau klik-nya" | high interaction cost, poor reachability | Fitts's law, thumb zone |
| "warnanya samar / gak kebaca" | insufficient contrast (fails WCAG AA) | Contrast, accessibility |
| "kayak bukan satu aplikasi" | inconsistent patterns/components, design-system drift | Consistency |
| "beda sama aplikasi lain biasanya" | deviates from established convention / mental model | Jakob's law |
| "gak ngerti istilahnya" | system-oriented language, jargon mismatch | Match system ↔ real world |
| "gak ada kabar setelah diklik" | missing feedback / system status | Visibility of system status |
| "takut salah pencet" | destructive action without confirmation/undo | Error prevention, user control |
| "harus inget-inget lagi" | forces recall instead of recognition | Recognition over recall |
| "kepanjangan / males ngisi" | high form friction, excessive input cost | Progressive disclosure |
| "informasinya dobel-dobel" | redundant content, low information scent | Minimalist design |
| "kok tiba-tiba pindah halaman" | unexpected navigation, broken user control | User control & freedom |
| "loadingnya bikin bingung" | unclear loading state, missing skeleton/progress | System status |
| "teksnya kekecilan" | sub-minimum type size, poor readability | Typography, accessibility |
| "labelnya gak jelas" | ambiguous label, low information scent | Clarity, information scent |
| "itemnya kayak nyampur semua" | weak grouping, unclear proximity | Gestalt: proximity |
| "gak sadar ada fitur itu" | low discoverability | Discoverability |
| "keburu ilang notifnya" | insufficient toast duration, transient feedback | Feedback, accessibility (timing) |
| "error-nya nyalahin aku" | blame-framed error message | Error message quality |
| "gak tau udah sampai mana" | missing progress indication in flow | Wayfinding, system status |
| "tombolnya kayak disabled padahal bisa" | misleading state styling | State communication |
| "banyak banget pilihannya" | choice overload | Hick's law |
| "kayaknya penting tapi kecil banget" | size/importance mismatch | Visual hierarchy |
| "scroll-nya kepanjangan" | poor content prioritization above the fold | Content hierarchy |
| "iconnya gak ngerti artinya" | unlabeled/ambiguous iconography | Recognition, icon+label |
| "formnya nolak terus" | unclear validation rules, late validation | Error prevention, inline validation |
| "kepotong teksnya" | text truncation without affordance / i18n overflow | Content resilience |
| "gak bisa balik" | dead end, missing back/escape route | User control & freedom |
| "nunggu lama gak jelas" | unbounded wait without progress feedback | System status, perceived performance |
| "kelihatan murahan / gak rapi" | inconsistent spacing/alignment, weak craft | Spacing scale, alignment |
| "aku kira udah kesimpen" | unclear save state / silent failure | System status, feedback |
| "pop-up nya ganggu" | disruptive interruption, poor modality choice | Interruption cost |
| "gak tau bedanya dua tombol ini" | insufficient differentiation between actions | Visual hierarchy, button roles |
| "di HP-ku berantakan" | broken responsive behavior / reflow | Responsive design |
| "warnanya sama semua jadi bingung" | color used as sole differentiator | Color independence (WCAG) |

## 3. UX principles cheatsheet

Cite the principle by name when it strengthens the point; one principle per statement — don't stack.

- **Visual hierarchy** — size, weight, color, and position should mirror importance; the primary action must win a 5-second glance. Cite when: something important is being missed.
- **Affordance** — an element's appearance should signal how to use it; flat text that is clickable has weak affordance. Cite when: users don't realize something is interactive.
- **Fitts's law** — time to reach a target depends on its size and distance; small or far targets cost more. Cite when: targets are small, cramped, or far from the flow of action.
- **Hick's law** — decision time grows with number of options. Cite when: too many equally-weighted choices.
- **Jakob's law** — users expect your product to work like the products they already use. Cite when: a pattern deviates from convention without payoff.
- **Gestalt: proximity** — items close together are read as related. Cite when: grouping/spacing misleads about relationships.
- **Cognitive load** — every element competes for attention; noise taxes comprehension. Cite when: layouts are dense or over-decorated.
- **Progressive disclosure** — show only what's needed now; reveal complexity on demand. Cite when: forms/screens front-load everything.
- **Consistency** — same thing, same look, same behavior everywhere; deviations must be intentional. Cite when: components drift from the system.
- **Visibility of system status** — the interface must always answer "what is happening?". Cite when: feedback, loading, or save states are missing.
- **Recognition over recall** — show options instead of making users remember. Cite when: users must memorize codes, previous steps, or hidden commands.
- **Error prevention & user control** — confirm destructive actions, provide undo and exits. Cite when: mistakes are easy and irreversible.
- **Match with the real world** — speak the user's language, not the system's. Cite when: labels use internal jargon.
- **WCAG contrast** — text ≥ 4.5:1 (large text 3:1), non-text UI ≥ 3:1; color never the only signal. Cite with numbers — this one is measurable, don't hedge.
- **Target size** — ≥ 44×44 px on touch, ≥ 24×24 on desktop pointer. Also measurable.

## 4. Tone per audience

Same substance, different framing:

- **Sesama designer** — full terminology, direct, reference principles by name, propose token-level fixes. "Primary CTA-nya kalah prominence sama secondary — coba naikkan ke filled style dan turunkan yang secondary ke ghost."
- **Developer** — lead with the concrete change and acceptance criteria; principle as one-line rationale. "Tolong naikkan kontras label button ini ke minimal 4.5:1 (sekarang ~2.8:1) — gagal WCAG AA. Token yang benar: `text-on-primary`."
- **Stakeholder non-design** — lead with user/business impact, no jargon, one clear ask. "Tombol pembelian utama saat ini mudah terlewat oleh pengguna, yang berisiko menurunkan konversi. Kami merekomendasikan membuatnya lebih menonjol."

## 5. Critique structure & severity

Formal critique format (mode `critique`):

```
Observasi   : <elemen + konteks + apa yang terjadi>
Dampak      : <konsekuensi ke user/bisnis, hedged bila belum teruji>
Rekomendasi : <perubahan konkret, dengan nilai/token bila ada>
Severity    : 🔴 Blocker | 🟡 Major | 🟢 Minor | ⚪ Polish
```

Severity scale:
- 🔴 **Blocker** — users cannot complete the task, or a hard accessibility failure (contrast, target size, keyboard trap).
- 🟡 **Major** — task completable but with significant friction, confusion, or conversion risk.
- 🟢 **Minor** — noticeable inconsistency or friction with a workaround.
- ⚪ **Polish** — craft-level: alignment, micro-spacing, wording refinement.

## 6. Sentence frames

Fill-in patterns for building statements fast:

- EN: "The [element] on [screen] lacks [property], so users may [impact]. Consider [recommendation]."
- EN: "[Element] deviates from [convention/pattern], which risks [impact]."
- EN: "Because [observation], the [metric/task] may suffer; a [recommendation] would address this."
- ID: "[Element] di [screen] kurang [properti] sehingga user berisiko [dampak]. Rekomendasinya: [perbaikan konkret]."
- ID: "Saat ini [observasi]; ini membuat [dampak]. Usulan saya: [rekomendasi]."
- ID (stakeholder): "Saat ini [masalah dalam bahasa awam-bisnis], yang berisiko [dampak bisnis]. Kami merekomendasikan [ask tunggal]."

## 7. Worked example (canonical)

Input awam: *"Saya menemukan posisi button itu kurang terlihat jadi tidak tau bahwa itu primary."*

- 🇮🇩 "Primary button ini kurang menonjol secara visual hierarchy — kontras dan penempatannya tidak mengomunikasikan bahwa ini primary action, sehingga user berisiko melewatkannya."
- 🇬🇧 "The primary button lacks visual prominence — its contrast and placement don't communicate that it's the primary action, so users may overlook it."
- 💡 Principle: **Visual hierarchy** — the most important action must be visually dominant.
- Tone-developer: "Primary button ini perlu dinaikkan prominence-nya: pakai filled variant + token `bg-primary`, dan pastikan posisinya konsisten di area action utama."
- Tone-stakeholder: "Tombol aksi utama saat ini mudah terlewat pengguna, yang berisiko menurunkan penyelesaian tugas. Kami merekomendasikan membuatnya lebih menonjol."
- Critique: Observasi: primary button pada screen ini memiliki kontras dan posisi yang setara dengan elemen sekunder. Dampak: user berisiko tidak mengenali primary action, menambah waktu penyelesaian tugas. Rekomendasi: gunakan filled style dengan token warna primary, tempatkan pada posisi action yang konsisten, pastikan non-text contrast ≥ 3:1. Severity: 🟡 Major.
