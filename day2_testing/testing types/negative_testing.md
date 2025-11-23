

# ✅Negative Test Cases

**Definition:** Ensures the system gracefully handles invalid, unexpected, or malicious inputs without crashing, exposing vulnerabilities, or leaking sensitive information.

---

## **TC-101 | Incorrect Password Should Not Authenticate**

**Test Type:** Negative / Functional / Security
**Priority:** High

**Preconditions:**

* User account exists with a known email.
* Account is not locked or rate-limited.

**Test Data:**

* Email: `valid_user@example.com`
* Password: `WrongPassword!`

**Steps:**

1. Navigate to the login page.
2. Enter valid email and an incorrect password.
3. Click **Login**.

**Expected Result:**

* Error message displayed: “Invalid credentials”.
* No session token or cookie is created.
* User remains on login page.
* Lockout/brute-force rules behave as expected.

---

## **TC-102 | Password Reset with Unregistered Email**

**Test Type:** Negative / Security / Privacy
**Priority:** High

**Preconditions:**

* None.

**Test Data:**

* Email: `unknown_user@example.com`

**Steps:**

1. Navigate to the **Forgot Password** page.
2. Enter an unregistered email address.
3. Click **Send Reset Link**.

**Expected Result:**

* Generic success message displayed (no indication whether email exists).
* No email is sent.
* System does not reveal account existence (“email enumeration” protection).

---

## **TC-103 | Oversized Profile Picture Upload**

**Test Type:** Negative / Validation
**Priority:** Medium

**Preconditions:**

* User is logged in on the **Profile** page.
* Tester has an image file larger than the allowed size limit (e.g., >5MB).

**Test Data:**

* Oversized File: `large_image.jpg` (> allowed limit)

**Steps:**

1. Choose the oversized image file.
2. Attempt to upload or save the profile picture.

**Expected Result:**

* Validation error displayed: “File too large” or similar.
* File is not uploaded or stored.
* No server errors, crashes, or partial uploads occur.

---

## **TC-104 | Script Injection Attempt in Profile Name**

**Test Type:** Negative / Security (XSS Validation)
**Priority:** Critical

**Preconditions:**

* User is logged in on the **Profile Edit** page.

**Test Data:**

* Name field input: `<script>alert(1)</script>`

**Steps:**

1. Enter `<script>alert(1)</script>` into the name field.
2. Click **Save**.

**Expected Result:**

* Input is rejected OR sanitized before saving.
* UI displays safe text or validation error.
* No script is executed in the browser.
* No XSS vulnerability.

---

## **TC-105 | Expired or Tampered Password Reset Token**

**Test Type:** Negative / Security
**Priority:** High

**Preconditions:**

* Tester possesses an expired or modified reset token (URL or JWT).

**Test Data:**

* Expired token link OR tampered link with altered token parameter.

**Steps:**

1. Open the expired or tampered password reset link.
2. Attempt to set a new password.

**Expected Result:**

* Reset request is blocked.
* Error message shown: “Invalid or expired token”.
* User is prompted to request a new reset link.
* No password is changed.

---


