# 🌴 Cape Verde Tourism App – Documentation

This repository contains the complete documentation for the **Cape Verde Tourism App**, including the Agile Backlog, Domain-Driven Design (DDD), services, and architecture.  
The app supports **multi-language functionality** (English, French, Portuguese), and users can select their preferred language in the app.

---

## 📚 Table of Contents

### 1️⃣ Agile Backlog

- [Backlog & Roadmap](./docs/backlog.md) – User Stories, Sprints, Priorities, and Story Points.

### 2️⃣ Domain-Driven Design (DDD)

- [Contexts](./docs/ddd/contexts.md) – Bounded Contexts and their responsibilities.
- [Aggregates](./docs/ddd/aggregates.md) – Aggregates, Entities, and Value Objects per context.
- [Value Objects](./docs/ddd/value_objects.md) – Immutable domain objects with validation rules.
- [Domain Events](./docs/ddd/domain_events.md) – Events triggered by domain actions.
- [Services](./docs/ddd/services.md) – Domain and Application Services orchestrating business logic.

### 3️⃣ Architecture

- [Architecture Overview](./docs/architecture.md) – DDD diagram, tech stack, deployment notes, and event-driven architecture.

---

## 🗺 Project Overview

**Purpose:** Provide premium trips to Cape Verde with authentic local experiences, secure payment, and AI-powered recommendations.

**Key Features:**

- Multi-language support (English, French, Portuguese)
- User authentication and profile management
- Trip catalog with filtering, sorting, and interactive map
- Booking & payment system with invoices and cart management
- Admin dashboard and back-office management
- Marketing, loyalty programs, and newsletters
- AI-driven recommendations, chatbot, and dynamic pricing

**Technology Stack:**

- Backend: Nest JS, PostgreSQL, Redis, Stripe API
- Frontend Web: React.js + Material UI
- Mobile: React Native (iOS + Android)
- AI: Python (scikit-learn, TensorFlow, OpenAI API)
- Infrastructure: Docker + CI/CD, AWS / DigitalOcean

---

## 📦 Repository Structure

```text
/docs
  ├── backlog.md
  ├── architecture.md
  └── ddd/
       ├── contexts.md
       ├── aggregates.md
       ├── value_objects.md
       ├── domain_events.md
       └── services.md

- `/docs/backlog.md` – Agile backlog and sprints
- `/docs/architecture.md` – Global architecture and deployment notes
- `/docs/ddd/` – Domain-Driven Design documentation
  - `contexts.md`
  - `aggregates.md`
  - `value_objects.md`
  - `domain_events.md`
  - `services.md`

---

## 🚀 How to Use

1. Open `backlog.md` to see all **User Stories**, Sprints, and priorities.
2. Navigate to `/ddd/contexts.md` to understand **Bounded Contexts**.
3. Use `/ddd/aggregates.md` and `/ddd/value_objects.md` to see **aggregates and domain objects** for implementation.
4. Check `/ddd/domain_events.md` and `/ddd/services.md` for **event-driven workflows and service orchestration**.
5. Refer to `architecture.md` for **overall architecture, deployment, and tech stack**.

---

## 💡 Notes

- All documentation is maintained in **Markdown format** for easy readability and version control.
- The system is designed to be **modular**, supporting either a **monolith** or **microservices architecture**.
- **Domain Events** enable cross-context communication, ensuring **loose coupling** between modules.
- **Multi-language support** is centralized, making it easy to add or modify translations.

---

## 📌 Quick Links

- [Backlog & Roadmap](./docs/backlog.md)
- [Bounded Contexts](./docs/ddd/contexts.md)
- [Aggregates](./docs/ddd/aggregates.md)
- [Value Objects](./docs/ddd/value_objects.md)
- [Domain Events](./docs/ddd/domain_events.md)
- [Services](./docs/ddd/services.md)
- [Architecture](./docs/architecture.md)
```
