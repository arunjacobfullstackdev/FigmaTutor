# Figma Production Best Practices — Index

This directory is the **cross-project, cross-skill knowledge base** of
production-ready Figma best practices discovered during learning and hands-on
experimentation.

## How Other Projects & Skills Consume This Index

Both the global `figma-best-practices` skill and any other skill performing
production Figma work (design generation, component libraries, logo/vector
authoring, design-to-code handoff, or automated `use_figma` scripting) should:

1. Read this `INDEX.md` first to scan the one-line production rules relevant to
   the current task's domain tags.
2. Open only the specific `<topic>.md` file(s) needed for deeper do/don't
   examples and MCP implementation notes.
3. Apply the documented rules as defaults unless the user explicitly overrides
   them.

## Domain Tags

`layout` · `auto-layout` · `components` · `variables` · `tokens` · `vectors` ·
`typography` · `color` · `naming` · `prototyping` · `handoff` · `export` ·
`mcp-automation`

## Best Practices Registry

| Date | Topic File | Domain Tags | One-Line Production Rule |
| :--- | :--- | :--- | :--- |
| 2026-11-26 | [vectors.md](./vectors.md) | `vectors`, `color`, `variables`, `components`, `mcp-automation` | Author symmetrical marks as layered SVG paths, import via `createNodeFromSvg()`, wrap in a `COMPONENT`, and bind every fill/stroke to scoped Color Variables. |
