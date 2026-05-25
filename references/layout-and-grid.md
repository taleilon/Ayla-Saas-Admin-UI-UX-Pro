# Layout & grid

How an Ayla admin screen is assembled. Read this before laying out *any* full page.

## Overall page anatomy

The design is built at 1920px wide. From left to right:

```
┌──────────┬────────────────────────────────────────────────────────┐
│          │ Top Navigation                    (1640 × 72)          │  ← y=0
│          ├────────────────────────────────────────────────────────┤
│          │                                                        │
│  Sidebar │   ┌─ 40px page padding ──────────────────────┐         │  ← y=72
│  (280)   │   │  Breadcrumbs                  (1560×51)  │ 40px    │
│          │   │                                          │         │
│          │   │  Content grid (1560 wide, 24px gap)      │         │
│          │   │                                          │         │
│          │   │  Footer                       (1560×68)  │         │
│          │   └──────────────────────────────────────────┘         │
└──────────┴────────────────────────────────────────────────────────┘
   x=0        x=280  x=320                       x=1880  x=1920
```

Numeric facts to encode literally:

| Element | x | y | Width × Height |
| --- | --- | --- | --- |
| Sidebar | 0 | 0 | 280 × full page height |
| Top Navigation | 280 | 0 | 1640 × 72 |
| Breadcrumbs | 320 | 96 | 1560 × 51 (sometimes 55 in older variants) |
| Content blocks | 320 | 176+ | column widths from set below |
| Footer | 320 | bottom | 1560 × 68 |

The 40px padding between the sidebar (ends at x=280) and the content (starts at x=320) **is real and load-bearing** — the design relies on this breathing room. The top nav still extends edge-to-edge under the sidebar's gap, with its content starting at the left edge of the column area.

## Responsive intent

The design system is a fixed 1920px desktop design — there are no breakpoint variants. When porting to a real responsive build:

- ≥1440px: render at native 1920 scale, or compress proportionally.
- 1024–1439px: collapse content gutters from 24→16 and let the content area flex. Sidebar stays 280px.
- <1024px: sidebar collapses to a 64px icon rail or off-canvas drawer; content padding drops to 16-20px. (This is your design judgment — not in the source.)
- <640px: stack everything; the table variants typically need a horizontal scroll or card-style row collapse.

## The 1560px content grid

The content area is 1560px wide with a 24px gutter. Every card width in the system is one of:

| Width | Fraction of grid | Common contents |
| --- | --- | --- |
| **372** | 1/4 col (4 × 372 + 3 × 24 = 1560) | Stat cards, small widgets, the right rail of a 2-column layout, sidebar inside file manager |
| **504** | 1/3 col (3 × 504 + 2 × 24 = 1560) | Medium card (Social Media Traffic, Account Settings/Contact Info) |
| **636** | (636 + 24 + 372 + 24 + 504 = 1560) — fits with siblings | Operating System card, Upgrade Plans card |
| **768** | 1/2 col (2 × 768 + 1 × 24 = 1560) | Form panels, side-by-side tables, User Location map card |
| **1164** | (1164 + 24 + 372 = 1560) — pairs with one 372 sibling | User Overview chart, primary content block w/ a side widget |
| **1560** | full | Wide tables, payment method, invoice, kanban board |

When laying out a page, **always solve the width arithmetic first**: pick a row composition that sums to 1560 (counting 24px gaps). Don't invent intermediate widths.

### Common row compositions (each row sums to 1560)

- 4-up stats: `372 + 24 + 372 + 24 + 372 + 24 + 372`
- 2/3 + 1/3: `1164 + 24 + 372`
- 1/4 + 1/2 + 1/4: `372 + 24 + 768 + 24 + 372`
- 1/3 + 1/4 + 1/3 + (squeezed): see screens.md — there are a few specific compositions for the settings page
- Hero + small: `636 + 24 + 372 + 24 + 504`
- Full row: `1560`

### Vertical rhythm

Rows of cards in the dashboard are spaced with **24px gaps** between rows too. The full vertical sequence for the canonical dashboard is:

```
y=72   Top Nav
y=96   Breadcrumbs (24px gap to first content row)
y=172  Row 1: 4 stat cards, height 272
y=468  Row 2: 1164 + 372, height 416    (gap = 468 - (172+272) = 24)
y=908  Row 3: 372 + 768 + 372, height 488
y=1420 Row 4: 504 + 372 + 636, height 400
y=1820 Footer
```

## Sidebar internals (280 × full height)

```
┌──────────────────────────┐
│ 24 ━━━━━━━━━━━━━━━━━━━━ │  ← Logo row, 32px diamond icon + brand wordmark (24px SemiBold)
│ 24 ━━━━━━━━━━━━━━━━━━━━ │
│                          │
│   ─ DASHBOARD ─          │  ← section heading, 12px Medium Gray 400 uppercase
│   [icon] Dashboard       │  ← active item, Primary 50 bg, 3px left accent
│   [icon] Calendar        │
│   [icon] Kanban Board  ⌄ │  ← expandable items show a 16px caret
│   [icon] File Manager  ⌄ │
│   [icon] Authentication⌄ │
│                          │
│   ─ PAGES ─              │
│   [icon] Profile       ⌄ │
│   [icon] Invoice       ⌄ │
│   [icon] Billing         │
│   [icon] Pricing Plans   │
│   [icon] FAQs            │
│   [icon] Blank Page      │
│                          │
│   ─ COMPONENTS ─         │
│   [icon] Card            │
│   [icon] Table           │
│   [icon] Form Elements   │
│   [icon] Widgets         │
│   [icon] Documentation ⌄ │
└──────────────────────────┘
```

Vertical: 16px top padding before the logo; 24px gap between major sections; 8px gap between a section heading and its first item; 4px gap between items.

Horizontal: every nav item is padded `10px 24px`. The icon (20px) and label (14px Medium) are separated by 12px. Expandable items have a 16px caret aligned right.

The right edge of the sidebar has a 1px Gray 100 inset shadow — this is the visual divider from the content.

## Top Navigation internals (1640 × 72)

```
┌─────────────────────────────────────────────────────────────────┐
│ [🔎  Search        ]                       [🌐 English ⌄] ⊞ 🔔 ● │
└─────────────────────────────────────────────────────────────────┘
```

- 40px horizontal padding on both ends.
- Left: 240×40 search input. Gray-50 alpha background (`rgba(242,243,244,0.5)`), 4px radius, 20px magnifying glass icon at left=16, placeholder "Search" at left=48.
- Right cluster, gap 16px between items:
  - Language pill: 116×32, Gray 50 background, 4px radius. Inside: 16px flag image + "English" + 24px chevron.
  - Layout icon: 20px.
  - Notification icon: 20px with a red dot (8px circle, Danger 500) overlaid at top-right.
  - Profile avatar: 40px circle, Warning 200 background, 32px inner avatar image.

## Breadcrumbs (1560 × 51)

A single row with: `Page Title` on the left (`Heading 05`, 24px SemiBold Gray 900), and the breadcrumb trail on the right (`Home / Section / Current`, 14px Medium Gray 600, current page Gray 900). On screens that also have action buttons (Kanban, Calendar, etc.) the buttons sit at the right edge instead of the breadcrumb trail.

## Footer (1560 × 68)

A simple row: copyright text on the left, version / link cluster on the right, both 14px Regular Gray 600. Sits 24-40px below the last content row.

## Modals & drawers

- **Modal overlay**: full-viewport `rgba(0,0,0,0.4)` wash. Center modal vertically and horizontally.
- **Modal card**: 8px radius, white, 32px padding inside. Common widths: 424 (small), 472 (card form), 600 (form), 648 (multi-field form), 784 (Card Detail).
- **Right drawer** (Notification panel, Settings panel): pinned to right edge. Notification = 372 wide. Settings drawer = 552 wide. Full viewport height. 8px outer radius optional.

## Variants of the dashboard chrome

The source ships several chrome variants — they share the content grid but rearrange the navigation:

1. **Vertical (default)**: 280 sidebar + 72 top nav. Sidebar is white.
2. **Horizontal**: no left sidebar; instead a 64-high top brand bar + a 52-high menu bar with horizontal nav. Content starts at x=180, y=140.
3. **Black sidebar**: same as vertical but sidebar bg is Gray 900 (#191B1C), nav items white with Primary 500 active accent.
4. **Navy sidebar**: sidebar bg is a deep navy (#0E2A47-ish).
5. **With notification drawer open**: vertical layout + 372-wide drawer floating top-right.
6. **With settings drawer open**: vertical layout + 552-wide drawer floating right edge, plus a `rgba(0,0,0,0.4)` overlay over the rest.

If the user asks for the dark or navy variant, swap only the sidebar background + label colors; leave the content grid untouched.
