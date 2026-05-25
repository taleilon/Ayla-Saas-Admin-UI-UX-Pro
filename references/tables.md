# Tables

Six table variants ship in the design. They share a column-header strip and a body of rows separated by 1px Gray 100 dividers — never full borders, never alternating row backgrounds (with one exception: the Striped variant). All sit inside a `.ayla-card` shell with 24px outer padding.

The variants:

1. **Basic** — header + rows + dividers. 768px wide.
2. **Striped** — alternating row backgrounds for scannability. 768px.
3. **Hoverable** — basic with hover state on rows; usually pairs with avatar cells.
4. **Highlight Column** — first column has a Primary-50 background strip the full height of the column.
5. **Advanced** — full-width (1560px), with avatar+name combined cell, pagination row, and "Showing X to Y of Z entries" caption.
6. **Small** — compact variant with denser rows (48px instead of 64px).

## Universal table CSS

Use this as a base; the variants extend it.

```css
.ayla-table {
  width: 100%;
  border-collapse: separate;
  border-spacing: 0;
  font: 400 14px/20px 'Public Sans', sans-serif;
  color: var(--color-gray-900);
}

.ayla-table thead th {
  height: 36px;
  padding: 12px 0;
  text-align: left;
  font: 600 12px/14px 'Public Sans', sans-serif;
  color: var(--color-gray-400);
  text-transform: uppercase;
  letter-spacing: 0;
  vertical-align: middle;
}
.ayla-table thead th:first-child { padding-left: 24px; }
.ayla-table thead th:last-child  { padding-right: 24px; text-align: right; }

.ayla-table tbody td {
  height: 36px;  /* visual; with vertical padding the row reads as ~52-64px */
  padding: 14px 0;
  vertical-align: middle;
  color: var(--color-gray-900);
  border-top: 1px solid var(--color-gray-100);
}
.ayla-table tbody tr:first-child td { border-top: 0; }
.ayla-table tbody td:first-child { padding-left: 24px; }
.ayla-table tbody td:last-child  { padding-right: 24px; text-align: right; }
```

## 1) Basic table

768px wide, ID / Name / Phone / Date of Birth / Action columns. Action column contains two 36×36 icon buttons (X and Check).

```html
<section class="ayla-card ayla-card--table">
  <header class="ayla-card__heading">
    <h2 class="ayla-card__title">Basic Table</h2>
    <button class="ayla-card__menu" aria-label="More"><i class="ph-dots-three"></i></button>
  </header>

  <table class="ayla-table">
    <thead>
      <tr>
        <th style="width: 88px">ID</th>
        <th style="width: 208px">Name</th>
        <th style="width: 124px">Phone</th>
        <th style="width: 124px">Date of Birth</th>
        <th style="width: 80px">Action</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>647</td>
        <td>Wade Warren</td>
        <td>(252) 555-0126</td>
        <td>Oct. 18, 1996</td>
        <td>
          <div class="ayla-table__actions">
            <button class="ayla-btn--icon" aria-label="Reject"><i class="ph-x"></i></button>
            <button class="ayla-btn--icon" aria-label="Approve"><i class="ph-check"></i></button>
          </div>
        </td>
      </tr>
      <!-- … -->
    </tbody>
  </table>
</section>
```

```css
.ayla-card__heading {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 0 16px;
  border-bottom: 1px solid var(--color-gray-100);
  margin-bottom: 8px;
}
.ayla-card__title {
  margin: 0;
  font: 600 16px/23px 'Public Sans', sans-serif;
  color: var(--color-gray-900);
}
.ayla-card__menu { background: transparent; border: 0; padding: 4px; color: var(--color-gray-400); cursor: pointer; font-size: 20px; }

.ayla-table__actions { display: inline-flex; gap: 8px; justify-content: flex-end; }
```

## 2) Striped table

Same as Basic but tbody rows alternate. Used for Social Media Traffic style data.

```css
.ayla-table--striped tbody tr:nth-child(even) td {
  background: var(--color-gray-50);
}
.ayla-table--striped tbody td { border-top: 0; }
```

## 3) Hoverable table (with avatar)

64px row height. First column is an avatar + name pair.

```html
<tr>
  <td>
    <div class="ayla-cell-avatar">
      <span class="ayla-cell-avatar__img"><img src="/u1.jpg" alt=""></span>
      <span>Darrell Steward</span>
    </div>
  </td>
  <td>tanya.hill@example.com</td>
  <td>(307) 555-0133</td>
</tr>
```

```css
.ayla-table--hoverable tbody tr { transition: background-color .12s; }
.ayla-table--hoverable tbody tr:hover td { background: var(--color-gray-50); }

.ayla-cell-avatar { display: inline-flex; align-items: center; gap: 12px; }
.ayla-cell-avatar__img {
  width: 32px; height: 32px; border-radius: 50%; overflow: hidden;
  background: var(--color-warning-200); flex: none;
}
.ayla-cell-avatar__img img { width: 100%; height: 100%; object-fit: cover; }
```

## 4) Highlight column

The first column visually pops with a Primary-50 background. The simplest implementation: wrap the first `<td>` content and paint its cell.

```css
.ayla-table--highlight tbody td:first-child {
  background: var(--color-primary-50);
  color: var(--color-gray-900);
  font-weight: 500;
}
.ayla-table--highlight thead th:first-child {
  background: var(--color-primary-50);
  color: var(--color-primary-500);
  border-radius: 8px 8px 0 0;
}
```

Pair with: the highlight strip extending to the top and bottom of the card. If you want the strip *outside* the data area too, render an absolutely-positioned 248px-wide rectangle behind the first column instead of cell backgrounds.

## 5) Advanced table (1560px, full-width)

User ID / Users / Email / Phone / Date of Birth / Location / Balance + pagination row.

```html
<section class="ayla-card ayla-card--table ayla-card--full">
  <header class="ayla-card__heading">
    <h2 class="ayla-card__title">All Users</h2>
    <div class="ayla-card__actions">
      <button class="ayla-btn ayla-btn--subtle ayla-btn--compact"><i class="ph-funnel"></i> Filter</button>
      <button class="ayla-btn ayla-btn--primary ayla-btn--compact"><i class="ph-plus"></i> Add User</button>
    </div>
  </header>

  <table class="ayla-table">
    <thead>
      <tr>
        <th style="width: 124px">User ID</th>
        <th style="width: 224px">Users</th>
        <th style="width: 148px">Email</th>
        <th style="width: 148px">Phone</th>
        <th style="width: 124px">Date of Birth</th>
        <th style="width: 424px">Location</th>
        <th style="width: 176px; text-align: right">Balance</th>
      </tr>
    </thead>
    <tbody>
      <!-- 6-8 rows -->
    </tbody>
  </table>

  <footer class="ayla-table-footer">
    <p>Showing 1 to 8 of 16 entries</p>
    <nav class="ayla-pagination" aria-label="Table pages">
      <button aria-label="Previous"><i class="ph-caret-left"></i></button>
      <button class="is-current" aria-current="page">1</button>
      <button>2</button>
      <button>3</button>
      <button>4</button>
      <button>5</button>
      <button aria-label="Next"><i class="ph-caret-right"></i></button>
    </nav>
  </footer>
</section>
```

```css
.ayla-card--full { padding: 0; }
.ayla-card--full .ayla-card__heading { padding: 24px; margin: 0; }
.ayla-card--full .ayla-table thead th { border-bottom: 1px solid var(--color-gray-100); }

.ayla-table-footer {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 16px 24px;
  border-top: 1px solid var(--color-gray-100);
  font: 400 14px/20px 'Public Sans', sans-serif;
  color: var(--color-gray-600);
}
.ayla-table-footer p { margin: 0; }

.ayla-pagination {
  display: inline-flex;
  align-items: center;
  gap: 4px;
}
.ayla-pagination button {
  min-width: 32px;
  height: 32px;
  padding: 0 8px;
  background: var(--color-white);
  border: 1px solid var(--color-gray-100);
  border-radius: var(--radius-sm);
  font: 500 14px/20px 'Public Sans', sans-serif;
  color: var(--color-gray-700);
  cursor: pointer;
}
.ayla-pagination button.is-current {
  background: var(--color-primary-500);
  border-color: var(--color-primary-500);
  color: var(--color-white);
}
.ayla-pagination button:disabled { opacity: 0.5; cursor: not-allowed; }
```

## 6) Small / compact table

48px rows, no avatar. Used in the dashboard sidebar widgets.

```css
.ayla-table--small tbody td { padding: 14px 0; height: 20px; }
.ayla-table--small tbody tr td { border-top: 1px solid var(--color-gray-100); }
.ayla-table--small thead th { height: 36px; padding: 12px 0; }
```

## Column-sizing rule of thumb

In a 768px-wide basic table, after subtracting 24px left + 24px right padding, you have 720px of content. Distribute columns roughly as:

- Numeric / short IDs: 88px
- Names: 208–272px
- Emails: 244px
- Phone: 124–156px
- Dates: 124px
- Actions: 80px (two 36-wide buttons + 8 gap)

For the 1560px advanced table, after the 24+24 padding (1512 content), columns become 124 / 224 / 148 / 148 / 124 / 424 / 176 (= 1368, with the rest absorbed in gaps).

## Sortable column treatment

Not in the source, but if needed: keep the 12px uppercase header text, suffix with a 16px Phosphor caret in Gray 400; on the active sort column, color the header text Gray 900 and the caret Primary 500.

## Empty state

Inside the card, after the heading row: a 200-tall centered block with a 120px illustration, 16px SemiBold heading, 14px Regular Gray 600 body, and a primary or subtle CTA button. The Blank Page screen (node `307:10305`) is a good reference.
