[README.md](https://github.com/user-attachments/files/30222335/README.md)
# Football Players API — API Testing Project

This repository contains an API testing project for the [Free API Live Football Data](https://rapidapi.com/Creativedev/api/free-api-live-football-data) (RapidAPI), covering player search and country data endpoints.
It demonstrates manual API testing using **Postman**: request design, response validation, edge-case testing, and automated assertions.

---

## 📌 Scope

**In Scope**
- Player Search endpoint — valid queries, empty queries, special characters, missing parameters
- Countries endpoint — valid GET request, invalid HTTP method (negative testing)
- Response validation: status codes, JSON structure, response time, data presence

**Out of Scope**
- Load/performance testing
- Authentication/security penetration testing
- Full API surface (Livescores, Fixtures, Standings — not covered in this pass)

---

## 🎯 Test Objectives

1. Verify the Player Search endpoint returns correct data for valid queries.
2. Confirm the API handles empty, special-character, and missing search parameters gracefully.
3. Validate the Countries endpoint returns a complete dataset on a valid request.
4. Confirm the API correctly rejects unsupported HTTP methods with an appropriate error.
5. Assert response time, JSON structure, and required data fields across all endpoints.

---

## 🧪 Endpoints Tested

| Endpoint | Method | Purpose |
|---|---|---|
| `/football-players-search` | GET | Search players by name |
| `/football-get-all-countries` | GET | Retrieve full list of countries |

---

## 📂 Test Cases

### Player Search
| Test Case | Query | Expected Result | Status |
|---|---|---|---|
| Valid Query | `search=m` | 200 OK, returns matching players | ✅ Pass |
| Empty Query | `search=` | 200 OK, handled gracefully | ✅ Pass |
| Special Characters | `search=@#$%` | 200 OK, handled gracefully | ✅ Pass |
| Missing Parameter | *(no search param)* | 200 OK, returns empty array | ✅ Pass |

### Countries
| Test Case | Method | Expected Result | Status |
|---|---|---|---|
| Valid Request | GET | 200 OK, returns full country list | ✅ Pass |
| Wrong HTTP Method | POST | 404 Not Found, clear error message | ✅ Pass |

---

## 📊 Test Execution Summary

| Module | Total Cases | Pass | Fail | Errors |
|---|---|---|---|---|
| Player Search | 4 | 4 | 0 | 0 |
| Countries | 2 | 2 | 0 | 0 |
| **TOTAL** | **6 requests / 10 assertions** | **10** | **0** | **0** |

*Full run: 10/10 assertions passed, 0 errors, avg. response time 438ms.*

---

## 📸 Test Run Screenshot

![Test Run Summary](screenshots/test-run-summary.png)

*Collection Runner result: 10/10 assertions passed, 0 errors, across all 6 requests.*

---

## ✅ Key Findings

- The Player Search endpoint handles edge cases (empty search, special characters, missing parameter) **without crashing**, consistently returning `200 OK`.
- Omitting the `search` parameter returns an **empty array** rather than an error or unfiltered dataset — expected, safe behavior.
- The Countries endpoint correctly rejects unsupported HTTP methods (POST) with a `404` and a clear error message (`"Endpoint '/football-get-all-countries' does not exist"`), confirming proper method-based routing.
- No critical bugs found — the API handled all tested edge cases gracefully.

---

## 🛠️ Tools Used

- **Postman** — request design, assertions, Collection Runner
- **RapidAPI** — API subscription and endpoint discovery

---

## 📁 Files in This Project

| File | Description |
|---|---|
| `Football-Players-API.postman_collection.json` | Full Postman collection (6 requests, 10 assertions) |

---

## ▶️ How to Use

1. Import `Football-Players-API.postman_collection.json` into Postman.
2. Create a Postman environment with a variable named `api_key`, and set it to your own [RapidAPI](https://rapidapi.com/) key for this API.
3. Select that environment in Postman, then run individual requests or use **Collection Runner** to execute all requests at once.

> **Note:** API keys are not included in this repository. The collection uses a `{{api_key}}` variable — you'll need your own free RapidAPI subscription to this API to run the tests.

---

*Part of Tanvi Sonani's QA Testing Portfolio.*
