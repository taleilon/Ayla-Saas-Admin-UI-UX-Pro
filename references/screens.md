# Screens catalogue

Every screen in the system, with its content blueprint and canvas dimensions. Use these as recipes — pick the closest match, then compose the content area from the widgets in `widgets.md`, tables in `tables.md`, and forms in `forms.md`.

For every screen below, the rendered structure is:

```
Sidebar (280) + [ Top Nav (1640×72) + Breadcrumbs (1560×51) + <content> + Footer (1560×68) ]
```

…unless explicitly noted otherwise (e.g., the auth pages have no chrome).

## Dashboards

### 01 — Dashboard Vertical *(default)*
**Canvas:** 1920×1888

Standard analytics dashboard. Row composition top-to-bottom:

| Row | Composition | Height |
| --- | --- | --- |
| Row 1 | 4 stat cards: Active Visitors / Visitor Per Minute / Conversion Rate / Bounce Rate (4 × 372) | 272 |
| Row 2 | User Overview (1164) + Most Visited Page (372) | 416 |
| Row 3 | Browser Overview (372) + User Location (768) + Devices Overview (372) | 488 |
| Row 4 | Social Media Traffic (504) + Calendar (372) + Operating System (636) | 400 |

### 02 — Dashboard Horizontal
**Canvas:** 1920×1080

No left sidebar. Instead a 64-tall top brand bar + a 52-tall menu bar. Content starts at x=180, y=140. Same content rows as Vertical but at 1560 wide.

### 03 — Dashboard with Notification drawer

Vertical layout + the 372-wide notification drawer at top-right starting at x=1468, y=56. Content underneath is unmodified.

### 04 — Dashboard with Settings drawer

Vertical layout + a 552-wide settings drawer pinned to the right edge, plus a full-viewport `rgba(0,0,0,0.4)` overlay over the rest. See `references/widgets.md` § Settings drawer.

### 05 — Dashboard Vertical (Black sidebar)

Same content as 01. Sidebar background switches to Gray 900, inactive labels become Gray 300, active item label is white.

### 06 — Dashboard Vertical (Navy sidebar)

Same as 05 but with a deep navy sidebar (roughly `#10204A`).

---

## Calendar app

### 07 — Calendar Year view
**Canvas:** 1920×1196

Mini-calendar widget at top-right (372×398), then Types selector (372×124) and Label list (372×332). Main area (1164×952): 12 mini-month thumbnails in a 4×3 grid.

### 08 — Calendar This Month
**Canvas:** 1920×1080

Main area (1164×836): full month grid, each day cell ~166×140 with stacked event chips. Right rail same as Year. Two dropdowns: at `1331,156` (View dropdown, 160×120) and `1724,822` (Day-action dropdown, 120×88).

### 09 — Calendar Week
**Canvas:** 1920×1533

Same chrome. Main area shows 7 day columns × 24 hourly rows.

### 10 — Calendar Today (Day view)
**Canvas:** 1920×1533

Single-day column with hour-rows on the left. Event blocks rendered as colored cards.

### 11 — Calendar / Create New (basic modal)

Today view + a 648×406 centered modal: Title, Type+Label row, Date. Two buttons: "Cancel" subtle + "Save" primary + an "Advance Option" link.

### 12 — Calendar / Create New (advance modal)

Same context, larger 648×710 modal: Title, Type+Label, Date, Description, Bookmark URL, Add Member.

### 13 — Calendar / Create Label modal

648×242 small modal: a color-dot select + Title field + 2 buttons.

---

## Kanban Board app

### 14 — Kanban Board

3 columns (To-do / Doing / Done, each 372×836) + a 372×56 "Add Column" button-card at position [1188, 0] inside the kanban area at [320, 176]. Above the board, breadcrumb row holds an action cluster ("Add Label" 130 + "Create New" 153).

### 15 — Kanban / Create New Column modal

424×242 modal with a Title field and Cancel + Save buttons.

### 16 — Kanban / Card Detail modal

784×784 modal containing the full card detail: title, badge, fun-fact row (Label + Created date + Due date), description, members grid, tabs (Comments / Activity), comment composer, latest comments list.

### 17 — Kanban / Create New Card modal

648×628 modal: Title + Priority/Label row + Description + Created/Due Date row + Add Member + Save/Cancel buttons.

---

## File Manager app

### 18 — File Manager

Sidebar (372 wide) of folder rows + main file grid (1164 wide). 1080 tall.

### 19 — File Manager / Upload File modal

Same screen + a 504×220 upload modal with a dashed dropzone.

### 20 — File Manager / Shared Files

Same screen, sidebar selection switched to "Shared Files", main pane shows the shared file list.

---

## Pages (Profile, Settings, Invoice, Billing, Pricing, FAQs, Blank)

### 22 — Profile
**Canvas:** 1920×1520

Row 1: full-width Profile/Banner (1560×320). Row 2: Profile/Info (372×296) + User Overview (1164×416). Row 3: Biography (372×612) + Notification & Activity (1164×492).

### 23 — Settings (Account)
**Canvas:** 1920×1544

A grid of account-setting cards: Profile Photo (372) + Banner Photo (372) + Basic Info (768) on row 1. Then Private Info (504) + Social Account (504) + Contact Info (504). Then Change Password (504) + Advance Setting (372) + Pricing Plans & Deactivated Account (636).

### 24 — Invoice
**Canvas:** 1920×1288

Full-width Invoice card (1560×1044).

### 25 — Invoice Detail
**Canvas:** 1920×1202

Full-width Invoice Detail card (1560×958).

### 26 — Billing
**Canvas:** 1920×1264

Row 1: Upgrade Plans (636) + Next Invoice (372) + Current Plans Benefits (504). Row 2: full-width Payment Method (1560×322). Row 3: full-width Payment History (1560×380).

### 27 — Billing / Add New Card modal

Same as Billing + a 472×400 centered modal: Card Number / Name on Card / CVC + Expire Date / Cancel + Save buttons.

### 28 — Pricing Plans
**Canvas:** 1920×1080

A Monthly/Yearly toggle at top right (150×20). Four plan cards in a row: Basic 372×476, Standard 372×540, Premium 372×604, Business 372×668. The taller, "Premium" / "Business" cards visually pop.

### 29 — FAQs
**Canvas:** 1920×1080

Heading row (1560×112) with title + descriptor. Then 3 rows × 2 columns of FAQ items (each 768 wide).

### 30 — Blank Page

Empty-state placeholder. A 160×160 illustration circle, then heading + body + primary CTA, all centered horizontally.

---

## Auth

### 31 — Login
**Canvas:** 1920×1080

Standalone (no sidebar / nav / footer). Logo at top center, 506×440 login card centered, "Don't have an account?" link below.

### 32 — Register
**Canvas:** 1920×1080

Standalone. Logo at top, 1010×522 split card (504 photo on left + 506 form on right), "Already have an account?" link below.

---

## Component documentation pages

### 33 — Cards (catalogue)

Documentation page listing 16 card variants: Basic / Basic with Image / Basic with Image+Overlay / Basic with Overlay / Light / Dark / Primary / Secondary / Success / Warning / Danger / Horizontal w/ Image / Align Left / Align Center / Align Right.

### 34 — Tables (catalogue)

Documentation page with: Basic Table (768) + Basic Table again (768) on row 1, Striped (768) + Hoverable (768) on row 2, Small Tables (768) + Highlight Column (768) on row 3, Advance Table full-width (1560×564) on row 4.

### 35 — Form Elements

Documentation page showing: text input variants (Text / Email / Password / Search / Left-icon / Date / Message) in a 768-wide column, select variants in another 768-wide column, Checkbox / Radio / Switch trios at 240 wide each, then a Login form variant, a horizontal form variant, and the full Advance Form (1560×630).

### 36 — Widgets catalogue

Massive catalogue showing every widget at its native size. Includes Fun-Fact (768×148), Profile (372×148), Upgrade Plans (372×148), all the Account Setting cards, Payment Method, Payment History, Invoice, Profile/Banner — basically every reusable widget in one place.

### 37 — Documentation

A docs-page template with side nav (the same Sidebar component), main content (Heading 01/02/03 stacked, body text, bullet list, number list, code block, file structure tree).

---

## Iconography page


Catalogues every icon used in the system — Phosphor "Outline" (light), "Normal" (regular), "Fill" (filled), plus Brands. If you need a specific glyph, browse the Phosphor Icons gallery directly.

---

## How to use this catalogue

1. **User asks for a named screen** ("make me the billing page") → look it up here → read its row composition → assemble using `references/widgets.md` and `references/components.md`.
2. **User asks for "an admin dashboard"** → default to screen 01 (Dashboard Vertical).
3. **User asks for "a login screen" or "sign up"** → use 31/32 — and remember these have no chrome.
