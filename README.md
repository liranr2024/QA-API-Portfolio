# QA API Testing Portfolio

![Postman](https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)
![Newman](https://img.shields.io/badge/Newman-CLI-4A90D9?style=for-the-badge&logo=npm&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)
![JWT](https://img.shields.io/badge/Auth-JWT-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white)

A comprehensive API testing portfolio built with Postman and Newman, demonstrating real-world QA skills across **two different APIs** with full coverage of CRUD operations, authentication flows, schema validation, and edge cases.

🌐 **Live Demo:** [liranr2024.github.io/QA-API-Portfolio](https://liranr2024.github.io/QA-API-Portfolio/)

---

## 📊 Test Coverage Overview

**Total: 16 endpoints · 65 assertions · 2 API suites · 6+ testing techniques**

### Suite 1: JSONPlaceholder (CRUD Fundamentals)

| Endpoint | Method | Assertions | Technique |
|----------|--------|------------|-----------|
| `/posts` | GET | 5 | Array validation, field schema, response time |
| `/posts/:id` | GET | 4 | JSON Schema, chained ID, field content |
| `/posts` | POST | 4 | Status 201, payload echo, ID assignment |
| `/posts/:id` | PUT | 3 | Full replace, field persistence |
| `/posts/:id` | PATCH | 3 | Partial update, field preservation |
| `/posts/:id` | DELETE | 3 | Status 200, empty body |
| `/posts/9999` | GET | 2 | Negative test, 404 handling |
| `/posts/:id/comments` | GET | 4 | Chained request, email regex, data integrity |

**Subtotal: 8 endpoints · 28 assertions**

### Suite 2: DummyJSON (E-commerce + Auth)

| Endpoint | Method | Assertions | Technique |
|----------|--------|------------|-----------|
| `/products?limit=10` | GET | 5 | Pagination, 22-field schema, UUID uniqueness |
| `/products/:id` | GET | 6 | Schema validation, business rules, image URLs |
| `/products/search?q=phone` | GET | 3 | Multi-field search matching |
| `/products/category/smartphones` | GET | 4 | Category filtering, stock validation |
| `/products/add` | POST | 5 | Creation with rich payload, ID assignment |
| `/products/:id` | PUT | 4 | Update validation, field preservation |
| `/products/:id` | DELETE | 3 | Soft delete, isDeleted flag, timestamps |
| `/auth/login` | POST | 7 | JWT structure validation, email regex, gender |

**Subtotal: 8 endpoints · 37 assertions**

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| **Postman** | Collection authoring, test scripting (`pm.test` / `pm.expect`) |
| **Newman** | CLI runner for local and CI/CD execution |
| **GitHub Actions** | Automated test runs on every push (planned) |
| **JSONPlaceholder** | Public REST API for CRUD testing |
| **DummyJSON** | Public e-commerce API with JWT auth support |
| **JWT** | Authentication token validation |

---

## 🎯 Skills Demonstrated

- ✅ **Full CRUD coverage** - GET, POST, PUT, PATCH, DELETE across both APIs
- ✅ **JWT authentication testing** - Token structure validation, login flow
- ✅ **JSON Schema validation** - Deep nested object structures with `pm.response.to.have.jsonSchema()`
- ✅ **Chained requests** - Variables captured from one request and reused in subsequent ones
- ✅ **Search & filtering logic** - Multi-field search validation, category filtering
- ✅ **Pagination testing** - `limit`/`skip` parameters, metadata validation
- ✅ **Negative testing** - Deliberate 404 cases, error handling verification
- ✅ **Cross-field business rules** - Price ranges, rating bounds, age consistency
- ✅ **Soft delete patterns** - `isDeleted` flag and `deletedOn` timestamps
- ✅ **Response time validation** - Performance budgets enforced (`< 1000ms`)
- ✅ **Email & URL regex validation** - Pattern matching for data integrity

---

## 🚀 How to Run

### Option A - Postman GUI

1. Open Postman
2. Click **Import** → select either collection (`.json`) file
3. Hit **Run collection** in Collection Runner

### Option B - Newman CLI

```bash
# Install Newman with HTML reporter
npm install -g newman newman-reporter-htmlextra

# Clone the repo
git clone https://github.com/liranr2024/QA-API-Portfolio.git
cd QA-API-Portfolio

# Run JSONPlaceholder collection
newman run jsonplaceholder.postman_collection.json \
  -r htmlextra,cli \
  --reporter-htmlextra-export ./reports/jsonplaceholder-report.html

# Run DummyJSON collection
newman run dummyjson.postman_collection.json \
  -r htmlextra,cli \
  --reporter-htmlextra-export ./reports/dummyjson-report.html
```

---

## 📁 Project Structure

```
QA-API-Portfolio/
├── jsonplaceholder.postman_collection.json   # Suite 1: 8 requests, 28 assertions
├── dummyjson.postman_collection.json         # Suite 2: 8 requests, 37 assertions
├── index.html                                # Live portfolio landing page
├── .gitignore                                # Standard Node.js / OS ignores
└── README.md                                 # This file
```

---

## 📸 Sample Output

```
$ newman run dummyjson.postman_collection.json

DummyJSON E-Commerce API Tests

→ 01 - GET products with pagination
  ✓  Status code is 200
  ✓  Response time is under 2000ms
  ✓  Returns exactly 10 products
  ✓  Pagination metadata is correct
  ✓  Each product has core fields

→ 02 - GET single product by ID
  ✓  Status code is 200
  ✓  Schema validation - product structure
  ✓  Price is positive and reasonable
  ✓  Rating is between 0 and 5
  ✓  Has at least one image

→ 08 - POST authentication (login)
  ✓  Status code is 200
  ✓  Response includes accessToken
  ✓  Token follows JWT structure (3 parts)
  ✓  Username matches login attempt
  ✓  User has email and gender info

┌─────────────────────────┬───────────────────┬──────────────────┐
│                         │          executed │           failed │
├─────────────────────────┼───────────────────┼──────────────────┤
│              iterations │                 1 │                0 │
│                requests │                 8 │                0 │
│            test-scripts │                16 │                0 │
│              assertions │                37 │                0 │
└─────────────────────────┴───────────────────┴──────────────────┘
```

**Combined run (both suites):**

```
┌─────────────────────────┬───────────────────┬──────────────────┐
│                         │          executed │           failed │
├─────────────────────────┼───────────────────┼──────────────────┤
│              iterations │                 2 │                0 │
│                requests │                16 │                0 │
│            test-scripts │                32 │                0 │
│              assertions │                65 │                0 │
└─────────────────────────┴───────────────────┴──────────────────┘
```

---

## 💡 Why This Project

Built as part of my QA portfolio to demonstrate practical API testing skills across diverse scenarios. Rather than focusing on a single API, this project intentionally tests **two different APIs** to showcase:

- **Adaptability** - Same QA mindset applied to different domain models (blog posts vs. e-commerce)
- **Breadth** - From basic CRUD to advanced authentication flows
- **Depth** - Schema validation that goes beyond status codes to enforce business rules

Each test is designed to mirror real production testing workflows: schema contracts, chained data dependencies, negative scenarios, and CI/CD-ready execution.

---

## 🔗 Connect

- 🌐 **Live Portfolio:** [liranr2024.github.io/QA-API-Portfolio](https://liranr2024.github.io/QA-API-Portfolio/)
- 📦 **GitHub:** [github.com/liranr2024](https://github.com/liranr2024)
- 💼 **LinkedIn:** [linkedin.com/in/liran-raphael](https://www.linkedin.com/in/liran-raphael/)

---

## 📄 License

MIT © [Liran Raphael](https://github.com/liranr2024)
