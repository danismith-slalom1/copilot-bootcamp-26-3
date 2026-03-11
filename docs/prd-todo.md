# Product Requirements Document (PRD) - TODO App Upgrade

## 1. Overview

Upgrade the current basic TODO application (title + completed) to improve task planning while keeping implementation simple and teachable for the bootcamp. The MVP focuses on adding due dates, priority levels, and date-based filters without backend changes. Additional visual emphasis and sorting logic are explicitly deferred to Post-MVP.

---

## 2. MVP Scope

- Add an optional `dueDate` field to each task.
- `dueDate` must use ISO `YYYY-MM-DD` format.
- Invalid `dueDate` values are ignored and treated as absent.
- Add a `priority` field with enum values `P1 | P2 | P3`.
- Default `priority` to `P3` when not provided.
- Keep `title` as a required field.
- Add filter tabs/views: `All`, `Today`, `Overdue`.
- Filter behavior:
- `All` includes completed and incomplete tasks.
- `Today` and `Overdue` show only incomplete tasks.
- Persist tasks in local storage only.
- No backend or external storage changes.

---

## 3. Post-MVP Scope

- Visually highlight overdue tasks.
- Add deterministic task sorting in this order:
- Overdue tasks first.
- Then by priority (`P1` to `P3`).
- Then by due date ascending.
- Tasks without due dates last.

---

## 4. Out of Scope

- Notifications/reminders.
- Recurring tasks.
- Multi-user support.
- Keyboard navigation enhancements.
- Special accessibility feature work beyond current baseline.
- External storage integrations.
- Backend architecture changes.
