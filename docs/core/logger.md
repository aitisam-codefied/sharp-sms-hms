## 📋 Logger

A custom logging system based on Winston and integrated with Morgan request logs.

---

### 📦 Features

* Console + file-based logging
* Used for all app-level errors and events
* Stream-compatible with Morgan for request logging

---

### 🪵 Usage

Import anywhere:

```js
import logger from './logger.js'
```

Log entries:

```js
logger.info("Server started")
logger.warn("Slow query detected")
logger.error("Unhandled exception")
```

---

### 📡 Morgan Stream

```js
import { stream } from './logger.js'
app.use(morgan("combined", { stream }))
```

Logs HTTP requests to console or file.

---

### 🧠 Notes

* Centralized error visibility
* Fully structured JSON logs
* Ready for integration with external log processors

---

> All critical operations and system exceptions should use `logger.error()` for persistent diagnostics.