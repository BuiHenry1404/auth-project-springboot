# 🔐 Auth Project Example using Spring Security and JWT

This is a basic authentication and authorization example using **Spring Boot**, **Spring Security 6**, and **JWT (JSON Web Token)**.  
It provides endpoints for user registration, login, and role-based access control (RBAC).

---

## 📦 Features

- ✅ User registration and login
- 🔐 Secure password hashing using BCrypt
- 🪪 JWT access token generation and validation
- 👤 Role-based authorization (`ROLE_USER`, `ROLE_ADMIN`)
- 🔄 Token filter to authenticate requests
- ❌ Access denied and exception handling
- 📁 Clean package structure (controller, service, repository, security, config, etc.)

---

## 🛠️ Tech Stack

- Java 17+
- Spring Boot 3.x
- Spring Security 6.x
- JWT (io.jsonwebtoken / jjwt)
- H2 / MySQL (configurable)
- Lombok
- Maven

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/BuiHenry1404/auth-project.git
cd auth-jwt-springboot
```

### 2. Configure application properties

Edit `src/main/resources/application.yml` or `application.properties`:

```yaml
spring:
  datasource:
    url: jdbc:mysql://localhost:3306/auth_db
    username: root
    password: yourpassword

jwt:
  secret: your_jwt_secret_key
  expiration: 3600000 # 1 hour
```

> 💡 You can switch to H2 for testing by modifying the `datasource` section.

---

## 📑 API Endpoints

| Method | Endpoint           | Description              | Access       |
|--------|--------------------|--------------------------|--------------|
| POST   | `/api/auth/register` | Register new user       | Public       |
| POST   | `/api/auth/login`    | Login and get JWT token | Public       |
| GET    | `/api/user/me`       | Get user info           | ROLE_USER    |
| GET    | `/api/admin/dashboard` | Admin dashboard       | ROLE_ADMIN   |

---

## 🧪 Example JSON

### Register

```json
POST /api/auth/register
{
  "username": "john",
  "email": "john@example.com",
  "password": "123456"
}
```

### Login

```json
POST /api/auth/login
{
  "email": "john@example.com",
  "password": "123456"
}
```

Response:

```json
{
  "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "tokenType": "Bearer"
}
```

---

## 🧰 Project Structure

```
src
├── config            # Security config
├── controller        # API endpoints
├── dto               # Request/Response DTOs
├── model             # JPA entities (User, Role)
├── repository        # Spring Data JPA
├── security          # JWT utils, filter, services
├── service           # Business logic
└── AuthApplication.java
```

---

## 🛡️ Security Flow

1. User logs in with email & password
2. JWT is generated and sent back
3. On next request, client sends `Authorization: Bearer <token>`
4. JWT filter authenticates and sets the user in the SecurityContext

---

## 🧾 License

This project is open-source under the [MIT License](LICENSE).

---

## 🙋‍♂️ Author

Developed by BuiHenry1404.  
Feel free to fork or contribute! PRs welcome 🤝
