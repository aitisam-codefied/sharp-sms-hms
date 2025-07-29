# Socket

## 📡 `app/socket.js`

This file initializes **Socket.IO server** and integrates it with the Express app instance.

---

### 🔗 Responsibilities

* Create an HTTP server from Express
* Initialize Socket.IO with CORS
* Handle connection lifecycle (`connect`, `disconnect`, `error`)
* Join users to rooms by `userId` and `userRoles`
* Export the `server` for use in `main.js`

---

### ⚙️ Setup Summary

```js
const server = http.createServer(app)
const io = new Server(server, { cors: { ... } })
```

---

### 🧠 Connection Logic

When a client connects:

```js
const userId = socket.handshake.query.userId
const userRoles = socket.handshake.query.userRoles
```

* `userId` room is joined for private targeting
* `userRoles` are joined as rooms for broadcasting

---

### 🔊 Event Lifecycle

```js
io.on("connection", socket => {
  socket.on("disconnect", ...)
  socket.on("error", ...)
})
```

All connection/disconnection/error events are logged via the custom logger.

---

### 🌐 CORS Support

```js
origin: SOCKET_ORIGIN
methods: ['GET', 'POST', 'OPTIONS']
credentials: true
```

---

### 📤 Emitting Events

Since the `io` instance is exported, other files can do:

```js
import { io } from './socket.js';
io.to(userId).emit("new-notification", payload);
```

---

> `socket.js` ensures real-time communication between frontend clients and the backend via WebSocket rooms.