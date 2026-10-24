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
| GET | `/booking/{id}` | Verify deleted booking returns HTTP 404 |
| PUT | `/booking/{id}` | Verify unauthorized update returns HTTP 403 |
| POST | `/booking` | Explore invalid booking data |
| POST | `/booking` | Explore missing booking fields |

## Automated Test Scenarios

### 1. Positive CRUD Flow

An automated end-to-end API test flow covering the complete booking lifecycle:

1. **Authentication** — Generate an authentication token.
2. **Create** — Create a new booking and store its ID.
3. **Read** — Retrieve the created booking by ID.
4. **Update** — Fully update the booking using PUT.
5. **Partial Update** — Modify selected booking fields using PATCH.
6. **Delete** — Delete the booking.
7. **Verify Deletion** — Confirm that the deleted booking returns HTTP 404.

**Execution:** 7 requests, 26 assertions.

### 2. Negative Authentication Tests

An automated negative test scenario verifying that booking updates require authentication:

1. **Create Booking** — Create a booking for negative testing.
2. **Unauthorized Update** — Attempt to update the booking without an authentication token.
3. **Verify Rejection** — Assert HTTP 403 and verify the response contains `Forbidden`.
4. **Generate Token** — Obtain a valid authentication token.
5. **Cleanup** — Delete the test booking using authorized access.

The scenario uses four API requests and automatically cleans up its test data.

**Execution:** 4 requests, 14 assertions.

Both automated scenarios use Postman environment variables to store and reuse booking IDs and authentication tokens.

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
- Unauthorized access verification (HTTP 403)
- Test data cleanup

## Negative Testing

The project includes automated authentication testing and exploratory negative testing.

**Automated negative testing:**

- Updating a booking without an authentication token returns HTTP 403 Forbidden.
- The response contains `Forbidden`.
- Test data is removed after the negative scenario.

**Exploratory observations:**

- Invalid `totalprice` values may be converted to `null` while the booking is created.
- A missing `firstname` field may result in a booking with an empty string.

These observations require confirmation against API requirements before being classified as defects.

## Running Tests in Postman

1. Import the Postman Collection JSON file.
2. Import the Postman Environment JSON file.
3. Select the imported environment.
4. Open the Collection Runner.
5. Select either **Positive CRUD Flow** or **Negative Authentication Tests**.
6. Run the requests in their predefined order.

The collection automatically manages authentication and booking identifiers throughout each workflow.

## Continuous Integration (GitHub Actions)

The project uses **GitHub Actions** to automatically execute API tests with Newman.

The CI workflow:

- Runs automatically on every push to the repository.
- Supports manual execution using `workflow_dispatch`.
- Installs Newman and the HTML Extra Reporter.
- Executes both `Positive CRUD Flow` and `Negative Authentication Tests`.
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

The latest verified automated test execution completed successfully using Newman and GitHub Actions.

| Test Suite | Requests | Assertions | Failed |
|---|---:|---:|---:|
| Positive CRUD Flow | 7 | 26 | 0 |
| Negative Authentication Tests | 4 | 14 | 0 |
| **Total** | **11** | **40** | **0** |

### Latest CI Execution

| Metric | Result |
|---|---|
| API Requests | 11 |
| Assertions | 40 |
| Passed | 40 |
| Failed | 0 |
| Skipped | 0 |
| Total Execution Time | 615 ms |
| Average Response Time | 32 ms |
| Execution Date | October 24, 2026 |

**Result: 40 passed, 0 failed.**

These results represent a verified execution and do not guarantee future test outcomes.

## Author

[Nikolai Volkov](https://github.com/NickV1199)
