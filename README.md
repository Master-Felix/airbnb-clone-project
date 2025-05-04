# Airbnb Clone Project

## Overview

The Airbnb Clone Project is a comprehensive full-stack development exercise inspired by the popular booking platform, Airbnb. The aim of this project is to simulate the design and development of a scalable, secure, and feature-rich web application that allows users to list, discover, and book accommodations.

This project serves as a deep dive into backend development, database design, API security, CI/CD integration, and collaborative team workflows—preparing developers for real-world software engineering challenges.

## Project Goals

- Build a scalable and secure backend system using Django.
- Design a relational database using MySQL to store user, property, and booking data.
- Develop RESTful (and optionally GraphQL) APIs to support frontend communication.
- Implement CI/CD pipelines for continuous integration and deployment.
- Strengthen collaborative development through GitHub workflows and documentation.

## Tech Stack

- **Backend Framework**: Django (Python)
- **Database**: MySQL
- **API**: REST (with optional GraphQL)
- **Containerization**: Docker
- **CI/CD**: GitHub Actions
- **Version Control**: Git + GitHub

## Status

✅ Initialized repository  
✅ Created initial README.md  
⬜️ Database Design  
⬜️ API Development  
⬜️ CI/CD Setup  
⬜️ Security Implementation

## Team Member Responsibilities

For the purpose of accomplishing the effective collaboration and delivering the project successfully, understanding team roles is needful. Here is an explanation of the roles done in the Airbnb Clone Project which is modeled from actual development teams.

### 1. **Project Manager (PM)**

- **Responsibilities**: Ensures deadlines are achieved, facilitates communication among team members, prevents any blockers, and supervises the holistic progress of the project. Coordinates timelines and manages deliverables.

### 2. **Product Manager**

- **Responsibilities**: Guarantees that the final product meets user need as well as define the vision and scope of the product while prioritizing features based on business value.

### 3. **Backend Developer**

- **Responsibilities**: Designs and implements the business logic server-side using Django, builds and secures APIs, integrates with the database, and ensures the application works behind the scenes.

### 4. **Database Administrator (DBA)**

- **Responsibilities**: Oversees the designing and managing of the database schema in MySQL. Maintains data integrity, manages backups, migrations, and optimizes queries.

### 5. **DevOps Engineer**

- **Responsibilities**: Automate, monitor, and ensure consistency of the tests and the deploys using CI/CD pipelines in tools like GitHub Actions and Docker. Guarantee reliability and scalability of the system in development and production.

## Database Design

This project uses a **relational database model** designed with MySQL to manage and persist application data. Below is a breakdown of the key entities and their relationships:

### 📌 Entities & Fields

### 1. **Users**

- `id` (Primary Key)
- `full_name` (VARCHAR)
- `email` (Unique, VARCHAR)
- `password_hash` (TEXT)
- `created_at` (TIMESTAMP)

### 2. **Properties**

- `id` (Primary Key)
- `owner_id` (Foreign Key → Users.id)
- `title` (VARCHAR)
- `description` (TEXT)
- `location` (VARCHAR)
- `price_per_night` (DECIMAL)

### 3. **Bookings**

- `id` (Primary Key)
- `user_id` (Foreign Key → Users.id)
- `property_id` (Foreign Key → Properties.id)
- `start_date` (DATE)
- `end_date` (DATE)
- `total_price` (DECIMAL)

### 4. **Reviews**

- `id` (Primary Key)
- `user_id` (Foreign Key → Users.id)
- `property_id` (Foreign Key → Properties.id)
- `rating` (INT)
- `comment` (TEXT)

### 5. **Payments**

- `id` (Primary Key)
- `booking_id` (Foreign Key → Bookings.id)
- `amount` (DECIMAL)
- `payment_method` (VARCHAR)
- `status` (ENUM: "pending", "completed", "failed")

---

### 🔗 Entity Relationships

![ERD](/ERD.png)

- A **User** can own multiple **Properties** (One-to-Many).
- A **User** can make multiple **Bookings** (One-to-Many).
- A **Property** can have multiple **Bookings** (One-to-Many).
- A **Booking** is associated with one **User** and one **Property** (Many-to-One).
- A **User** can leave multiple **Reviews** for different **Properties**.
- A **Property** can have multiple **Reviews** (One-to-Many).
- Each **Booking** has one corresponding **Payment** (One-to-One).

## Feature Breakdown

This section outlines the core features of the Airbnb Clone project, each of which contributes to building a robust, user-centric booking platform.

### 1. **User Management**

Users can register, log in, update their profiles, and securely manage their account credentials. This feature ensures personalized experiences and supports role-based actions like hosting or booking properties.

### 2. **Property Management**

Registered users can list their properties by adding details such as title, description, location, price per night, and photos. This feature enables property owners to showcase and manage their listings on the platform.

### 3. **Booking System**

Users can search for available properties and make bookings for specific dates. The system calculates total cost, checks for availability, and prevents overlapping reservations—ensuring a smooth reservation experience.

### 4. **Review & Rating System**

After completing a booking, users can leave a review and rate the property. This encourages quality service and builds trust within the platform by allowing future guests to make informed decisions.

### 5. **Payment Integration**

The platform supports payment processing tied to bookings, ensuring transactions are tracked and securely handled. Users can choose payment methods and view the status of their payments.

### 6. **Authentication & Authorization**

The app uses secure authentication mechanisms, including password hashing and session/token-based access control. This safeguards user data and restricts access to authorized content and actions.

### 7. **Admin Dashboard (Optional Advanced Feature)**

Admins can monitor system activity, manage users, review listings, and resolve disputes. This ensures platform integrity and operational oversight.

## API Security

Securing the backend API is critical to maintaining the integrity, confidentiality, and availability of the system. Below are key security measures implemented in the Airbnb Clone project and their significance:

### 🔐 Authentication

**What it is**: Validates the identity of users using secure login mechanisms (e.g., token-based authentication like JWT or session-based login).
**Why it matters**: Ensures only verified users can access protected routes, protecting sensitive data such as booking history and payment details.

### 🔒 Authorization

**What it is**: Determines what resources a user can access based on their role (e.g., host, guest, admin).
**Why it matters**: Prevents unauthorized access to actions such as editing properties or viewing another user's information.

### 📈 Rate Limiting

**What it is**: Controls the number of API requests a user or IP can make in a given timeframe.
**Why it matters**: Prevents abuse, brute-force login attempts, and denial-of-service (DoS) attacks that can slow or crash the server.

### 🧼 Input Validation & Sanitization

**What it is**: Cleans and checks all incoming data for expected formats.
**Why it matters**: Protects the system from common vulnerabilities such as SQL injection and cross-site scripting (XSS).

### 🧾 Secure Payment Handling

**What it is**: Uses encrypted communication channels and third-party payment gateways to handle transactions.
**Why it matters**: Ensures users' financial data remains private and that payments are processed safely and accurately.

### 🔐 HTTPS Enforcement

**What it is**: Forces all requests to go through encrypted HTTPS connections.
**Why it matters**: Protects data in transit from being intercepted or tampered with during communication between client and server.

## CI/CD Pipeline

### What is CI/CD?

CI/CD stands for **Continuous Integration** and **Continuous Deployment**. It is a set of practices and tools that automate the process of building, testing, and deploying code. This ensures that every code change is automatically validated and deployed, minimizing human error and accelerating the development cycle.

### Why It Matters

- **Faster Development**: Automates testing and deployment, allowing features and fixes to reach production faster.
- **Improved Code Quality**: Automatically runs tests and linting to catch bugs early in the development process.
- **Team Collaboration**: Streamlines integration of contributions from multiple developers, reducing merge conflicts and deployment issues.
- **Reliability**: Ensures consistent environments across development, staging, and production.

### Tools We Use

- **GitHub Actions**: Automates workflows like testing, linting, and deployment on every push or pull request.
- **Docker**: Creates isolated environments to run the application, ensuring consistency across different machines and stages.
- **MySQL Service**: Used in CI to test database interactions during automated builds.
- **Optional**: Tools like **Heroku**, **AWS**, or **Render** for deployment depending on the hosting setup.
