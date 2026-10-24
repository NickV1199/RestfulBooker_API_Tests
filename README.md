# Restful Booker API Testing

Automated REST API testing project built with **Postman and JavaScript**, using the public [Restful Booker API](https://restful-booker.herokuapp.com/apidoc/index.html).

The project demonstrates API functional testing, CRUD operations, authentication, response validation, negative testing, and automated test execution.

## Tech Stack

- Postman
- JavaScript
- REST API
- JSON / JSON Schema
- Postman Collection Runner

## Test Coverage

| HTTP Method | Endpoint | Test Scenario |
|---|---|---|
| GET | `/booking` | Retrieve all booking IDs |
| GET | `/booking/{id}` | Retrieve a booking by ID |
| POST | `/booking` | Create a new booking |
| POST | `/auth` | Generate authentication token |
| PUT | `/booking/{id}` | Fully update a booking |
| PATCH | `/booking/{id}` | Partially update a booking |
| DELETE | `/booking/{id}` | Delete a booking |
| GET | `/booking/{id}` | Verify handling of a non-existent booking |
| POST | `/booking` | Test invalid booking data |
| POST | `/booking` | Test missing booking fields |

## Automated Validations

- HTTP status code verification
- Response body validation
- JSON Schema validation
- Data type and required field checks
- Response time checks
- Environment variable management
- Authentication token handling
- CRUD workflow verification

## Negative Testing

Exploratory negative tests identified the following API behaviors:

- Invalid `totalprice` values may be converted to `null` while the booking is created.
- A missing `firstname` field may result in a booking with an empty string.

These observations require confirmation against API requirements before being classified as defects.

## Running Tests in Postman

1. Import the Postman Collection JSON file.
2. Import the Postman Environment JSON file.
3. Select the imported environment.
4. Open the Collection Runner.
5. Run the positive CRUD requests in the following order:
   - POST - Create Token
   - POST - Create Booking
   - GET - Booking by ID
   - PUT - Update Booking
   - PATCH - Partial Update Booking

The collection automatically stores the authentication token and booking ID using Postman environment variables.

Negative tests are designed to explore API behavior and may contain intentionally failing assertions.

## Test Execution

The selected positive workflow completed successfully in Postman Collection Runner:

**20 passed, 0 failed.**

This result represents a local test run, not a guarantee of future executions.

## Author

[Nikolai Volkov](https://github.com/NickV1199)
