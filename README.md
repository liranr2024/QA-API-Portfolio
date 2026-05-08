# QA API Testing Portfolio

![Postman](https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)
![Newman](https://img.shields.io/badge/Newman-CLI-4A90D9?style=for-the-badge&logo=npm&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)
![JSONPlaceholder](https://img.shields.io/badge/API-JSONPlaceholder-6DB33F?style=for-the-badge&logo=json&logoColor=white)

A professional API testing suite built with Postman and Newman, demonstrating real-world QA skills across a full REST API lifecycle.  
Tests cover all CRUD operations with schema validation, chained requests, and negative testing — ready to run locally or in CI/CD.

---

## 📊 Test Coverage

| Endpoint | Method | Assertions | Technique |
|----------|--------|-----------|-----------|
| `/posts` | GET | 5 | Array validation, field schema, response time |
| `/posts/:id` | GET | 4 | JSON Schema, chained ID, field content |
| `/posts` | POST | 4 | Status 201, payload echo, ID assignment |
| `/posts/:id` | PUT | 3 | Full replace, field persistence |
| `/posts/:id` | PATCH | 3 | Partial update, field preservation |
| `/posts/:id` | DELETE | 3 | Status 200, empty body |
| `/posts/9999` | GET | 2 | Negative test, 404 handling |
| `/posts/:id/comments` | GET | 4 | Chained request, email regex, data integrity |

**Total: 8 endpoints · 28 assertions · 6 testing techniques**

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| **Postman** | Collection authoring, test scripting (pm.test / pm.expect) |
| **Newman** | CLI runner for local and CI/CD execution |
| **GitHub Actions** | Automated test runs on every push |
| **JSONPlaceholder** | Free public REST API used as the test target |

---

## 🎯 Skills Demonstrated

- ✅ **Status code assertions** — 200, 201, 404 validated per endpoint
- ✅ **JSON Schema validation** — object structure enforced with `pm.response.to.have.jsonSchema()`
- ✅ **Chained requests** — `savedPostId` captured from GET all, reused in GET single and GET comments
- ✅ **Negative testing** — deliberate 404 case to verify error handling
- ✅ **Response time validation** — performance budget enforced (`< 1000ms`)
- ✅ **Full CRUD coverage** — GET, POST, PUT, PATCH, DELETE all tested

---

## 🚀 How to Run

### Option A — Postman GUI

1. Open Postman
2. Click **Import** → select `jsonplaceholder.postman_collection.json`
3. Hit **Run collection**

### Option B — Newman CLI

```bash
# Install Newman
npm install -g newman

# Run the collection
newman run jsonplaceholder.postman_collection.json

# Run with HTML report (optional)
npm install -g newman-reporter-htmlextra
newman run jsonplaceholder.postman_collection.json -r htmlextra
```

---

## 📁 Project Structure

```
qa-api-portfolio/
├── jsonplaceholder.postman_collection.json   # Postman collection (8 requests, 28 assertions)
├── index.html                                # Portfolio landing page
└── README.md                                 # This file
```

---

## 📸 Sample Output

```
newman run jsonplaceholder.postman_collection.json

JSONPlaceholder API Tests

→ 01 - GET all posts
  ✓  Status code is 200
  ✓  Response time is below 1000ms
  ✓  Response is an array
  ✓  Returns exactly 100 posts
  ✓  Each post has required fields

→ 02 - GET single post
  ✓  Status code is 200
  ✓  Schema validation - post object structure
  ✓  Returned post id matches requested id
  ✓  Title is not empty

→ 03 - POST create new post
  ✓  Status code is 201 Created
  ✓  Response has new id assigned
  ✓  Title matches request payload
  ✓  Body matches request payload

→ 04 - PUT full update
  ✓  Status code is 200
  ✓  ID is preserved after PUT
  ✓  Title was updated

→ 05 - PATCH partial update
  ✓  Status code is 200
  ✓  Title was updated to new value
  ✓  Original body field is preserved

→ 06 - DELETE post
  ✓  Status code is 200
  ✓  Response time is acceptable
  ✓  Response body is empty object

→ 07 - GET non-existent post (404)
  ✓  Status code is 404 Not Found
  ✓  Response body is empty object

→ 08 - GET comments by post (chained)
  ✓  Status code is 200
  ✓  Response is a non-empty array
  ✓  Every comment belongs to the requested post
  ✓  Each comment has valid email format

┌─────────────────────────┬───────────────────┬──────────────────┐
│                         │          executed │           failed │
├─────────────────────────┼───────────────────┼──────────────────┤
│              iterations │                 1 │                0 │
│                requests │                 8 │                0 │
│            test-scripts │                 8 │                0 │
│      prerequest-scripts │                 0 │                0 │
│              assertions │                28 │                0 │
├─────────────────────────┴───────────────────┴──────────────────┤
│ total run duration: 1247ms                                      │
│ total data received: 48.62kB                                    │
│ average response time: 142ms                                    │
└─────────────────────────────────────────────────────────────────┘
```

---

## 💡 Why This Project

Built as part of my QA portfolio to demonstrate practical API testing skills.
This project goes beyond simple status code checks — showcasing schema validation,
chained requests, and CI/CD integration that mirror real production testing workflows.

---

## 📄 License

MIT © [Liran Raphael](https://github.com/liranr2024)
