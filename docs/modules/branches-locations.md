## 🏬 Branches & Locations Module

Represents physical hotel **branches** and sub-units within them called **locations** (floors, blocks, wings, etc).

---

### 📌 Branch Routes

`/api/v1/branch`

| Method | Endpoint  | Description         |
| ------ | --------- | ------------------- |
| GET    | `/list`   | List all branches   |
| POST   | `/create` | Create a new branch |
| GET    | `/:id`    | Get branch by ID    |
| PATCH  | `/:id`    | Update branch       |
| DELETE | `/:id`    | Delete branch       |

---

### 📌 Location Routes

`/api/v1/location`

| Method | Endpoint  | Description           |
| ------ | --------- | --------------------- |
| GET    | `/list`   | List all locations    |
| POST   | `/create` | Create a new location |
| GET    | `/:id`    | Get location by ID    |
| PATCH  | `/:id`    | Update location       |
| DELETE | `/:id`    | Delete location       |

---

### 🧠 Notes

* Each **Company** contains one or more **Branches**
* Each **Branch** contains one or more **Locations**
* Locations may contain Rooms, QR Codes, and Staff assignments
* Branches and Locations are required for managing shifts, tasks, welfare checks, etc.

---

### 🔐 Access Control

All routes require:

* `authGuard`
* `checkPermission('branch' | 'location', action)`

---

> Branches and Locations define the physical and logical layout of operations inside a hotel group.