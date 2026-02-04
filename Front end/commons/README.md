# Stock Ticker Notification System (Pub/Sub from Scratch)

Implemented a stock/news notification system using a custom Publish/Subscribe architecture.
Includes a master node, a secondary node, and multiple subscribers. Subscribers register and receive topic-based updates.

## Problem
Build a lightweight messaging system that supports topic subscriptions and real-time notifications without using a broker (Kafka/RabbitMQ).

## Architecture
- **Master Node**: `server1.java` (listens on `5040`)
- **Secondary Node**: `server2.java` (listens on `5041`, communicates with master)
- **Subscribers**: `subscriber1.java`, `subscriber2.java`, `subscriber3.java` (connect to `5041`)

Topics (example): Economic Reports, Sector Performance, Inflation

## Tech Stack
- Java
- Socket programming (TCP)
- Multithreading / concurrent collections

## Setup / Run
Open 4 terminals and run in this order.

### 1) Start Master Node (port 5040)
```bash
cd Downloads/stocmarket/master_node
javac server1.java
java server1
