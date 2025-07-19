# 🧰 Templates for Projects

This folder contains boilerplates and architecture templates used across my professional repositories and client projects.

## 📄 Files

| File                | Purpose                                                |
|---------------------|--------------------------------------------------------|
| `README-template.md` | Standard service-level readme (full structure)         |
| `ADR-template.md`    | Architecture Decision Record template (Michael Nygard-style) |
| `mermaid/*.mmd`      | Mermaid diagrams to embed in docs or generate images  |

> These templates reflect my architectural style: traceable, modular, and readable.

```mermaid
  A[📦 Microservice Entry]
  A --> B[Interfaces Layer (REST, CLI)]
  B --> C[Application Layer (Use Cases)]
  C --> D[Domain Layer (Entities, VO, Services)]
  C --> E[Ports (DB, Queue, External APIs)]
  E --> F[Adapters: PostgreSQL, Kafka, API Clients]
```
```mermaid
  P[💬 Proposed]
  A[✅ Accepted]
  D[🗑 Deprecated]
  S[🔁 Superseded]

  P --> A
  A --> D
  A --> S
  S --> A
```
