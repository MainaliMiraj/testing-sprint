# TC_019 Email max length (254 chars)

- Module: Login
- Preconditions: On login page
- Priority: Medium
- Type: Functional
- Status: Pass

## Steps
Enter 254-char email; enter valid password; submit.

## Expected
Login succeeds if email is valid; handled without truncation errors.
