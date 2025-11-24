## Test Case 2- Successful Booking Creation
Test ID: API_TC_01
Title: Verify booking is created successfully with valid data
Preconditions:
API URL is accessible.
Steps:
Open Postman.
Set method to POST and URL to https://restful-booker.herokuapp.com/booking.
Set body type to raw → JSON.
Enter valid JSON payload (as above with firstname "Miraj").
Click Send.
Expected Result:
Status code is 200 or 201.
Response contains bookingid.
Response body’s firstname and lastname match the request body.

## Test Case 2 – Get Booking by ID

Test ID: API_TC_02
Title: Verify booking details for a valid booking ID
Preconditions:
A booking exists with known ID (add:2913 as booking ID).
Steps:
Send GET request to https://restful-booker.herokuapp.com/booking/{bookingid}.
Use the bookingid created in TC_01.
Expected Result:
Status code 200.
Response fields (firstname, lastname, etc.) match the booking created in TC_01.

## Test Case 3 – Invalid Booking ID

Test ID: API_TC_03
Title: Verify error for non-existent booking ID
Precondition:
API URL is accessible.
Steps:
Send GET request to https://restful-booker.herokuapp.com/booking/99999999.
Expected Result:
Expected status: 404 (or whatever the API actually returns, you’ll note it).
Response should indicate that booking is not found or is empty.
