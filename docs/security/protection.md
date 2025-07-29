## 🛡️ Express Protection Middleware

The app uses several middleware layers to enhance security, performance, and request handling.

---

### 🔐 Helmet

```js
app.use(helmet());
```

Sets secure HTTP headers (e.g. disables `x-powered-by`, sets `X-Frame-Options`, CSP, etc).

---

### 🧼 XSS Protection

```js
import { xss } from 'express-xss-sanitizer';
app.use(xss());
```

Sanitizes request bodies, query strings, and params to prevent Cross-Site Scripting attacks.

---

### 🗂️ CORS

```js
app.use(cors({
  origin: FRONTEND_ORIGIN,
  methods: ["GET", "POST", "PUT", "PATCH", "DELETE", "OPTIONS"],
  allowedHeaders: ["Content-Type", "Authorization", ...],
  credentials: true,
}))
```

Controls which frontend origins are allowed to interact with the backend.

---

### 🍪 Cookie Parser

```js
app.use(cookieParser())
```

Enables signed cookie reading, used with refresh tokens and user sessions.

---

### 🗜️ Compression

```js
app.use(compression())
```

Compresses all response bodies using gzip — improves response time and bandwidth usage.

---

### 📝 Logger (Morgan)

```js
app.use(morgan("combined", { stream }))
```

Logs incoming HTTP requests to the logger, useful for debugging and analytics.

---

> These protection layers work together to keep the application secure and performant in both dev and production environments.