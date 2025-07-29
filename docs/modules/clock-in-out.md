## ⏱️ Clock In/Out Module

Tracks staff attendance and shift check-ins using QR-based or manual time stamps.

---

### 📌 Routes

`/api/v1/clock-in-out`

| Method | Endpoint  | Description           |
| ------ | --------- | --------------------- |
| GET    | `/list`   | List all records      |
| POST   | `/create` | Create a clock in/out |
| GET    | `/:id`    | Get record by ID      |
| PATCH  | `/:id`    | Update record         |
| DELETE | `/:id`    | Delete record         |

Protected by:

* `authGuard`
* `checkPermission('clockInOut', action)`

---

### 📋 Record Fields

* `staffId` — who checked in/out
* `locationId` — where the activity happened
* `qrCodeId` — scanned to verify presence
* `type` — `IN` or `OUT`
* `timestamp` — recorded datetime

---

### 🔗 Linked To

* QR Codes (physical points of entry)
* Users (staff performing the action)
* Shifts (can be correlated)

---

### 🧠 Use Cases

* Verifying staff shift start/end via QR codes
* Logging exact time and place for compliance
* Managing automated attendance reports

---

> This module ensures staff presence tracking is reliable and verifiable through time-stamped scans.