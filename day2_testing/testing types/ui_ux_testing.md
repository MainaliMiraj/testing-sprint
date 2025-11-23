---

# ✅ **UI/UX Test Cases**

**Definition:** Ensures the interface is visually consistent, readable, accessible, responsive, and behaves according to UX expectations.

---

## **TC-401 | Login Form Layout & Readability**

**Test Type:** UI / UX / Visual
**Priority:** Medium

**Preconditions:**

- None.

**Steps:**

1. Open the login page on a desktop viewport.
2. Switch to a mobile viewport (e.g., 375px width).
3. Inspect alignment between labels and inputs.
4. Review font sizes, spacing, and element visibility.

**Expected Result:**

- Labels align with the correct input fields.
- Font size meets readability standards (14px+).
- Primary CTA button is visible without scrolling.
- No overlapping, clipping, or misaligned UI elements.

---

## **TC-402 | Keyboard Navigation & Focus Order**

**Test Type:** Accessibility / UX
**Priority:** High

**Preconditions:**

- None.

**Steps:**

1. Use the **Tab** key to navigate the login form from top to bottom.
2. Observe visual focus indicators on each element.
3. Press **Enter** on the final input or button.

**Expected Result:**

- Focus order follows the logical visual order.
- Focus outline is clearly visible and high contrast.
- Pressing **Enter** triggers the primary action (e.g., Login).
- No elements are skipped or require mouse interaction.

---

## **TC-403 | Error State Usability**

**Test Type:** UI / UX / Validation
**Priority:** High

**Preconditions:**

- Login page is accessible.

**Steps:**

1. Enter a valid email and an invalid password.
2. Submit the login form.
3. Observe the error styling and placement.

**Expected Result:**

- Clear, readable error message shown (inline or page-level).
- Error text meets contrast requirements (WCAG AA).
- Error state styling is consistent with design system.
- Helpful guidance provided (e.g., “Incorrect password”).

---

## **TC-404 | Responsive Layout Validations**

**Test Type:** UI / UX / Responsive Design
**Priority:** Medium

**Preconditions:**

- Login page is accessible.

**Steps:**

1. Resize viewport to **320px**, **768px**, and **1024px** widths.
2. Observe layout of form fields, CTAs, and navigation components.
3. Check mobile tap target usability.

**Expected Result:**

- No horizontal scrolling at any tested breakpoint.
- Elements stack properly at smaller widths.
- Primary actions (e.g., Login button) remain visible and reachable.
- Touch targets meet recommended minimum sizes (44px).

---

## **TC-405 | Password Show/Hide Toggle Behavior**

**Test Type:** UI / UX / Accessibility
**Priority:** Medium

**Preconditions:**

- Login form includes a password visibility toggle icon/button.

**Steps:**

1. Enter a password in the password field.
2. Click the **Show** icon/button.
3. Click the **Hide** icon/button.

**Expected Result:**

- Toggle control has an accessible name or ARIA label.
- Icon visually updates between show & hide states.
- Password value remains intact during toggle.
- Form state and cursor position remain unchanged.

---
