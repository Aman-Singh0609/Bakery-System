Here's the enhanced README.md with your screenshots incorporated at optimal locations:

# Bakery Management System - Docker Implementation

## Table of Contents
1. [System Architecture](#system-architecture)
2. [Prerequisites](#prerequisites)
3. [Setup Instructions](#setup-instructions)
4. [API Documentation](#api-documentation)
5. [Design Decisions](#design-decisions)
6. [Screenshots](#screenshots)
7. [Advanced Features](#advanced-features)

## System Architecture

The bakery management system is a containerized application with the following components:

```
Frontend (React) → Backend (Node.js/Express) → PostgreSQL Database
                     ↓
                RabbitMQ Queue → Worker Service
```

![System Overview](images/Docker%20Desktop%20showing%20all%20running%20containers.jpeg)  
*Docker Desktop showing all running containers*

## Prerequisites

Before running the application, ensure you have installed:
- Docker (version 20.10.0 or higher)
- Docker Compose (version 1.29.0 or higher)
- Git (optional, for cloning the repository)

## Setup Instructions

1. **Clone the repository** (if applicable):
   ```bash
   git clone https://github.com/yourusername/bakery-management-system.git
   cd bakery-management-system
   ```

2. **Build and start the containers**:
   ```bash
   docker-compose up --build
   ```
   ![Docker Build Process](images/Container%20build%20process%20in%20progress.jpeg)  
   *Container build process in progress*

3. **Verify running containers**:
   ```bash
   docker ps
   ```
   ![Running Containers](images/Output%showing%all%active%containers.jpeg)  
   *Output showing all active containers*

4. **Access the application**:
   - Frontend: http://localhost:3000
   - Backend API: http://localhost:5000
   - RabbitMQ Management: http://localhost:15672 (guest/guest)

## API Documentation

### Base URL: `http://localhost:5000/api`

### Endpoints:

1. **GET /products**
   - Lists all bakery products
   - Response:
     ```json
     [
       {
         "id": 1,
         "name": "Croissant",
         "price": 2.50,
         "description": "Buttery flaky pastry"
       }
     ]
     ```

2. **POST /orders**
   - Places a new order
   - Request Body:
     ```json
     {
       "productId": 1,
       "quantity": 2,
       "customerName": "John Doe"
     }
     ```

3. **GET /orders/:orderId**
   - Checks order status

## Design Decisions

1. **Containerization Approach**:
   - Each service has its own Dockerfile for clear separation
   - Used multi-stage builds for production optimization

2. **Message Queue**:
   - Implemented RabbitMQ for asynchronous order processing
   ![RabbitMQ Logs](images/RabbitMQ%20service%20initialization%20logs.jpeg)  
   *RabbitMQ service initialization logs*

3. **Backend Setup**:
   ![Backend Setup](images/Initializing%20Node.js%20backend%20with%20Express%20and%20PostgreSQL.jpeg)  
   *Initializing Node.js backend with Express and PostgreSQL*

## Screenshots

### Frontend Interface
![Frontend View](images/Sweet%20Dreams%20Bakery%20homepage%20showing%20product%20offerings.jpeg)  
*Sweet Dreams Bakery homepage showing product offerings*

### Docker Desktop Overview
![Docker Desktop](images/Docker%20Desktop%20showing%20all%20running%20containers.jpeg)  
*Container status in Docker Desktop*

## Advanced Features

1. **RabbitMQ Integration**:
   - Configured with management plugin
   - Dedicated worker service for order processing

2. **Container Health Monitoring**:
   - Implemented health checks for all services
   - Resource limits for production stability

---