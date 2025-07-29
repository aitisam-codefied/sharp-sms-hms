# tenant.md

## 🏢 `seeders/tenant.seed.js`

This seeder creates a **Tenant (Hotel Group)** and an associated **Admin user**.

---

### 🔗 Responsibilities

* Connect to MongoDB
* Create a new Tenant document
* Seed Admin roles (using `MODULES.ADMIN`)
* Create one default Admin user under that tenant

---

### 🏨 Tenant Object Structure

```js
{
  owner: 'Fahim Aslam',
  phoneNumber: '+923001234567',
  emailAddress: 'admin@happy-hotels.com',
  details: {
    paymentInfo: {
      plan: 'Basic'
    }
  }
}
```

> Each tenant must have a unique email and phone.

---

### 👤 Admin User

**Admin User Info:**

* Email: `fahim@happy-hotels.com`
* Password: `admin123`
* Username: Auto-generated from name
* Role: `Admin` (assigned manually)

---

### 🎯 Role Assignment

```js
const roleMap = {
  Admin: permissions.filter(p => MODULES.ADMIN.includes(p.resource))
}
```

Each role is inserted and attached to the user using:

```js
roles: [adminRoleId]
```

---

### 🧠 Duplicate Safety

If an Admin with the email already exists, it logs:

```txt
User with that email already exists!!
```

And skips creating tenant/user again.

---

### 📤 Run This Second

```bash
node seeders/tenant.seed.js
```

---

> Always run this after `init.seed.js` to ensure role and permission dependencies are already in place.