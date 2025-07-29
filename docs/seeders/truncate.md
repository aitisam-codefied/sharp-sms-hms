# truncate.md

## 🧹 `seeders/truncate.seed.js`

This utility seeder truncates (empties) **all collections** in the MongoDB database.

---

### ⚠️ Purpose

Used during development/testing to quickly reset the database by removing all existing documents.

---

### 🔗 Responsibilities

* Connect to MongoDB
* Fetch list of all collections
* Call `deleteMany({})` on each one
* Log the number of deleted documents per collection

---

### 🧠 Collection Scan & Truncate

```js
const collections = await mongoose.connection.db.listCollections().toArray()
...
await mongoose.connection.db.collection(collectionName).deleteMany({})
```

---

### 🛡️ Safe Usage

* This script **does not drop collections** — it only clears data
* Use only in local or dev environments
* Will log warnings for any failed truncations

---

### 📤 Run With Caution

```bash
node seeders/truncate.seed.js
```

> Make sure you never run this on a production database.

---

> `truncate.seed.js` is a non-destructive tool to clear all documents from collections without removing the schema or indexes.