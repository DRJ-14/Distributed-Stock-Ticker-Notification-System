# Distributed Stock Ticker Notification System (Pub/Sub in Java)

![Java](https://img.shields.io/badge/Java-17%2B-blue)
![TCP Sockets](https://img.shields.io/badge/TCP-Sockets-success)
![Distributed Systems](https://img.shields.io/badge/Distributed-Systems-orange)
![Docker](https://img.shields.io/badge/Docker-optional-informational)

Real-time **stock/news ticker notifications** built with a **custom Publish/Subscribe architecture** in **Java** using **TCP sockets** — **no Kafka/RabbitMQ**.

---

## 🚀 Quickstart (30 seconds)

1. Start **Master Node**
2. Start **Secondary Node**
3. Start **Subscribers**
4. Watch **live topic notifications** stream in real-time 🚀

---

## ✨ Key Features

* **Topic-based subscriptions** (e.g., Economic Reports, Sector Performance, Inflation)
* **Master–Secondary coordination** for routing + registration
* **Multiple subscribers** receive real-time updates based on topics
* **Lightweight TCP protocol** (simple message/command handling)
* Optional **Docker + docker-compose** setup for quick runs

---

## 🧠 Architecture Overview

### Diagram (high-level)

```text
Publisher/News Generator
        |
        v
  Secondary Node (5041)  <---->  Master Node (5040)
        |
   -----------------
   |       |       |
Sub1     Sub2     Sub3
(topic filters + real-time updates)
(pic filters + real-time updates)
```

### Master Node (port `5040`)

* Accepts registration from nodes/subscribers
* Maintains **subscriber ↔ topic** mappings
* Routes updates to the correct recipients

### Secondary Node (port `5041`)

* Connects to Master for coordination
* Accepts subscriber connections
* Forwards/relays topic updates to subscribers

### Subscribers

* Register and subscribe to topics
* Receive real-time notifications when updates are published

---

## 📸 Demo / Output

> Add a screenshot showing **Master + Secondary + Subscriber receiving updates**.

Example (after uploading a screenshot into the repo):

```md
![Demo Output](assets/demo.png)
```

---

## 📁 Project Structure

* `master_node/` → Master server (`server1.java`)
* `secondary_node/` → Secondary server (`server2.java`)
* `subscriber_1/`, `subscriber_2/`, `subscriber_3/` → Subscriber clients
* `Front end/` → Optional simple UI assets
* `docker-compose.yml` → Multi-container orchestration
* `Dockerfile` → Base container setup

---

## 🏃 How to Run (Local)

> Open **4 terminals** and run in this order.

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

### 3) Start Subscribers (separate terminals)

```bash
cd ../subscriber_1
javac subscriber1.java
java subscriber1 subscriber_1
```

Repeat similarly for `subscriber_2` and `subscriber_3`.

---

## 🐳 How to Run (Docker)

```bash
docker-compose up --build
```

---

## ✅ Example Flow

1. Subscriber connects and registers (e.g., `subscriber_1`)
2. Subscriber subscribes to one or more topics
3. Nodes publish stock/news updates
4. Subscriber receives real-time messages for subscribed topics

---

## 🛠 Tech Stack

* **Java (17+)**
* **TCP Socket Programming**
* **Distributed Systems (Pub/Sub from scratch)**
* **Docker / Docker Compose** (optional)

---

## 🧹 Repo Cleanup (important)

Make sure **no `.class` files** are tracked in GitHub:

```bash
git ls-files | grep "\.class$"
```

If it prints anything, remove them from tracking and push cleanly.

---

## 📌 Future Improvements

* Heartbeats + retry logic for fault tolerance
* Message serialization (JSON / Protobuf)
* Topic persistence + replay
* Monitoring metrics (latency, throughput)
