

---

# ✅ **Regression Test Cases**

**Definition:** Re-validates existing features to ensure recent changes, deployments, or fixes did not break previously working functionality.

---

## **TC-201 | Valid Login After Auth Middleware Changes**

**Test Type:** Regression / Functional
**Priority:** High

**Preconditions:**

* A known-good user exists.
* Build containing updated authentication middleware is deployed.

**Test Data:**

* Email: `valid_user@example.com`
* Password: `ValidPass123`

**Steps:**

1. Navigate to the login page.
2. Enter valid credentials and submit.
3. Navigate to a protected page (e.g., `/dashboard`).

**Expected Result:**

* Login succeeds without errors.
* Session token/cookie is created correctly.
* Protected page loads successfully.
* No new console, network, or backend log errors.

---

## **TC-202 | Password Reset After Email Provider Change**

**Test Type:** Regression / Integration
**Priority:** High

**Preconditions:**

* Email provider/SMTP service has been changed.
* QA has access to a test email inbox.

**Test Data:**

* Email: `valid_user@example.com`

**Steps:**

1. Request a password reset using a registered email.
2. Open the received email and click the reset link.
3. Set a new password.
4. Attempt login using the new password.

**Expected Result:**

* Reset email arrives successfully with correct subject, body, and reset link.
* Reset link works and allows password change.
* User can log in using the newly set password.
* No delivery delays, formatting issues, or incorrect links.

---

## **TC-203 | Profile Update After Schema Migration**

**Test Type:** Regression / Data Integrity
**Priority:** Medium

**Preconditions:**

* Database schema migration has been completed.
* User can access the Profile page.

**Test Data:**

* Updated Name: `QA Test User`
* Updated Phone: `0412 345 678`

**Steps:**

1. Modify profile fields (e.g., display name, phone number).
2. Click **Save**.
3. Refresh the page.
4. (Optional) Trigger GET `/profile` API to fetch latest user data.

**Expected Result:**

* Updated profile values persist correctly after reload and API fetch.
* No data corruption, data loss, or type errors.
* UI and API return consistent values.
* No migration-related fallback or casting errors.

---

## **TC-204 | Logout Behavior After Remember-Me Feature**

**Test Type:** Regression / Security
**Priority:** High

**Preconditions:**

* Remember-me functionality has been deployed.
* User is logged in with “Remember Me” enabled.

**Steps:**

1. Click **Logout**.
2. Attempt to access a protected route manually (e.g., via URL).
3. Inspect cookies/local storage/session storage for remaining tokens.

**Expected Result:**

* User is logged out completely.
* Remember-me token is cleared or invalidated.
* Protected route redirects to login page.
* No stale session or remember-me artifacts remain in storage.

---

## **TC-205 | Account Deletion After Caching Layer Changes**

**Test Type:** Regression / Security
**Priority:** High

**Preconditions:**

* Caching layer (Redis, CDN, etc.) has been updated.
* Valid user account exists.

**Test Data:**

* Account credentials: user to be deleted.

**Steps:**

1. Delete the user account via UI.
2. Attempt to log in again using the deleted account credentials.
3. Attempt authenticated API calls using the old token (if available).

**Expected Result:**

* Account deletion is acknowledged and completed successfully.
* Subsequent login attempts are blocked.
* API calls with old tokens return `401 Unauthorized` or `403 Forbidden`.
* No cached data is served for a deleted account.
* No stale tokens remain valid after deletion.

---

