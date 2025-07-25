# 🧱 Architectural Shift: From Monolith to Modular REST (Idealista, 2012–2014)

> A technical reflection on how we transitioned from a classic Java monolith to a more modular, decoupled architecture at Idealista — before "microservices" became trendy.

---

## 🧭 Starting Point: The Monolith

When I joined Idealista in late 2012, the core backend was a large Java-based monolith with server-side rendered views (JSP), direct DB access, and tight coupling between components.

### 🔴 Monolithic Characteristics

- Business logic, presentation, and data access **in the same layer**
- Shared mutable state across features
- Endpoints often returned HTML directly
- Session-based auth (no tokens)
- Deployment = full build, all or nothing

---

## 🔄 The Transition: Modular Thinking Emerges

During 2013–2014, we began abstracting layers and exposing true RESTful endpoints using token-based auth and JSON payloads. These services initially served frontend views, but laid the foundation for future reuse.

### ⚙️ Technical shifts:

- 🔑 Token-based authentication replaces session cookies
- 🧩 Business logic separated into internal service modules
- 📦 Partial views reused via Mustache and server-side includes
- ⚙️ Simple REST endpoints: `/search?location=barcelona&sort=score`
- 📁 Java packages reorganized by responsibility (not feature)

---

## 🧱 Diagram: From Monolith (2012) to Modular REST (2014)

Due to GitHub Markdown limitations, this diagram is best viewed using an external Mermaid-compatible tool.

👉 [🧠 View this diagram in the Mermaid Live Editor](https://mermaid.live/edit#pako:eNptUM1OwzAM_JXLnW0a7m-5FJXRGY6kmYrRtBt2JUnYjUosTP_3xFmkfRQd29Kx76lZJfGxZgZkUtzTS5Edp1jxiU_M-3AErzS3-WwR4f_HnC2LIYtXPLtv_o_Lkgk-91m6EKdjY_QVXtM1nGVHRU4sCAbIQ55cUiDjFZx1ZKqF_5aGC9CU3I)

```mermaid
flowchart LR

  subgraph Monolith_2012
    UI1[HTML + JSP]
    Logic1[Java Business Logic]
    DB1[MySQL]
    UI1 --> Logic1 --> DB1
  end

  subgraph Modular_REST_2014
    UI2[Mustache + jQuery]
    API[REST API]
    Services[Internal Modules]
    DB2[MySQL]
    UI2 --> API --> Services --> DB2
  end

  Monolith_2012 --> Modular_REST_2014
```

##### 🧠 What I Contributed
Designed dynamic filters with decoupled logic

Helped define internal service boundaries (search, scoring, real estate data)

Worked on token-based auth system with JSON payload validation

Coordinated with frontend to deliver API responses compatible with new Mustache-based views

🪜 What This Transition Taught Me
💡 That modularity is a mindset, not just a tech stack

🧰 That moving away from monoliths requires process orchestration, not only refactor

🔍 That clarity in naming, isolation, and API contracts pays off long-term

🧠 That architecture is communication: how devs talk to the system, and to each other


