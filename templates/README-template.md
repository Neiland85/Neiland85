# 🧩 <Service Name> – Microservice Overview

> Short description of what this service does and how it fits into the system.

## 🧠 Purpose

Explain what business problem this service solves. One paragraph max.

## 🚀 Stack

- Language: Node.js + TypeScript
- Framework: Express / Fastify
- Database: PostgreSQL
- Communication: REST / Kafka / gRPC
- Auth: JWT / OAuth2

## ⚙️ Architecture

- Hexagonal (Ports & Adapters)
- Domain-Driven Design (DDD)
- Clean folder structure with DI

## 📂 Folder Structure

```bash
src/
├── domain/          # Entities, value objects, domain services
├── application/     # Use cases, ports, orchestrators
├── infrastructure/  # DB, HTTP, Kafka adapters
├── interfaces/      # Controllers (REST, CLI, GraphQL)
└── main.ts          # Entry point
```

🧪 Testing
Unit tests: Jest

Integration: Supertest

E2E: Playwright / Postman Collections

🧬 Observability
Metrics: Prometheus

Logs: Loki + Grafana

Traces: Elastic APM

🔐 Security
Auth validation

Rate limiting

Input schema (Zod / Joi)

📘 Documentation
OpenAPI 3.1 (Swagger)

ADRs in /docs/adr/

---

### ✅ `ADR-template.md`

```md
# Architecture Decision Record: [YYYY-MM-DD] [TITLE]

## ✅ Status

Proposed | Accepted | Deprecated | Superseded by [ADR-XXX]

## 🎯 Context

What is the technical or business context that led to this decision?

## 💡 Decision

What choice was made? Include relevant trade-offs and rejected alternatives if necessary.

## 📈 Consequences

- Immediate consequences of this decision (technical, team, ops)
- Long-term effects: coupling, flexibility, cost
- Monitoring, reversibility plan, if any

## 🔁 Alternatives Considered

(Optional) List alternatives that were evaluated but not chosen, and why.

## 📚 Related Documents

- Link to related ADRs, issues, RFCs, discussions
```
