# Docker Quick Commands & Database Setup

This document contains handy Docker commands for running shells inside containers, copying files, and setting up PostgreSQL and MySQL using Docker.

---

## 1. Running Bash in a Docker Container

Use the following command to run an interactive bash shell inside a running container:

```bash
docker exec -it <ContainerName or ContainerID> bash
```

---

## 2. Copy File into Docker Container

To copy a file from the host machine into a Docker container:

```bash
docker cp <file-path> <ContainerName>:<destinationPath>
```

---

## 3. Docker PostgreSQL Setup

### Step 1: Pull PostgreSQL Image
```bash
docker pull postgres
```

### Step 2: Run PostgreSQL Container
```bash
docker run --name postgresContainer -e POSTGRES_PASSWORD=123 -d -p 5432:5432 postgres
```

### Step 3: Verify Container
```bash
docker ps
```

### Step 4: Access PostgreSQL
```bash
docker exec -it postgresContainer psql -U postgres
```

### Step 5: Create Database
Inside `psql`, run:
```sql
CREATE DATABASE test_db;
```

📖 More resources: [Postgres Docker Hub](https://hub.docker.com/_/postgres)

---

## 4. Docker MySQL Setup

### Step 1: Pull MySQL Image
```bash
docker pull mysql
```

### Step 2: Run MySQL Container
```bash
docker run --name mysqlContainer -e MYSQL_ROOT_PASSWORD=123 -d -p 3306:3306 mysql
```

### Step 3: Verify Container
```bash
docker ps
```

### Step 4: Access MySQL
```bash
docker exec -it mysqlContainer mysql --user=root --password
```

Enter the password when prompted (`123` in this example).

### Step 5: Create Database
Inside MySQL, run:
```sql
CREATE DATABASE test_db;
```

📖 More resources: [MySQL Docker Hub](https://hub.docker.com/_/mysql)

---

## ✅ Summary

- Run bash in container → `docker exec -it <container> bash`
- Copy file → `docker cp <file-path> <container>:<destinationPath>`
- PostgreSQL setup → pull, run, access, create DB
- MySQL setup → pull, run, access, create DB

---
