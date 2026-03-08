# ShopSphere

A scalable and secure E-Commerce backend built with **Spring Boot 3** and **MySQL**, featuring **User Authentication (JWT)**, **Product Management**, **Shopping Cart**, **Orders**, and **Payment Processing**. Fully tested with **Postman** and documented with **Swagger**.

---

## Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
- [Database Setup](#database-setup)
- [API Endpoints](#api-endpoints)
- [Postman Testing Workflow](#postman-testing-workflow)
- [Swagger Documentation](#swagger-documentation)
- [Running Tests](#running-tests)
- [License](#license)

---

## Features

- **User Authentication:** Register and login with **JWT** tokens.
- **User Management:** Create and fetch users with pagination support.
- **Product Management:** CRUD operations for products with category and price filters.
- **Shopping Cart:** Add items to cart, view cart contents, manage quantities.
- **Order Management:** Place orders, cancel orders, view user orders.
- **Payment Processing:** Simulated payment flow with status updates.
- **Security:** Passwords encoded with **BCrypt**, JWT authentication for all protected endpoints.
- **Validation & Exception Handling:** Input validation and global exception handling.
- **Documentation:** Swagger/OpenAPI documentation for all endpoints.

---

## Tech Stack

- **Backend:** Java 17, Spring Boot 3, Spring Security, Spring Data JPA
- **Database:** MySQL
- **Authentication:** JWT (JSON Web Tokens)
- **Testing:** JUnit 5, Mockito
- **API Documentation:** Swagger (Springdoc OpenAPI)
- **Build Tool:** Maven
- **IDE Friendly:** Compatible with IntelliJ IDEA, VS Code

---

## Getting Started

### Prerequisites

- Java 17
- Maven 3.8+
- MySQL 8+
- Postman (optional, for testing)
  
### Steps to Run Locally

1. Clone the repository:

```bash
git clone https://github.com/darshan-p-2508/ShopSphere.git
cd ShopSphere
```

2. Configure application.properties:
```bash
spring.datasource.url=jdbc:mysql://localhost:3306/shopsphere
spring.datasource.username=YOUR_DB_USERNAME
spring.datasource.password=YOUR_DB_PASSWORD
jwt.secret=YOUR_SECRET_KEY
jwt.expiration=86400000
```

3. Build the project with Maven:
```bash
mvn clean install
```

4. Run the application:
```bash
mvn spring-boot:run
```

Database Setup

Create the MySQL database:
```bash
CREATE DATABASE shopsphere;
```
The application will automatically create tables using spring.jpa.hibernate.ddl-auto=update.

# Project Structure

ShopSphere/
├── .gitignore
├── README.md
├── LICENSE
├── pom.xml
├── application.properties
│
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/dars/shopsphere/
│   │   │       ├── ShopsphereApplication.java
│   │   │       ├── config/
│   │   │       │   ├── AppConfig.java
│   │   │       │   └── SwaggerConfig.java
│   │   │       ├── security/
│   │   │       │   ├── SecurityConfig.java
│   │   │       │   ├── CustomUserDetailsService.java
│   │   │       │   └── jwt/
│   │   │       │       ├── JwtAuthenticationFilter.java
│   │   │       │       └── JwtUtil.java
│   │   │       ├── common/
│   │   │       │   ├── response/
│   │   │       │   │   └── ApiResponse.java
│   │   │       │   └── exception/
│   │   │       │       └── GlobalExceptionHandler.java
│   │   │       ├── auth/
│   │   │       │   ├── controller/
│   │   │       │   │   └── AuthController.java
│   │   │       │   ├── dto/
│   │   │       │   │   ├── AuthResponse.java
│   │   │       │   │   ├── LoginRequest.java
│   │   │       │   │   └── RegisterRequest.java
│   │   │       │   └── service/
│   │   │       │       ├── AuthService.java
│   │   │       │       └── AuthServiceImpl.java
│   │   │       ├── user/
│   │   │       │   ├── controller/UserController.java
│   │   │       │   ├── dto/
│   │   │       │   │   ├── UserRequest.java
│   │   │       │   │   └── UserResponse.java
│   │   │       │   ├── entity/User.java
│   │   │       │   ├── repository/UserRepository.java
│   │   │       │   └── service/
│   │   │       │       ├── UserService.java
│   │   │       │       └── UserServiceImpl.java
│   │   │       ├── product/
│   │   │       │   ├── controller/ProductController.java
│   │   │       │   ├── dto/
│   │   │       │   │   ├── ProductRequest.java
│   │   │       │   │   └── ProductResponse.java
│   │   │       │   ├── entity/Product.java
│   │   │       │   ├── repository/ProductRepository.java
│   │   │       │   └── service/
│   │   │       │       ├── ProductService.java
│   │   │       │       └── ProductServiceImpl.java
│   │   │       ├── cart/
│   │   │       │   ├── controller/CartController.java
│   │   │       │   ├── dto/
│   │   │       │   │   ├── AddToCartRequest.java
│   │   │       │   │   ├── CartItemResponse.java
│   │   │       │   │   └── CartResponse.java
│   │   │       │   ├── entity/
│   │   │       │   │   ├── Cart.java
│   │   │       │   │   └── CartItem.java
│   │   │       │   ├── repository/
│   │   │       │   │   ├── CartRepository.java
│   │   │       │   │   └── CartItemRepository.java
│   │   │       │   └── service/
│   │   │       │       ├── CartService.java
│   │   │       │       └── CartServiceImpl.java
│   │   │       ├── order/
│   │   │       │   ├── controller/OrderController.java
│   │   │       │   ├── dto/
│   │   │       │   │   ├── OrderItemResponse.java
│   │   │       │   │   └── OrderResponse.java
│   │   │       │   ├── entity/
│   │   │       │   │   ├── Order.java
│   │   │       │   │   └── OrderItem.java
│   │   │       │   ├── enums/OrderStatus.java
│   │   │       │   ├── repository/OrderRepository.java
│   │   │       │   └── service/
│   │   │       │       ├── OrderService.java
│   │   │       │       └── OrderServiceImpl.java
│   │   │       └── payment/
│   │   │           ├── controller/PaymentController.java
│   │   │           ├── dto/PaymentRequest.java
│   │   │           └── service/
│   │   │               ├── PaymentService.java
│   │   │               └── PaymentServiceImpl.java
│   │   └── resources/
│   │       ├── application.properties
│   │       └── (optional) data.sql, schema.sql
│   │
│   └── test/
│       └── java/com/dars/shopsphere/
│           ├── ShopsphereApplicationTests.java
│           ├── cart/service/CartServiceImplTest.java
│           ├── order/service/OrderServiceImplTest.java
│           └── payment/service/PaymentServiceImplTest.java
│
└── .gitignore
