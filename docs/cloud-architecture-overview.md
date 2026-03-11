# Cloud Architecture Overview

This document provides a simple system context view of the TODO app monorepo.

## System Context

```mermaid
flowchart LR
    User[User Browser]
    FE[React Frontend\npackages/frontend]
    API[Express API\npackages/backend]
    DB[(In-Memory SQLite Store)]

    User -->|HTTPS| FE
    FE -->|REST /api/tasks| API
    API -->|SQL queries| DB
```

## Sequence: Create TODO

```mermaid
sequenceDiagram
    autonumber
    actor U as User
    participant B as Browser (React UI)
    participant A as Express API
    participant D as In-Memory SQLite

    U->>B: Enter title/details and click Add Task
    B->>A: POST /api/tasks { title, description, due_date }
    A->>D: INSERT task row
    D-->>A: Insert result (id)
    A->>D: SELECT task by id
    D-->>A: New task record
    A-->>B: 201 Created + task JSON
    B->>A: GET /api/tasks
    A->>D: SELECT all tasks
    D-->>A: Task list
    A-->>B: 200 OK + tasks JSON
    B-->>U: Updated task list displayed
```

## Notes

- The React frontend is the user-facing application.
- The Express API exposes task endpoints consumed by the frontend.
- Data is stored in an in-memory SQLite database, so data resets when the backend process restarts.
