# E-Commerce API Analysis (Business Analyst Mini Project)

A hands-on project that analyzes a REST API from a Business Analyst's point of view: test it in Postman, record what it really does, and turn the observed behavior into requirements, user stories, acceptance criteria and a gap analysis.

## Objective
Show how API behavior feeds good requirements. The scenario is an e-commerce app where customers log in and browse products, and admins add, update and delete products.

## API and tools
- **API:** DummyJSON (https://dummyjson.com), a free public API
- **Tools:** Postman, Google Sheets / Excel, a flow diagram, GitHub

## What I did
- Built a Postman collection of 12 test cases covering authentication, reading products, creating, updating and deleting products, and negative scenarios (wrong password, missing token, invalid token, missing product, empty request)
- Used a Postman environment with variables (`base_url`, `username`, `password`, `token`) and a post-response script that saves the login token automatically
- Documented each test in an analysis table: method, endpoint, auth needed, request fields, key response fields, status codes, response times and error messages
- Wrote 8 user stories with 19 Given/When/Then acceptance criteria, each linked to its test cases and tagged with an evidence status
- Performed a gap analysis of 8 business needs with impact ratings and recommendations
- Drew the login and protected-endpoint flow

## Project contents

```
postman-api-analysis-ba/
├── README.md
├── postman/
│   ├── ecommerce-api-analysis.postman_collection.json
│   └── dummyjson-test.postman_environment.json
├── docs/
│   ├── api-response-analysis.xlsx / .pdf / .docx / .csv
│   ├── user-stories-and-acceptance-criteria.pdf / .csv
│   ├── gap-analysis.pdf / .csv
│   └── login-flow-diagram.png
└── screenshots/
```

| Deliverable | What it is |
|---|---|
| `docs/api-response-analysis` | Results of all 12 test cases, with expected vs actual status and BA observations |
| `docs/user-stories-and-acceptance-criteria` | 8 user stories, 19 acceptance criteria, linked to test cases |
| `docs/gap-analysis` | 8 business needs checked against the API, with status, impact and recommendations |
| `docs/login-flow-diagram.png` | Flow of login, token use and error responses |

## Test results at a glance
- 12 test cases run; 11 matched the expected status code
- Status codes observed: 200, 201, 400, 401, 404
- One test (empty request body, TC-12) was set up incorrectly the first time and is being re-run [TODO: update after the re-run]

## Key findings
1. **The customer read-only journey works well.** Login, profile, product list and product detail all returned the expected 200 responses with the fields a front end needs.
2. **Error handling is clear.** Wrong credentials return 400 "Invalid Credentials", a missing token and an invalid token return different 401 messages, and a missing product returns 404 with the product ID in the message.
3. **Security gap:** adding, updating and deleting products worked without any access token. Recommendation: require a valid token and an admin role (401 for no or invalid token, 403 for non-admins).
4. **Performance:** the product list was the slowest call at 2,900 ms in a single run, above a proposed 2,000 ms target. Recommendation: agree a target and require paging.
5. **Still to verify:** validation of an empty product, whether changes are really saved, search/filter/sort options, and the token refresh flow [TODO: update statuses after retesting].

## Skills demonstrated
- REST API basics: HTTP methods, status codes, JSON, authentication with bearer tokens
- Postman: collections, environments, variables, post-response scripts, negative testing
- Requirements: user stories, Given/When/Then acceptance criteria, traceability to test cases
- Analysis: gap analysis with impact ratings and recommendations
- Process modelling: flow diagram of the authentication journey

## How to reproduce
1. Import the files from `postman/` into Postman.
2. Select the `DummyJSON - Test` environment.
3. Run TC-01 first, then the other requests.

## Notes
- The username and password in the environment are DummyJSON's public test credentials.
- Response times come from a single run on a public API and are indicative only.
- DummyJSON is a demo API, so its behavior may differ from a production system.

## Author
Jatin Vishwakarma
