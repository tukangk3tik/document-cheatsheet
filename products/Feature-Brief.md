# 📄 Feature Brief: [Backend Feature Name]

## 🧭 Summary

> High-level overview of the backend feature, its purpose, and value.

**Example:**  
Implement a new `/users/activity` API endpoint to return recent user actions for activity feed rendering.

---

## 🎯 Goals

- Expose a performant, secure API endpoint for user activity.
- Ensure compatibility with frontend consumption patterns.
- Enable analytics logging for future product insights.

---

## ❌ Non-Goals

- Building UI for the activity feed.
- Real-time push or websocket implementation.

---

## 🧩 Scope

### 📌 Endpoint(s)

- `GET /users/activity`
  - Authenticated route returning last N actions by user.

### 📌 Inputs

| Field     | Type   | Description           |
|-----------|--------|-----------------------|
| `limit`   | int    | Max number of entries |
| `cursor`  | string | Pagination cursor     |

### 📌 Outputs

```json
[
  {
    "id": "activity_123",
    "type": "LOGIN",
    "timestamp": "2025-05-25T12:00:00Z"
  }
]
