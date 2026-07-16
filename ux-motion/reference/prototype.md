# Mode: prototype — Wire Click-Through Flows in Figma

Wires prototype reactions between frames via `use_figma` (Plugin API `setReactionsAsync`). Reactions are NOT gated by the motion feature flag — this mode always works.

Prerequisites: `figma-use` skill loaded; `motion-principles.md` read (§4 transitions).

## 1. Intake

Collect the connection list, one row per interaction:

```
<frame/elemen asal> --(trigger)--> <frame tujuan>  [jenis transisi]
```

- Accept it from: the user directly, an existing user-flow .md (ux-design flow output), or infer an obvious linear flow from frame names/order and CONFIRM before writing.
- **Ask the precision level** (one question, skip if already clear from the request):
  - `komponen spesifik` (DEFAULT when the user names buttons/components, or when clear CTAs exist) — only the actual button advances; see "Attaching to a specific component" below.
  - `walkthrough` (klik di mana pun) — frame-level ON_CLICK; only when the user asks for a quick click-through deck OR a screen has no identifiable CTA.
- Defaults when unspecified: trigger `ON_CLICK`; transition SMART_ANIMATE 300 ms EASE_OUT if the frames share layers, else DISSOLVE 200 ms EASE_OUT; drawers/sheets → OVERLAY with MOVE_IN from the relevant edge; "kembali" → action `BACK`, not a reverse NAVIGATE.
- **Loading/status screens** ("Submitting…", spinner, progress): offer `AFTER_TIMEOUT` (default `{type:'AFTER_TIMEOUT', timeout: 1.5}`) instead of ON_CLICK — in the real product these screens advance by themselves. Attach it at frame level (that's where Figma expects it).

## 1b. Attaching to a specific component

Decision tree for the reaction SOURCE:

1. **Plain node** (frame, group, text, or a whole top-level instance — anything that is NOT a sub-layer of an instance) → attach the reaction directly. Text nodes work (verified).
2. **Sub-layer of a component instance** (node id starts with `I…;…` — e.g. a Button inside a Popup instance) → Figma does not allow interactions on instance children, via UI or API. Use the **HOTSPOT PATTERN**:

```js
// target = the button sub-node inside the instance (readable, not writable)
const tb = target.absoluteBoundingBox;          // reads are allowed on instance sub-layers
const fb = screenFrame.absoluteBoundingBox;
const hs = figma.createRectangle();
hs.name = 'hotspot/' + intentSlug;              // e.g. hotspot/upload-data
hs.fills = [];                                   // truly invisible, still receives clicks
hs.resize(tb.width, tb.height);
screenFrame.appendChild(hs);                     // appended last = topmost
hs.x = tb.x - fb.x;                              // convert to frame-relative coords
hs.y = tb.y - fb.y;
await hs.setReactionsAsync([reaction]);
```

   - Name every hotspot `hotspot/<intent>` — cleanup later is one query: `frame.query('RECTANGLE[name^=hotspot/]')`.
   - Hotspots do NOT follow the design if elements move/resize — say so in the handback ("kalau tombolnya digeser, jalankan ulang mode prototype untuk menyelaraskan hotspot").
   - A hotspot covers whatever is beneath it — keep it exactly button-sized (optional ±4 px padding, never bigger).

3. **NEVER** as a workaround: write reactions onto the MAIN component's children (propagates the interaction to every instance in every file — design-system pollution), or `detachInstance()` (destructive). If neither direct attach nor hotspot fits, report it instead.

## 2. Pre-check Smart Animate pairs

For every SMART_ANIMATE connection, compare layer names of the two frames (`get_metadata` on both). Report unmatched names — Figma matches by name+hierarchy and silently degrades to dissolve on mismatch. Offer to rename layers to match (with confirmation) or downgrade that connection to DISSOLVE.

## 3. Write reactions

Exact Plugin API shapes (from `plugin-api-standalone.d.ts` — there is no official pattern doc for this):

```js
// APPEND to existing reactions — never overwrite silently
const node = await figma.getNodeByIdAsync(SOURCE_ID);
const existing = node.reactions ?? [];
await node.setReactionsAsync([
  ...existing,
  {
    trigger: { type: 'ON_CLICK' },            // AFTER_TIMEOUT needs {timeout}, MOUSE_ENTER/LEAVE need {delay, deprecatedVersion:false}
    actions: [{                                // use `actions` array — `action` (singular) is deprecated
      type: 'NODE',
      destinationId: DEST_FRAME_ID,
      navigation: 'NAVIGATE',                  // or 'OVERLAY' | 'SWAP' | 'SCROLL_TO' | 'CHANGE_TO'
      transition: {
        type: 'SMART_ANIMATE',                 // SimpleTransition: DISSOLVE | SMART_ANIMATE | SCROLL_ANIMATE
        easing: { type: 'EASE_OUT' },
        duration: 0.3,                         // NOTE: seconds, not ms (0.3 = 300 ms) — sanity-check via readback once
      },
    }],
  },
]);
```

- Directional transition (PUSH/MOVE_IN/SLIDE_IN/…): add `direction: 'LEFT'|'RIGHT'|'TOP'|'BOTTOM'` and `matchLayers: boolean`.
- Back: `actions: [{ type: 'BACK' }]` (no destination/transition).
- **Sanitize when re-writing existing reactions**: reactions read from the API can contain `trigger.deprecatedVersion`, which `setReactionsAsync` REJECTS on echo-back ("Unrecognized key(s)"). Before appending to `node.reactions`, rebuild each existing reaction as `{trigger, actions}` via JSON round-trip and `delete trigger.deprecatedVersion` unconditionally. Also expect design-system buttons to carry their own hover reactions (MOUSE_ENTER) — preserve them.
- **Duration unit sanity-check (once per session)**: after the first write, read back `node.reactions[…].transition.duration` and confirm the Figma UI shows the intended ms; adjust convention if it doesn't.
- Overlays: `navigation: 'OVERLAY'` + optional `overlayRelativePosition`; destination frame should have overlay settings set in Figma.

## 4. Verify & hand back

1. Read back `reactions` from every touched node (hotspots included) and print the connection table — the Asal column states whether the source is the real node or a `hotspot/…`:

```
| # | Asal (node / hotspot) | Trigger | Tujuan | Navigasi | Transisi | Durasi |
```

2. Flag anything that didn't round-trip (null destination, empty reactions).
3. Tell the user plainly: readback confirms the wiring EXISTS; the FEEL (smart-animate matching, timing) must be checked by pressing ▶ Play in Figma. List 2–3 things to watch for while playing (e.g. "kartu resep harus terasa membesar dari posisinya, bukan cross-fade").
4. If a flow starting point makes sense, offer to set it (`page.flowStartingPoints`).
