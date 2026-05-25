# AGENTS.md

This directory is the **Ayla SaaS Admin UI/UX Pro** skill — an Agent Skills bundle for generating admin / analytics dashboard UI in a specific design system. It conforms to the [Agent Skills open standard](https://agents.md/) and works with Claude Code, Codex CLI, OpenClaw, Gemini CLI, Cursor, GitHub Copilot, and any other agent that supports the SKILL.md format.

## What this skill does

Generates pixel-faithful admin panels, back-office UIs, SaaS consoles, and internal tools from a unified design system: blue-accented, Public Sans typography, 280px sidebar, 1560px content grid, six table variants, a full form-element kit, and 30+ catalogued screens (dashboards, kanban, billing, invoice, auth, settings, pricing, file manager, etc.).

## Entry point

Read **`SKILL.md`** first. It contains the workflow, critical rules, and pointers to the reference files. If your runtime auto-loads SKILL.md files based on frontmatter triggers, you can ignore this file; if not, treat SKILL.md as the canonical instructions.

## Directory layout

```
.
├── SKILL.md                  # Canonical skill instructions (YAML frontmatter + workflow)
├── AGENTS.md                 # This file — orientation for AGENTS.md-aware agents
├── README.md                 # Human-facing documentation
├── assets/
│   ├── tokens.css            # Drop-in CSS custom properties (Google Fonts + base resets)
│   └── starter.html          # Working scaffold (sidebar + nav + breadcrumbs + footer)
└── references/
    ├── design-tokens.md      # Colors, typography, spacing, radii, icon mapping
    ├── layout-and-grid.md    # Page anatomy, 1560 grid math, column widths, chrome variants
    ├── components.md         # Sidebar, top nav, breadcrumbs, buttons, badges, card shell
    ├── tables.md             # All 6 table variants + universal CSS base
    ├── forms.md              # Inputs, selects, checkboxes, radios, switches, auth screens
    ├── widgets.md            # Stat cards, charts, kanban, pricing, invoice, file manager
    └── screens.md            # Catalogue of ~30 screens with content blueprints
```

## How to operate the skill

1. **Identify the deliverable** — one HTML file, React components, a Tailwind config, a multi-page mock, or just CSS variables. Match the user's target stack.
2. **Always read `references/design-tokens.md` and `references/layout-and-grid.md`** before generating any screen.
3. **Read the screen-specific or component-specific reference file** (`screens.md`, `tables.md`, `forms.md`, `widgets.md`, `components.md`) based on the request.
4. **Compose, don't invent.** Every screen is: `Sidebar (280px) + Top Nav (72px) + Breadcrumbs + Content (cards/tables/forms in a 1560px grid) + Footer`. Pick widths from `{372, 504, 636, 768, 1164, 1560}` so columns sum cleanly with 24px gaps.
5. **Use the design tokens, not literals.** Wire all colors and font sizes through the CSS custom properties in `assets/tokens.css`.
6. **Default to drop-in HTML + CSS** when the user hasn't named a stack. Use `assets/starter.html` as the scaffold and fill the content area from `references/screens.md`.

## Critical rules (most common drift)

- **Font:** Public Sans (Google Fonts), weights 400/500/600. Not Inter, not Roboto.
- **Primary blue:** `#005CE8`. Not generic Tailwind blue.
- **Sidebar:** white background by default (black and navy variants exist in `components.md`).
- **Card radius 8px, padding 24px, gap 24px.** Inputs use 4px radius.
- **Tables:** 12px uppercase column headers, 14px body, 1px row dividers — no full-cell borders.
- **Icons:** Phosphor Icons family, normal weight. Fall back to Lucide if Phosphor is not available.

## Programmatic checks (optional)

This skill produces static visual output, so there are no commands to run. To validate by eye:

- Open `assets/starter.html` in any browser — the page chrome must render with the correct sidebar, nav, and footer before adding content.
- Diff generated screens against `references/screens.md` blueprints.

## Agent-specific notes

- **Claude Code:** install as `~/.claude/skills/ayla-saas-admin-ui-ux-pro/`. Frontmatter triggers handle activation.
- **Codex CLI:** drop the folder into the project; Codex will pick up this AGENTS.md and load `references/` on demand. Or install globally at `~/.codex/skills/`.
- **OpenClaw:** install under your workspace skills directory (typically `~/.openclaw/skills/`). The skill is consumed by your agent's normal workflow — no SOUL.md or workspace file changes needed unless you want the agent to auto-prefer this style.
- **Gemini CLI / Cursor / Copilot / Aider:** drop into the workspace; the SKILL.md format is supported across all of them.

## License

MIT. Use, modify, and redistribute freely. See `LICENSE`.
