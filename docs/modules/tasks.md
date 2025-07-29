## ✅ Tasks Module

Manages staff task assignments — typically triggered via QR code scans or admin panel.

---

### 📌 Routes

`/api/v1/task`

| Method | Endpoint  | Description     |
| ------ | --------- | --------------- |
| GET    | `/list`   | List all tasks  |
| POST   | `/create` | Create new task |
| GET    | `/:id`    | Get task by ID  |
| PATCH  | `/:id`    | Update task     |
| DELETE | `/:id`    | Delete task     |

Protected by:

* `authGuard`
* `checkPermission('task', action)`

---

### 📦 Task Model Fields

Common fields:

* `title` / `description`
* `staffId` → who performs the task
* `roomId`, `locationId` → where task occurs
* `status` → e.g., pending, in-progress, completed
* `createdBy` / `createdAt`

---

### 🔗 Relations

* Tasks link to Rooms, Locations, QR Codes
* Can be initiated via QR scan
* May include timestamps (e.g., acceptedAt, completedAt)

---

### 📌 Use Cases

* Assigning laundry or cleaning to staff
* Completing welfare or meal marking tasks
* Recording incident response actions

---

> Tasks represent actionable units of work that are tightly integrated with user, room, and QR systems.