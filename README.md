# Docker Compose PostgreSQL and Adminer Lab

## 1. Project Overview

This project demonstrates how to deploy PostgreSQL and Adminer using Docker Compose on an Ubuntu EC2 instance.

The purpose is to understand container management, database connectivity, Docker networking, and volume persistence.

## 2. Technologies Used

- Ubuntu Linux
- Docker
- Docker Compose
- PostgreSQL 16
- Adminer
- Git and GitHub

## 3. Project Architecture

This project contains two Docker services:

### PostgreSQL Database
- Container image: `postgres:16-alpine`
- Database name: `labdb`
- Username: `labuser`
- Port: `5432`

### Adminer
- Container image: `adminer:latest`
- Web-based database management interface
- Port: `8082`

## 4. Deployment Instructions

### Step 1: Start the containers

```bash
docker compose up -d
```

### Step 2: Check container status

```bash
docker compose ps
```

### Step 3: View container logs

```bash
docker compose logs --tail 20
```

### Step 4: Access Adminer

Open the following URL in a browser:

`http://YOUR_EC2_PUBLIC_IP:8082`

Use these connection details:

- System: PostgreSQL
- Server: db
- Username: labuser
- Database: labdb
- Password: Configure using your `.env` file

## 5. Database Verification

The following command verifies PostgreSQL connectivity:

```bash
docker compose exec db psql -U labuser -d labdb -c "SELECT current_database(), current_user;"
```

## 6. Docker Compose Management

Stop containers:

```bash
docker compose stop
```

Start containers:

```bash
docker compose start
```

Restart Adminer:

```bash
docker compose restart adminer
```

Stop and remove containers:

```bash
docker compose down
```

## 7. Volume Persistence

A test table and record were created in PostgreSQL.

After removing and recreating the containers, the record was successfully retrieved.

This confirms that the PostgreSQL Docker volume preserves database data.

## 8. Git and GitHub

The project was uploaded to GitHub using Git version control.

Repository: https://github.com/sabithkk/docker-compose-postgres-lab

Branch: `main`

## 9. Security

- Database password is stored in `.env`.
- `.env` is excluded using `.gitignore`.
- `.env.example` provides a sample environment variable.
- Never upload passwords, private keys, or access tokens.

## 10. Author

**Sabith**

## 11. Result

Successfully deployed PostgreSQL and Adminer using Docker Compose, verified database connectivity, tested container lifecycle management, confirmed volume persistence, and uploaded the project to GitHub.
