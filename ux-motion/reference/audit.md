# Mode: audit — Check Existing Motion & Interactions

Three input paths, one output format. Prerequisite: `motion-principles.md` loaded — every finding cites it.

## Input path A — Figma file/prototype

1. `get_metadata` on the target page/frames → map the structure.
2. `get_motion_context` (authoritative animation values: per-node duration, easing, properties, `timelineCohorts` with `recursive: true` for full frames).
3. Readback prototype wiring via `use_figma` (load `figma-use` first): collect `node.reactions` across frames → connection map (trigger, navigation, transition type, duration, easing).
4. Judge against motion-principles: durations outside scale (§2), easing direction wrong (§3), all-dissolve monotony / inconsistent direction model (§4), missing feedback or status motion where interaction demands it (§1), vestibular risks (§5).
5. Screenshot ≠ motion — if judgment truly needs to SEE it, offer `export_video` (top-level frame only, slow, needs ffmpeg for frame extraction); otherwise reason from the data, which is usually enough.

## Input path B — Live web page

1. Load the `claude-in-chrome` skill; open the page, then exercise real interactions: hover key controls, open/close modal or drawer, navigate between views, submit a form, scroll.
2. Extract ground-truth values with `javascript_tool`:
   - `document.getAnimations()` → running/registered animations (duration, easing, keyframes).
   - `getComputedStyle(el).transition / animation` on key components.
   - Reduced-motion handling: check for `@media (prefers-reduced-motion)` rules in stylesheets (`[...document.styleSheets].flatMap(s => { try { return [...s.cssRules] } catch { return [] } }).filter(r => r.media?.mediaText.includes('prefers-reduced-motion'))`).
   - Jank suspects: animations touching layout properties (width/height/top/left/margin).
3. Note interactions with NO feedback motion at all where confirmation matters (buttons, async submits).

## Input path C — Video / GIF recording

1. User provides the file path. Requires ffmpeg (`which ffmpeg`; if absent, tell the user and stop this path).
2. Extract frames: `ffmpeg -i <file> -vf fps=30 frames/f_%04d.png` (30 fps → each frame ≈ 33 ms).
3. Measure: find transition start/end frames visually → duration = frame delta × 33 ms. Read a few mid-transition frames to judge easing qualitatively (position vs time) and spot degraded smart-animate (cross-fade where movement was intended).
4. Be explicit about precision limits: ±1 frame (~±33 ms); easing judgments are qualitative.

## Output format (all paths)

Ranked findings, most severe first — same shape as ux-design critique:

```
## Temuan motion

### 🔴 Blocker
1. [Lokasi/interaksi] — masalah. Prinsip: <nama §>. → Rekomendasi konkret (nilai baru: durasi ms + easing + properti).

### 🟡 Major / 🟢 Minor / ⚪ Polish
...

## Yang sudah bagus
- (2–3 hal — audit yang kredibel mengakui yang benar)
```

Rules: every finding names its location, cites one principle, and gives replacement VALUES (not "perhalus animasinya"). If ≤ 3 findings, say the motion is solid — don't pad. Close by offering next steps: `propose` for gaps found, or `figma-implement-motion` if the user wants fixes as code.
