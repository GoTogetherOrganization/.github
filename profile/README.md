# Food Delivery Application

## Table of Contents

- [Overview](#overview)
- [Tech Stack](#tech-stack)
- [Features](#features)
  - [Customer Features](#customer-features)
  - [Restaurant Features](#restaurant-features)
  - [Rider Features](#rider-features)
- [High-Level Architecture](#high-level-architecture)
- [Database Design](#database-design)
- [Deployment](#deployment)
- [Contributors](#contributors)

## Overview

This project was completed during an internship at ISA (Information Systems Associates (Pvt) Ltd, previously known as Accelero), as a preparatory exercise before starting our industry project, with the aim of familiarizing ourselves with their tech stack. It was developed by a team of 3 members.

This is a **Microservices-based event-driven Food Delivery Application** that allows customers to order food from restaurants, riders to deliver orders, and restaurants to manage their menus and orders. The project follows a **three-tier architecture** and utilizes **modern technologies** to ensure scalability, security, and performance.

## Tech Stack

<div align="left" style="display: flex; flex-wrap: wrap; gap: 10px;">
  <a href="https://reactjs.org" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/react/react-original-wordmark.svg" alt="React" width="40" height="40"/>
  </a>
  <a href="https://ant.design" target="_blank" rel="noreferrer">
    <img src="https://avatars.githubusercontent.com/u/12101536?s=200&v=4" alt="Ant Design" width="40" height="40"/>
  </a>
  <a href="https://www.postman.com/" target="_blank" rel="noreferrer">
    <img src="https://www.vectorlogo.zone/logos/getpostman/getpostman-icon.svg" alt="Postman" width="40" height="40"/>
  </a>
  <a href="https://www.java.com/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/java/java-original.svg" alt="Java" width="40" height="40"/>
  </a>
  <a href="https://spring.io/projects/spring-boot" target="_blank" rel="noreferrer">
    <img src="https://www.vectorlogo.zone/logos/springio/springio-icon.svg" alt="Spring Boot" width="40" height="40"/>
  </a>
  <a href="https://jwt.io/" target="_blank" rel="noreferrer">
    <img src="https://jwt.io/img/pic_logo.svg" alt="JWT" width="40" height="40"/>
  </a>
  <a href="https://grpc.io/" target="_blank" rel="noreferrer">
    <img src="https://grpc.io/img/logos/grpc-icon-color.png" alt="gRPC" width="40" height="40"/>
  </a>
  <a href="https://developers.google.com/protocol-buffers" target="_blank" rel="noreferrer">
    <img src="https://protobuf.dev/img/protobuf-logo.svg" alt="Protobuf" width="40" height="40"/>
  </a>
  <a href="https://kafka.apache.org/" target="_blank" rel="noreferrer">
    <img src="https://upload.wikimedia.org/wikipedia/commons/0/0a/Apache_kafka-icon.svg" alt="Kafka" width="40" height="40"/>
  </a>
  <a href="https://redis.io/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/redis/redis-original.svg" alt="Redis" width="40" height="40"/>
  </a>
  <a href="https://www.postgresql.org/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/postgresql/postgresql-original.svg" alt="PostgreSQL" width="40" height="40"/>
  </a>
  <a href="https://www.cloudflare.com/r2/" target="_blank" rel="noreferrer">
    <img src="https://avatars.githubusercontent.com/u/314135?s=200&v=4" alt="Cloudflare R2" width="40" height="40"/>
  </a>
  <a href="https://www.zookeeper.apache.org/" target="_blank" rel="noreferrer">
    <img src="https://zookeeper.apache.org/images/zookeeper_small.gif" alt="Zookeeper" width="40" height="40"/>
  </a>
  <a href="https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API" target="_blank" rel="noreferrer">
    <img src="https://upload.wikimedia.org/wikipedia/commons/d/db/Websocket_icon.png" alt="WebSocket" width="40" height="40"/>
  </a>
  <a href="https://www.docker.com/" target="_blank" rel="noreferrer">
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/docker/docker-original.svg" alt="Docker" width="40" height="40"/>
  </a>
</div>

### **Frontend**:

- **React** with **Ant Design** for UI components.
- Communication with backend via **RESTful APIs (HTTP)** and **WebSockets** for real-time notifications.
- **Postman** for API testing and documentation.

### **Backend**:

- **Java 17** with **Spring Boot**.
- **Spring Security** with **JWT** for authentication & authorization.
- **gRPC** with **Protocol Buffers (protobuf)** for synchronous inter-service communication.
- **Apache Kafka** for asynchronous messaging and event-driven architecture.
- **Redis** for caching frequently accessed data.

### **Database & Storage**:

- **PostgreSQL** (3 databases for different services).
- **Cloudflare R2 (S3-compatible storage)** for storing images (restaurant logos, food images, etc.).
- **Docker & Docker Compose** for containerized deployment.

### **Other Key Technologies**:

- **Zookeeper** for managing distributed services.
- **WebSockets** for real-time notifications (e.g., order status updates, rider location tracking).
- **OpenStreet API** for location and mapping.

---

## Features

### **Customer Features**

- Create (with email verification) and edit customer profiles.
- Customer login with credentials (JWT token).
- Search for restaurants or food items.
- Place food orders.
- View payment amount and pay the rider upon delivery.
- Track orders with rider live location.
- Order management with real-time order status.

### **Restaurant Features**

- Create (with email verification) and edit restaurant profiles.
- Restaurant login with credentials (JWT token).
- Manage menus by adding, editing, or deleting food items.
- Accept customer orders.
- Request riders for deliveries.
- Password recovery functionality.
- Real-time order notifications using WebSocket.
- Caching for restaurants, menus, and menu items with Redis.
- Forget password functionality.
- Track order state in real-time.

### **Rider Features**

- Create (with email verification) and edit rider accounts.
- Rider login with credentials (JWT token).
- Update location and availability for deliveries.
- Accept delivery requests from restaurants.
- Collect food from restaurants.
- Deliver to customers and update delivery status.
- Real-Time Live Location Updates Interactive Map View.
- Path finding Using A\* Algorithm.
- Concurrency Handling in Request Acceptance.

---

## High-Level Architecture

![High-Level Architecture](https://github.com/FoodDeliveryApp-ISA/FoodDeliveryApp-ISA/blob/main/diagrams/High%20level%20architecture.png)
Microservices, event-driven, 3-tier architecture.
_(Refer to the provided image for detailed visualization)_

### **Architecture Breakdown**

- **Frontend (React)**
- **Backend (Spring Boot, Microservices)**
- **Database Layer (PostgreSQL)**
- **Message Queue (Apache Kafka)**
- **Cache Layer (Redis)**
- **File Storage (Cloudflare S3)**
- **WebSockets for Notifications**
- **API Communication**:
  - REST API for frontend communication.
  - gRPC for backend service communication.
  - Kafka for event-driven architecture.

---

## Database Design

![ER Diagram](https://github.com/FoodDeliveryApp-ISA/FoodDeliveryApp-ISA/blob/main/diagrams/er%20diagram.png)
The application is built using **3 PostgreSQL databases**, each serving a separate microservice:

1. **Customer Service Database**: Manages user accounts, orders.
2. **Restaurant Service Database**: Manages restaurants, menus, notifications, and orders.
3. **Delivery Service Database**: Manages rider details.

Each database follows **normalized relational database design**, ensuring data consistency and integrity.

**ER Diagram and High-Level Architecture**
The repository contains visual representations of the system architecture and database design.

- **ER Diagram**: Depicts the database structure with three PostgreSQL databases.
- **High-Level Architecture**: Shows the microservices architecture and interactions.

Find these diagrams in the repository under the `diagrams` directory:
[Repository Link](https://github.com/FoodDeliveryApp-ISA/Restaurant)

---

## Deployment

The application is containerized using **Docker** and managed via **Docker Compose**.

### **Docker Components**

- **Frontend (React App)**
- **Backend (Spring Boot Microservices)**
- **PostgreSQL Databases**
- **Redis Cache**
- **Kafka & Zookeeper**
- **Cloudflare S3 for image storage**

---

## Contributors

- **Restaurant Side:** Harshana ([UchihaIthachi](https://github.com/UchihaIthachi))
- **Customer Side:** Kavindu ([senaMora](https://github.com/senaMora))
- **Rider Side:** Sahan ([sahan-vishwajith](https://github.com/sahan-vishwajith))
