# Airbnb Clone Project

## Project Overview
This project is a full-stack web application clone of Airbnb, built to simulate a real-world booking platform. The goal is to master collaborative development, backend architecture, database design, API security, and CI/CD pipeline implementation.

## Tech Stack
The project will utilize a modern tech stack including:
- **Backend:** Django & Django REST Framework
- **Database:** PostgreSQL
- **API Query Language:** GraphQL
- **Containerization:** Docker
- **CI/CD:** GitHub Actions
- **Deployment:** (e.g., Heroku, AWS, or DigitalOcean)

- ## Team Roles

In a project of this scale, team members assume specialized roles:

- **Backend Developer:** Responsible for building the core application logic, APIs (REST/GraphQL), and integrating with the database using Django.
- **Database Administrator (DBA):** Designs, implements, and maintains the PostgreSQL database schema. Ensures data integrity, optimizes queries, and handles migrations.
- **DevOps Engineer:** Sets up and manages the CI/CD pipeline using GitHub Actions and Docker. Automates testing, building, and deployment processes.
- **Security Specialist:** Implements authentication (JWT/OAuth), authorization, encryption, and other security best practices across the application.
- **Project Manager / Tech Lead:** Oversees the project timeline, coordinates tasks between team members, facilitates agile ceremonies (stand-ups, sprints), and ensures alignment with project goals.
- **Quality Assurance (QA) Engineer:** Writes and executes manual and automated test plans to identify bugs and ensure the application meets functional requirements.
## Technology Stack

- **Django & Django REST Framework (DRF):** A high-level Python web framework that encourages rapid development. DRF is used to build a robust, RESTful API that handles requests for user, property, and booking data.
- **PostgreSQL:** A powerful, open-source relational database system. It is chosen for its reliability, robustness, and ability to handle complex queries and relationships, which are crucial for a booking platform.
- **GraphQL:** A query language for APIs. It allows frontend clients to request exactly the data they need in a single request, improving efficiency, especially for complex data structures like property listings with reviews.
- **Docker:** A containerization platform used to package the application and its dependencies into isolated containers. This ensures consistency across different development and deployment environments (e.g., "It works on my machine" is eliminated).
- **GitHub Actions:** A CI/CD (Continuous Integration/Continuous Deployment) tool integrated into GitHub. It automates the process of testing code and deploying it to a live server whenever changes are pushed to the main branch.
- **Nginx:** A web server that will act as a reverse proxy for our Django application, handling client requests and serving static files efficiently.
- **Gunicorn:** A Python WSGI HTTP Server that will serve our Django application in production.
- ## Database Design

The database will consist of the following key entities and relationships:

1.  **User**
    - `id` (Primary Key), `username`, `email`, `password_hash`, `first_name`, `last_name`, `profile_picture_url`, `is_host`
    - *Relationships:* A User can have many Properties (One-to-Many). A User can have many Bookings (One-to-Many). A User can have many Reviews (One-to-Many).

2.  **Property**
    - `id` (Primary Key), `title`, `description`, `price_per_night`, `location`, `host_id` (Foreign Key to User)
    - *Relationships:* A Property belongs to one User (the host). A Property can have many Bookings (One-to-Many). A Property can have many Reviews (One-to-Many).

3.  **Booking**
    - `id` (Primary Key), `property_id` (Foreign Key to Property), `guest_id` (Foreign Key to User), `check_in_date`, `check_out_date`, `total_price`, `status` (e.g., pending, confirmed, cancelled)
    - *Relationships:* A Booking belongs to one Property. A Booking belongs to one User (the guest).

4.  **Review**
    - `id` (Primary Key), `booking_id` (Foreign Key to Booking), `property_id` (Foreign Key to Property), `guest_id` (Foreign Key to User), `rating`, `comment`
    - *Relationships:* A Review belongs to one Booking. A Review belongs to one Property. A Review belongs to one User.

5.  **Payment**
    - `id` (Primary Key), `booking_id` (Foreign Key to Booking), `amount`, `payment_method`, `status` (e.g., pending, completed, failed), `transaction_id`
    - *Relationships:* A Payment transaction belongs to one Booking.
    - ## Feature Breakdown

- **User Authentication & Authorization:** Allows users to securely sign up, log in, and log out. This is the foundation for personalizing the user experience and protecting sensitive actions and data.
- **Property Management:** Enables hosts to create, read, update, and delete property listings. This feature is core to populating the platform with bookable spaces.
- **Booking System:** Allows guests to search for properties, check availability, and make reservations. This handles the core business logic of calculating stay duration, total cost, and managing availability conflicts.
- **Review & Rating System:** Allows guests to leave reviews and ratings for properties they've booked. This builds trust and community on the platform by providing social proof for listings.
- **Payment Processing Integration:** A secure system to handle financial transactions for bookings. This is critical for the platform's commercial viability and requires strict security measures.
- ## API Security

Implementing robust security measures is non-negotiable for a platform handling personal and financial data.

- **Authentication (JWT Tokens):** JSON Web Tokens will be used to verify a user's identity after login. This is crucial to ensure that only logged-in users can perform actions like making bookings or creating listings.
- **Authorization (Permission Classes):** Django REST Framework's permission classes will ensure users can only edit or delete their own resources (e.g., a user can only update their own property listing, not others'). This protects data integrity and user privacy.
- **Data Encryption (HTTPS & Database):** All data in transit will be encrypted using HTTPS/TLS. Sensitive data like passwords will be hashed (using bcrypt/Argon2) before being stored in the database, protecting it even in the event of a breach.
- **Rate Limiting:** APIs, especially for login and signup, will have rate limiting to prevent abuse and Denial-of-Service (DoS) attacks by blocking excessive requests from a single IP address.
- **Input Validation & Sanitization:** All user input will be rigorously validated on the backend to prevent common vulnerabilities like SQL Injection and Cross-Site Scripting (XSS), which are critical for maintaining database and user security.
- ## CI/CD Pipeline

A CI/CD (Continuous Integration/Continuous Deployment) pipeline automates the steps from code commit to deployment, reducing human error and ensuring faster, more reliable releases.

- **What it is:** CI/CD is an automated process. **CI (Continuous Integration)** automatically builds and tests code every time a developer pushes changes. **CD (Continuous Deployment)** automatically deploys that tested code to a live server.
- **Why it's important:** It ensures that code in the main branch is always deployable. It catches bugs early through automated testing, accelerates the release process, and allows for frequent, small updates.
- **Tools for this project:** We will use **GitHub Actions** to define our CI/CD workflow. The pipeline will:
    1.  **Lint & Test:** Run automatically on every pull request to the main branch to check code style and run unit tests.
    2.  **Build & Containerize:** If tests pass, the workflow will build the Docker image for the application.
    3.  **Deploy:** The workflow will then deploy the updated Docker container to our production server (e.g., AWS EC2, DigitalOcean Droplet).
