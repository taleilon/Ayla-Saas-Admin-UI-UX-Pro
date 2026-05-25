# Forms

All form atoms in the system, plus the assembled login / register / advanced form patterns.

## The field block

Every input is wrapped in a 66px-tall "field" block: a 20px label row, a 6px gap, and a 40px input row.

```html
<div class="ayla-field">
  <label class="ayla-field__label" for="email">Email</label>
  <input class="ayla-input" id="email" type="email" placeholder="you@example.com">
</div>
```

```css
.ayla-field { display: flex; flex-direction: column; gap: 6px; }
.ayla-field__label {
  font: 500 14px/20px 'Public Sans', sans-serif;
  color: var(--color-gray-900);
}
.ayla-field__hint {
  font: 400 12px/14px 'Public Sans', sans-serif;
  color: var(--color-gray-600);
}
.ayla-field--error .ayla-input { border-color: var(--color-danger-500); }
.ayla-field--error .ayla-field__hint { color: var(--color-danger-500); }
```

## Text input

```css
.ayla-input {
  height: 40px;
  width: 100%;
  background: var(--color-white);
  border: 1px solid var(--color-gray-100);
  border-radius: var(--radius-sm);
  padding: 10px 12px;
  font: 400 14px/20px 'Public Sans', sans-serif;
  color: var(--color-gray-900);
  outline: 0;
  transition: border-color .12s, box-shadow .12s;
}
.ayla-input::placeholder { color: var(--color-gray-400); }
.ayla-input:focus {
  border-color: var(--color-primary-500);
  box-shadow: 0 0 0 3px rgba(0, 92, 232, 0.12);
}
.ayla-input:disabled {
  background: var(--color-gray-50);
  color: var(--color-gray-400);
  cursor: not-allowed;
}
```

### With a left icon

```html
<div class="ayla-input-wrap">
  <i class="ph-magnifying-glass ayla-input-wrap__icon"></i>
  <input class="ayla-input ayla-input--with-icon" type="text" placeholder="Search">
</div>
```

```css
.ayla-input-wrap { position: relative; }
.ayla-input-wrap__icon {
  position: absolute;
  left: 12px;
  top: 50%;
  transform: translateY(-50%);
  font-size: 20px;
  color: var(--color-gray-400);
  pointer-events: none;
}
.ayla-input--with-icon { padding-left: 40px; }
```

### Textarea (Message field)

```html
<div class="ayla-field">
  <label class="ayla-field__label" for="message">Message</label>
  <textarea class="ayla-input ayla-textarea" id="message" rows="3" placeholder="Type your message…"></textarea>
</div>
```

```css
.ayla-textarea {
  height: 88px;
  resize: vertical;
  padding: 10px 12px;
}
```

## Select

Looks identical to a text input but with a chevron at the right.

```html
<div class="ayla-field">
  <label class="ayla-field__label" for="country">Country</label>
  <div class="ayla-input-wrap">
    <select class="ayla-input ayla-select" id="country">
      <option>United States</option>
      <option>Israel</option>
    </select>
    <i class="ph-caret-down ayla-input-wrap__icon ayla-input-wrap__icon--right"></i>
  </div>
</div>
```

```css
.ayla-select {
  appearance: none;
  -webkit-appearance: none;
  padding-right: 40px;
  background-image: none;
  cursor: pointer;
}
.ayla-input-wrap__icon--right { left: auto; right: 12px; }
```

### Select with leading dot (status / label picker)

Used in the Kanban "Create New" and Calendar "Create Label" modals. The select shows a colored 12px dot + a label.

```html
<button class="ayla-input ayla-select-button" type="button">
  <span class="ayla-dot" style="background: var(--color-danger-500)"></span>
  <span>Urgent</span>
  <i class="ph-caret-down" style="margin-left: auto"></i>
</button>
```

```css
.ayla-select-button {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  text-align: left;
  cursor: pointer;
}
.ayla-dot { width: 12px; height: 12px; border-radius: 50%; flex: none; }
```

## Checkbox

20px square, 4px radius. Checked = filled Primary 500 with white check.

```html
<label class="ayla-todo">
  <input type="checkbox" class="ayla-checkbox">
  <span>I agree with all of your terms &amp; conditions.</span>
</label>
```

```css
.ayla-todo {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  cursor: pointer;
  font: 400 14px/20px 'Public Sans', sans-serif;
  color: var(--color-gray-900);
}

.ayla-checkbox {
  appearance: none;
  -webkit-appearance: none;
  width: 20px;
  height: 20px;
  border: 1px solid var(--color-gray-300);
  border-radius: var(--radius-sm);
  background: var(--color-white);
  cursor: pointer;
  display: grid;
  place-items: center;
  flex: none;
}
.ayla-checkbox:checked {
  background: var(--color-primary-500);
  border-color: var(--color-primary-500);
}
.ayla-checkbox:checked::after {
  content: "";
  width: 12px;
  height: 12px;
  background: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='white' stroke-width='3' stroke-linecap='round' stroke-linejoin='round'><polyline points='20 6 9 17 4 12'/></svg>") center/contain no-repeat;
}
```

## Radio

20px circle, same logic.

```html
<label class="ayla-todo">
  <input type="radio" class="ayla-radio" name="layout" checked>
  <span>Vertical</span>
</label>
```

```css
.ayla-radio {
  appearance: none;
  -webkit-appearance: none;
  width: 20px;
  height: 20px;
  border: 1px solid var(--color-gray-300);
  border-radius: 50%;
  background: var(--color-white);
  cursor: pointer;
  display: grid;
  place-items: center;
  flex: none;
}
.ayla-radio:checked { border-color: var(--color-primary-500); border-width: 6px; }
```

## Switch

32×20 pill with a 16px circular knob.

```html
<label class="ayla-todo">
  <button type="button" class="ayla-switch" role="switch" aria-checked="true">
    <span></span>
  </button>
  <span>Notifications</span>
</label>
```

```css
.ayla-switch {
  position: relative;
  width: 32px;
  height: 20px;
  background: var(--color-gray-300);
  border: 0;
  border-radius: 9999px;
  padding: 0;
  cursor: pointer;
  flex: none;
  transition: background .15s;
}
.ayla-switch::after {
  content: "";
  position: absolute;
  top: 2px;
  left: 2px;
  width: 16px;
  height: 16px;
  background: var(--color-white);
  border-radius: 50%;
  transition: transform .15s;
  box-shadow: 0 1px 2px rgba(0,0,0,0.15);
}
.ayla-switch[aria-checked="true"] { background: var(--color-primary-500); }
.ayla-switch[aria-checked="true"]::after { transform: translateX(12px); }
```

## Assembled patterns

### Vertical form column (768 wide form block)

Each field full-width, stacked with 16px gaps between fields.

```html
<form class="ayla-card ayla-form" style="width: 768px">
  <header class="ayla-card__heading">
    <h2 class="ayla-card__title">Personal Info</h2>
  </header>

  <div class="ayla-field"><label class="ayla-field__label" for="f1">Text Field</label><input id="f1" class="ayla-input"></div>
  <div class="ayla-field"><label class="ayla-field__label" for="f2">Email</label><input id="f2" type="email" class="ayla-input"></div>
  <div class="ayla-field"><label class="ayla-field__label" for="f3">Password</label><input id="f3" type="password" class="ayla-input"></div>

  <button class="ayla-btn ayla-btn--primary" type="submit">Save Changes</button>
</form>
```

```css
.ayla-form { display: flex; flex-direction: column; gap: 16px; }
.ayla-form .ayla-btn { align-self: flex-start; }
```

### Two-column "advance" form (1560 wide)

Field pairs side-by-side, full-width fields for address lines, then a 3-column row for Country / City / Zip Code.

```html
<form class="ayla-card ayla-form" style="width: 1560px">
  <header class="ayla-card__heading"><h2 class="ayla-card__title">Advance Form</h2></header>

  <div class="ayla-form__row">
    <div class="ayla-field"><label class="ayla-field__label">Email</label><input class="ayla-input" type="email"></div>
    <div class="ayla-field"><label class="ayla-field__label">Email</label><input class="ayla-input" type="email"></div>
  </div>
  <div class="ayla-form__row">
    <div class="ayla-field"><label class="ayla-field__label">Password</label><input class="ayla-input" type="password"></div>
    <div class="ayla-field"><label class="ayla-field__label">Password</label><input class="ayla-input" type="password"></div>
  </div>
  <div class="ayla-field"><label class="ayla-field__label">Address Line 1</label><input class="ayla-input"></div>
  <div class="ayla-field"><label class="ayla-field__label">Address Line 2</label><input class="ayla-input"></div>
  <div class="ayla-form__row ayla-form__row--3">
    <div class="ayla-field"><label class="ayla-field__label">Country</label><select class="ayla-input"></select></div>
    <div class="ayla-field"><label class="ayla-field__label">City</label><select class="ayla-input"></select></div>
    <div class="ayla-field"><label class="ayla-field__label">Zip Code</label><input class="ayla-input"></div>
  </div>

  <label class="ayla-todo"><input type="checkbox" class="ayla-checkbox"> Check this to confirm you're not a robot</label>

  <button class="ayla-btn ayla-btn--primary" type="submit">Save</button>
</form>
```

```css
.ayla-form__row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}
.ayla-form__row--3 {
  /* row math: 740 + 550 + 174 = 1464, plus two 16px gaps = 1496 */
  grid-template-columns: 740fr 550fr 174fr;
}
```

### Login screen (auth_login_node `321:20979`)

Centered card on a plain white page. Card is 506×440. Inside: 32px padding, a 32px title row, two stacked fields (Email + Password), a "Forget Password" link aligned right inside the password label row, a full-width primary "Login" button, an "or Login with" divider, and three 134-wide social buttons.

```html
<main class="ayla-auth">
  <div class="ayla-auth__logo"><img src="/logo.svg" alt="Ayla"></div>

  <section class="ayla-card ayla-auth__card">
    <h1 class="ayla-auth__title">Login to your account</h1>

    <div class="ayla-field">
      <label class="ayla-field__label" for="login-email">Email</label>
      <input class="ayla-input" id="login-email" type="email">
    </div>

    <div class="ayla-field">
      <div class="ayla-field__label-row">
        <label class="ayla-field__label" for="login-password">Password</label>
        <a class="ayla-link" href="#">Forget Password</a>
      </div>
      <input class="ayla-input" id="login-password" type="password">
    </div>

    <button class="ayla-btn ayla-btn--primary ayla-btn--block" type="submit">Login</button>

    <div class="ayla-auth__divider"><span>or Login with</span></div>

    <div class="ayla-auth__socials">
      <button class="ayla-btn ayla-btn--icon ayla-btn--block"><img src="/google.svg" alt=""> Google</button>
      <button class="ayla-btn ayla-btn--icon ayla-btn--block"><img src="/apple.svg" alt=""> Apple</button>
      <button class="ayla-btn ayla-btn--icon ayla-btn--block"><img src="/github.svg" alt=""> GitHub</button>
    </div>
  </section>

  <p class="ayla-auth__alt">Don't have an account? <a href="#">Create Account</a></p>
</main>
```

```css
.ayla-auth {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 32px;
  padding: 80px 24px;
}
.ayla-auth__logo img { width: 209px; height: 50px; }
.ayla-auth__card {
  width: 506px;
  padding: 40px;
  display: flex;
  flex-direction: column;
  gap: 16px;
}
.ayla-auth__title {
  margin: 0 0 16px;
  font: 600 24px/32px 'Public Sans', sans-serif;
  color: var(--color-gray-900);
}
.ayla-field__label-row { display: flex; justify-content: space-between; align-items: center; }
.ayla-link { color: var(--color-primary-500); text-decoration: none; font: 500 14px/20px 'Public Sans', sans-serif; }

.ayla-btn--block { width: 100%; }

.ayla-auth__divider {
  position: relative;
  text-align: center;
  margin: 12px 0;
  font: 500 12px/1 'Public Sans', sans-serif;
  color: var(--color-gray-400);
}
.ayla-auth__divider::before,
.ayla-auth__divider::after {
  content: "";
  position: absolute;
  top: 50%;
  width: calc(50% - 56px);
  height: 1px;
  background: var(--color-gray-100);
}
.ayla-auth__divider::before { left: 0; }
.ayla-auth__divider::after  { right: 0; }
.ayla-auth__divider span { padding: 0 8px; background: var(--color-white); }

.ayla-auth__socials { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 12px; }
.ayla-auth__alt { font: 400 14px/20px 'Public Sans', sans-serif; color: var(--color-gray-600); }
.ayla-auth__alt a { color: var(--color-primary-500); text-decoration: none; font-weight: 500; }
```

### Register screen (auth_register node `326:21253`)

Same as Login but the card is 1010×522 — a 504×522 photo panel on the left and a 506×522 form on the right. Form has Name + Email side-by-side, then Password, then Confirm Password, then Create Account button, then the same social cluster.

The photo panel uses `border-radius: 8px 0 0 8px` (rounded on the left only) and the form panel `border-radius: 0 8px 8px 0`. They sit in a flex row inside `.ayla-auth__card--split` with `padding: 0; gap: 0; overflow: hidden`.
