## 🕒 Shifts Module

Handles staff shift assignments across different locations.

---

### 📌 Routes

`/api/v1/shift`

| Method | Endpoint  | Description        |
| ------ | --------- | ------------------ |
| GET    | `/list`   | List all shifts    |
| POST   | `/create` | Create a new shift |
| GET    | `/:id`    | Get shift by ID    |
| PATCH  | `/:id`    | Update shift       |
| DELETE | `/:id`    | Delete shift       |

All routes are protected with:

* `authGuard`
* `checkPermission('shift', action)`

---

### 🧠 Notes

* Shifts are associated with:

  * A `locationId`
  * A `staffId`
* Typically assigned by Admin or Manager roles
* Each shift record can contain:

  * startTime
  * endTime
  * assigned location

---

### 🔗 Relations

* Linked to Clock In/Out records
* Used for reporting and scheduling

---

> Shifts help organize staff workload and time management at the location level.