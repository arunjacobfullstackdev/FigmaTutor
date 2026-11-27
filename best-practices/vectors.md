# Vectors & Logos — Production Best Practices

**Domain Tags:** `vectors`, `color`, `variables`, `components`, `mcp-automation`  
**Last Updated:** 2026-11-26

---

## BP-001: Import Symmetrical Marks via SVG and Bind All Vector Paints to Color Variables

- **Rule:** When building geometric logos, emblems, or monoline marks in Figma (especially via `use_figma`), author symmetrical cubic Bézier paths in SVG with explicit `width`, `height`, and `viewBox`, import via `figma.createNodeFromSvg()`, wrap inside a reusable `COMPONENT`, and bind every solid fill and stroke to scoped Color Variables.
- **Why It Matters:**
  - Produces clean, mathematically symmetrical, resolution-independent vector paths instead of fragile rotated primitives.
  - Wrapping the mark in a `COMPONENT` with variable-bound paints lets any downstream screen or theme switch colors globally without hunting through dozens of vector layers.
  - Separating flat fill regions (layered back-to-front) from uniform monoline black linework prevents gaps/seams at curve junctions and makes stroke-weight adjustments trivial.
- **Do:**
  - Use a shared centerline mirror helper (`mx(x) = 2 * CX - x`) when authoring bilaterally symmetrical marks so left and right halves are mathematically identical.
  - Extend underlying fill regions slightly behind overlapping foreground shapes (e.g., chin pad behind muzzle lobes) to eliminate sub-pixel background/seam bleed.
  - Set explicit `variable.scopes` (`["FRAME_FILL", "SHAPE_FILL"]` for fills, `["STROKE_COLOR", "SHAPE_FILL"]` for strokes) and bind every imported vector's `fills` and `strokes` using `figma.variables.setBoundVariableForPaint()`.
  - Visually verify against the reference with `await node.screenshot({ scale: 1 })` and apply targeted curve refinements rather than rebuilding from scratch.
- **Don't:**
  - Don't reconstruct complex curved marks or icons from rotated rectangles/lines in `use_figma` — line rotation and corner alignment are brittle.
  - Don't leave imported SVG fills/strokes as hardcoded hex values when a color token collection exists.
  - Don't embed a flattened raster PNG as the deliverable in place of editable vector paths.
- **Figma MCP / Automation Note:**
  - `figma.createNodeFromSvg(svgString)` returns a `FrameNode` containing editable `VECTOR` children. Walk `svgFrame.findAll(() => true)` after import and reassign cloned `fills` and `strokes` arrays with `setBoundVariableForPaint()` to bind every vector paint to your local or library variables.
- **Discovered:** 2026-11-26 (during Geometric Big Cat Emblem reproduction test)
