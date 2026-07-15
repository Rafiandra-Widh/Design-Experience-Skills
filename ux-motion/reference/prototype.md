# Mode: prototype — Wire Click-Through Flows in Figma

Wires prototype reactions between frames via `use_figma` (Plugin API `setReactionsAsync`). Reactions are NOT gated by the motion feature flag — this mode always works.

Prerequisites: `figma-use` skill loaded; `motion-principles.md` read (§4 transitions).

## 1. Intake

Collect the connection list, one row per interaction:

```
<frame/elemen asal> --(trigger)--> <frame tujuan>  [jenis transisi]
```

- Accept it from: the user directly, an existing user-flow .md (ux-design flow output), or infer an obvious linear flow from frame names/order and CONFIRM before writing.
- Defaults when unspecified: trigger `ON_CLICK`; transition SMART_ANIMATE 300 ms EASE_OUT if the frames share layers, else DISSOLVE 200 ms EASE_OUT; drawers/sheets → OVERLAY with MOVE_IN from the relevant edge; "kembali" → action `BACK`, not a reverse NAVIGATE.
- The reaction source can be a whole frame or a specific element (button) inside it — prefer the actual button when it exists.

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
- **Duration unit sanity-check (once per session)**: after the first write, read back `node.reactions[…].transition.duration` and confirm the Figma UI shows the intended ms; adjust convention if it doesn't.
- Overlays: `navigation: 'OVERLAY'` + optional `overlayRelativePosition`; destination frame should have overlay settings set in Figma.

## 4. Verify & hand back

1. Read back `reactions` from every touched node and print the connection table:

```
| # | Asal | Trigger | Tujuan | Navigasi | Transisi | Durasi |
```

2. Flag anything that didn't round-trip (null destination, empty reactions).
3. Tell the user plainly: readback confirms the wiring EXISTS; the FEEL (smart-animate matching, timing) must be checked by pressing ▶ Play in Figma. List 2–3 things to watch for while playing (e.g. "kartu resep harus terasa membesar dari posisinya, bukan cross-fade").
4. If a flow starting point makes sense, offer to set it (`page.flowStartingPoints`).
