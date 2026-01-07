# Cloud Architecture Overview

A simple system context for the TODO monorepo.

```mermaid
flowchart LR
  User["User (Browser)"]
  Frontend["React Frontend (MUI)"]
  API["Express API Server"]
  DB[("In-memory SQLite")]
  User --> Frontend
  Frontend -->|HTTP JSON /api| API
  API -->|SQL| DB
```

## C4 System Context

```mermaid
C4Context
title TODO Monorepo - System Context
Person(user, "User", "Interacts via web browser")
System(todo, "TODO App", "React frontend + Express API")
Rel(user, todo, "Uses", "HTTP/HTTPS")
```

Note: C4 diagrams in Mermaid are experimental and may not render in all viewers. If your renderer does not support C4, use the flowchart above as a portable fallback.

## Sequence: Create a TODO

```mermaid
sequenceDiagram
  participant U as User (Browser)
  participant FE as React Frontend
  participant API as Express API Server
  participant DB as In-memory SQLite
  U->>FE: Enter new task (title, description, due date)
  FE->>API: POST /api/tasks {title, description, due_date}
  API->>DB: INSERT task
  DB-->>API: New task id
  API-->>FE: 201 Created + task JSON
  FE-->>U: Task appears in list
```
