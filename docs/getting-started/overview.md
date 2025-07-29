# 🏨 Sharp SMS HMS Overview

**Sharp SMS HMS** is a multi-tenant, role-based Hotel Management System (HMS) built with Node.js, Express, MongoDB, and Socket.IO.

It supports:
- Multi-hotel tenancy (one or more branches under a single tenant/company)
- Role-based access control (RBAC) with scoped permissions
- QR-based task management for staff
- Real-time updates with Socket.IO
- Automated job processing using Agenda

---

## 🧩 Key Features

| Feature                | Description                                                                 |
|------------------------|-----------------------------------------------------------------------------|
| Multi-Tenant Structure | Each tenant (hotel group) has its own companies, branches, and staff.       |
| RBAC System            | Roles and permissions are dynamically created and assigned per branch.      |
| QR Task Management     | Staff check-in/out and task execution via QR scanning.                      |
| Food & Feedback Module | Add meals, categories, and collect structured feedback from guests.         |
| Incident Reporting     | Capture incidents per location with room and staff linkage.                 |
| Welfare & Meal Checks  | Routine logging of guest welfare and meals using QR codes.                  |
| Shift Scheduling       | Manage shifts per staff and location.                                       |
| Real-time System       | WebSocket notifications and events via Socket.IO.                           |
| Background Jobs        | Periodic tasks like cleaning expired tokens and backing up tenant data.     |

---

## 🛠️ Technology Stack

| Layer         | Tech Used                       |
|---------------|----------------------------------|
| Backend       | Node.js, Express                |
| Database      | MongoDB, Mongoose               |
| Realtime      | Socket.IO                       |
| Scheduler     | Agenda.js                       |
| Authentication| Passport JWT                    |
| Dev Tools     | Docsify (for docs), Dotenv, Helmet, Morgan, XSS, etc. |

---

## 📦 System Modules

- Authentication & Token Lifecycle
- User & Role Management
- Tenant → Company → Branch → Location → Room Hierarchy
- QR Code-Based Check-in/out System
- Welfare Checks & Incident Reports
- Meals, Ratings, Feedback
- Background Jobs (Backup & Maintenance)
- WebSocket-based Real-time Layer

---

## 📁 Folder Snapshot
- `root/`
  - `/config`         # DB connection & environment configs
  - `/app`            # Core app logic: logger, socket, etc.
  - `/routes`         # Express routes (organized by module)
  - `/controllers`    # Business logic for each module
  - `/models`         # Mongoose models
  - `/constants`      # System-wide constants (roles, permissions, modules)
  - `/jobs`           # Scheduled job definitions (Agenda)
  - `/seeders`        # Initial DB seeders for roles, tenants, truncation
  - `/public`         # Static files
  - `main.js`         # App entry point