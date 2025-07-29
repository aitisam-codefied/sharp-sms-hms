## 🆘 S.O.S. Module

Used internally for **daily backup snapshots** and emergency storage of operational data.

---

### 📌 Routes

`/api/v1/sos`

| Method | Endpoint  | Description          |
| ------ | --------- | -------------------- |
| GET    | `/list`   | List all snapshots   |
| POST   | `/create` | Create manual backup |
| GET    | `/:id`    | Get backup by ID     |
| PATCH  | `/:id`    | Update backup data   |
| DELETE | `/:id`    | Delete snapshot      |

All routes are protected with:

* `authGuard`
* `checkPermission('sos', action)`

---

### 💾 Backup Contents

Backups can include:

* Tenants, Companies, Branches
* Users, Shifts, Tasks
* Rooms, Locations
* Incidents, Reports
* QR logs, Clock-In/Out
* Meals, Feedback
* Welfare Checks, Ratings

---

### 🧠 Agenda Job Integration

The following job runs daily (defined in `agenda.job.js`):

```js
agenda.define('daily company backup', async job => {...})
```

This fetches all data created in the last 24 hours and saves it in `SOS` collection under `dailyBackup`.

---

### 🧩 Use Cases

* Audit trail or operational recovery
* Offline analysis or logs
* System debugging or export needs

---

> The S.O.S. module is not used manually by users, but is essential for maintaining backup health and system snapshots.