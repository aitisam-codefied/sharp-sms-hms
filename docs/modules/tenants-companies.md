## 🏢 Tenants & Companies Module

Manages the top-level hierarchy: **Tenants** (hotel owners/groups) and their **Companies** (business units/brands).

---

### 📌 Tenant Routes

`/api/v1/tenant`

| Method | Endpoint  | Description      |
| ------ | --------- | ---------------- |
| POST   | `/create` | Create a tenant  |
| GET    | `/list`   | List all tenants |
| GET    | `/:id`    | Get tenant by ID |
| PATCH  | `/:id`    | Update tenant    |
| DELETE | `/:id`    | Delete tenant    |

---

### 📌 Company Routes

`/api/v1/company`

| Method | Endpoint          | Description                         |
| ------ | ----------------- | ----------------------------------- |
| POST   | `/create`         | Create a company                    |
| GET    | `/list`           | List all companies                  |
| GET    | `/list-by-tenant` | List companies under current tenant |
| GET    | `/:id`            | Get company by ID                   |
| PATCH  | `/:id`            | Update company                      |
| DELETE | `/:id`            | Delete company                      |

All routes are protected by:

* `authGuard`
* `checkPermission('tenant' | 'company', action)`

---

### 🧠 Notes

* A **Tenant** is seeded via `tenant.seed.js`
* A **Tenant** can have multiple **Companies**, and each company can span multiple branches
* All companies are linked to a `tenantId`
* Admin-level users operate at the **company** level, not tenant-global unless Super Admin

---

> These modules define the root of the hierarchical structure in SharpHMS, from tenant → company → branch → location.