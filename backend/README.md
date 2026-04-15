
---

# 📌 BACKEND README (`/backend/README.md`)

```md
# TaskFlow Backend (Spring Boot)

## 📖 Overview

This is the backend service for TaskFlow — a project and task management system.

It provides:
- User authentication (JWT)
- Project management
- Task tracking system
- RESTful APIs for frontend consumption

---

## 🧱 Tech Stack

- Java 17
- Spring Boot 3
- Spring Security (JWT)
- Spring Data JPA
- PostgreSQL
- Flyway
- Maven

---

## 🏗️ Architecture

Controller → Service → Repository → PostgreSQL


### Layers

- **Controller**: Handles HTTP requests
- **Service**: Business logic layer
- **Repository**: Database access layer (JPA)
- **Entity**: Database models

---

## 🔐 Security

- JWT-based authentication
- Stateless session handling
- Custom JWT filter for request validation

---

## 🧱 Database Migration

Flyway is used for schema management:

src/main/resources/db/migration


- `V1__create_tables.sql` → schema creation
- `V2__seed_data.sql` → initial data

---

## ⚙️ Configuration

Application uses environment variables:

Example:

```properties
spring.datasource.url=jdbc:postgresql://db:5432/TaskflowDB
spring.datasource.username=${DB_USERNAME}
spring.datasource.password=${DB_PASSWORD}

🚀 Running Backend (Standalone)

mvn spring-boot:run
docker build -t taskflow-backend .
docker run -p 8080:8080 taskflow-backend

🧠 Design Decisions
1. Monolithic Architecture

Kept backend as a single Spring Boot application for simplicity and faster development.

2. JWT instead of Sessions

Chosen for stateless authentication and scalability.

3. Flyway instead of manual SQL

Ensures reproducible database state across environments.

4. Layered Architecture

Improves maintainability and separation of concerns.

4. Layered Architecture

Improves maintainability and separation of concerns.

⚖️ Tradeoffs

-> No microservices → simpler deployment but less scalability
-> No Redis caching → reduced complexity
-> No async messaging (Kafka/RabbitMQ) → kept synchronous APIs

📌 Future Improvements

-> Role-based access control (RBAC)
-> Redis caching layer
-> API rate limiting
-> Microservices split (Auth / Task / Project services)

