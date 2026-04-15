# TaskFlow 🚀  
A Full-Stack Task & Project Management System

---

## 📖 What is this project?

TaskFlow is a full-stack task and project management system inspired by tools like Jira and Trello.  
It allows users to:

- Create and manage projects
- Assign and track tasks
- Set priority and status (Todo, In Progress, Done)
- Authenticate users using JWT-based login system
- Persist data using PostgreSQL

The system is designed as a production-style monorepo with a Spring Boot backend and React frontend, fully containerized using Docker.

---

## 🧱 Tech Stack

### Backend
- Java 17
- Spring Boot
- Spring Security (JWT Authentication)
- Spring Data JPA (Hibernate)
- PostgreSQL
- Flyway (DB migrations)
- Maven

### Frontend
- React (Vite)
- TypeScript
- FetchAPI
- React Router
- Material UI (MUI)

### DevOps
- Docker
- Docker Compose
- Environment-based configuration (.env)

---

## 🏗️ System Architecture
Frontend (React + Vite)
↓ (HTTP REST API)
Backend (Spring Boot + JWT Security)
↓
PostgreSQL Database

---

### 🔄 Flow Overview

1. User interacts with React UI
2. React sends API requests to Spring Boot backend
3. Backend validates JWT token (if required)
4. Business logic executed in Service layer
5. Data persisted in PostgreSQL via JPA
6. Flyway handles DB schema versioning

---

## 🧠 Architecture Decisions

### 1. Monorepo Structure
I chose a monorepo approach:
taskflow/
├── backend/
├── frontend/

### Why?
- Easier local development
- Single repository for full system
- Simplified Docker orchestration
- Better evaluation for reviewers/interviewers

---

### 2. Layered Backend Architecture

Backend follows a clean layered structure:
Controller → Service → Repository → DB

### Why?
- Separation of concerns
- Easier testing and debugging
- Scalable for future microservices conversion

---

### 3. JWT Authentication

I used stateless JWT authentication instead of session-based auth.

### Why?
- Better scalability
- Works well with REST APIs
- No server-side session storage needed

---

### 4. Flyway for Database Migrations

### Why Flyway?
- Version-controlled DB schema
- Prevents manual SQL execution
- Ensures consistent setup across environments

---

### 5. Dockerized Setup

Entire system runs using:

```bash
docker compose up
Why?
-> Eliminates "it works on my machine" problem
-> Single-command project setup
-> Production-like environment locally

⚖️ Tradeoffs
1. No Microservices
Kept as monolith backend
Reason: simplicity and faster development
2. No Advanced Caching (Redis)
-> Not included
-> Reason: scope focused on core full-stack system
3. No CI/CD Pipeline
-> Not implemented
-> Reason: local + evaluation-ready project only
4. Basic Role System
-> Only basic user authentication implemented
->No RBAC (Admin/User roles)
-> Reason: focus on core CRUD + auth flow

🚀 How to Run
git clone https://github.com/shashank-varshney21/taskflow-shashank_varshney.git
cd taskflow
cp .env.example .env
docker compose up
Frontend → http://localhost:3000
Backend → http://localhost:8080

👨‍💻 Author

Shashank Varshney
(varshneys495@gmail.com)
