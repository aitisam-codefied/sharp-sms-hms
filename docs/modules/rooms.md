## 🚪 Rooms Module

Represents individual guest rooms or units within a Location.

---

### 📌 Routes

`/api/v1/room`

| Method | Endpoint  | Description         |
| ------ | --------- | ------------------- |
| GET    | `/list`   | List all rooms      |
| POST   | `/create` | Create a new room   |
| GET    | `/:id`    | Get room by ID      |
| PATCH  | `/:id`    | Update room details |
| DELETE | `/:id`    | Delete room         |

All endpoints are protected by:

* `authGuard`
* `checkPermission('room', action)`

---

### 🧠 Notes

* Rooms belong to a **location**, which belongs to a **branch**
* Rooms are used in:

  * Task Assignments
  * QR Code Scanning
  * Incident Reports
  * Ratings and Feedback
* Rooms can have optional fields like room number, type, assigned guest/user, etc.

---

> The rooms module allows fine-grained control over operational units and is tightly linked to task tracking, guest feedback, and shift planning.