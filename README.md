# Distributed Stock Ticker Notification System (Pub/Sub in Java)

Real-time **stock/news ticker notification system** built using a **custom Publish/Subscribe architecture** in **Java** with **TCP sockets** — no Kafka/RabbitMQ.

---

## ✨ Key Features

* **Topic-based subscriptions** (e.g., Economic Reports, Sector Performance, Inflation)
* **Master node + Secondary node** coordination for message routing
* **Multiple subscribers** receive real-time updates based on subscribed topics
* **Lightweight TCP socket messaging** with simple protocol handling
* Optional **Docker + docker-compose** setup for quick runs

---

## 🧠 Architecture Overview

**Master Node** (port `5040`)

* Accepts registration from nodes/subscribers
* Tracks subscribers + topics
* Routes messages to the correct recipients

**Secondary Node** (port `5041`)

* Connects to Master for coordination
* Accepts subscriber connections
* Forwards/relays topic updates

**Subscribers**

* Register and subscribe to topics
* Receive real-time notifications when updates are published

---

## 📁 Project Structure

* `master_node/` → Master server (`server1.java`)
* `secondary_node/` → Secondary server (`server2.java`)
* `subscriber_1/`, `subscriber_2/`, `subscriber_3/` → Subscriber clients
* `Front end/` → Simple UI assets (optional)
* `docker-compose.yml` → Multi-container orchestration
* `Dockerfile` → Base container setup

---

## 🚀 How to Run (Local)

### 1) Start Master Node

```bash
cd master_node
javac server1.java
java server1
```

### 2) Start Secondary Node

```bash
cd ../secondary_node
javac server2.java
java server2 secondary_node
```

### 3) Start Subscribers (in separate terminals)

```bash
cd ../subscriber_1
javac subscriber1.java
java subscriber1 subscriber_1
```

Repeat similarly for `subscriber_2`, `subscriber_3`.

---

## 🐳 How to Run (Docker)

```bash
docker-compose up --build
```

---

## ✅ Example Flow

1. Subscriber connects and registers (ex: `subscriber_1`)
2. Subscriber subscribes to one or more topics
3. Nodes publish stock/news updates
4. Subscriber receives real-time messages for subscribed topics

---

## 🛠 Tech Stack

* **Java**
* **TCP Socket Programming**
* **Docker / Docker Compose**

---

## 📌 Notes / Improvements (Future Work)

* Add heartbeats + retry for fault tolerance
* Message serialization (JSON/protobuf)
* Topic persistence + replay
* Monitoring metrics (latency, throughput)

---

If you use this for coursework, keep the README + structure clear and include a short demo video/GIF for maximum impact.
