# Design tokens

The full palette, type ramp, and spacing system for the Ayla SaaS Admin design.

## Color

### Primary (brand blue)

| Token | Hex | Use |
| --- | --- | --- |
| `--color-primary-50` | `#F0F6FF` | Active sidebar nav background; chart track fill; very light accent backgrounds |
| `--color-primary-100` | `#CFDFF7` | Hover backgrounds on primary chips |
| `--color-primary-200` | `#9FBFF0` | Decorative |
| `--color-primary-300` | `#6E9FE8` | Decorative |
| `--color-primary-500` | `#005CE8` | Brand blue — primary buttons, active link text, focus rings, the 3px left accent on the active sidebar item |
| `--color-primary-accent-bar` | `#0E5FD9` | Used for filled bars inside stat-card charts and progress fills (slightly darker than 500) |

### Semantic

| Token | Hex | Use |
| --- | --- | --- |
| `--color-success-50` | `#E7F7EF` | Success-pill background |
| `--color-success-500` | `#0FAF62` | Success text / "up" trend arrow + percentage |
| `--color-warning-200` | `#FFD599` | Warning-pill background; default profile avatar background |
| `--color-danger-500` | `#E84646` | Danger text; "down" trend arrow; destructive action; the red dot on the bell notification icon |

### Neutral (gray)

| Token | Hex | Use |
| --- | --- | --- |
| `--color-white` | `#FFFFFF` | Page background, card background, sidebar background |
| `--color-gray-50` | `#F5F6F7` | Page background tint when contrast against white cards is needed; language pill bg |
| `--color-gray-100` | `#E5E7E8` | Default input border; row dividers in tables; the 1px right edge of the sidebar |
| `--color-gray-300` | `#B0B7BA` | Disabled borders, subtle dividers |
| `--color-gray-400` | `#959FA3` | Placeholder text; sidebar section headings ("DASHBOARD", "PAGES", "COMPONENTS"); search icon |
| `--color-gray-600` | `#626C70` | Inactive sidebar nav label text; muted body text |
| `--color-gray-700` | `#4A5154` | Stat-card label text (the small uppercase one above the big number); language pill label |
| `--color-gray-900` | `#191B1C` | Body text default; logo wordmark; the big number in stat cards; active sidebar nav label |

Search-field background also uses an alpha overlay: `rgba(242, 243, 244, 0.5)`. Keep that as a literal — it's not in the token set.

## Typography

Font family throughout: **Public Sans** (Google Fonts). Weights used: 400 (Regular), 500 (Medium), 600 (SemiBold). Letter-spacing is 0 everywhere.

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Public+Sans:wght@400;500;600&display=swap" rel="stylesheet">
```

### Heading ramp

| Token | Size / Line | Weight | Where it appears |
| --- | --- | --- | --- |
| `--font-heading-01` | 48 / 56 | SemiBold | Documentation H1 (large display) |
| `--font-heading-02` | 40 / 48 | SemiBold | Documentation H2 |
| `--font-heading-03` | 32 / 40 | SemiBold | Documentation H3 |
| `--font-heading-04` | 28 / 36 | SemiBold | Section headings inside content |
| `--font-heading-05` | 24 / 32 | SemiBold | **Stat-card numbers**, modal titles ("Create New", "Login to your account"), drawer titles ("Notification", "Settings"), page-title H1 |
| `--font-heading-06` | 20 / 28 | SemiBold | Card titles inside the dashboard widgets |

### Sub-heading / body / label

| Token | Size / Line | Weight | Where it appears |
| --- | --- | --- | --- |
| `--font-sub-02` | 16 / 23 | SemiBold | Card heading inside widgets ("User Overview"); breadcrumb current page |
| `--font-sub-03` | 14 / 20 | SemiBold | Tab labels; "Heading" text on form sections; button text |
| `--font-sub-04` | 12 / 14 | SemiBold | Small emphasized labels |
| `--font-body-large-500` | 16 / 24 | Medium | Larger body text (paragraphs in FAQs answers, etc.) |
| `--font-body-regular-400` | 14 / 20 | Regular | **Default body text** — table cells, input placeholders, paragraph copy |
| `--font-body-regular-500` | 14 / 20 | Medium | Sidebar nav labels; field labels above inputs ("Email", "Password"); table cell emphasis |
| `--font-body-small-400` | 12 / 14 | Regular | Captions, timestamps, secondary info |
| `--font-label-regular` | 12 / 1 | Medium | Stat-card uppercase labels ("ACTIVE VISITORS"); sidebar section headings ("DASHBOARD"); table column headers (uppercase) |
| `--font-label-tiny` | 10 / 1 | Medium | Tiniest captions / micro-labels |

### Common text patterns

- **Sidebar section heading**: 12px Medium Gray 400, **uppercase**, letter-spacing 0.
- **Sidebar nav item**: 14px Medium. Inactive: Gray 600. Active: Gray 900 (icon also Gray 900) with Primary 50 background and a 3px-wide Primary 500 inset shadow on the left edge.
- **Stat-card label**: 12px Medium Gray 700, **uppercase**.
- **Stat-card number**: 24px SemiBold Gray 900.
- **Table column header**: 12px SemiBold, uppercase, Gray 400 typically (verify against `tables.md`).
- **Table cell**: 14px Regular Gray 900.
- **Placeholder**: 14px Regular Gray 400.
- **Field label** (above an input): 14px Medium Gray 900.

## Spacing scale

The design uses a 4 / 8 / 12 / 16 / 24 / 32 / 40 grid. There is no formal "spacing token" naming in the source, so use this scale directly:

```css
--space-1: 4px;
--space-2: 8px;
--space-3: 12px;
--space-4: 16px;
--space-5: 24px;   /* most common — card padding, card gap, between major sections */
--space-6: 32px;
--space-7: 40px;   /* page padding, top-nav horizontal padding */
```

Concrete uses:

- **Card padding**: 24px.
- **Card gap (grid gutter)**: 24px.
- **Page padding** (sidebar → content): 40px on the left, 40px on the right (sidebar is 280px wide, content starts at x=320, ends at x=1880, so 1560px content width).
- **Top-nav padding**: 16px vertical, 40px horizontal.
- **Sidebar nav item padding**: 10px vertical, 24px horizontal. Gap between icon and label: 12px.
- **Sidebar section gap**: 8px between section heading and first item, 24px between sections.
- **Sidebar nav item gap**: 4px between items within a section.
- **Input field padding**: 10px vertical, 12-16px horizontal (depending on whether there's a left icon).
- **Field-label → input gap**: 6px.
- **Button padding**: 10px vertical, 16-24px horizontal.

## Border-radius scale

```css
--radius-sm: 4px;    /* inputs, selects, buttons, small pills, language-switcher chip */
--radius-md: 8px;    /* cards, modals, drawers, dropdowns */
--radius-lg: 40px;   /* bar-chart bars (rounded "pill" bars in stat cards) */
--radius-full: 9999px;  /* avatars, dots, notification badge, switch knobs */
```

## Borders & dividers

- Default border: `1px solid var(--color-gray-100)` (#E5E7E8).
- Sidebar right edge: an inset shadow `inset -1px 0 0 0 #F2F3F4` (essentially Gray 100).
- Table row divider: a single 1px line spanning the full row width in Gray 100.
- Active sidebar item left accent: `inset 3px 0 0 0 #0E5FD9`.
- No outer border on cards — they sit on a white page; the white-on-white separation is achieved by 24px gaps, not lines.

## Shadows

The design is largely flat. The only documented shadow:

- Cards on hover / elevated overlays: a soft `0 1px 2px 0 rgba(0, 0, 0, 0.04), 0 4px 8px 0 rgba(0, 0, 0, 0.04)`. Use sparingly — only on modal popovers and the right-side settings drawer.
- Modal/drawer overlay background: `rgba(0, 0, 0, 0.4)` covering the full viewport (1920×1080 in the source).

## Iconography

Source uses **Phosphor Icons** in "Normal" (regular) weight, occasionally "Fill" (the green check on notifications, the warning triangle). Sizes: 16px (chevrons, in-button), 20px (sidebar nav, top-nav icons), 24px (notification panel icons, larger CTAs).

If Phosphor isn't available in the target project, **Lucide** is the closest substitute. Material Icons and Font Awesome solid are too heavy and will visibly clash with the design.
