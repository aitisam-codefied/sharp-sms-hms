## ⏰ Agenda Job Schedule

All background jobs in SharpHMS are powered by Agenda.js, which runs on MongoDB.

---

### 🗓️ Scheduled Jobs

| Job Name                       | Frequency     | Purpose                        |
| ------------------------------ | ------------- | ------------------------------ |
| remove lockoutTime for users   | every 5 mins  | Clears expired login locks     |
| cleanup expired refresh tokens | daily @ 00:00 | Cleans outdated refresh tokens |
| cache tenant data              | daily @ 00:00 | Warmup tenant metadata         |
| daily company backup           | daily @ 00:00 | Full tenant+branch data backup |

---

### 🧠 How They Work

Each job is defined in `agenda.job.js` using:

```js
agenda.define("job-name", async job => { ... })
```

They are scheduled inside `db.js` after DB connection:

```js
agenda.every("5 minutes", "remove lockoutTime for users")
agenda.every("0 0 * * *", "cleanup expired refresh tokens")
```

---

### ✅ Job Events

Agenda emits events:

* `start`
* `complete`
* `fail`

Used for logging job progress in real time.

---

> Jobs automate crucial cleanup, lock resets, and nightly backups — keeping the system optimized and audit-ready.