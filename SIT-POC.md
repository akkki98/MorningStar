# 🚀 Lab Instructions: Smart Campus Utility Application Using GitHub Copilot

## 📌 Background

Modern educational institutions face challenges in efficiently managing campus services such as issue reporting, room availability, announcements, and shared resources. Students and staff often rely on manual or fragmented systems, leading to delays, lack of transparency, and poor user experience.

In this lab, you will design and build a **Smart Campus Utility Application** using **GitHub Copilot as your primary AI assistant** throughout the development lifecycle.

---

## 🎯 Objective

Develop a **full-stack web application** that enables students and campus administrators to interact with common campus utilities on a single platform, while demonstrating effective usage of GitHub Copilot for:

* Requirement analysis
* Architecture & design planning
* Code generation
* Unit & integration testing
* Documentation
* Refactoring and optimization

---

## 🧰 Technology Stack

### Frontend

* ReactJS
* REST API integration

### Backend (choose ONE)

* Java (Spring Boot)
* Node.js (Express / NestJS)
* .NET (ASP.NET Core)
* Python (FastAPI / Flask)

### Database

* SQL Database (PostgreSQL / MySQL / SQL Server)

### Tooling

* GitHub
* GitHub Copilot (Chat, Inline, Agent modes)

---

## 🧩 Application Features (Minimum Requirements)

### 1️⃣ User Management

* Student and Admin login
* Role-based access control
* Secure authentication (JWT or session-based)

### 2️⃣ Issue Reporting System

* Students can report campus issues (Wi-Fi, classrooms, labs, etc.)
* Admins can view, assign, and update issue status
* Issue lifecycle: OPEN → IN_PROGRESS → RESOLVED

### 3️⃣ Campus Announcements

* Admins can create and publish announcements
* Students can view announcements in real time

### 4️⃣ Resource Booking (Optional – Bonus)

* Book study rooms, labs, or equipment
* Prevent double booking
* View booking history

---

## 🧪 Lab Structure & Tasks

---

## 🔹 Lab 1: Requirement Analysis Using GitHub Copilot

### Objective

Use GitHub Copilot to clarify requirements and identify edge cases.

#### Sample Prompts

```text
@workspace /explain Identify functional and non-functional requirements for this Smart Campus application.
```

```text
List possible edge cases and failure scenarios for user registration and issue reporting.
```

---

## 🔹 Lab 2: High-Level Architecture Design

### Objective

Design frontend, backend, and database architecture.

#### Sample Prompts

```text
Design a scalable full-stack architecture for this application with clear separation of concerns.
```

```text
Propose a REST API design for user management, issues, and announcements.
```

Deliverables:

* Architecture diagram (logical)
* API endpoint list

---

## 🔹 Lab 3: Backend Development with Copilot

### Objective

Generate backend APIs using Copilot.

#### Tasks

* User authentication & authorization
* Issue CRUD APIs
* Announcement APIs

#### Sample Prompts

```text
Generate a REST API for user login and role-based authorization using JWT.
```

```text
Create backend endpoints to report, update, and fetch campus issues.
```

---

## 🔹 Lab 4: Frontend Development with Copilot

### Objective

Build a React-based UI using Copilot assistance.

#### Tasks

* Login & registration pages
* Student dashboard
* Admin dashboard

#### Sample Prompts

```text
Create a React login page with role-based redirection for admin and student users.
```

```text
Generate a React component to list and update issue status.
```

---

## 🔹 Lab 5: Database Design & Integration

### Objective

Design relational schema and integrate persistence.

#### Sample Prompts

```text
Design SQL tables for users, roles, issues, and announcements.
```

```text
Add database migrations and seed sample data.
```

---

## 🔹 Lab 6: Unit Testing Using GitHub Copilot

### Objective

Write unit tests for backend and frontend logic.

#### Sample Prompts

```text
Generate unit tests for the issue reporting service covering success and failure cases.
```

```text
Create unit tests for this React component using React Testing Library.
```

---

## 🔹 Lab 7: Refactoring & Code Quality

### Objective

Improve readability, maintainability, and modularity.

#### Sample Prompts

```text
Refactor this code to improve readability and separation of concerns.
```

```text
Identify technical debt and suggest improvements.
```

---

## 🔹 Lab 8: Documentation with Copilot

### Objective

Generate developer and user documentation.

#### Sample Prompts

```text
Generate a README.md explaining setup, architecture, and API usage.
```

```text
Add inline documentation and comments for complex logic.
```

---

## 🔹 Lab 9: Copilot Agent Mode (Advanced)

### Objective

Use Copilot Agent for end-to-end improvements.

#### Sample Prompt

```text
@workspace /agent Improve code quality, add missing tests, update documentation, and ensure all features meet requirements.
```

---

## ✅ Success Criteria

* All core features implemented
* Clean role-based access control
* Working frontend and backend integration
* Unit tests added
* Clear documentation
* Effective use of GitHub Copilot demonstrated

---

## 🏆 Bonus Challenges

* Add real-time updates using WebSockets
* Implement notification system
* Add audit logs for admin actions
* Deploy application using Docker

---

## 📦 Final Deliverables

* Source code repository
* README.md
* API documentation
* Test reports
* Screenshots or demo video

---

**End of Lab – Smart Campus Utility Application**
