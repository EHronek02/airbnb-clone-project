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

## ⚙️ Technology Stack

| Component            | Technology            | Purpose in project |
|---------------------|------------------------|---------------------
| Backend Framework   | Django                 | A high level python web framework used for building secure, scalable web APIs. |
| API Layer           | Django REST Framework  | An extension of Django that simplifies the creation of RESTful APIs. |
| Database            | PostgreSQL             | A powerful, open-source relational database used to store and manage all data. |
| Query Language      | GraphQL                | A flexible query language that allows clients to request exactly the data they need. |
| Async Tasks         | Celery                 | A task queue used to handle asynchronous background tasks (e.g., sending emails). |
| Caching             | Redis                  | An in-memory data store used for caching, speeding up API responses and task queues. |
| Containerization    | Docker                 | Ensures consistency across development and production by containerizing the app. |
| CI/CD Pipelines     | GitHub Actions / CI/CD | Automates testing and deployment processes to ensure faster and more reliable delivery. |

---

## Database Design

The database is designed to capture all core entities and relationships needed to replicate AirBnB's backend functionality. Below are the primary models/entities and their key fields along with a description of how they relate to each other.

### Users
Represents all users on the platform (both guests and hosts).

**Key Fields:**
- `id` - Unique identifier for a user object (UUID)
- `first_name` - First name of the user
- `Last_name` - Last name of the user
- `email` - email address (used for login)
- `password` - hashed password for authentication
- `is_host` - Boolean indicating if the user can list properties
- `role` - Enum : Guest, host, admin
- `created_at` - date user was created
- `update_at` - last time user was updated

**Relationships:**
- a user can list multiple
- a user can make multiple bookings
- a user can leave multiple reviews

---

### Properties
Represents a property that can be booked by users.

**Key Fields:**
- `id` - unique identifier for property objects
- `host_id` - references the user who owns the property
- `title` - Title of the listing
- `description` - description of the property
- `location` - address/ general location of the property
- `price_per_night` - cost per night
- `max_guests` - maximum guest accomodate
- `is_available` - status of the property if is available or not
- `created_at` - date object was created
- `updated_at` - date object was updated

**Relationships:**
- Each property belongs to one host (user)
- A property can have many bookings
- A property can receive many reviews

---

### Bookings
Represents a reservation made by a user for a property.

**Key Fields**
- `id` - unique identifier for the booking object
- `user_id` - refrences the user making the booking
- `property_id` - references the booked property
- `check_in` - start date of the booking
- `check_out` - End date of the booking
- `status` - Pending, confirmed, cancelled
- `created_at` - date object was created
- `updated_at` - date object was updated

**Relationships:**
- Each booking belongs to one user
- Each booking is associated with one review
- Each booking can have one payment

---

### Payments
Represents payments made for bookings.

**Key Fields:**
- `id` - unique identifier for a payment
- `booking_id` - references the associated booking
- `amount` - total amount paid
- `payment_method` - either credit_card, paypal, stripe
- `transaction_id` - transaction identity
- `payment_status` - status (e.g, paid, failed, pending)
- `timestamp` - Time of transaction
- `created_at` - date object was created
- `updated_at` - date object was updated

**Relationships:**
- Each payment is linked to one booking (one to one)

---

### Reviews
Represents feedback left by users on properties.

**Key Fields:**
- `id` - unique identifier
- `user_id` - references the user who wrote the review
- `booking_id` - specific booking id
- `rating` - numerical rating
- `comment` - textual review
- `created_at` - date object was created
- `updated_at` - date object was updated

**Relationships:**
- Each review is written by one user
- Each review is for one booking

---

### Entity Relationship Overview
- **User ↔ Properties**: One-to-Many (one user can list many properties)
- **User ↔ Bookings**: One-to-Many (one user can make many bookings)
- **User ↔ Reviews**: One-to-Many (one user can write many reviews)
- **Property ↔ Bookings**: One-to-Many (one property can be booked many times)
- **Property ↔ Reviews**: One-to-Many (one property can have many reviews)
- **Booking ↔ Payment**: One-to-One (each booking has one payment)

### Critical Optimizations
**Databse Indexes**
- **Users**: email(unique), role (for filtering hosts/guests).
- **Properties**: host_id, location, price_per_night
- **Bookings**: property_id, check_in, check_out
- **Reviews**: property_id (to calculate average rating quickly)

**Constraints**
- Check constraint: ensure check_out > check_in in bookings
- Unique constraint: Reviews.booking_id(one review per booking)

---
## Feature Breakdown

### 👤 User Management  
Securely handles user registration, authentication, and profile updates. Users can sign up as guests, hosts, or admins, with role-based access controls (e.g., only hosts can list properties). Built with JWT for stateless authentication and OAuth support for third-party logins.  

### 🏠 Property Management  
Allows hosts to create, update, and delete property listings with details like location, pricing, and amenities. Guests can search properties using filters (price, location, dates) and view availability calendars. Geospatial indexing enables "nearby properties" queries.  

### 📅 Booking System  
Guests can reserve properties by selecting check-in/check-out dates, with real-time availability validation. Hosts manage bookings (confirm, cancel) and track statuses (pending/confirmed/cancelled). Overlapping date conflicts are prevented using database constraints.  

### 💳 Payment Processing  
Integrated with Stripe/PayPal to securely handle transactions. Payments are linked to bookings, with idempotency to avoid duplicate charges. Webhooks update booking statuses asynchronously on payment success/failure.  

### ⭐ Review System  
Guests can leave ratings (1-5 stars) and comments for properties they’ve booked. Reviews are tied to specific bookings to prevent spam. Average ratings are dynamically calculated and cached for performance.  

### 🚀 Database Optimizations  
PostgreSQL with indexing (e.g., `property_id + dates` for bookings) and Redis caching for frequent queries like property searches. Partitioning and read replicas ensure scalability for high traffic.  

### 📚 API Documentation  
Comprehensive REST and GraphQL APIs documented via OpenAPI/Swagger. Supports CRUD operations for all entities and flexible queries (e.g., fetch a property’s details + reviews in one GraphQL request).  

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
