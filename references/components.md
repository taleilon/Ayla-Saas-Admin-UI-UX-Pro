# Core components

The reusable parts that appear on every screen. Build these once, drop them in everywhere.

---

## Sidebar (280 × full height)

White background. 1px Gray 100 right divider. Logo at top, then three sections (Dashboard / Pages / Components), each a small uppercase heading followed by a list of nav items.

### HTML

```html
<aside class="ayla-sidebar">
  <a class="ayla-sidebar__brand" href="#">
    <span class="ayla-sidebar__logo" aria-hidden="true">
      <!-- 32px diamond icon -->
    </span>
    <span class="ayla-sidebar__wordmark">Ayla</span>
  </a>

  <nav class="ayla-sidebar__nav">
    <section class="ayla-sidebar__section">
      <h3 class="ayla-sidebar__heading">Dashboard</h3>
      <ul>
        <li>
          <a class="ayla-sidebar__item is-active" href="#">
            <i class="ph-house-line" aria-hidden="true"></i>
            <span>Dashboard</span>
          </a>
        </li>
        <li>
          <a class="ayla-sidebar__item" href="#">
            <i class="ph-calendar-blank" aria-hidden="true"></i>
            <span>Calendar</span>
          </a>
        </li>
        <li>
          <a class="ayla-sidebar__item ayla-sidebar__item--expandable" href="#">
            <i class="ph-clipboard-text" aria-hidden="true"></i>
            <span>Kanban Board</span>
            <i class="ph-caret-down ayla-sidebar__caret" aria-hidden="true"></i>
          </a>
        </li>
        <!-- File Manager, Authentication … -->
      </ul>
    </section>

    <section class="ayla-sidebar__section">
      <h3 class="ayla-sidebar__heading">Pages</h3>
      <ul>
        <li><a class="ayla-sidebar__item ayla-sidebar__item--expandable" href="#"><i class="ph-user"></i><span>Profile</span><i class="ph-caret-down ayla-sidebar__caret"></i></a></li>
        <li><a class="ayla-sidebar__item ayla-sidebar__item--expandable" href="#"><i class="ph-notebook"></i><span>Invoice</span><i class="ph-caret-down ayla-sidebar__caret"></i></a></li>
        <li><a class="ayla-sidebar__item" href="#"><i class="ph-credit-card"></i><span>Billing</span></a></li>
        <li><a class="ayla-sidebar__item" href="#"><i class="ph-lightning"></i><span>Pricing Plans</span></a></li>
        <li><a class="ayla-sidebar__item" href="#"><i class="ph-question"></i><span>FAQs</span></a></li>
        <li><a class="ayla-sidebar__item" href="#"><i class="ph-note-blank"></i><span>Blank Page</span></a></li>
      </ul>
    </section>

    <section class="ayla-sidebar__section">
      <h3 class="ayla-sidebar__heading">Components</h3>
      <ul>
        <li><a class="ayla-sidebar__item" href="#"><i class="ph-cards"></i><span>Card</span></a></li>
        <li><a class="ayla-sidebar__item" href="#"><i class="ph-list-dashes"></i><span>Table</span></a></li>
        <li><a class="ayla-sidebar__item" href="#"><i class="ph-swatches"></i><span>Form Elements</span></a></li>
        <li><a class="ayla-sidebar__item" href="#"><i class="ph-leaf"></i><span>Widgets</span></a></li>
        <li><a class="ayla-sidebar__item ayla-sidebar__item--expandable" href="#"><i class="ph-book-open"></i><span>Documentation</span><i class="ph-caret-down ayla-sidebar__caret"></i></a></li>
      </ul>
    </section>
  </nav>
</aside>
```

### CSS

```css
.ayla-sidebar {
  position: relative;
  width: 280px;
  min-height: 100vh;
  background: var(--color-white);
  padding-top: 16px;
  box-shadow: inset -1px 0 0 0 var(--color-gray-100);
  display: flex;
  flex-direction: column;
  gap: 24px;
}

.ayla-sidebar__brand {
  display: flex;
  align-items: center;
  gap: 6px;
  padding: 0 24px;
  text-decoration: none;
}
.ayla-sidebar__logo { width: 32px; height: 32px; flex: none; }
.ayla-sidebar__wordmark {
  font: 600 24px/1 'Public Sans', sans-serif;
  color: var(--color-gray-900);
  text-transform: capitalize;
}

.ayla-sidebar__nav { display: flex; flex-direction: column; gap: 24px; }
.ayla-sidebar__section { display: flex; flex-direction: column; gap: 8px; }
.ayla-sidebar__heading {
  margin: 0;
  padding: 0 24px;
  font: 500 12px/1 'Public Sans', sans-serif;
  color: var(--color-gray-400);
  text-transform: uppercase;
}
.ayla-sidebar__section ul {
  list-style: none; margin: 0; padding: 0;
  display: flex; flex-direction: column; gap: 4px;
}

.ayla-sidebar__item {
  position: relative;
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 10px 24px;
  text-decoration: none;
  font: 500 14px/20px 'Public Sans', sans-serif;
  color: var(--color-gray-600);
}
.ayla-sidebar__item i { font-size: 20px; flex: none; color: currentColor; }
.ayla-sidebar__item span { flex: 1; min-width: 0; }

.ayla-sidebar__item.is-active {
  background: var(--color-primary-50);
  color: var(--color-gray-900);
  box-shadow: inset 3px 0 0 0 var(--color-primary-accent-bar);
}

.ayla-sidebar__caret { font-size: 16px !important; color: var(--color-gray-400); }

.ayla-sidebar__item:hover {
  background: var(--color-gray-50);
  color: var(--color-gray-900);
}
```

### Dark-sidebar variant

Background `#191B1C` (Gray 900), inactive labels `#B0B7BA` (Gray 300), active labels white with the same 3px Primary 500 left accent and a slightly lighter active bg (`rgba(255,255,255,0.06)`). Section headings stay Gray 400.

### Navy-sidebar variant

Background `#10204A` (deep navy). Same color logic as the dark variant.

---

## Top Navigation (1640 × 72)

```html
<header class="ayla-topnav">
  <div class="ayla-search">
    <i class="ph-magnifying-glass ayla-search__icon" aria-hidden="true"></i>
    <input type="search" class="ayla-search__input" placeholder="Search">
  </div>

  <div class="ayla-topnav__cluster">
    <button class="ayla-langpill" type="button">
      <img class="ayla-langpill__flag" src="/flags/us.png" alt="">
      <span>English</span>
      <i class="ph-caret-down" aria-hidden="true"></i>
    </button>
    <button class="ayla-iconbtn" aria-label="Layout"><i class="ph-layout"></i></button>
    <button class="ayla-iconbtn ayla-iconbtn--with-dot" aria-label="Notifications">
      <i class="ph-bell"></i>
      <span class="ayla-iconbtn__dot" aria-hidden="true"></span>
    </button>
    <button class="ayla-avatar" aria-label="Account">
      <img src="/avatar.jpg" alt="">
    </button>
  </div>
</header>
```

```css
.ayla-topnav {
  position: relative;
  height: 72px;
  background: var(--color-white);
  padding: 16px 40px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  box-shadow: inset 1px 0 0 0 #F2F3F4;  /* a hairline against the sidebar edge */
}

.ayla-search {
  position: relative;
  width: 240px;
  height: 40px;
}
.ayla-search__icon {
  position: absolute;
  left: 16px;
  top: 50%;
  transform: translateY(-50%);
  font-size: 20px;
  color: var(--color-gray-400);
}
.ayla-search__input {
  width: 100%;
  height: 100%;
  background: rgba(242, 243, 244, 0.5);
  border: 0;
  border-radius: var(--radius-sm);
  padding: 10px 16px 10px 48px;
  font: 400 14px/20px 'Public Sans', sans-serif;
  color: var(--color-gray-900);
}
.ayla-search__input::placeholder { color: var(--color-gray-400); }

.ayla-topnav__cluster {
  display: flex;
  align-items: center;
  gap: 16px;
}

.ayla-langpill {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  height: 32px;
  padding: 0 4px 0 12px;
  background: var(--color-gray-50);
  border: 0;
  border-radius: var(--radius-sm);
  font: 400 14px/20px 'Public Sans', sans-serif;
  color: var(--color-gray-700);
  cursor: pointer;
}
.ayla-langpill__flag { width: 16px; height: 16px; border-radius: 50%; object-fit: cover; }
.ayla-langpill i { font-size: 16px; color: var(--color-gray-400); }

.ayla-iconbtn {
  position: relative;
  width: 20px;
  height: 20px;
  background: transparent;
  border: 0;
  padding: 0;
  color: var(--color-gray-700);
  cursor: pointer;
}
.ayla-iconbtn i { font-size: 20px; }
.ayla-iconbtn__dot {
  position: absolute;
  top: 0;
  right: 0;
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: var(--color-danger-500);
  box-shadow: 0 0 0 2px var(--color-white);
}

.ayla-avatar {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  background: var(--color-warning-200);
  border: 0;
  padding: 0;
  overflow: hidden;
  cursor: pointer;
}
.ayla-avatar img { width: 32px; height: 32px; margin: 4px; border-radius: 50%; object-fit: cover; }
```

---

## Breadcrumbs (1560 × ~51)

Two layouts share this row:

1. **Title + trail**: page title on the left (24px SemiBold), `Home / Section / Current` trail on the right (14px Medium Gray 600, current page Gray 900).
2. **Title + action buttons**: page title on the left, action buttons cluster on the right (e.g., the Kanban "Add Label" / "Create New" pair).

```html
<div class="ayla-breadcrumbs">
  <h1 class="ayla-breadcrumbs__title">Dashboard</h1>
  <nav class="ayla-breadcrumbs__trail" aria-label="Breadcrumb">
    <a href="#">Home</a>
    <span aria-hidden="true">/</span>
    <a href="#">Analytics</a>
    <span aria-hidden="true">/</span>
    <span class="is-current" aria-current="page">Overview</span>
  </nav>
</div>
```

```css
.ayla-breadcrumbs {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
  height: 51px;
}
.ayla-breadcrumbs__title {
  margin: 0;
  font: 600 24px/32px 'Public Sans', sans-serif;
  color: var(--color-gray-900);
}
.ayla-breadcrumbs__trail {
  display: flex;
  align-items: center;
  gap: 6px;
  font: 500 14px/20px 'Public Sans', sans-serif;
  color: var(--color-gray-600);
}
.ayla-breadcrumbs__trail a { color: var(--color-gray-600); text-decoration: none; }
.ayla-breadcrumbs__trail .is-current { color: var(--color-gray-900); }
```

---

## Footer (1560 × 68)

```html
<footer class="ayla-footer">
  <p>&copy; 2026 Ayla. All rights reserved.</p>
  <p>v1.0.0</p>
</footer>
```

```css
.ayla-footer {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
  height: 68px;
  font: 400 14px/20px 'Public Sans', sans-serif;
  color: var(--color-gray-600);
}
.ayla-footer p { margin: 0; }
```

---

## Buttons

The source uses a small set of button shapes. All have 4px radius, 40px tall (default), 14px SemiBold label.

### Variants

| Variant | Background | Text | Border |
| --- | --- | --- | --- |
| Primary | `--color-primary-500` (`#005CE8`) | white | none |
| Secondary | white | `--color-primary-500` | `1px solid --color-primary-500` |
| Subtle | `--color-gray-50` | `--color-gray-900` | none |
| Danger | `--color-danger-500` | white | none |
| Ghost / Cancel | transparent | `--color-gray-600` | none |
| Icon-only | white | `--color-gray-700` | `1px solid --color-gray-100` |

### Sizes

| Size | Height | Padding | Font |
| --- | --- | --- | --- |
| Default | 40 | 10px 16px | 14 SemiBold |
| Compact | 32 | 6px 12px | 12 SemiBold |
| Square (icon-only) | 36 × 36 | 10px | — |

### HTML

```html
<button class="ayla-btn ayla-btn--primary" type="button">Save Changes</button>
<button class="ayla-btn ayla-btn--secondary" type="button">Cancel</button>
<button class="ayla-btn ayla-btn--subtle" type="button">Skip</button>
<button class="ayla-btn ayla-btn--icon" type="button" aria-label="Edit"><i class="ph-pencil"></i></button>
```

### CSS

```css
.ayla-btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  height: 40px;
  padding: 0 16px;
  border-radius: var(--radius-sm);
  border: 0;
  cursor: pointer;
  font: 600 14px/20px 'Public Sans', sans-serif;
  white-space: nowrap;
  user-select: none;
}
.ayla-btn:focus-visible {
  outline: 2px solid var(--color-primary-500);
  outline-offset: 2px;
}

.ayla-btn--primary  { background: var(--color-primary-500); color: var(--color-white); }
.ayla-btn--primary:hover  { background: #004FC6; }

.ayla-btn--secondary { background: var(--color-white); color: var(--color-primary-500); box-shadow: inset 0 0 0 1px var(--color-primary-500); }
.ayla-btn--secondary:hover { background: var(--color-primary-50); }

.ayla-btn--subtle { background: var(--color-gray-50); color: var(--color-gray-900); }
.ayla-btn--subtle:hover { background: var(--color-gray-100); }

.ayla-btn--danger { background: var(--color-danger-500); color: var(--color-white); }

.ayla-btn--ghost { background: transparent; color: var(--color-gray-600); }
.ayla-btn--ghost:hover { color: var(--color-gray-900); }

.ayla-btn--icon {
  width: 36px; height: 36px; padding: 0;
  background: var(--color-white); color: var(--color-gray-700);
  box-shadow: inset 0 0 0 1px var(--color-gray-100);
}
.ayla-btn--icon i { font-size: 16px; }
```

---

## Badges & pills

Small inline status markers. 4px radius, 4px-8px horizontal padding, 12px Medium text.

```css
.ayla-badge {
  display: inline-flex;
  align-items: center;
  gap: 4px;
  height: 24px;
  padding: 0 8px;
  border-radius: var(--radius-sm);
  font: 500 12px/1 'Public Sans', sans-serif;
}
.ayla-badge--success { background: var(--color-success-50);  color: var(--color-success-500); }
.ayla-badge--danger  { background: #FDECEC;                  color: var(--color-danger-500); }
.ayla-badge--warning { background: var(--color-warning-200); color: #7A4400; }
.ayla-badge--info    { background: var(--color-primary-50);  color: var(--color-primary-500); }
.ayla-badge--neutral { background: var(--color-gray-50);     color: var(--color-gray-700); }
```

## Card shell

All "boxes" on the dashboard share the same chrome. Define one class:

```css
.ayla-card {
  background: var(--color-white);
  border-radius: var(--radius-md);
  padding: 24px;
}
```

Some cards have an internal "Heading" row at the top — a 56px-tall row containing the card title (16px SemiBold) and optionally a kebab menu icon at the right. Inside the Heading, content padding can drop to `24px` horizontal, `16px` vertical.
