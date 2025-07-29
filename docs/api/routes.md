## 🌐 API Route Index

This file lists all major REST API route prefixes in the SharpHMS backend.

---

### 🧩 Core Modules

| Prefix      | Purpose                 |
| ----------- | ----------------------- |
| `/auth`     | Authentication          |
| `/user`     | User Management         |
| `/role`     | Roles & Permissions     |
| `/branch`   | Branches                |
| `/company`  | Company-level structure |
| `/tenant`   | Tenant root entity      |
| `/location` | Hotel locations         |
| `/room`     | Room configuration      |

---

### 📋 Staff Operations

| Prefix           | Purpose                |
| ---------------- | ---------------------- |
| `/shift`         | Staff shifts           |
| `/task`          | Task tracking          |
| `/clock-in-out`  | QR-based time tracking |
| `/welfare-check` | Guest check-ins        |

---

### 📦 Facility & Food

| Prefix     | Purpose                  |
| ---------- | ------------------------ |
| `/qr-code` | Physical QR identifiers  |
| `/food`    | Meals, feedback, ratings |

---

### 🚨 Emergency & Reports

| Prefix      | Purpose           |
| ----------- | ----------------- |
| `/incident` | Emergency logging |
| `/report`   | General reporting |
| `/sos`      | Internal backups  |

---

> All routes are prefixed with `/api/v1` in production. Example: `/api/v1/auth/login`