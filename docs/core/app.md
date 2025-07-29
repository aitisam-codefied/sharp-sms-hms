# App

## 🧩 `app/app.js`

This file creates and configures the **Express.js application** instance used by `main.js` and `socket.js`.

---

### 🔗 Responsibilities

* Initialize Express app
* Apply middleware (helmet, bodyParser, cors, cookieParser, etc.)
* Set up Passport.js (JWT strategy)
* Define and mount all API routes
* Serve static pages (success, cancel, etc.)

---

### 🔐 Security Middleware

* `helmet` — secure HTTP headers
* `xss()` — prevents cross-site scripting
* `cors()` — cross-origin support with credentials
* `cookieParser()` — parses cookies for session/auth
* `compression()` — enables gzip compression

---

### 🛠️ Developer Middleware

* `morgan` — logs HTTP requests (combined mode)
* `logger` — custom logging stream

---

### 📦 Body Parsing

```js
app.use(bodyParser.json());
app.use(bodyParser.urlencoded({ extended: true }));
```

---

### 🧪 Passport Strategy

```js
passport.use(jwtStrategy);
```

Supports protected routes using JWT tokens.

---

### 🌐 CORS Configuration

```js
origin: FRONTEND_ORIGIN
methods: [GET, POST, PUT, PATCH, DELETE, OPTIONS]
credentials: true
```

---

### 📁 Static File Routes

* `/` → `index.html`
* `/success` → `success.html`
* `/cancel` → `cancel.html`

---

### 🚏 API Routes

All routes are mounted under `/api/v1`:

```txt
/api/v1/auth
/api/v1/user
/api/v1/task
... and more
```

Each route has its own file in the `/routes/` directory and its own permission-based middleware.

---

### 🧼 Error Handling Middleware

Handles any uncaught Express errors and returns JSON output with status.

```js
res.status(err.status || 500).json({ success: false, message: err.message })
```

---

> `app.js` is the core glue that combines middleware, routing, error handling, and auth strategies into a single cohesive server application.
