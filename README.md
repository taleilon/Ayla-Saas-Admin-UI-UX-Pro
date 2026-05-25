# Ayla SaaS Admin UI/UX Pro

A cross-agent skill for building admin / analytics dashboards in a clean, blue-accented design system. Drop in, prompt for the screen you want, get back pixel-faithful HTML + CSS (or your framework of choice) that stays on-model across the whole catalogue.

Built on the [Agent Skills open standard](https://agents.md/) — works with **Claude Code, Codex CLI, OpenClaw, Gemini CLI, GitHub Copilot, Cursor, Aider, Zed, Windsurf**, and any other agent that supports the SKILL.md format.

---

## What it does

Without a skill, asking any agent for "an admin dashboard" gives you a different look every time — generic grays, off-by-a-pixel spacing, no shared design tokens between screens. This skill pins the system so every screen, component, and prompt produces output from the same kit:

- **One palette** — `#005CE8` primary blue, semantic greens/reds/oranges, six-step gray ramp.
- **One type ramp** — Public Sans, 11/12/14/16/18/20/24/28 px, weights 400/500/600.
- **One grid** — 280 px sidebar, 72 px top nav, 1560 px content area, 24 px gutters. Column widths always sum cleanly: `{372, 504, 636, 768, 1164, 1560}`.
- **One component kit** — buttons (6 variants × 3 sizes), six table variants, full form-element set, stat cards, breadcrumbs, footer, modals.
- **A catalogue of 30+ ready-to-assemble screens** — dashboards, calendar, kanban, file manager, profile, settings, invoice, billing, pricing, FAQs, login, register, blank.

---

## What's inside

```
ayla-saas-admin-ui-ux-pro/
├── SKILL.md                       # Agent Skills spec (YAML frontmatter + workflow)
├── AGENTS.md                      # Project-scope orientation for AGENTS.md-aware agents
├── README.md                      # This file (human-facing)
├── assets/
│   ├── tokens.css                 # Drop-in CSS custom properties + Google Fonts import
│   └── starter.html               # Working scaffold: sidebar + nav + breadcrumbs + footer
└── references/
    ├── design-tokens.md           # Full palette, type ramp, spacing, radii, icon mapping
    ├── layout-and-grid.md         # Page anatomy, the 1560 grid math, chrome variants
    ├── components.md              # Sidebar, nav, breadcrumbs, buttons, badges, card shell
    ├── tables.md                  # All 6 table variants + universal CSS base
    ├── forms.md                   # Inputs, selects, checkboxes, radios, switches, auth screens
    ├── widgets.md                 # Stat cards, charts, kanban, pricing, invoice, file manager
    ├── screens.md                 # Catalogue of all ~30 screens with Figma node IDs
    └── figma-workflow.md          # When/how to call Figma MCP for live design lookups
```

---

## Install

The `.skill` archive is just a zipped folder. Unzip it and drop the contents into the skills directory of whichever agent you use:

| Agent | Install path |
|---|---|
| **Claude Code** | `~/.claude/skills/ayla-saas-admin-ui-ux-pro/` |
| **Codex CLI** | `~/.codex/skills/ayla-saas-admin-ui-ux-pro/` (or drop into the project root — Codex will pick up AGENTS.md) |
| **OpenClaw** | `~/.openclaw/skills/ayla-saas-admin-ui-ux-pro/` |
| **Gemini CLI** | `~/.gemini/skills/ayla-saas-admin-ui-ux-pro/` |
| **Cursor** | drop the folder into the workspace; reference SKILL.md from your `.cursor/rules` if desired |
| **GitHub Copilot** | drop into the workspace; Copilot's agent mode reads AGENTS.md |
| **Aider / Zed / Windsurf** | drop into the workspace root — all read AGENTS.md |

The skill is self-contained: no scripts to run, no dependencies, no build step. Activation happens via the `description:` trigger in `SKILL.md` for skill-aware agents, or via the orientation in `AGENTS.md` for project-scope discovery.

---

## How to invoke

The skill description is greedy on purpose. Any compatible agent will trigger it when you say things like:

- "Build me an admin dashboard for X"
- "Make a SaaS console / back-office UI / internal tool for Y"
- "I need a kanban board screen" / "design a billing page" / "draft an invoice detail view"
- "Use the Ayla style" / "Ayla admin" / "Ayla SaaS"
- "Use the Raple / Analytix design" (legacy reference to the source template)
- "Make me a login screen" or any of the 30+ catalogued screens

If you want a different aesthetic (dark mode trading terminal, glassmorphic dashboard, Linear-style UI), say so explicitly — the agent will skip this skill or offer to deviate.

---

## Example prompts

**Single screen:**

> Build me the Drip Envy admin dashboard landing page using Ayla. Top stat row should cover today's revenue, appointments, new clients, no-show rate. Below that, a chart of revenue trend and a recent-bookings table.

**Specific component:**

> Using Ayla, give me an HTML+CSS snippet for the "Active Visitors" stat card with a bar chart sparkline.

**Full screen set:**

> Generate the auth flow for LogicEMR in Ayla — login, register, forgot password.

**Framework target:**

> Convert the Ayla button system to a Tailwind config and a React `<Button />` component.

---

## Design system at a glance

### Color

| Token | Value | Use |
|---|---|---|
| `--primary-500` | `#005CE8` | Primary buttons, links, brand accents |
| `--primary-50`  | `#F0F6FF` | Hover/selected backgrounds |
| `--success-500` | `#0FAF62` | Positive states, badges |
| `--danger-500`  | `#E84646` | Errors, destructive actions |
| `--warning-200` | `#FFD599` | Warning badges |
| `--gray-900`    | `#191B1C` | Headings, body text |
| `--gray-600`    | `#626C70` | Secondary text, labels |
| `--gray-300`    | `#B0B7BA` | Disabled, dividers |
| `--gray-100`    | `#E5E7E8` | Borders |
| `--gray-50`     | `#F5F6F7` | Page background, striped rows |

### Type

Public Sans (Google Fonts), weights 400 / 500 / 600.
Scale: 11 / 12 / 14 / 16 / 18 / 20 / 24 / 28 px.

### Layout

- Design width: 1920 px
- Sidebar: 280 px (fixed left)
- Top nav: 72 px (fixed top)
- Content area: 1560 px wide, 40 px page padding
- Grid: 12 logical columns, 24 px gutters
- Card radius: 8 px • Input radius: 4 px • Card padding: 24 px

### Chrome variants

- Default (light sidebar, white nav)
- Black sidebar
- Navy sidebar
- Horizontal layout (top-only navigation)

---

## Figma integration

The skill ships with the Figma node IDs for every screen and component in `references/screens.md` and `references/figma-workflow.md`. If you have the Figma MCP connector enabled in your agent (supported by Claude Code, Codex, OpenClaw, Cursor, and others), the agent will:

- Pull live screenshots when asked to "match the design"
- Read component metadata (props, variants) directly from the source file
- Stay in sync if the underlying template is updated

If Figma MCP isn't connected, the skill works standalone — all design data is captured in the reference files.

---

## Versioning

- **v1.0** — Initial release. 30+ screens, 6 table variants, full form set, light/black/navy chrome variants.
- 
---

## Customizing

Treat `assets/tokens.css` as the brand surface. To re-skin the entire system:

1. Edit the CSS custom properties (`--primary-500`, font family, radii).
2. Don't touch the layout math (column widths, grid gaps, sidebar width) — those are tuned to keep the kit composable.
3. If you swap the primary blue, also update the accent bar color (`#0E5FD9`) and the primary-50 tint (`#F0F6FF`) to stay in the same hue family.

For per-brand variants (e.g. Drip Envy in pink-purple, Brokerkey in green), keep one fork of the skill per brand with a different `tokens.css`. The reference markdown stays identical.

---

## License

The skill structure (markdown, CSS, HTML scaffolds) is yours to use, modify, and redistribute freely. Check the source file's terms before using in commercial products.
