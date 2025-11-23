
---

# ✅ **Functional Test Cases

---

## **TC-001 | Valid Login Succeeds**

**Test Type:** Functional / Smoke
**Priority:** High

**Preconditions:**

* User account exists with valid email and password.
* User is on the login page.

**Test Data:**

* Email: `valid_user@example.com`
* Password: `ValidPass123`

**Steps:**

1. Navigate to the login page.
2. Enter valid email and valid password.
3. Click **Login**.

**Expected Result:**

* User is authenticated successfully.
* Dashboard/homepage loads.
* Session cookie or JWT token is created and stored.
* API returns status `200` with correct user profile data.

---

## **TC-002 | Password Reset Email Is Sent**

**Test Type:** Functional / Regression
**Priority:** High

**Preconditions:**

* User exists with a verified email.
* Tester has access to the mailbox.

**Test Data:**

* Registered email: `valid_user@example.com`

**Steps:**

1. Navigate to the **Forgot Password** page.
2. Enter the registered email.
3. Click **Send Reset Link**.

**Expected Result:**

* Success message is displayed.
* Password reset email is sent to the inbox.
* Email contains correct reset link or token.
* API returns status `200` or `202`.

---

## **TC-003 | Profile Update Persists After Refresh**

**Test Type:** Functional
**Priority:** Medium

**Preconditions:**

* User is logged in.
* User is on the **Profile** page.

**Test Data:**

* New Name: `Miraj QA`
* New Phone: `0450 123 456`

**Steps:**

1. Update the display name and phone number fields.
2. Click **Save**.
3. Refresh the page.
4. Reopen the **Profile** page.

**Expected Result:**

* Success message is shown.
* Updated name and phone appear after refresh.
* API response shows updated values.
* Status code returns `200`.

---

## **TC-004 | Logout Clears Session and Restricts Access**

**Test Type:** Functional / Security
**Priority:** High

**Preconditions:**

* User is logged in.

**Steps:**

1. Click **Logout**.
2. Attempt to open a protected route directly via URL (e.g., `/dashboard`).

**Expected Result:**

* User is redirected to login/public landing page.
* Session storage/local storage/cookies are cleared.
* Protected route cannot be accessed without re-login.
* API returns `401 Unauthorized` for protected endpoints.

---

## **TC-005 | Account Deletion Prevents Future Login**

**Test Type:** Functional / Security
**Priority:** High

**Preconditions:**

* User is logged in with an active account.

**Steps:**

1. Navigate to **Account Settings → Delete Account**.
2. Confirm the deletion action.
3. Log out (if not done automatically).
4. Attempt to log in again using the same credentials.

**Expected Result:**

* Account is deleted or disabled.
* Login attempt fails with a descriptive error:

  * “Account not found” or
  * “Account disabled”.
* API returns `404 Not Found` or `403 Forbidden` depending on system design.

---

## **TC-006 | Invalid Login Shows Error Message**

**Test Type:** Negative / Functional
**Priority:** High

**Preconditions:**

* User is on the login page.

**Test Data:**

* Email: `valid_user@example.com`
* Password: `WrongPassword!`

**Steps:**

1. Navigate to the login page.
2. Enter valid email and invalid password.
3. Click **Login**.

**Expected Result:**

* Login fails.
* Error message shown: “Invalid credentials”.
* User stays on login page.
* API returns `401 Unauthorized`.

---

## **TC-007 | Required Fields Validation on Profile Page**

**Test Type:** Functional / Validation
**Priority:** Medium

**Preconditions:**

* User is on the profile page.

**Steps:**

1. Clear mandatory fields (e.g., Name, Email).
2. Click **Save**.

**Expected Result:**

* Validation messages show for required fields.
* Save action is blocked until mandatory fields are filled.
* API is not called (No network request triggered).

---

## **TC-008 | Session Expiry Redirects to Login**

**Test Type:** Functional / Security
**Priority:** Medium

**Preconditions:**

* User is logged in.
* Session expiry time is known or manually manipulated.

**Steps:**

1. Wait for session token to expire OR manually delete the token from storage.
2. Attempt navigating to a protected route.

**Expected Result:**

* User is redirected to login.
* A message appears: “Session expired” (if implemented).
* API returns `401 Unauthorized`.

---

## **TC-009 | Form Input Should Reject Invalid Phone Number**

**Test Type:** Functional / Validation
**Priority:** Medium

**Test Data:**

* Name: `Miraj`
* Phone: `abc123` (invalid)

**Steps:**

1. Go to the Profile page.
2. Enter invalid phone number format.
3. Click **Save**.

**Expected Result:**

* Validation error is shown: “Invalid phone number”.
* Profile is not updated.
* API call is blocked or API returns `400 Bad Request`.

---

## **TC-010 | UI Should Load User Profile on Login**

**Test Type:** Functional / Integration
**Priority:** High

**Preconditions:**

* User exists with valid profile details.

**Steps:**

1. Log in with valid credentials.
2. Navigate to Profile page.

**Expected Result:**

* Profile fields load with correct user data.
* No empty/undefined fields.
* API returns `200 OK` with profile JSON.

---

