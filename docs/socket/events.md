## 📡 Socket.IO Event Layer

Socket.IO is used to implement real-time communication in SharpHMS — including role-specific rooms and live updates.

---

### 🔗 Socket Initialization

Happens inside `socket.js`:

```js
const io = new Server(server, { cors: { ... } })
```

---

### 🧠 Connection Lifecycle

```js
io.on("connection", socket => {
  // Rooms are joined here
  // Listeners are defined here
})
```

---

### 🏷️ Room-Based Segmentation

When a socket connects:

* `userId` room is joined for private events
* `userRoles[]` rooms are joined for role-based events

---

### ✉️ Event Examples

```js
io.to(userId).emit("notification", payload)
io.to("Admin").emit("task-created", data)
```

---

### 📌 Common Use Cases

* Notify a user about new task
* Broadcast updates to roles (Admin, Staff, etc.)
* Send alert when welfare check is missed

---

### 🧠 Notes

* Each socket is fully identified by its `socket.id`
* Disconnection and error events are logged

---

> The socket layer is essential for real-time tracking of task creation, QR scans, and staff responses.