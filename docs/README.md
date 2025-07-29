# <img src="sharp-sms-hms.png" alt="Sharp SMS HMS Logo" width="56" style="vertical-align: middle;" /> Sharp SMS HMS Developer Documentation

> Multi-Tenant Role-Based Hotel Management System  
> Built with Node.js, MongoDB, Socket.IO, Agenda, and Express

---

## 🚀 Getting Started
- [Project Overview](getting-started/overview.md)
- [Installation & Setup](getting-started/setup.md)
- [Environment Variables](getting-started/env.md)

## ⚙️ Core Structure
- [main.js (Entry Point)](core/main.md)
- [app.js (Express App)](core/app.md)
- [socket.js (WebSocket Layer)](core/socket.md)
- [db.js (MongoDB Connection)](core/db.md)
- [agenda.job.js (Jobs)](core/agenda.md)

## 🗃️ Seeders
- [init.seed.js (Super Admin)](seeders/init.md)
- [tenant.seed.js (Company Admin)](seeders/tenant.md)
- [truncate.seed.js (Clear DB)](seeders/truncate.md)

## 📦 Modules
- [Authentication](modules/auth.md)
- [Users](modules/users.md)
- [Roles & Permissions](modules/roles.md)
- [Tenants & Companies](modules/tenants-companies.md)
- [Branches & Locations](modules/branches-locations.md)
- [Rooms](modules/rooms.md)
- [Shifts](modules/shifts.md)
- [Tasks](modules/tasks.md)
- [Welfare Checks](modules/welfare-checks.md)
- [Clock In/Out](modules/clock-in-out.md)
- [QR Codes](modules/qr-codes.md)
- [Incidents & Reports](modules/incidents-reports.md)
- [Food Management](modules/food.md)
- [S.O.S. & Ratings](modules/sos.md)

## 🔒 Security
- [Passport JWT Strategy](security/passport.md)
- [Middleware Layers](security/middleware.md)
- [XSS/CORS/Helmet](security/protection.md)

## 🔧 API Structure
- [API Route List](api/routes.md)

## 🧠 Socket Events
- [Real-time Events](socket/events.md)

## 🗓️ Scheduled Jobs (Agenda)
- [Daily Jobs](agenda/jobs.md)
- [Backup & Cleanup Logic](agenda/backup.md)

## 📄 Miscellaneous
- [Logger & Streams](core/logger.md)
- [Static Pages (Success/Cancel)](core/static.md)

---
© SharpHMS Docs — 2025