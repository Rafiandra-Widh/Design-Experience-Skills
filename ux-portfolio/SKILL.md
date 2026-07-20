---
name: ux-portfolio
description: >
  UX portfolio workflows: structure the portfolio, turn projects into case-study
  narratives, prepare the presentation deck, and review existing portfolios.
  Use when the user wants to plan a portfolio's structure — project selection, order,
  table of contents ("susun portfolio", "rancang portfolio", "proyek mana yang
  dimasukkan", "table of contents portfolio"); write a case study from raw project
  material ("tulis case study", "ubah proyek ini jadi cerita", "alur cerita",
  "storytelling proyek"); prepare a portfolio presentation ("deck portfolio",
  "portfolio presentation", "presentasi interview"); or review an existing
  portfolio/case study — their own or a team member's ("review portfolio ku",
  "kenapa portfolio ku gak dilirik", "audit case study").
  Modes: structure, case-study, present, review.
  Not for measuring/defining the metrics themselves (use ux-metrics), critiquing
  the underlying design work (use ux-design critique), or polishing feedback
  language (use ux-voice).
user-invocable: true
argument-hint: "[structure|case-study|present|review]"
---

# ux-portfolio

Portfolio workflows: structuring, case-study storytelling, presentation prep, and portfolio review — for job applications, personal branding, internal promotion, and mentoring team members.

## Routing

Read `reference/storytelling.md` and `reference/impact.md` first, then the mode's reference file BEFORE producing anything. If the user passed a mode argument, use it; otherwise infer, and ask if ambiguous.

| Mode | When | Reference |
|---|---|---|
| `structure` | Plan the portfolio: select & order projects, TOC per case study, positioning | `reference/structure.md` |
| `case-study` | Turn raw project material into a layered case-study narrative | `reference/case-study.md` |
| `present` | Build the presentation deck + speaker notes + panel Q&A prep | `reference/present.md` |
| `review` | Audit an existing portfolio/case study through three reader lenses | `reference/review.md` |

## Cross-mode rules

1. **Audience first.** Establish at intake: purpose (melamar kerja / personal branding / promosi internal / mentoring anggota tim), target reader (recruiter skim vs hiring manager deep-read vs leadership), and target role/level. All three change the structure, length, and tone — never produce without them.
2. **Bilingual by reader.** Language follows the target reader (perusahaan lokal → ID, internasional/remote → EN); the user can ask for both versions. UX terms stay in English in either version.
3. **Never fabricate the story.** Impact, metrics, and role are never invented or inflated: numbers without a source are labeled; role is written honestly ("saya" vs "tim — bagian saya: …"); impact without data uses the honest framings in `impact.md`. Kredibilitas > kemilau — senior reviewers smell inflation instantly.
4. **Confidentiality.** For NDA/government projects: ask what may be shown; offer anonymization (mask product names, absolute numbers → relative, blur data in visuals); never place sensitive data in any output, including drafts.
5. **Output medium.** Drafts & outlines → .md in the project folder; visual preview of a case study/site page → HTML artifact; layout to polish manually → Figma (load `figma-use`, always confirm first); deck → .md outline + artifact slides or Figma.
6. **Defer, don't duplicate.** Defining/measuring the project's metrics → `ux-metrics`; critiquing the design work itself → `ux-design critique`; register of feedback language → `ux-voice`; deep verbal-delivery practice → `ux-voice coach`.
