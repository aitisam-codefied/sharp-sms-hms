## 🚨 Incidents & Reports Module

Handles the logging of incidents and general-purpose reporting in the system.

---

### 📌 Incident Routes

`/api/v1/incident`

| Method | Endpoint  | Description         |
| ------ | --------- | ------------------- |
| GET    | `/list`   | List all incidents  |
| POST   | `/create` | Create new incident |
| GET    | `/:id`    | Get incident by ID  |
| PATCH  | `/:id`    | Update incident     |
| DELETE | `/:id`    | Delete incident     |

---

### 📌 Report Routes

`/api/v1/report`

| Method | Endpoint  | Description       |
| ------ | --------- | ----------------- |
| GET    | `/list`   | List all reports  |
| POST   | `/create` | Create new report |
| GET    | `/:id`    | Get report by ID  |
| PATCH  | `/:id`    | Update report     |
| DELETE | `/:id`    | Delete report     |

Both modules are protected by:

* `authGuard`
* `checkPermission('incident' | 'report', action)`

---

### 🧠 Use Cases

* Incident Module:

  * Medical emergencies
  * Room-level disturbances
  * Maintenance issues

* Report Module:

  * Daily summaries
  * Task or meal logs
  * Shift statistics

---

### 📦 Data Fields (Examples)

**Incident:**

* `roomId`, `locationId`
* `description`, `severity`
* `staffId`, `timestamp`

**Report:**

* `generatedBy`
* `reportType` (daily, custom)
* `data[]` — dynamic payload

---

> These modules offer transparency and auditability across the property by tracking significant events and compiling summaries.