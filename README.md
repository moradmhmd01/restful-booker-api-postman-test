# Automated API Integration Testing Suite (Postman & JavaScript)

## 📌 Project Overview
This repository contains a fully automated, data-driven API integration testing suite designed for the `Restful-Booker` flight and hotel reservation system. The suite tests complete CRUD lifecycle data mutations across microservices with continuous request chaining, dynamic parameter passing, and explicit payload verification assertions.

---

## 🔄 Automated Test Architecture Workflow

The test suite validates the integration of backend microservices by automating the following transactional sequence:



1. **POST Authentication Token:** Submits credentials, validates authorization headers, and securely caches the session token.
2. **POST Create Booking:** Generates a unique reservation record, asserts schema structure compliance, and dynamically captures the random `bookingId`.
3. **GET Flight Details:** Requests the record created in Step 2 by pulling the `bookingId` environmental variable to confirm database write validation.
4. **PUT Update Details:** Mutates the booking payload data securely by checking both the active `bookingId` and the explicit validation `token` simultaneously.
5. **DELETE Purge Record:** Drops the testing data record from the live schema matrix, confirming a clean transactional teardown.

---

## 🛠️ Key Technical Implementations
* **Dynamic Chaining:** Implemented zero-hardcoding environment configuration states. Responses are evaluated during execution using the JavaScript sandbox engine to write runtime variables (`pm.environment.set`) for down-funnel HTTP methods.
* **Functional Test Assertions:** Includes strict validation checks to verify HTTP status codes, confirm deep-object key parity, and prevent data collision or corruption.

---

## 🚀 How to Execute This Collection Locally

### Method 1: Via Postman App UI
1. Clone this repository to your local computer.
2. Open the Postman Desktop App and click **Import** in the upper left corner.
3. Select both the `.postman_collection.json` file and the `.postman_environment.json` file from your disk.
4. Ensure the **`Restful-Booker-Env`** environment option is selected active in the top-right dropdown menu.
5. Right-click the imported folder collection, select **Run collection**, and click **Run Restful-Booker API Testing**.

### Method 2: Via Newman CLI (Bonus Portability)
If you have Node.js installed, you can execute these tests straight inside your terminal just like a CI/CD pipeline:
```bash
npm install -g newman
newman run *.postman_collection.json -e *.postman_environment.json
---

## Step 3: Push to GitHub
Open Git Bash or your terminal inside your project directory and run your standard deployment commands:

```bash
git init
git add .
git commit -m "feat: implement automated booking api test suite with collection environment variables"
git branch -M main
git remote add origin <your-github-repo-url>
git push -u origin main
