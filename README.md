# Trackly---A-Task-Management-Application
Trackly is a microservice-based task management application built on the MERN stack (MongoDB, Express.js, React, Node.js). It leverages modern technologies like ElasticSearch for centralized logging, and Docker for scalable deployment, and GitHub Actions for continuous integration.

## Features Overview

### 1. User Authentication
- Secure registration and login using JWT-based authentication.
- Passwords are hashed using bcryptjs.
- Role-based access control (RBAC) with JWT tokens.
- Email verification with OTP ensures secure account activation before login.
- Password reset via OTP, allowing users to recover access securely.

### 2. Task Management
- Create, view, update, and delete tasks.
- Assign tasks to users and track progress.

### 3. Notification Handling
- View real-time task-related notifications through API polling.

### 4. Centralized Logging & Monitoring
- Logs from all services are stored in ElasticSearch.
- Kibana provides a visual interface for monitoring and analysis.

### 5. Security
- JWT Authentication with RSA asymmetric encryption (RS256).
- Passwords are securely hashed before storage.
- Role-based authorization for various user roles.
- API Rate Limiting implemented to prevent abuse and brute-force attacks.

### 6. Deployment
- Docker-based containerization for all services.
- Docker Compose setup for easy deployment.

### 7. Continuous Integration
- GitHub Actions automate dependency installation, testing, and builds for the backend and frontend services.

## Tech Stack

### Backend
- Node.js (Express)
- MongoDB (Database)
- JWT (RSA encryption)

### Frontend
- React
- CORS-enabled API calls

### Infrastructure
- Docker Compose
- ElasticSearch, Logstash & Kibana (for logging and monitoring)
- GitHub Actions (for CI/CD workflows)

## Microservice Architecture

![Architecture Overview](assets/images/image.png)

### authService
**Port:** 5005  
**Responsibilities:**
- Handles user registration, login, and profile management.
- Issues JWT tokens signed with RSA private keys.
- Enforces role-specific permissions for users.

**API Endpoints:**
- `POST /api/auth/register`
- `POST /api/auth/login`
- `GET /api/auth/profile`
- `GET /api/auth/is-auth`
- `POST /api/auth/logout`

### taskService
**Port:** 5000  
**Responsibilities:**
- Provides CRUD operations for tasks.
- Manages task assignment to users.
- Sends notifications to the Notification Service.

**API Endpoints:**
- `POST /tasks`
- `GET /tasks`
- `PUT /tasks/:id`
- `DELETE /tasks/:id`
- `POST /tasks/assign`

### notificationService
**Port:** 5001  
**Responsibilities:**
- Stores and serves task-related notifications.
- Provides APIs for fetching notifications.

**API Endpoints:**
- `GET /notifications`
- `POST /notifications`

### frontend
**Port:** 5173  
**Responsibilities:**
- Provides the user interface for Trackly.

### mongodb
**Port:** 27017  
**Responsibilities:**
- Stores data for authentication, tasks, and notifications.

### elasticSearch
**Port:** 9200  
**Responsibilities:**
- Stores and indexes logs.
- Provides search and analytics capabilities.

### logstash
**Port:** 5044  
**Responsibilities:**
- Processes and forwards logs to ElasticSearch.

### kibana
**Port:** 5601  
**Responsibilities:**
- Visualizes and analyzes logs from ElasticSearch.

## Setup Instructions

### Using Docker Compose

1. Clone the repository:
   ```sh
   git clone https://github.com/Study-Program-Applied-Computer-Science/software-architecture-and-development-trackly.git
   ```
2. Navigate to the project directory:
   ```sh
   cd software-architecture-and-development-trackly
   ```
3. Run the following command to build and start the services:
   ```sh
   docker-compose up --build -d
   ```

## Access the Services

- **Frontend:** [http://localhost:5173](http://localhost:5173)
- **Auth Service:** [http://localhost:5005](http://localhost:5005)
- **Task Service:** [http://localhost:5000](http://localhost:5000)
- **Notification Service:** [http://localhost:5001](http://localhost:5001)
- **Kibana:** [http://localhost:5601](http://localhost:5601)
