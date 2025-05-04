# AirBnB Clone Project

## Project Overview

The **AirBnB Clone Backend** is a robust, scalable, and fully functional API Service designed to replicate the core features of AirBnB. It manages **user authentication**, **property listings**, **booking flows** and **reviews**, providing both RESTful and GraphQL endpoints for flexible client interaction.

---

## Project Goals

- **User Management:** Secure registration, login, and profile handling.
- **Property Management:** CRUD operations for property listings.
- **Booking System:** End-to-end booking and reservation flows.
- **Payment Processing:** Integrated system to handle transactions.
- **Review System:** Posting and managing property reviews.
- **Data Optimization:** Efficient querying and storage via indexing and caching.

---

## 🛠️ Features Overview

### 1. API Documentation
- **OpenAPI Standard:** For easy integration and clear documentation.
- **Django REST Framework:** RESTful interface for all CRUD operations.
- **GraphQL Support:** Efficient and flexible data querying.

### 2. User Authentication
- **Endpoints:** `/users/`, `/users/{user_id}/`
- **Features:** Register, authenticate, view, update, and delete users.

### 3. Property Management
- **Endpoints:** `/properties/`, `/properties/{property_id}/`
- **Features:** List, create, retrieve, update, and delete properties.

### 4. Booking System
- **Endpoints:** `/bookings/`, `/bookings/{booking_id}/`
- **Features:** Make, view, and manage reservations.

### 5. Payment Processing
- **Endpoints:** `/payments/`
- **Features:** Handle all payments securely and reliably.

### 6. Review System
- **Endpoints:** `/reviews/`, `/reviews/{review_id}/`
- **Features:** Post, update, and delete property reviews.

### 7. Database Optimization
- **Indexing:** Improved speed for common queries.
- **Caching (Redis):** Reduced load and improved response time.

---

## ⚙️ Technology Stack

| Component            | Technology            |
|---------------------|------------------------|
| Backend Framework   | Django                 |
| API Layer           | Django REST Framework  |
| Database            | PostgreSQL             |
| Query Language      | GraphQL                |
| Async Tasks         | Celery                 |
| Caching             | Redis                  |
| Containerization    | Docker                 |
| CI/CD Pipelines     | GitHub Actions / CI/CD |

---

## 📌 API Endpoints Overview

### 🧑 Users
- GET /users/ - List all users
- POST /users/ - Create a new user
- GET /users/{user_id}/ - Retrieve user
- PUT /users/{user_id}/ - Update user
- DELETE /users/{user_id}/ - Delete user

### 🏠 Properties
- GET /properties/ - List all properties
- POST /properties/ - Create property
- GET /properties/{id}/ - Retrieve property
- PUT /properties/{id}/ - Update property
- DELETE /properties/{id}/ - Delete property

### 📅 Bookings
- GET /bookings/ - List all bookings
- POST /bookings/ - Create booking
- GET /bookings/{id}/ - Retrieve booking
- PUT /bookings/{id}/ - Update booking
- DELETE /bookings/{id}/ - Delete booking

### 💳 Payments
- POST /payments/ - Process a payment

### 📝 Reviews
- GET /reviews/ - List all reviews
- POST /reviews/ - Create review
- GET /reviews/{id}/ - Retrieve review
- PUT /reviews/{id}/ - Update review
- DELETE /reviews/{id}/ - Delete review


---

## 📈 API Documentation

- **REST API Docs:** Available via `/docs/` (Swagger/OpenAPI)
- **GraphQL Playground:** Access at `/graphql/` for flexible data queries

---

## 👥 Team Roles

| Role                | Responsibilities                              |
|---------------------|-----------------------------------------------|
| Backend Developer   | API endpoints, database schemas, business logic |
| Database Admin      | Schema design, performance tuning, indexing   |
| DevOps Engineer     | Facilitate cooporation between development and operations teams. Roles include Docker setup, Build CI/CD pipelines for fast delivery, monitoring  |
| QA Engineer         | Writing test cases and validating endpoints   |
| Business Analyst    | Translates customers business needs into requrirements |
| Product Owner       | Makes sure the final product meets customer requirements |
| Project Manager     | Makes sure a product or its part is delivered on time and within budget |
| UI/UX designer      | Transforms a product vision into user-friendly designs |
| Software architect  | Designs a high-level software architecture by selecting appropriate tools and platforms to implement the product vision |
| Test automation engineer | Designs a test automation ecosystem. Write and maintains test scripts for automated testing |

---

## 📚 Additional Resources

- 📘 [System design architecture for hotel booking apps](https://medium.com/nerd-for-tech/system-design-architecture-for-hotel-booking-apps-like-airbnb-oyo-6efb4f4dddd7)

---

## 💡 Getting Started

To get this backend up and running on your local machine:

```bash
# Clone the repo
git clone https://github.com/EHronek02/airbnb-clone-project.git
cd airbnb-clone-project

# Build and run with Docker
docker-compose up --build
