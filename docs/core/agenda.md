# Agenda

## 🗓️ `jobs/agenda.job.js`

This file defines all **scheduled background jobs** used by SharpHMS using Agenda.js.

---

### 🔗 Responsibilities

* Define background tasks (jobs)
* Attach logic to run periodically via cron or interval
* Used in `db.js` to register jobs with the Agenda instance

---

### 📌 Defined Jobs

#### 🔓 Remove User Lockouts

```js
agenda.define('remove lockoutTime for users', ...)
```

Resets `lockoutTime` and `failedLoginAttempts` for all users whose lock time has expired.

---

#### 🧹 Cleanup Expired Refresh Tokens

```js
agenda.define('cleanup expired refresh tokens', ...)
```

Cleans all expired refresh tokens from the database.

---

#### 💾 Daily Company Backup

```js
agenda.define('daily company backup', async job => { ... })
```

Backs up:

* Tenants
* Companies
* Branches
* Locations
* Rooms
* Users
* Shifts
* Tasks
* QR Codes
* ClockInOuts
* MealMarkings
* Food & Categories
* Feedbacks
* Incidents
* Reports
* Ratings
* WelfareChecks

Each backup includes only records created in the **last 24 hours**. Backups are stored in the `SOS` collection under `dailyBackup`.

---

### 🔁 Job Schedules

Defined in `db.js`:

```js
agenda.every('5 minutes', 'remove lockoutTime for users')
agenda.every('0 0 * * *', 'cleanup expired refresh tokens')
agenda.every('0 0 * * *', 'cache tenant data')
```

---

### 🧠 Job Lifecycle Events

Agenda also listens for:

* `start`: logs job start
* `complete`: logs job finish
* `fail`: logs job failure

---

> Agenda ensures critical maintenance tasks and backups run in the background at defined intervals.