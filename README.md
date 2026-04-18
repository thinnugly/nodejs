# Task Management System

A comprehensive task management system for managing tasks, users, comments, and notifications in an organizational environment. The system ensures users are informed about important changes, including task assignments, status updates, and comments.

**Author**: Renato Madeia Muiambo  
**Email**: [renatomuiambo24@gmail.com](mailto:renatomuiambo24@gmail.com)

---

## Table of Contents

- [Technologies](#technologies)
- [Prerequisites](#prerequisites)
- [How to Run Locally](#how-to-run-locally)
- [User Management](#user-management)
- [System Features](#system-features)
- [Docker Commands](#docker-commands)
- [Troubleshooting](#troubleshooting)
- [Project Structure](#project-structure)
- [Development Workflow](#development-workflow)
- [Production Deployment](#production-deployment)
- [Environment Variables](#environment-variables)
- [API Documentation](#api-documentation)
- [License](#license)
- [Contact](#contact)

---

## Technologies

### **Backend**
- **Node.js** + **Express.js** - REST API
- **JWT** - Authentication & Authorization
- **bcrypt** - Password hashing
- **mongoose** - MongoDB ODM

### **Frontend**
- **Vue.js 3** - Progressive JavaScript Framework
- **Vue Router** - Client-side routing
- **Vuex** - State management
- **Axios** - HTTP client
- **Bootstrap 5** - UI components

### **Database**
- **MongoDB** - NoSQL Database

### **Infrastructure**
- **Docker** - Containerization
- **Docker Compose** - Multi-container orchestration
- **Multi-stage Docker builds** - Optimized production images

---

## Prerequisites

Before starting, ensure you have the following installed on your machine:

- [Docker](https://www.docker.com/) (version 20.10+)
- [Docker Compose](https://docs.docker.com/compose/) (version 2.0+)
- [Git](https://git-scm.com/) (for cloning the repository)
- [Node.js](https://nodejs.org/) (v18+ - optional, for local development without Docker)

---

## 🔧 How to Run the Application Locally

### Step-by-Step Guide

#### 1. **Verify Docker Installation**

```bash
docker --version
docker compose version
```
#### 2. **Clone the repository**
```bash
git clone https://github.com/thinnugly/nodejs.git
cd nodejs
```
#### 3. **Create environment configuration file**

Inside the `server` directory, create a `.env.dev` file based on the `.env.example` template:
```sh
cd server
cp .env.example .env.dev
```

#### 4. **Edit the `.env.dev` file with your configuration**

#### 5. **Return to Project Root**

```sh
cd ..
```

#### 6. **Start all services**
```bash
docker compose -f docker-compose.dev up --build -d
```
This command:

- Builds the Docker images for backend and frontend
- Starts the MongoDB database
- Runs the backend API on port 3000
- Runs the frontend on port 8081
- Sets up the network for inter-container communication

You should see three services running: `nodejs-api-1`, `nodejs-db-1`, `nodejs-client-1`.

#### 7. **Verify Services are Running**
```bash
docker compose -f docker-compose.dev.yml ps
```

#### 8. **Access the Application**

| Service | URL | Description |
|---------|-----|-------------|
| **Backend API** | http://localhost:3000 | REST API endpoint |
| **API Documentation** | http://localhost:3000/api-docs | Swagger UI |
| **Frontend** | http://localhost:8081 | Vue.js client application |

#### 8. **Stop the Application**
```bash
docker compose -f docker-compose.dev.yml down
```
To stop and remove all data (including database):
```bash
docker compose -f docker-compose.dev.yml down -v
```
---
## User Management & Default Admin

### User Roles

The system supports two user roles:

| Role | Permissions | Access Level |
|------|-------------|--------------|
| **Administrator** | Full system access | Can create users, assign tasks, manage all resources |
| **Employee** | Standard user | Can view and manage assigned tasks only |

### Default Administrator Account

On the first run, an administrator account is **automatically created** if none exists in the database.

**Default Admin Credentials:**

| Field | Value |
|-------|-------|
| **Username/Email** | `renatomuiambo24@admin.com` |
| **Password** | `admin@admin` |

---
## Docker Commands

### Basic Commands

```bash
# Start all services
docker compose -f docker-compose.dev.yml up -d

# Start with build (recreate images)
docker compose -f docker-compose.dev.yml up --build -d

# View running containers
docker compose -f docker-compose.dev.yml ps

# View logs for specific service
docker compose -f docker-compose.dev.yml logs -f nodejs-api-1
docker compose -f docker-compose.dev.yml logs -f nodejs-client-1
docker compose -f docker-compose.dev.yml logs -f nodejs-db-1
```

### Container Management

```bash
# Stop all services
docker compose -f docker-compose.dev.yml down

# Stop and remove volumes (deletes database data)
docker compose -f docker-compose.dev.yml down -v

# Stop and remove everything including images
docker compose -f docker-compose.dev.yml down --rmi all -v

# Restart specific service
docker compose -f docker-compose.dev.yml restart api
```

---
## API Documentation

Once the application is running, access the interactive Swagger documentation at:

```bash
http://localhost:3000/api-docs
```
---
## Contact

| Platform | Details |
|----------|---------|
| **Author** | Renato Madeia Muiambo |
| **Email** | [renatomuiambo24@gmail.com](mailto:renatomuiambo24@gmail.com) |
| **GitHub** | [@thinnugly](https://github.com/thinnugly) |
| **Repository** | [https://github.com/thinnugly/nodejs](https://github.com/thinnugly/nodejs) |

---

## Acknowledgments

| Contributor | Role |
|-------------|------|
| **Advanced Web Programming Course** | Project inspiration and requirements |
| **Instructor** | Guidance and feedback |
| **Contributors** | Testing and contributions |
| **Open Source Community** | Amazing tools and libraries |

> 💡 *Special thanks to everyone who contributed to this project!*