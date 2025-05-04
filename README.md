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
