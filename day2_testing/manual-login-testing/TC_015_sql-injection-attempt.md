# TC_015 SQL injection attempt

- Summary: SQL injection attempt
- Module: Login
- Preconditions: On login page
- Priority: High
- Type: Security
- Status: Pass
- Test Data: N/A

## Steps
1. Enter "' OR 1=1 --" in email
2. Any password
3. Submit

## Expected Result
Login blocked; error for invalid credentials.
