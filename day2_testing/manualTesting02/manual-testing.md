\*/
Tests in this flle:
Boundary tests (min character, max character)

Email format tests (wrong formats)

SQL Injection (test' OR '1'='1)

Case sensitivity tests

Space before/after input

Special characters

Multiple failed attempts (lockout scenario)

UI tests (button disabled? field placeholders?)

Remember Me functionality

Page navigation tests
\*/


---
---

# TC_001 Boundary Test (Min)

- Summary: Boundary test min-Character (Email & Password)
- Module: Login
- Preconditions: On login page
- Priority: High
- Type: Functional
- Status: Not executed
- Test Data: Email: "[a@b.com](mailto:a@b.com)", Password: "1"

## Steps

1. Enter minimum allowed email (e.g., "[a@b.com](mailto:a@b.com)")
2. Enter minimum allowed password (1 character)
3. Click Login

## Expected Result

System should show “Invalid username or password”.

---

# TC_002 Boundary Test (Max)

- Summary: Boundary test Max-Character (Email & Password)
- Module: Login
- Preconditions: On login page
- Priority: High
- Type: Functional
- Status: Not executed
- Test Data: Email length = 255 chars

## Steps

1. Enter 243 "a"s + "@mail.com" (total 255 chars)
2. Enter password with max allowed length
3. Click Login

## Expected Result

System should reject and show “Invalid username or password”.

---

# TC_003 Email Format (Missing @)

- Summary: Invalid email missing '@'
- Module: Login
- Preconditions: On login page
- Priority: High
- Type: Functional
- Status: Not executed
- Test Data: "usergmail.com"

## Steps

1. Enter email without @
2. Enter valid password
3. Click Login

## Expected Result

Validation error: “Enter a valid email address”.

---

# TC_004 Email Format (Missing domain)

- Summary: Email missing domain
- Module: Login
- Preconditions: On login page
- Priority: Medium
- Type: Functional
- Status: Not executed
- Test Data: "user@"

## Steps

1. Enter "user@"
2. Enter valid password
3. Click Login

## Expected Result

Validation error displayed.

---

# TC_005 Email Format (Missing username)

- Summary: Email missing username
- Module: Login
- Preconditions: On login page
- Priority: Medium
- Type: Functional
- Status: Not executed
- Test Data: "@gmail.com"

## Steps

1. Enter "@gmail.com"
2. Enter valid password
3. Click Login

## Expected Result

Validation error displayed.

---

# TC_006 Email Format (Double @)

- Summary: Invalid email with two '@'
- Module: Login
- Priority: Medium

## Steps

1. Enter "user@@gmail.com"
2. Enter valid password
3. Click Login

## Expected Result

Validation error displayed.

---

# TC_007 Email Format (Special chars)

- Summary: Email with invalid special characters
- Module: Login
- Priority: Medium

## Steps

1. Enter "user!@gmail.com"
2. Enter valid password
3. Click Login

## Expected Result

Validation error displayed.

---

# TC_008 Email Format (No .com TLD)

- Summary: Email without top-level domain
- Module: Login

## Steps

1. Enter "user@gmail"
2. Enter valid password
3. Click Login

## Expected Result

Validation error displayed.

---

# TC_009 SQL Injection (Email Field)

- Summary: SQL Injection attempt
- Module: Login
- Priority: High

## Steps

1. Enter: `test' OR '1'='1`
2. Enter any password
3. Click Login

## Expected Result

System should prevent login and sanitize input.

---

# TC_010 SQL Injection (Password Field)

- Summary: SQL Injection attempt in password
- Module: Login

## Steps

1. Enter valid email
2. Enter password: `abc' OR '1'='1`
3. Click Login

## Expected Result

Login blocked, input sanitized.

---

# TC_011 Case Sensitivity (Email)

- Summary: Email uppercase & lowercase handling
- Module: Login

## Steps

1. Enter email in uppercase ([USER@GMAIL.COM](mailto:USER@GMAIL.COM))
2. Enter valid password
3. Click Login

## Expected Result

Login succeeds (emails are case-insensitive).

---

# TC_012 Case Sensitivity (Password)

- Summary: Password case sensitivity
- Module: Login

## Steps

1. Enter correct email
2. Enter same password but with different case
3. Click Login

## Expected Result

Login fails.

---

# TC_013 Leading Space in Email

- Summary: Leading space before email
- Module: Login

## Steps

1. Enter " [user@gmail.com](mailto:user@gmail.com)"
2. Enter valid password
3. Click Login

## Expected Result

System should trim or show validation error.

---

# TC_014 Trailing Space in Email

- Summary: Space after email
- Module: Login

## Steps

1. Enter "[user@gmail.com](mailto:user@gmail.com) "
2. Enter valid password
3. Click Login

## Expected Result

System should trim or show validation error.

---

# TC_015 Leading/Trailing Spaces Password

- Summary: Spaces before/after password
- Module: Login

## Steps

1. Enter valid email
2. Enter " password123 "
3. Click Login

## Expected Result

Login fails (passwords must match exactly).

---

# TC_016 Special Characters Password

- Summary: Password with special characters
- Module: Login

## Steps

1. Enter valid email
2. Enter password with special chars !@#$%^&\*()
3. Click Login

## Expected Result

Should accept if special chars allowed.

---

# TC_017 Blank Email

- Summary: Click login with empty email
- Module: Login

## Steps

1. Leave email field empty
2. Enter valid password
3. Click Login

## Expected Result

Validation error: “Email required”.

---

# TC_018 Blank Password

- Summary: Click login with empty password
- Module: Login

## Steps

1. Enter valid email
2. Leave password blank
3. Click Login

## Expected Result

Validation error: “Password required”.

---

# TC_019 Multiple Failed Login Attempts

- Summary: Account lockout after multiple attempts
- Module: Login
- Priority: High

## Steps

1. Attempt login with incorrect password 5 times

## Expected Result

Account should lock after X attempts (based on requirement).

---

# TC_020 Login After Lockout

- Summary: Try login after lockout
- Module: Login

## Steps

1. After lockout, attempt correct login

## Expected Result

System blocks login until lockout expires.

---

# TC_021 UI Test – Login Button Disabled

- Summary: Check login button disabled for empty fields
- Module: UI

## Steps

1. Keep email & password empty
2. Check login button

## Expected Result

Button should be disabled.

---

# TC_022 UI Test – Placeholder Text

- Summary: Check field placeholders
- Module: UI

## Steps

1. Inspect email and password fields

## Expected Result

Email field placeholder: “Enter your email”
Password field placeholder: “Enter your password”.

---

# TC_023 UI Test – Password Masking

- Summary: Password characters masked
- Module: UI

## Steps

1. Enter characters in password field

## Expected Result

Characters replaced with bullets or asterisks.

---

# TC_024 Remember Me – Positive

- Summary: “Remember Me” stores login
- Module: Login

## Steps

1. Enter valid login
2. Check “Remember Me”
3. Login and refresh page

## Expected Result

User remains logged in.

---

# TC_025 Remember Me – Negative

- Summary: Without “Remember Me” user logged out
- Module: Login

## Steps

1. Login without selecting Remember Me
2. Close and reopen browser

## Expected Result

User is logged out.

---

# TC_026 Navigation – Forgot Password

- Summary: Verify navigation
- Module: Navigation

## Steps

1. Click “Forgot Password?”

## Expected Result

System navigates to password reset page.

---

# TC_027 Navigation – Sign Up Link

- Summary: Verify sign-up redirect
- Module: Navigation

## Steps

1. Click “Create Account”

## Expected Result

Redirect to registration page.

---

# TC_028 Successful Login Flow

- Summary: Valid login
- Module: Login

## Steps

1. Enter valid email
2. Enter valid password
3. Click Login

## Expected Result

Redirect to dashboard.

---

# TC_029 Invalid Credentials (General)

- Summary: Invalid login attempt
- Module: Login

## Steps

1. Enter random invalid email/password

## Expected Result

Error: “Invalid username or password”.

---

# TC_030 Session Timeout After Login

- Summary: Auto logout after inactivity
- Module: Login Session

## Steps

1. Login
2. Stay idle for X minutes

## Expected Result

Session expires & login screen appears.

---

# TC_031 Browser Back After Logout

- Summary: Ensure secure logout
- Module: Login

## Steps

1. Logout
2. Click browser back button

## Expected Result

User should NOT access previous pages.

---

# TC_032 Keyboard Shortcut Login

- Summary: Press Enter to login
- Module: UI

## Steps

1. Enter valid email & password
2. Press Enter

## Expected Result

Login should trigger.

---
