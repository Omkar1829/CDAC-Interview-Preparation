# Senior & Mid-Level (4-5+ YOE) Onboarding Questionnaire

This onboarding questionnaire is designed to capture all essential signals for experienced engineers (Mid to Senior SDE-2/SDE-3 level). It runs only once and permanently configures your evaluation bar.

---

## 📋 The 6 Onboarding Questions

1. **Exact Total Experience & Current Domain:**
   - How many years/months of professional experience do you have?
   - What kind of systems do you build currently (e.g., distributed microservices, fintech payment gateways, high-throughput backend, monolithic legacy, SaaS product)?

2. **Primary Tech Stack & Ecosystem Depth:**
   - What is your primary language and ecosystem? (e.g., Java 17/21 + Spring Boot 3, Go, C# .NET, Python FastAPI)
   - What databases and storage engines do you work with in production? (e.g., PostgreSQL, MySQL, Redis, MongoDB, DynamoDB, Elasticsearch)
   - Messaging / Streaming platforms? (e.g., Apache Kafka, RabbitMQ, SQS)

3. **Target Roles, Companies & Package Expectations:**
   - What roles are you interviewing for? (e.g., SDE-2 Backend, Lead Engineer, Senior Software Engineer)
   - What tier of companies? (e.g., Top Product Companies / Tier-1 MNCs / High-growth Startups / Fintech)
   - Target CTC / compensation range (e.g., 18–35+ LPA) so the evaluation bar matches that bracket.

4. **DSA & Problem Solving Target:**
   - What level of algorithmic questions do you want to practice?
     - LeetCode Mediums only (Arrays, HashMaps, Sliding Window, Trees, Graphs, BFS/DFS, Heaps)
     - LeetCode Medium to Hard (DP, Tries, Disjoint Set, Segment Trees)
   - Which coding language do you prefer to write solutions in?

5. **System Design & Architecture Focus:**
   - Do you want to include **Low-Level Design (LLD)**? (SOLID principles, Design Patterns, Schema Design, Concurrency & Thread-Safety, Machine Coding round).
   - Do you want to include **High-Level Design (HLD)**? (Microservices, Caching strategies, Database Sharding/Replication, Rate Limiters, Message Queue decoupling, CAP theorem, Fault Tolerance).

6. **Self-Assessed Weaknesses / Immediate Focus:**
   - Are there specific topics you feel rusty on? (e.g., Concurrency/Multithreading, Distributed Transactions / 2PC / Sagas, SQL Query Optimization & B-Tree Indexing, or Graph algorithms).

---

## 💾 Saved Format in `AGENTS_MEMORY/memory.json`

```json
{
  "user_profile": {
    "experience_years": 4.5,
    "current_level": "Senior Backend Engineer (4-5 YOE)",
    "target_roles": ["SDE-2", "Senior Software Engineer"],
    "target_ctc_tier": "20-35 LPA Tier-1 / Product MNCs",
    "primary_stack": {
      "language": "Java 17/21",
      "frameworks": ["Spring Boot 3", "Spring Cloud", "Hibernate/JPA"],
      "databases": ["PostgreSQL", "Redis"],
      "messaging": ["Kafka"]
    },
    "dsa_level": "LeetCode Medium with focus on Graphs, Trees, Heaps & DP",
    "system_design_focus": ["HLD (Distributed Systems)", "LLD (Design Patterns & Concurrency)"],
    "priority_weak_areas": ["Multithreading & Virtual Threads", "Distributed Transactions (Saga)", "Kafka Partitioning & Consumer Groups"],
    "onboarded_at": "2026-10-25"
  },
  "weak_topics": [],
  "strong_topics": [],
  "practice_history": []
}
```
