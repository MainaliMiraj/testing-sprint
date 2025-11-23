# TC_015 SQL injection attempt

- Module: Login
- Preconditions: On login page
- Priority: High
- Type: Security
- Status: Pass

## Steps
Enter "' OR 1=1 --" in email; any password; submit.

## Expected
Login blocked; error for invalid credentials.
