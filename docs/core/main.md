# Main

## 📂 `main.js`

This is the **entry point** of the SharpHMS backend application.

---

### 🔗 Responsibilities

* Loads environment variables from `.env`
* Connects to MongoDB
* Starts the HTTP + Socket.IO server
* Registers global process error handlers

---

### ⚙️ Flow Summary

```js
1. Load dotenv configs
2. Import DB and socket server
3. Setup error handlers (uncaughtException & unhandledRejection)
4. Connect to MongoDB
5. Start Express server with Socket.IO
```

---

### 🧠 Error Handling

```js
process.on('uncaughtException', handler);
process.on('unhandledRejection', handler);
```

Ensures fatal errors are logged and the app exits cleanly.

---

### 📦 Dependencies Used

* `dotenv`: Loads environment variables
* `mongoose`: For MongoDB connection
* `socket.js`: To bind Express + Socket.IO
* `logger.js`: To log startup status or errors

---

### ✅ Output Example

```txt
🔗 MongoDB connected in development environment to mongodb+srv://...
🚀 Server running in development environment on port 5001
```

---

> This file is essential for initializing all major app components.
> It delegates Express-related logic to `app.js` and socket handling to `socket.js`.