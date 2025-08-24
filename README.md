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
