# HandyHub

HandyHub is a platform that connects customers with local service providers (electricians, plumbers, AC technicians, cleaners) for home jobs. Customers post a job, and providers browse the open job board and send quotes.

## Features (planned)

**Customers**
- Register and log in
- Post a job with a description, category, urgency and location
- Compare offers from providers and pick one
- Track job status and leave a review 

**Providers**
- Register and create a profile
- Browse all open jobs, filtered by category and distance
- Send quotes and update job status
- Build a rating through customer reviews

## Tech stack

- **Backend:** Java 21, Spring Boot 4, Spring Data JPA, Spring Security
- **Database:** PostgreSQL 16, Flyway migrations
- **DevOps:** Docker Compose, GitHub Actions CI
- **Monitoring:** Spring Boot Actuator
- **Frontend:** React (planned)

## Status

Work in progress.

**Done**
- Project setup with package-by-feature structure

- PostgreSQL running in Docker, with profile-based configuration (dev / prod)
- Flyway migrations for the `users` table
- CI pipeline that builds and tests every push and pull request
- Global exception handling with a consistent JSON error format

**Next**
- User registration and login (JWT)
- Job posting
- Open job board for providers

## Run locally

**Prerequisites:** JDK 21, Docker Desktop, Git

```bash
git clone https://github.com/mayantha22/Handyhub.git
cd Handyhub

# 1. Start PostgreSQL
docker compose up -d

# 2. Start the application
./mvnw spring-boot:run
```

On Windows PowerShell, use `.\mvnw.cmd spring-boot:run` for the last command.

The app runs on http://localhost:8080. Check that it is healthy at http://localhost:8080/actuator/health. The response should contain `"status": "UP"`.

**Run the tests** (the database must be running):

```bash

./mvnw verify
```

**Configuration:** the dev profile is active by default and uses the local Docker database. You can override the connection with the environment variables `DB_URL`, `DB_USERNAME` and `DB_PASSWORD`.