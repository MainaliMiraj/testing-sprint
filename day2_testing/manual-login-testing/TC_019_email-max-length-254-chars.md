# TC_019 Email max length (254 chars)

- Summary: Email max length (254 chars)
- Module: Login
- Preconditions: On login page
- Priority: Medium
- Type: Functional
- Status: Pass
- Test Data: N/A

## Steps
1. Enter 254-char email
2. Enter valid password
3. Submit

## Expected Result
Login succeeds if email is valid; handled without truncation errors.
