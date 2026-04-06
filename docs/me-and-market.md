# My role and skills

## My role

**Back-end Engineer**

I chose this role because:

1. It is the core role behind building and maintaining server-side services like those in Telegram's architecture (Message Handling Service, Auth Service, etc.), which I found most interesting during the architecture analysis.
2. Back-end engineering offers a wide range of technologies and problem domains — from databases and APIs to distributed systems and microservices — which keeps the work intellectually stimulating.
3. There is strong market demand for back-end developers in Russia and globally, with competitive salaries and opportunities for growth into senior and architect roles.

## Skills I already have

1. **Git / Version Control** (roadmap.sh: Version Control Systems) — **Intermediate**. Comfortable with branching, merging, rebasing, pull requests, and resolving conflicts. Used in academic and personal projects.
2. **HTTP / REST APIs** (roadmap.sh: RESTful APIs) — **Beginner–Intermediate**. Understand the basics of HTTP methods, status codes, request/response cycles, and REST API design principles from coursework and self-study.
3. **Linux / CLI** (roadmap.sh: Linux Basics) — **Beginner**. Can navigate the filesystem, run basic shell commands, manage processes, and use tools like `grep`, `ssh`, and `systemctl`.
4. **Databases (SQL)** (roadmap.sh: SQL) — **Beginner**. Familiar with basic SQL queries (SELECT, JOIN, GROUP BY), understand relational database concepts, and have worked with PostgreSQL/MySQL in small projects.
5. **Docker** (roadmap.sh: Containerization) — **Beginner**. Can write simple Dockerfiles, run containers, and use `docker-compose` for local development environments.

## Skills I clearly lack

1. **System Design / Distributed Systems** — Critical for a back-end engineer working on large-scale systems like Telegram. Involves designing scalable, fault-tolerant architectures with load balancing, caching, and message queues. Without this skill, it's impossible to architect production-grade services.

2. **Message Brokers (Kafka, RabbitMQ)** — Essential for asynchronous communication between microservices. Telegram's architecture uses an event bus (Kafka) for propagating updates. Understanding pub/sub patterns and event-driven architecture is key for modern back-end development.

3. **CI/CD Pipelines** — Automating build, test, and deployment processes is a standard expectation for back-end engineers. Without CI/CD knowledge, a developer cannot efficiently deliver code to production or ensure code quality at scale.

4. **Cloud Platforms (AWS, GCP, Yandex Cloud)** — Most companies deploy back-end services to cloud infrastructure. Understanding cloud services (compute, storage, networking, managed databases) is increasingly required in job postings and is essential for real-world deployment.

5. **Testing (Unit, Integration, E2E)** — Writing automated tests is a fundamental responsibility of a back-end engineer. Without strong testing skills, code quality suffers and production bugs become more frequent. This includes knowledge of testing frameworks, mocking, and test-driven development (TDD).

The most challenging skills to acquire would likely be **System Design / Distributed Systems** and **Message Brokers**, as they require both theoretical knowledge and hands-on experience with production-scale systems that are hard to replicate in a home environment.

## Market snapshot

Below are 6 job postings for back-end developer roles:

### Posting 1: Middle Python Developer (Backend)
- **Link:** https://hh.ru/vacancy/123456789 *(example)*
- **Key skills:**
  - Python (FastAPI / Django)
  - PostgreSQL, Redis
  - Docker, Kubernetes
  - REST API, gRPC
  - Git, CI/CD

### Posting 2: Backend Developer (Go)
- **Link:** https://hh.ru/vacancy/987654321 *(example)*
- **Key skills:**
  - Go (Golang)
  - Microservices architecture
  - Kafka / RabbitMQ
  - PostgreSQL, MongoDB
  - Docker, Kubernetes

### Posting 3: Junior/Middle Backend Developer
- **Link:** https://hh.ru/vacancy/111222333 *(example)*
- **Key skills:**
  - Python or Java
  - SQL (PostgreSQL / MySQL)
  - REST API design
  - Git, Linux
  - Basic understanding of Docker

### Posting 4: Senior Backend Engineer
- **Link:** https://hh.ru/vacancy/444555666 *(example)*
- **Key skills:**
  - Go / Python / Java
  - System design and architecture
  - Kafka, Redis, Elasticsearch
  - Kubernetes, Helm, CI/CD
  - Cloud platforms (Yandex Cloud / AWS)

### Posting 5: Backend Developer (Yandex)
- **Link:** https://hh.ru/vacancy/777888999 *(example)*
- **Key skills:**
  - C++ / Python / Go
  - Distributed systems
  - High-load system design
  - Linux, performance optimization
  - Testing (unit, integration, load)

### Posting 6: Backend Developer (Fintech Startup)
- **Link:** https://hh.ru/vacancy/101112131 *(example)*
- **Key skills:**
  - Node.js (TypeScript)
  - PostgreSQL, Redis
  - Docker, docker-compose
  - REST API, WebSockets
  - Agile / Scrum methodology

## Skills that appear in several postings

1. **Docker / Containerization** — mentioned in **5 out of 6** postings. Nearly universal requirement for packaging and deploying services.
2. **PostgreSQL / SQL databases** — mentioned in **5 out of 6** postings. The go-to relational database for back-end services.
3. **REST API** — mentioned in **4 out of 6** postings. Standard for designing service interfaces.
4. **Git** — mentioned in **3 out of 6** postings. Fundamental version control tool.
5. **Kafka / Message Brokers** — mentioned in **3 out of 6** postings. Critical for event-driven and microservice architectures.
6. **Redis** — mentioned in **3 out of 6** postings. Used for caching, session management, and pub/sub.
7. **CI/CD** — mentioned in **2 out of 6** postings. Automated pipelines for build, test, and deploy.
8. **Kubernetes** — mentioned in **2 out of 6** postings. Container orchestration for production deployments.

## Skills specific to a single posting

1. **Elasticsearch** — required only in Posting 4 (Senior Backend Engineer). Likely a niche requirement for search-heavy or log-aggregation use cases.
2. **Helm** — required only in Posting 4. Specific to Kubernetes package management; not yet a mainstream requirement for mid-level roles.
3. **WebSockets** — required only in Posting 6 (Fintech Startup). Relevant for real-time communication features but not universally needed.
4. **Agile / Scrum** — mentioned only in Posting 6. More of a process/methodology skill than a technical one; common in startups but not always listed explicitly.
5. **Performance optimization / High-load design** — required only in Posting 5 (Yandex). This is a senior-level expectation specific to companies dealing with massive scale.

## My skills and market demands

Looking at the gap between my current skills and what the market demands, the most obvious gap is in **message brokers (Kafka)** and **container orchestration (Kubernetes)** — these appear in multiple postings but I have no hands-on experience with them. My SQL and Docker knowledge is at a beginner level, which might be enough for junior roles but not for middle positions that expect deeper understanding. I also lack experience with **CI/CD pipelines**, which is becoming a baseline expectation even for junior developers. On the positive side, my Git skills are solid, and my understanding of REST APIs and Linux basics aligns with entry-level requirements. The biggest takeaway is that the market expects back-end developers to be comfortable with the full deployment lifecycle — from writing code to containerizing it, setting up CI/CD, and deploying to a cluster — whereas my current experience is mostly limited to writing code and running it locally.

## Skills that I can improve

1. **Message Brokers (Kafka)** — I want to learn Kafka fundamentals: topics, partitions, consumer groups, and how to produce/consume messages in Python or Go. This is a priority because it appears in multiple job postings and is central to the architecture of products like Telegram. I plan to set up a local Kafka instance using Docker, follow the official quickstart guide, and build a small project with a producer-consumer pattern.

2. **CI/CD Pipelines (GitHub Actions)** — I want to learn how to create CI/CD pipelines that automatically run tests, lint code, build Docker images, and deploy. This is a priority because it's a practical skill I can apply immediately in this course and in future projects. I plan to start by adding a GitHub Actions workflow to one of my existing repositories, then gradually add more stages (testing, Docker build, deployment to a free cloud tier like Render or Railway).
