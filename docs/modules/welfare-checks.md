## 🧾 Welfare Checks Module

Logs scheduled checks performed by staff to ensure guest well-being and safety.

---

### 📌 Routes

`/api/v1/welfare-check`

| Method | Endpoint  | Description              |
| ------ | --------- | ------------------------ |
| GET    | `/list`   | List all welfare checks  |
| POST   | `/create` | Create new welfare check |
| GET    | `/:id`    | Get check by ID          |
| PATCH  | `/:id`    | Update welfare check     |
| DELETE | `/:id`    | Delete welfare check     |

Protected by:

* `authGuard`
* `checkPermission('welfareCheck', action)`

---

### 🧠 Data Tracked

* `staffId`: Who performed the check
* `qrCodeId`: Location or room QR code
* `status`: success / failed / missed
* `comment`: Optional notes
* `timestamp`: Check time

---

### 🔗 Use Cases

* Periodic check-ins for vulnerable guests
* Logging guest availability and room status
* Confirming staff rounds at specific intervals

---

> Welfare checks are critical for ensuring guest safety and fulfilling compliance or operational protocols.