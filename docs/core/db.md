# DB

## 🗄️ `config/db.js`

This file connects the app to **MongoDB** using Mongoose and initializes scheduled jobs using Agenda.js.

---

### 🔗 Responsibilities

* Connect to MongoDB using `mongoose.connect`
* Create missing collections on startup
* Initialize Agenda job scheduler
* Schedule recurring background jobs
* Export the `connectDB` function and the `agenda` instance

---

### ⚙️ Database Connection

```js
mongoose.connect(ENV.DATABASE_URI)
```

* Uses URI from `.env`
* Sets server selection timeout and unified topology

---

### 📁 Collection Initialization

```js
await db.createCollection(collection)
```

If a listed collection doesn't exist, it is created on startup. Example collections:

* tenants
* companies
* branches
* locations
* users
* shifts
* qrCodes
* tasks
* ... and more

---

### 📅 Agenda Jobs Setup

```js
agenda = new Agenda({ db: { address: ENV.DATABASE_URI, collection: 'agendaJobs' } })
```

Defines and starts jobs using `defineJobs()`:

* Remove expired `lockoutTime` on users
* Clean up expired refresh tokens
* Cache tenant data

---

### 🧠 Job Events Tracked

* `start` — Logs job start
* `complete` — Logs job finish
* `fail` — Logs job error

---

### 🔃 Recurring Jobs

```js
agenda.every('5 minutes', 'remove lockoutTime for users')
agenda.every('0 0 * * *', 'cleanup expired refresh tokens')
agenda.every('0 0 * * *', 'cache tenant data')
```

---

> `db.js` ensures the database is ready and all recurring background jobs are scheduled before app startup.