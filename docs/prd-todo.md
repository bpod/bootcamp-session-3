# Product Requirements Document (PRD) - TODO App Upgrade: Due Dates, Priorities, Filters

## 1. Overview

We are upgrading the basic TODO app (currently title + completed) to support due dates, priorities, and quick filters so users can better organize tasks without adding backend complexity. The MVP prioritizes a simple, teachable implementation using local storage only. Post‑MVP adds visual overdue highlighting and deterministic sorting that reflects urgency and importance.

Sources: docs/artifacts/09162025-requirements-meeting.vtt, docs/artifacts/09172025-slack-conversation-export.txt.

---

## 2. MVP Scope

- Data model and validation
  - title: required.
  - priority: enum "P1" | "P2" | "P3"; default "P3".
  - dueDate: optional ISO `YYYY-MM-DD`; invalid values are ignored (treated as absent).
- Features
  - Add optional due date to tasks.
  - Add priority selection with three levels: P1, P2, P3.
  - Display priorities with color badges for quick scanning: P1 red, P2 orange, P3 gray.
  - Add filters: All, Today, Overdue.
  - Filter behavior: Today and Overdue show only incomplete tasks; All includes completed tasks.
- Storage and architecture
  - Local-only persistence; no backend or external storage changes.
- Constraints and notes
  - Keep implementation simple and teachable; no backend changes.
  - Advanced accessibility/keyboard navigation not required for MVP (per meeting notes).

---

## 3. Post-MVP Scope

- Visual overdue highlighting for overdue tasks (e.g., red highlight) so urgency stands out.
- Sorting rules for task list:
  - Overdue first → Priority (P1 → P2 → P3) → Due date ascending → Undated last.

---

## 4. Out of Scope

- Notifications.
- Recurring tasks.
- Multi-user functionality.
- Keyboard navigation / advanced accessibility work.
- External storage or backend changes (app remains local-only).
- Any filter sets beyond All, Today, Overdue.