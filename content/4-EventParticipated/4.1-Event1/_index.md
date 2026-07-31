---
title: "Event 1"
date: 2026-06-06
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# MULTIPLAYER GAME NETWORKING WORKSHOP SUMMARY REPORT

## Event Objectives
* **Share network architecture protocols** in multiplayer game development.
* **Introduce workflows** for building Serverless WebSocket systems on AWS.
* **Guide Client-side network programming** using the Godot Game Engine.
* **Introduce application packaging solutions** using Containerization technology (Docker).

---

## Key Highlights

### 1. Analysis of Multiplayer Game Networking Protocols
* **HTTP Polling:**
  * Mechanism: Client continuously sends requests to check for Server updates.
  * Drawbacks: Long response times (High Latency), causing system overhead.
  * Use Cases: Suitable only for simple features like Login or Leaderboards.
* **UDP (User Datagram Protocol):**
  * Mechanism: Fast packet transmission protocol that accepts packet loss in exchange for ultra-low latency.
  * Use Cases: Optimized for high-speed games (FPS, MOBA, Racing).
  * In Godot: Enhanced as the ENet library.
* **WebSocket:**
  * Mechanism: Persistent two-way connection protocol delivering better real-time performance than HTTP Polling and more reliable data control.
  * Use Cases: Selected as the optimal solution for the Rock-Paper-Scissors demo game.

### 2. Setting Up Serverless WebSocket on AWS
The network logic processing system is built using 4 core services:
* **API Gateway:** Routes connections by configuring routes: `$connect`, `$disconnect`, and `$default` (using JSON format based on `request.body.action`).
* **Lambda Function:** Handles business logic for connection/disconnection events and message transmission.
* **DynamoDB Table:** Stores match data and player states across 5 main columns: `Connection ID`, `Status` (waiting/playing), `Opponent ID`, `Choice` (rock/paper/scissors), and `Create At` (timestamp).
* **CloudWatch:** Automatically records system logs to monitor data flows and facilitate debugging.

### 3. Client-Side Programming in Godot Engine
Handles 4 primary tasks to maintain game connectivity:
* **Initialization:** Establishes connection to the API Gateway URL via the `WebSocketPeer` object.
* **Message Polling:** Continuously checks data returned from the server (similar to checking a mailbox) to prevent system overload.
* **State Management:** Tracks 4 WebSocket states—`Connecting`, `Open`, `Closing`, and `Closed`—to issue appropriate Matchmaking requests.
* **Data Processing:** Parses incoming JSON packets from the Server to handle game outcomes.

### 4. Applying Containerization Technology (Docker)
* **Resolving Environment Conflicts:** Permanently eliminates configuration mismatch issues ("works on my machine but fails on yours").
* **Virtual Machine vs Container Comparison:** Virtual Machines (VMs) are heavy and resource-intensive because they boot separate Operating Systems (OS); Containers are significantly lighter as they share the host OS via a Container Engine.
* **Docker Cache/Layer Mechanism:** Builds images using a layered approach that stores history from previous steps, rebuilding only from modified layers $\rightarrow$ Optimizes packaging time.

---

## Key Takeaways

### Design Mindset
* **Real-World Error Scenarios:** Understood how to handle sudden disconnection exceptions (unavoidable network drops) to prevent "Ghost Connections" in DynamoDB that cause matchmaking errors for new players.
* **Performance Optimization:** Realized that executing `Scan Table` operations on DynamoDB for matchmaking creates bottlenecks under high user concurrency, highlighting the need for dedicated centralized management solutions.
* **System Resource Management:** Understood Lambda's Stateless nature to design appropriate data storage structures when implementing reconnection features.

### Technical Architecture
* **Deep Network Programming:** Mastered JSON packet transmission structures and writing synchronization source code between the Game Client and Cloud Server.
* **Practical Applications of Docker:** Learned to author complete `Dockerfile` setups (commands like `FROM`, `RUN`, `COPY`, `EXPOSE`...) and understood the underlying mechanics of `docker run -it` to create fully isolated sandbox environments for security testing and server-protecting malware isolation.

### Future Directions
* **AWS GameLift Adoption:** Adopted mindsets for hosting game servers on dedicated EC2 clusters and integrating advanced automated matchmaking algorithms for large-scale projects.

---

## Practical Applications to Work

1. **Applying WebSocket Mechanics:** Upgrade real-time network communication modules for personal projects or course assignments instead of using traditional HTTP.
2. **Building Serverless Clusters on AWS:** Experiment with combining API Gateway and Lambda for applications with asynchronous data pipelines.
3. **Standardizing Application Packaging Workflows:** Utilize Docker for product packaging, creating uniform execution environments across all team members to optimize development workflows.
4. **Applying Sandbox Containers:** Leverage Docker's application isolation mechanics to support safer software testing and security check workflows.

---

## Lessons Learned & Personal Reflections

Attending this workshop was an invaluable experience that provided deep technical insights into computer networking applied to the gaming industry and modern DevOps mindsets.

### 1. Learning from Real-World Insights
* The speaker shared hard-earned lessons regarding system failures, design patterns, and network infrastructure management optimized for both performance and operational costs.
* Through in-depth analyses of UDP, WebSocket, and DynamoDB storage mechanisms, I gained a clearer understanding of handling asynchronous data within distributed systems.

### 2. Hands-On Technical Experience
* Observed live connection demos between the Game Client (Godot) and Server (AWS), visually tracing data flows from initial Client requests to DynamoDB status updates.
* Mastered debugging and system monitoring techniques using CloudWatch and deep interactive commands inside Docker containers via terminal interfaces.

### 3. Applying Modern Technology Mindsets
* Understood the critical importance of virtualization and application packaging using Docker to free developers from environment configuration headaches.
* Learned to apply Docker Containers as flexible, secure "Sandbox" environments for testing and system security checks.

### 4. Conclusion & Core Lessons
* **Every system design involves Trade-offs** between performance, reliability, and cost. No single protocol or technology is universally perfect—only the most suitable option for a specific business domain exists.
* **Cloud Cost Optimization Awareness:** When working with Cloud environments, always maintain discipline to audit and shut down unused servers/services (such as EC2 clusters or databases) to prevent unexpected charges during development (The Cloud Invoice Lesson).

> **Summary:** The event provided not only deep technical networking knowledge but also transformed my mindset regarding system architecture design, Cloud infrastructure optimization, and software packaging standardization for real-world engineering projects.

![Event1](/images/4-EventParticipated/event_6-6-26/1.jpg)
![Event1](/images/4-EventParticipated/event_6-6-26/2.jpg)
![Event1](/images/4-EventParticipated/event_6-6-26/3.jpg)
![Event1](/images/4-EventParticipated/event_6-6-26/4.jpg)