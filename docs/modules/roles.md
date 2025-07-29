## 🛡️ Roles & Permissions Module

This module powers the **RBAC (Role-Based Access Control)** system. Roles are scoped per branch and control access to features using permissions.

---

### 📌 Route Prefix

`/api/v1/role`

---

### 🔗 Routes

| Method | Endpoint     | Description                             |
| ------ | ------------ | --------------------------------------- |
| GET    | `/list`      | List all roles                          |
| POST   | `/create`    | Create a new role                       |
| GET    | `/:id`       | Get role by name or ID                  |
| GET    | `/:branchId` | Get roles assigned to a specific branch |
| PATCH  | `/:id`       | Update role name or permission set      |
| DELETE | `/:id`       | Delete role                             |

> All routes require `authGuard` and proper `checkPermission("role", action)`.

---

### 🧠 Role Object

```js
{
  name: "Manager",
  permissions: [ObjectId("..."), ...]
}
```

* Roles are defined with an array of permission IDs.
* Users are assigned roles using `user.roles = [roleId1, roleId2]`

---

### 🔐 Permissions Model

Each permission document has:

```js
{
  resource: "user",    // module or entity
  action: "read"        // create / read / update / delete
}
```

Example permission:

```json
{ "resource": "task", "action": "create" }
```

---

### 🔄 Dynamic Evaluation

Permissions are evaluated dynamically in middleware:

```js
checkPermission("user", "update")
```

Checks if the current user has a role with the matching permission.

---

### 📦 Permission Constants

All permissions are defined in `constants/permissions.js`. Modules and permission groups are also listed in `constants/modules.js`.

---

### 🧩 Role Seeding

* `init.seed.js` creates `SUPER_ADMIN` role with **all** permissions
* `tenant.seed.js` creates `Admin` role using a filtered subset (e.g., `MODULES.ADMIN`)

---

### 📍 Scope

* Roles can be global (SuperAdmin) or scoped to a **branch**
* Each branch can define its own custom roles (e.g., Housekeeping, Reception)

---

> The Roles module is the foundation of authorization in SharpHMS — tightly integrated with middleware, users, and tenants.