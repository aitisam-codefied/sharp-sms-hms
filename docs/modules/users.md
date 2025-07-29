## 👤 Users Module

Handles creation, retrieval, update, and deletion of system users (staff, admins, managers, etc.).

---

### 📌 Route Prefix

`/api/v1/user`

---

### 🔗 Routes

| Method | Endpoint  | Description       |
| ------ | --------- | ----------------- |
| GET    | `/list`   | List all users    |
| POST   | `/create` | Create a new user |
| GET    | `/:id`    | Get user by ID    |
| PATCH  | `/:id`    | Update user by ID |
| DELETE | `/:id`    | Delete user by ID |

All routes require:

* `authGuard`
* `checkPermission('user', action)`

---

### 🔒 Permissions

This module is protected by RBAC:

```js
checkPermission('user', 'read')
checkPermission('user', 'create')
checkPermission('user', 'update')
checkPermission('user', 'delete')
```

---

### 🧠 Notes

* Users can belong to tenants, branches, and roles
* Users may be assigned to tasks, rooms, and QR scans
* Admins and Managers can only manage users within their scope (branch/tenant)

---

> The users module defines and enforces user lifecycle actions with strict permission checks.