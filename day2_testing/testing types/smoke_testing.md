# ✅ **Smoke Test Cases**

**Definition:** A quick, high-level check of critical application flows to ensure the build is stable enough for further testing.

---

## **TC-301 | Homepage Loads Cleanly**

**Test Type:** Smoke / Functional
**Priority:** High

**Preconditions:**

- None.

**Steps:**

1. Open the homepage.
2. Click the primary navigation links (e.g., Home, Dashboard, Profile, etc.).
3. Observe the browser console for errors.

**Expected Result:**

- Homepage renders successfully.
- Navigation links respond and switch pages without delays.
- No critical console, network, or rendering errors appear.

---

## **TC-302 | Valid Login (Known-Good User)**

**Test Type:** Smoke / Functional
**Priority:** Critical

**Preconditions:**

- Valid user credentials are available.

**Test Data:**

- Email: `valid_user@example.com`
- Password: `ValidPass123`

**Steps:**

1. Navigate to the login page.
2. Enter valid credentials.
3. Click **Login**.

**Expected Result:**

- Authentication succeeds without errors.
- Dashboard loads essential widgets/components.
- No blockers or major UI/network issues.

---

## **TC-303 | Logout Returns to Public Page**

**Test Type:** Smoke / Security / Functional
**Priority:** High

**Preconditions:**

- User is logged in.

**Steps:**

1. Click **Logout**.
2. Press the browser **Back** button.

**Expected Result:**

- User is redirected to the public/landing page.
- Session is cleared (cookie/local storage removed).
- Back button does **not** return to any authenticated pages.

---

## **TC-304 | Password Reset Request Works**

**Test Type:** Smoke / Functional
**Priority:** Medium

**Preconditions:**

- Registered email exists.

**Test Data:**

- Email: `valid_user@example.com`

**Steps:**

1. Navigate to the **Forgot Password** page.
2. Enter a registered email.
3. Submit the password reset request.

**Expected Result:**

- Page loads without errors.
- Success message appears.
- No server-side or client-side errors in UI or console.

---

## **TC-305 | Account Settings Page Loads Successfully**

**Test Type:** Smoke / Functional / UI
**Priority:** Medium

**Preconditions:**

- User is logged in.
- User has existing profile data.

**Steps:**

1. Navigate to the **Account Settings** page.
2. Observe data population and UI component rendering.

**Expected Result:**

- Page loads quickly and without errors.
- Profile data (name, email, phone, etc.) populates correctly.
- No broken components, missing data, or console errors.

---
