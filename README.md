![State: Early Stage](https://img.shields.io/badge/Stage-early_stage-orange)<br/>
<sub><small>⚠️ Project in early stage. Features under development and subject to change.</small></sub>

# Transaction Manager

A backend service for managing financial transactions in multiple currencies. Designed to demonstrate clean architecture, asynchronous messaging with Kafka, and real-time currency conversion using external APIs (e.g., Treasury Reporting Rates).

---

## 🧰 Tech Stack

- ![Java](https://img.shields.io/badge/Java-24-007396?logo=java&logoColor=white&style=flat-square)
- ![Spring Boot](https://img.shields.io/badge/Spring_Boot-3.5.3-6DB33F?logo=spring&logoColor=white&style=flat-square)
- ![Spring Web](https://img.shields.io/badge/Spring_Web-3.5.3-6DB33F?logo=spring&logoColor=white&style=flat-square)
    - ![Spring Validation](https://img.shields.io/badge/Spring_Validation-3.5.3-6DB33F?style=flat-square)
    - ![Spring Kafka](https://img.shields.io/badge/Spring_Kafka-3.5.3-6DB33F?logo=apachekafka&logoColor=white&style=flat-square)
- ![Apache Kafka](https://img.shields.io/badge/Apache_Kafka-latest-000000?logo=apachekafka&logoColor=white&style=flat-square) (via Docker)
- ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-runtime-336791?logo=postgresql&logoColor=white&style=flat-square) (via Neon Cloud)
- ![Maven](https://img.shields.io/badge/Maven-build_tool-C71A36?logo=apachemaven&logoColor=white&style=flat-square)
- ![Lombok](https://img.shields.io/badge/Lombok-optional-ED2B33?style=flat-square)
- ![Docker](https://img.shields.io/badge/Docker-runtime-2496ED?logo=docker&logoColor=white&style=flat-square) + ![Docker Compose](https://img.shields.io/badge/Docker_Compose-runtime-2496ED?logo=docker&logoColor=white&style=flat-square)

---

## 🎯 Highlights

- **Spring Boot** REST API with modular domain structure
- **Kafka** messaging via **local Docker**
- **PostgreSQL in the cloud** using [Neon](https://neon.tech)
- Clean code, service separation, DTO validation, and integration-ready architecture

---

## 🧱 Architecture & Event Flow

```text
Client → REST API (Spring Boot)
             ↓
      PostgreSQL (Neon Cloud)
      + Integration Events Outbox
             ↓
      Event Publisher (Async Scheduler)
             ↓
      Kafka Producer → Kafka Topic (Local Docker)
             ↓
      Kafka Consumer → External Currency Conversion API
```

- PostgreSQL is **hosted remotely** on Neon to simulate a production-like cloud environment.
- Kafka is **containerized locally** using Docker for simplicity and speed — running Kafka in the cloud was considered excessive for the scope of this project.

---

## 📄 Technical Decisions

- ✅ **Kafka via Docker**: Fast and isolated; avoids unnecessary complexity from cloud Kafka (SSL, auth, VPCs)
- ✅ **PostgreSQL via Neon**: Enables persistent cloud storage without local DB overhead
- 📦 Local development only requires Docker (for Kafka); database is already online

---

## 📫 Author

Developed by **Ítalo Lemos**  
📧 [italolemos4@gmail.com]  
🔗 [linkedin.com/in/italolemosgasparo](https://www.linkedin.com/in/italolemosgasparo)
