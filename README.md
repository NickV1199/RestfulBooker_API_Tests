[![Restful Booker API Tests](https://github.com/NickV1199/RestfulBooker_API_Tests/actions/workflows/api-tests.yml/badge.svg)](https://github.com/NickV1199/RestfulBooker_API_Tests/actions/workflows/api-tests.yml)

# Restful Booker API Testing

Automated REST API testing project built with **Postman and JavaScript**, using the public [Restful Booker API](https://restful-booker.herokuapp.com/apidoc/index.html).

The project demonstrates API functional testing, CRUD operations, authentication, response validation, negative testing, and automated test execution using **Newman and GitHub Actions**.

## Tech Stack

- Postman
- JavaScript
- REST API
- JSON / JSON Schema
- Postman Collection Runner
- Newman CLI
- Newman HTML Extra Reporter
- GitHub Actions (CI/CD)

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
| GET | `/booking/{id}` | Verify deleted or non-existent booking returns 404 |
| POST | `/booking` | Test invalid booking data |
| POST | `/booking` | Test missing booking fields |

## Automated CRUD Test Flow

The project includes an automated end-to-end API test flow covering the complete booking lifecycle:

1. **Authentication** — Generate an authentication token.
2. **Create** — Create a new booking and store its ID.
3. **Read** — Retrieve the created booking by ID.
4. **Update** — Fully update the booking using PUT.
5. **Partial Update** — Modify selected booking fields using PATCH.
6. **Delete** — Delete the booking.
7. **Verify Deletion** — Confirm that the deleted booking returns HTTP 404.

The collection automatically stores and reuses the authentication token and booking ID using Postman environment variables.

## Automated Validations

- HTTP status code verification
- Response body validation
- JSON Schema validation
- Data type and required field checks
- Response time checks
- Environment variable management
- Authentication token handling
- CRUD workflow verification
- Verification of deleted resources (HTTP 404)

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
5. Select the **Positive CRUD Flow** folder.
6. Run the requests in the following order:
   - POST - Create Token
   - POST - Create Booking
   - GET - Booking by ID
   - PUT - Update Booking
   - PATCH - Partial Update Booking
   - DELETE - Delete Booking
   - GET - Verify Deleted Booking

The collection automatically manages authentication and booking identifiers throughout the workflow.

Negative tests are designed to explore API behavior and may contain intentionally failing assertions.

## Continuous Integration (GitHub Actions)

The project uses **GitHub Actions** to automatically execute API tests.

The CI workflow:

- Runs automatically on every push to the repository.
- Supports manual execution using `workflow_dispatch`.
- Installs Newman and the HTML Extra Reporter.
- Executes the `Positive CRUD Flow` folder.
- Validates API responses using JavaScript assertions.
- Generates a detailed HTML test report.
- Uploads the report as a downloadable GitHub Actions artifact.

### Viewing Test Reports

1. Open the **Actions** tab in this repository.
2. Select a completed workflow run.
3. Scroll down to the **Artifacts** section.
4. Download the `api-test-report` artifact.
5. Extract the ZIP file and open `api-test-report.html` in a browser.

## Test Execution Results

The latest verified automated CRUD workflow completed successfully using Newman and GitHub Actions.

| Metric | Result |
|---|---|
| API Requests | 7 |
| Assertions | 26 |
| Passed | 26 |
| Failed | 0 |
| Skipped | 0 |
| Total Execution Time | 286 ms |
| Average Response Time | 11 ms |

**Result: 26 passed, 0 failed.**

These results represent a successful execution on October 24, 2026, and do not guarantee future test outcomes.

## Author

[Nikolai Volkov](https://github.com/NickV1199)
