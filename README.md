# FigmaTutor

Dedicated project for learning Figma interactively with Antigravity, running
hands-on Figma MCP exercises, saving study notes to Google Drive (Google Docs),
and maintaining a shared **Figma Production Best Practices** knowledge base
usable across all projects.

## Project Layout

```text
FigmaTutor/
├── README.md
├── best-practices/                  # Single source of truth for production rules
│   ├── INDEX.md                     # Cross-project registry (scan first)
│   └── TEMPLATE.md                  # Standard entry format
└── .agents/
    └── skills/
        ├── figma-tutor/             # Interactive tutor, exercises, notes & BP capture
        │   ├── SKILL.md
        │   └── references/
        │       ├── curriculum.md
        │       └── note-template.md
        └── figma-best-practices/    # Lean skill that applies learned rules in any project
            └── SKILL.md
```

## Global Availability

`/Users/arunjacobpackianathan/.gemini/config/skills.json` registers
`/Users/arunjacobpackianathan/Software/Antigravity/FigmaTutor/.agents/skills`
globally. That means:

- **`figma-tutor`** is available from this project or any other workspace.
- **`figma-best-practices`** is automatically discovered in every project (such
  as `LogoDesign` or future app/UI repos) so any agent or skill can consume the
  best practices you documented here during production Figma work.
