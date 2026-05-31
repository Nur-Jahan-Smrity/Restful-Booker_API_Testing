# 🏨 Restful Booker API Testing

![Postman](https://img.shields.io/badge/Postman-API%20Testing-FF6C37?logo=postman&logoColor=white)
![Newman](https://img.shields.io/badge/Newman-CLI-00A98F)
![Node.js](https://img.shields.io/badge/Node.js-Required-339933?logo=node.js&logoColor=white)
![Status](https://img.shields.io/badge/Last%20Run-2%20Failed%20Assertions-red)

A complete REST API testing project for the **Restful Booker** public API using **Postman**, **Newman**, and HTML reporting.  
This project validates the hotel booking API flow from booking creation to update, partial update, token generation, deletion, and booking list verification.

---

## 📋 Table of Contents

- [Project Overview](#-project-overview)
- [API Under Test](#-api-under-test)
- [Tech Stack](#-tech-stack)
- [Test Flow](#-test-flow)
- [Test Cases](#-test-cases)
- [Project Structure](#-project-structure)
- [Prerequisites](#-prerequisites)
- [Setup & Installation](#-setup--installation)
- [Running the Tests](#-running-the-tests)
- [Newman Report](#-newman-report)
- [Test Results Summary](#-test-results-summary)
- [Environment Variables](#-environment-variables)
- [Assertions Covered](#-assertions-covered)
- [Known Issues From Last Run](#-known-issues-from-last-run)

---

## 🔍 Project Overview

This repository contains an automated API test suite for the **Restful Booker** API.

The test suite checks:

- Correct HTTP status codes
- Response time validation
- Response payload size validation
- JSON response format
- Required field presence
- Data type validation
- Dynamic test data generation
- Token generation and usage
- Full booking lifecycle validation
- Create → Read → Update → Partial Update → Delete flow

---

## 🌐 API Under Test

**Base URL**

```text
https://restful-booker.herokuapp.com
```

| Endpoint | Method | Description |
|---|---:|---|
| `/booking` | `GET` | Retrieve all booking IDs |
| `/booking` | `POST` | Create a new booking |
| `/booking/{id}` | `GET` | Get a booking by ID |
| `/auth` | `POST` | Generate authentication token |
| `/booking/{id}` | `PUT` | Update a booking |
| `/booking/{id}` | `PATCH` | Partially update a booking |
| `/booking/{id}` | `DELETE` | Delete a booking |

---

## 🧰 Tech Stack

- **Postman** — API request creation and test scripting
- **Newman** — Command-line runner for Postman collections
- **Node.js / npm** — Required to install Newman
- **newman-reporter-html** — HTML report generation
- **newman-reporter-htmlextra** — Enhanced Newman dashboard report

---

## 🔁 Test Flow

```text
GetBookingIds
     ↓
CreateBooking
     ↓
CreateToken
     ↓
GetBooking
     ↓
UpdateBooking
     ↓
GetBooking
     ↓
PartialUpdateBooking
     ↓
DeleteBooking
     ↓
GetBookingIds
```

The collection uses Postman environment variables to store and reuse dynamic data such as booking ID, token, generated names, price, check-in date, and check-out date.

---

## 🧪 Test Cases

| # | Request Name | Method | Endpoint | Assertions |
|---:|---|---:|---|---:|
| 1 | GetBookingIds | `GET` | `/booking` | 3 |
| 2 | CreateBooking | `POST` | `/booking` | 17 |
| 3 | GetBooking | `GET` | `/booking/{id}` | 3 |
| 4 | CreateToken | `POST` | `/auth` | 6 |
| 5 | GetBooking | `GET` | `/booking/{id}` | 19 |
| 6 | UpdateBooking | `PUT` | `/booking/{id}` | 16 |
| 7 | GetBooking | `GET` | `/booking/{id}` | 19 |
| 8 | PartialUpdateBooking | `PATCH` | `/booking/{id}` | 7 |
| 9 | DeleteBooking | `DELETE` | `/booking/{id}` | 3 |
| 10 | GetBookingIds | `GET` | `/booking` | 10 |

---

## 📁 Project Structure

```text
Restful-Booker_API_Testing/
│
├── First_Hands_on_API_Testing.postman_collection.json
├── First_Hands_on_API_Class_Environment.postman_environment.json
│
├── newman/
│   ├── First_Hands_on_API_Testing-2026-05-31-12-01-57-137-0.html
│   └── newman-run-report-2026-05-31-12-01-47-776-0.html
│
├── newman-dashboard.png
└── README.md
```

---

## ✅ Prerequisites

Make sure the following are installed on your machine:

- [Node.js](https://nodejs.org/)
- npm
- Newman

Install Newman globally:

```bash
npm install -g newman
```

Install HTML reporters:

```bash
npm install -g newman-reporter-html newman-reporter-htmlextra
```

Verify Newman installation:

```bash
newman --version
```

---

## ⚙️ Setup & Installation

Clone the repository:

```bash
git clone https://github.com/Nur-Jahan-Smrity/Restful-Booker_API_Testing.git
```

Go to the project folder:

```bash
cd Restful-Booker_API_Testing
```

---

## ▶️ Running the Tests

### Basic Newman Run

```bash
newman run First_Hands_on_API_Testing.postman_collection.json \
  -e First_Hands_on_API_Class_Environment.postman_environment.json
```

### Run With HTML Report

```bash
newman run First_Hands_on_API_Testing.postman_collection.json \
  -e First_Hands_on_API_Class_Environment.postman_environment.json \
  -r html \
  --reporter-html-export newman/newman-run-report.html
```

### Run With htmlextra Dashboard Report

```bash
newman run First_Hands_on_API_Testing.postman_collection.json \
  -e First_Hands_on_API_Class_Environment.postman_environment.json \
  -r htmlextra \
  --reporter-htmlextra-export newman/First_Hands_on_API_Testing-report.html
```

### Run With CLI + HTML Report Together

```bash
newman run First_Hands_on_API_Testing.postman_collection.json \
  -e First_Hands_on_API_Class_Environment.postman_environment.json \
  -r cli,htmlextra \
  --reporter-htmlextra-export newman/First_Hands_on_API_Testing-report.html
```

> **Windows CMD users:** replace `\` with `^` for multiline commands.

---

## 📊 Newman Report

The generated Newman dashboard includes:

- Summary dashboard
- Request-level results
- Passed and failed assertions
- Response time details
- Request and response information
- Environment information

Report folder:

```text
/newman
```

GitHub report location:

```text
https://github.com/Nur-Jahan-Smrity/Restful-Booker_API_Testing/tree/main/newman
```

### Newman Run Dashboard Screenshot

![Newman Run Dashboard](newman-dashboard.png)

> This screenshot shows the latest Newman run dashboard with total requests, total assertions, failed tests, skipped tests, timing data, and overall execution summary.

---

## 📈 Test Results Summary

Latest Newman dashboard run:

| Metric | Result |
|---|---:|
| Total Iterations | 1 |
| Total Requests | 10 |
| Pre-request Scripts | 4 |
| Test Scripts | 10 |
| Total Assertions | 103 |
| Failed Assertions | 2 |
| Skipped Tests | 0 |
| Total Run Duration | 5.4s |
| Total Data Received | 4.48KB |
| Average Response Time | 518ms |

---

## 🔧 Environment Variables

| Variable | Type | Description |
|---|---|---|
| `base_Url` | Static | Base API URL |
| `id` | Dynamic | Booking ID created during test execution |
| `token` | Dynamic | Authentication token generated from `/auth` |
| `tPrice` | Dynamic | Random generated total price |
| `checkin` | Dynamic | Generated check-in date |
| `checkout` | Dynamic | Generated check-out date |
| `needs` | Dynamic | Additional needs value |
| `bookingIds` | Dynamic | Booking IDs list |
| `fname` | Dynamic | Random generated first name |
| `lname` | Dynamic | Random generated last name |
| `deposit_paid` | Dynamic | Random generated deposit paid status |

---

## ✅ Assertions Covered

The collection includes assertions for:

- HTTP status code validation
- Response time validation
- Response size validation
- JSON body validation
- Token existence validation
- Required field validation
- Field data type validation
- Dynamic data matching
- Booking date structure validation
- Date format validation: `YYYY-MM-DD`
- Checkout date after check-in date
- Positive total price validation
- Boolean validation for deposit paid
- No duplicate booking IDs
- Delete booking response validation

---

## ⚠️ Known Issues From Last Run

The latest Newman run completed with **2 failed assertions**.

| Request | Actual Result | Expected Result | Notes |
|---|---|---|---|
| `GetBooking` | Status code `200` | Status code `404` | This deleted-booking check should run after the delete request, or the expected status should be adjusted based on the test flow. |
| `DeleteBooking` | Status code `201` | Status code `200` | Restful Booker commonly returns `201` for successful delete. Update the assertion to expect `201`, or allow both `200` and `201`. |

Suggested assertion for delete request:

```javascript
pm.test("Status code is 200 or 201", function () {
    pm.expect([200, 201]).to.include(pm.response.code);
});
```

---

## 👤 Author

**Nur Jahan Smrity**

GitHub Repository:  
[Restful Booker API Testing](https://github.com/Nur-Jahan-Smrity/Restful-Booker_API_Testing)

---

## 📌 Notes

This project is created for API testing practice and demonstrates how to use Postman test scripts with Newman CLI automation and HTML reporting.
