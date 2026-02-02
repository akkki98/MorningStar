# GitHub Copilot Prompt Engineering Lab

## Lab Title

**Prompt Engineering with GitHub Copilot: Single, Specific, Short & Surround Principles**

## Target Audience

Backend Developers, Frontend Developers, Full‑Stack Engineers, QA/SDETs

## Lab Duration

## Tools Required

* VS Code
* GitHub Copilot enabled
* Sample Backend (Java / Node.js / Python – choose one)
* Sample Frontend (React / Angular / Vue – choose one)

---

## Learning Objectives

By the end of this lab, participants will be able to:

* Apply **Single, Specific, Short, and Surround** prompt engineering principles
* Use GitHub Copilot effectively for **backend** and **frontend** development
* Generate predictable, maintainable, and production‑ready code
* Reduce rework caused by vague or overloaded prompts

---

## Prompt Engineering Principles Overview

### 1. Single

Focus on **one task at a time**.

### 2. Specific

Provide **clear constraints, inputs, and expected outputs**.

### 3. Short

Keep prompts **concise and intent‑driven**.

### 4. Surround

Provide **context using surrounding code, comments, examples, or business rules**.

---

# LAB 1: SINGLE Principle

## Goal

Learn how breaking work into single‑purpose prompts improves Copilot accuracy.

---

## Backend Scenario (API Development)

### Task

Create a REST API endpoint to fetch user details by ID.

### ❌ Poor Prompt

```
Create user APIs with validation, logging, error handling, and database access
```

### ✅ Single Prompt

```
Create a GET REST endpoint to fetch a user by userId
```

### Steps

1. Open backend controller file
2. Place cursor inside the class
3. Enter the **Single prompt** as a comment
4. Accept Copilot suggestion

### Expected Outcome

* One endpoint
* Clear method signature
* No unrelated logic

---

## Frontend Scenario (UI Component)

### Task

Create a button component.

### ❌ Poor Prompt

```
Create a complete dashboard with buttons, tables, and charts
```

### ✅ Single Prompt

```
Create a reusable primary button component
```

### Expected Outcome

* One component
* Reusable props
* Clean JSX/HTML

---

# LAB 2: SPECIFIC Principle

## Goal

Use constraints to guide Copilot toward correct implementations.

---

## Backend Scenario (Validation Logic)

### Task

Validate email input in a request.

### ❌ Vague Prompt

```
Validate email
```

### ✅ Specific Prompt

```
Validate email using regex and return 400 if invalid
```

### Steps

1. Open request validation layer
2. Add comment with **specific rules**
3. Observe Copilot generate validation code

### Expected Outcome

* Regex‑based validation
* Proper HTTP error response

---

## Frontend Scenario (Form Validation)

### Task

Validate password field.

### ✅ Specific Prompt

```
Validate password with min 8 chars, one uppercase, one number
```

### Expected Outcome

* Clear validation logic
* User‑friendly error message

---

# LAB 3: SHORT Principle

## Goal

Understand that concise prompts outperform long descriptions.

---

## Backend Scenario (Utility Method)

### ❌ Long Prompt

```
Create a utility function that checks if a string is null, empty, or blank and returns true or false
```

### ✅ Short Prompt

```
Check if string is null or blank
```

### Expected Outcome

* Clean helper method
* Idiomatic language usage

---

## Frontend Scenario (State Handling)

### ❌ Long Prompt

```
Handle loading state when API is called and show spinner until response comes
```

### ✅ Short Prompt

```
Show loader while API call is in progress
```

---

# LAB 4: SURROUND Principle

## Goal

Provide context so Copilot understands business logic and intent.

---

## Backend Scenario (Business Rule‑Driven Logic)

### Context (Surrounding Comments)

```java
// Business Rules:
// - User status must be ACTIVE
// - Role must be ADMIN to access this API
// - Log access attempt
```

### Prompt

```
Implement authorization based on above rules
```

### Steps

1. Add business rules as comments
2. Place cursor below comments
3. Trigger Copilot

### Expected Outcome

* Role check
* Status validation
* Logging

---

## Frontend Scenario (UI Behavior Based on Rules)

### Context

```javascript
// Rules:
// - Disable submit if form is invalid
// - Show tooltip on hover when disabled
```

### Prompt

```
Implement button behavior based on above rules
```

### Expected Outcome

* Conditional disable logic
* Tooltip rendering

---

# BONUS LAB: Combining All Principles

## Backend Example

```java
// Rule: Apply 2% fee for retail, 3% for cash
// Input: transactionAmount, transactionType
// Output: finalAmount
// Single task: calculate fee
```

### Prompt

```
Calculate final amount based on above rules
```

---

## Frontend Example

```jsx
// Context:
// Display error banner
// Only when API fails
// Reusable component
```

### Prompt

```
Create error banner component based on above context
```

---

## Key Takeaways

* One prompt = one outcome
* Constraints improve correctness
* Short prompts reduce hallucination
* Surrounding context dramatically boosts Copilot quality

---

## Lab Completion Criteria

* Participants successfully generate backend and frontend code
* Prompts follow all four principles
* Code requires minimal manual correction

---

**End of Lab**
