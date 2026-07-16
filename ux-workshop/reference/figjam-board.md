# FigJam Board Patterns — shared by ideate / workshop / converge

Technical patterns for writing and reading workshop boards. ALWAYS load `figma-use` + `figma-use-figjam` before writing; `figma-create-new-file` before creating a new board.

## Editor-mode constraints (from figma-use §Editor Mode)

- FigJam = URL `/board/`. Available nodes include **Sticky, Section, ShapeWithText, Connector, Text**; many design-mode nodes are blocked, and `figma.createPage()` THROWS in FigJam — never call it.
- `use_figma` works on FigJam with the same rules (return IDs, ≤10 logical ops per call, atomic on error).

## Writing patterns

**Section per activity** (workshop template):
```js
const section = figma.createSection();
section.name = '1 · HMW — tulis idemu di sini (7 menit)';
section.resizeWithoutConstraints(1600, 900);
section.x = X; section.y = Y;                 // tile sections horizontally per agenda order
```
Put a Text node inside the section's top-left with the block instruction (2 lines max).

**Sticky grid**:
```js
const sticky = figma.createSticky();
await figma.loadFontAsync({ family: 'Inter', style: 'Medium' });   // sticky text needs font
sticky.text.characters = 'isi ide';
sticky.x = originX + col * 260; sticky.y = originY + row * 260;    // stickies ±240px; 260 spacing breathes
```
- Color per participant or per round: `sticky.fills = [{type:'SOLID', color:{r,g,b}}]` (0–1 range). Keep a small legend text on the board.
- Grid math: `col = i % perRow; row = Math.floor(i / perRow)`; perRow 4–6.

**Voting area / 2×2**: draw the axes with two thin `ShapeWithText`/lines or a Section per quadrant (simpler: 4 sections named "Quick wins", "Big bets", "Isi waktu luang", "Tidak dulu") and MOVE stickies into them (`section.appendChild(sticky)` keeps world position math — set x/y relative after append).

**Hasil Sintesis section** (converge write-back): one new section to the RIGHT of existing content (scan max x first — same rule as design mode), containing theme clusters: a Text label per theme + its stickies re-created (never move the team's original stickies without asking).

## Reading patterns

- **`get_figjam`** on the board or a specific section URL/node-id — primary read; returns structured content including sticky texts.
- Fallback `use_figma` read when you need color/author/position detail:
```js
const stickies = figma.currentPage.findAllWithCriteria({ types: ['STICKY'] })
  .map(s => ({ id: s.id, text: s.text.characters,
    section: s.parent?.type === 'SECTION' ? s.parent.name : null,
    fill: s.fills?.[0]?.color ?? null, x: s.x, y: s.y }));
return stickies;   // reconcile count with what the team says they wrote
```

## New board

Load `figma-create-new-file` skill → `create_new_file` with editorType `figjam` and a purposeful name ("Workshop — <topik> <tanggal>"). Then build sections in a second call (create → verify via `get_figjam` → fill).

## Verification rule

After any board write: read back (`get_figjam` or the STICKY query) and reconcile counts/section names in the chat recap. A board the user opens should match the recap exactly.
