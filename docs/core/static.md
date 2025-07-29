# static.md

## 🧾 Static Pages

The following public routes are served via static HTML files from the `/public` folder.

---

### 🧱 File Structure

- `/public`
  - `├── index.html`
  - `├── success.html`
  - `└── cancel.html`


---

### 🌐 Routes

| Route      | File Served    | Use Case                    |
| ---------- | -------------- | --------------------------- |
| `/`        | `index.html`   | Default page                |
| `/success` | `success.html` | After successful operations |
| `/cancel`  | `cancel.html`  | After canceled actions      |

These are configured in `app.js`:

```js
res.sendFile(path.join(...))
```

---

> Static files are useful for redirect confirmations, Stripe success/cancel, or embedding minimal content.