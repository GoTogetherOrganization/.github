# Food Delivery Application

## Overview
Internship in ISA (Information Systems Associates (Pvt) Ltd, previously known as Accelero),
for familiarizing with their tech stack before industry work, with a team of 3 members.
This is a **Microservices-based event-driven Food Delivery Application** that allows customers to order food from restaurants, riders to deliver orders, and restaurants to manage their menus and orders. The project follows a **three-tier architecture** and utilizes **modern technologies** to ensure scalability, security, and performance.

## Tech Stack
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
- **Cloudflare R2 (S3 Compatible Storage)** for storing images (restaurant logos, food images, etc.).
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
- Path finding Using A* Algorithm.
- Concurrency Handling in Request Acceptance.

---

## High-Level Architecture

![High-Level Architecture](https://github.com/FoodDeliveryApp-ISA/FoodDeliveryApp-ISA/blob/main/diagrams/High%20level%20architecture.png)
Microservices, event-driven, 3-tier architecture.
*(Refer to the provided image for detailed visualization)*

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

## Future Enhancements
- **AI-based food recommendations** using machine learning.
- **Multi-restaurant order support**.
- **Push notifications for order updates**.
- **Payment gateway integration** for secure transactions.

---

## Contributors
- **Restaurant Side:** Harshana ([GitHub: UchihaIthachi](https://github.com/UchihaIthachi))
- **Customer Side:** Kavindu ([GitHub: senaMora](https://github.com/senaMora))
- **Rider Side:** Sahan ([GitHub: sahan-vishwajith](https://github.com/sahan-vishwajith))

