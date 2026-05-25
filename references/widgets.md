# Widgets

The dashboard-specific content blocks: stat cards, charts, the calendar, the kanban board, plus the right-side notification and settings drawers.

## Stat card (372 × 272) — the canonical "Active Visitors" widget

The most-reused widget. Four sit in a row at the top of the dashboard. Anatomy:

```
┌── 24 padding ────────────────────┐
│  ACTIVE VISITORS    ↑ 6.7%       │  ← label + trend pill
│  157,367                         │  ← stat number
│                                  │
│  ┃ ┃ ┃ ┃ ┃ ┃ ┃ ┃                │  ← 8 bars in a 148-tall row
│                                  │
└──────────────────────────────────┘
```

```html
<article class="ayla-card ayla-stat-card">
  <header class="ayla-stat-card__head">
    <div>
      <p class="ayla-stat-card__label">Active Visitors</p>
      <p class="ayla-stat-card__value">157,367</p>
    </div>
    <span class="ayla-trend ayla-trend--up">
      <i class="ph-arrow-up"></i> 6.7% Increase
    </span>
  </header>

  <div class="ayla-stat-card__bars" aria-hidden="true">
    <span class="ayla-bar"><span style="--fill: 64px; --offset: 78px"></span></span>
    <span class="ayla-bar"><span style="--fill: 105px; --offset: 37px"></span></span>
    <span class="ayla-bar"><span style="--fill: 39px; --offset: 103px"></span></span>
    <span class="ayla-bar"><span style="--fill: 74px; --offset: 68px"></span></span>
    <span class="ayla-bar"><span style="--fill: 56px; --offset: 86px"></span></span>
    <span class="ayla-bar"><span style="--fill: 96px; --offset: 46px"></span></span>
    <span class="ayla-bar"><span style="--fill: 69px; --offset: 73px"></span></span>
    <span class="ayla-bar"><span style="--fill: 49px; --offset: 93px"></span></span>
  </div>
</article>
```

```css
.ayla-stat-card { gap: 24px; display: flex; flex-direction: column; }

.ayla-stat-card__head { display: flex; justify-content: space-between; align-items: flex-start; }

.ayla-stat-card__label {
  margin: 0 0 8px;
  font: 500 12px/1 'Public Sans', sans-serif;
  color: var(--color-gray-700);
  text-transform: uppercase;
}
.ayla-stat-card__value {
  margin: 0;
  font: 600 24px/32px 'Public Sans', sans-serif;
  color: var(--color-gray-900);
}

.ayla-trend {
  display: inline-flex;
  align-items: center;
  gap: 4px;
  font: 500 14px/20px 'Public Sans', sans-serif;
}
.ayla-trend--up   { color: var(--color-success-500); }
.ayla-trend--down { color: var(--color-danger-500); }

.ayla-stat-card__bars {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  height: 148px;
}
.ayla-bar {
  position: relative;
  width: 20px;
  height: 148px;
  background: var(--color-primary-50);
  border-radius: 40px;
}
.ayla-bar > span {
  position: absolute;
  left: 6px;
  top: var(--offset);
  width: 8px;
  height: var(--fill);
  background: var(--color-primary-accent-bar);
  border-radius: 40px;
}
```

Trend pill colors: success (Up) green, danger (Down) red. Always 14px Medium. Icon is a 16-20px Phosphor arrow.

## Compact stat card (372 × 148)

Same shape, no chart. Two stack inside a 372×272 panel.

```css
.ayla-stat-card--compact { padding: 24px; height: 148px; gap: 8px; }
.ayla-stat-card--compact .ayla-stat-card__bars { display: none; }
```

## User Overview chart (1164 × 416)

A card with a 56px heading row (title + tabs + filter), then a 320-tall area-chart canvas. Use Chart.js / Recharts / D3 for the chart; the card chrome is just `.ayla-card` with a bigger height.

Tabs in the heading: 14px SemiBold Gray 600 inactive, Primary 500 active with a 2px Primary 500 underline.

## Most Visited Page (372 × 416)

Small table inside a card. Use the `ayla-table--small` variant. 5-6 rows of "page path / visits / bounce" with a trailing chevron or progress sliver.

## Browser Overview / Devices Overview (372 × 488)

Card with a donut chart on top and a list of legends beneath. Each legend row: 12px color dot + label + percentage.

## User Location (768 × 488)

Card with a world-map illustration (use `topojson-client` + a world atlas, or an inline SVG world map) and a list of country rows beside or under it. The map uses Primary 50 for landmasses and Primary 500 for dot markers.

## Calendar widget (372 × 398)

Mini month calendar inside a card. Header row: month name + prev/next arrows. Day-of-week strip: 7 columns × 32 tall, 12px SemiBold Gray 400. Date grid: 6 rows × 7 columns, each cell ~44×44. Today: filled Primary 500 circle. Selected: outlined Primary 500 circle. Days with events: a 4px Primary 500 dot under the number.

## Operating System (636 × 400)

A list of OS rows with a 20px logo, name, percentage, and a horizontal progress bar (4px tall, Primary 500 fill on Gray 100 track).

## Notification panel (372 × 404, fixed at right)

```html
<aside class="ayla-drawer ayla-notification">
  <header class="ayla-drawer__head">
    <h2 class="ayla-drawer__title">Notification</h2>
    <a href="#" class="ayla-drawer__action">Clear All</a>
  </header>

  <ul class="ayla-notification__list">
    <li class="ayla-notification__item">
      <span class="ayla-notification__icon ayla-notification__icon--success">
        <i class="ph-check-circle-fill"></i>
      </span>
      <div>
        <p class="ayla-notification__text">This is a success notification.</p>
        <p class="ayla-notification__time">5 min ago</p>
      </div>
    </li>
    <!-- … -->
  </ul>
</aside>
```

```css
.ayla-drawer {
  position: fixed;
  right: 24px;
  top: 56px;
  width: 372px;
  background: var(--color-white);
  border-radius: var(--radius-md);
  box-shadow: 0 1px 2px rgba(0,0,0,0.04), 0 4px 8px rgba(0,0,0,0.08);
  padding: 0;
  z-index: 50;
}
.ayla-drawer__head {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 16px 24px;
}
.ayla-drawer__title { margin: 0; font: 500 14px/20px 'Public Sans', sans-serif; color: var(--color-gray-900); }
.ayla-drawer__action { font: 500 14px/20px 'Public Sans', sans-serif; color: var(--color-primary-500); text-decoration: none; }

.ayla-notification__list { list-style: none; padding: 0 24px 16px; margin: 0; display: flex; flex-direction: column; gap: 16px; }
.ayla-notification__item { display: flex; gap: 12px; align-items: flex-start; }
.ayla-notification__icon {
  width: 48px; height: 48px;
  border-radius: 50%;
  display: grid; place-items: center;
  background: var(--color-gray-50);
  color: var(--color-gray-700);
  flex: none;
}
.ayla-notification__icon--success { background: var(--color-success-50); color: var(--color-success-500); }
.ayla-notification__icon--warning { background: #FFF3E0; color: #B65000; }
.ayla-notification__text { margin: 0 0 4px; font: 500 14px/20px 'Public Sans', sans-serif; color: var(--color-gray-900); }
.ayla-notification__time { margin: 0; font: 400 12px/14px 'Public Sans', sans-serif; color: var(--color-gray-600); }
```

## Settings drawer (552 × full-height, right-side)

Sits at the right edge over an `rgba(0,0,0,0.4)` overlay. Contains three sections:

1. **Layout** — two preview cards (Vertical / Horizontal) with a radio under each.
2. **Left Side Bar** — radio list: White / Black / Navy Blue.
3. Footer: 2 buttons side-by-side ("Reset" subtle, "Apply" primary).

```css
.ayla-settings {
  position: fixed;
  top: 0; right: 0; bottom: 0;
  width: 552px;
  background: var(--color-white);
  z-index: 60;
  display: flex;
  flex-direction: column;
}
.ayla-settings__head { display: flex; justify-content: space-between; padding: 16px 24px; border-bottom: 1px solid var(--color-gray-100); }
.ayla-settings__section { padding: 24px; }
.ayla-settings__preview {
  width: 240px; height: 135px;
  border-radius: var(--radius-md);
  background: var(--color-gray-50);
}
```

## Kanban column (372 × 836)

```html
<section class="ayla-kanban__col">
  <header class="ayla-kanban__col-head">
    <h3 class="ayla-kanban__col-title">To-do <span class="ayla-badge ayla-badge--neutral">5</span></h3>
    <button class="ayla-btn--icon" aria-label="Column menu"><i class="ph-dots-three"></i></button>
  </header>

  <div class="ayla-kanban__col-list">
    <article class="ayla-kanban__card">
      <span class="ayla-badge ayla-badge--danger">Urgent</span>
      <h4>New Project Idea &amp; Research</h4>
      <p>In lobortis fermentum venenatis…</p>
      <footer>
        <div class="ayla-kanban__members">
          <img src="/u1.jpg" alt=""><img src="/u2.jpg" alt=""><span>+3</span>
        </div>
        <time>15 Nov, 2021</time>
      </footer>
    </article>
    <!-- … -->
  </div>
</section>
```

```css
.ayla-kanban__col {
  width: 372px;
  background: var(--color-gray-50);
  border-radius: var(--radius-md);
  padding: 16px;
  display: flex;
  flex-direction: column;
  gap: 12px;
}
.ayla-kanban__col-head { display: flex; justify-content: space-between; align-items: center; }
.ayla-kanban__col-title { margin: 0; font: 600 16px/23px 'Public Sans', sans-serif; color: var(--color-gray-900); display: inline-flex; gap: 8px; align-items: center; }

.ayla-kanban__card {
  background: var(--color-white);
  border-radius: var(--radius-md);
  padding: 16px;
  display: flex;
  flex-direction: column;
  gap: 12px;
}
.ayla-kanban__card h4 { margin: 0; font: 600 14px/20px 'Public Sans', sans-serif; color: var(--color-gray-900); }
.ayla-kanban__card p { margin: 0; font: 400 14px/20px 'Public Sans', sans-serif; color: var(--color-gray-600); }
.ayla-kanban__card footer { display: flex; justify-content: space-between; align-items: center; }

.ayla-kanban__members { display: inline-flex; align-items: center; }
.ayla-kanban__members img { width: 24px; height: 24px; border-radius: 50%; margin-left: -6px; border: 2px solid var(--color-white); }
.ayla-kanban__members img:first-child { margin-left: 0; }
.ayla-kanban__members span { margin-left: 4px; font: 500 12px/1 'Public Sans', sans-serif; color: var(--color-gray-600); }
```

## Pricing plan card (372 × 476-668)

Four cards side-by-side, each progressively taller: Basic 476, Standard 540, Premium 604, Business 668. Inside: badge ("Most Popular"), plan name (20px SemiBold), price ($X /month, 32px SemiBold + 14px Gray 600), bullet list of features (16px check icon + 14px Regular text), CTA button at the bottom.

```css
.ayla-pricing-card {
  width: 372px;
  padding: 32px;
  display: flex;
  flex-direction: column;
  gap: 24px;
}
.ayla-pricing-card--popular {
  background: var(--color-primary-500);
  color: var(--color-white);
}
.ayla-pricing-card--popular .ayla-card__title,
.ayla-pricing-card--popular .ayla-pricing-card__price { color: var(--color-white); }
```

## Invoice card (1560 × 1044)

Full-width white card with: company logo + invoice number top, billed-to / from address blocks, an items table (description / qty / price / total), totals block on the right (subtotal / tax / total), and a footer with a primary "Print" CTA. Use `.ayla-card--full` and the `.ayla-table` from `tables.md` for the items list.

## Upgrade Plans (636 × 270)

Three-column mini info block: heading "Upgrade Your Plan" + body copy on the left, the next-tier price center, two CTAs on the right ("View Plans" subtle, "Upgrade Now" primary). Uses Primary 50 as background tint or a soft gradient.

## File Manager pieces

- **Folder sidebar** (372 wide): list of folder rows (icon + name + size + chevron).
- **File grid** (1164 wide): 3-column grid of file thumbnails. Each tile: 48px icon, file name, file size, 16px kebab menu.
- **Upload modal** (504 × 220): centered, with a dotted 1px Gray 300 border, "Drag & drop" 14px Gray 600 text inside, a primary "Choose File" button.
