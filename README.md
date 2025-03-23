## 🛒 Order Flow

![Order Flow Diagram](https://github.com/FoodDeliveryApp-ISA/FoodDeliveryApp-ISA/blob/main/diagrams/order%20flow.png)

This section describes how a customer's food order flows through the system, covering **gRPC communication**, **Kafka topics**, **status transitions**, and **real-time updates**.

---

### **1. Search and Select Food**

- The **Customer** searches for restaurants and food items.
- A **gRPC call** is made from the **Customer Service** to the **Restaurant Service** to retrieve restaurant and menu information.
- The customer browses the results and selects food items to place an order.

---

### **2. Place Order**

- After finalizing the selection, the customer places the order.
- The system:
  - **Publishes order details** to the Kafka topic: `order-restaurant-request`.
  - **Persists the order** in the **Customer Service database**.

---

### **3. Restaurant Receives Order**

- The **Restaurant Service** listens to the `order-restaurant-request` topic.
- It:
  - Extracts the order data.
  - Saves it in the **Restaurant database**.
  - Sends a **notification** to the restaurant UI/agent.

---

### **4. Restaurant Responds to Order**

- The restaurant can either **accept** or **reject** the incoming order.
- Upon action:
  - The system **publishes an order status update** to the Kafka topic: `order-status` with either `"PLACED"` or `"REJECTED"`.
  - Both **Customer** and **Restaurant Services** subscribe to this topic to:
    - Update their databases.
    - Trigger UI notifications for status changes.

---

### **5. Order Preparation and Rider Request**

- If the order is accepted:

  - The **Restaurant Service** updates the order status to `"PREPARED"` and publishes it to the `order-status` topic.
  - Then, it publishes a rider request to the `rider-request` Kafka topic.

- The **Rider Service** listens to `rider-request` and initiates **rider matching**.

---

### **6. Rider Notification**

- Riders receive **delivery request notifications** in real-time.
- A rider can accept the request within a configured **timeout window**.

---

### **7. Rider Selected**

- When a rider accepts the delivery:
  - The order status is updated to `"ONTHEWAY"` and published to `order-status`.
  - The **rider's live location** is continuously published to the `rider-location-updates` topic.
  - The **Customer Service** consumes this topic to allow customers to track their delivery in real-time.

---

### **8. Order Delivered**

- After successful delivery:
  - The **Rider Service** updates the order status to `"DELIVERED"`.
  - This is published to the `order-status` topic and synchronized across all involved services and UIs.

---
