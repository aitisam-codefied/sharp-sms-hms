## 📲 QR Codes Module

Enables room, location, and task verification through QR code scanning.

---

### 📌 Routes

`/api/v1/qr-code`

| Method | Endpoint  | Description        |
| ------ | --------- | ------------------ |
| GET    | `/list`   | List all QR codes  |
| POST   | `/create` | Create new QR code |
| GET    | `/:id`    | Get QR code by ID  |
| PATCH  | `/:id`    | Update QR code     |
| DELETE | `/:id`    | Delete QR code     |

All routes protected via:

* `authGuard`
* `checkPermission('qrCode', action)`

---

### 🔗 QR Code Usage

* Assigned to specific rooms or locations
* Used to:

  * Trigger task creation
  * Log clock-in/out
  * Track welfare check-ins

---

### 📦 QR Data Fields

* `code`: unique identifier or encoded link
* `locationId` / `roomId`: where it is attached
* `type`: room, location, task, etc.
* `userId`: who last interacted
* `createdAt` / `lastScannedAt`

---

### 🧠 Use Cases

* Scan to perform cleaning or maintenance
* Confirm location visit during shift
* Associate feedback or tasks to scanned room

---

> QR codes are central to physical verification and real-world interaction with the system. Each scan action can trigger workflows or logs automatically.