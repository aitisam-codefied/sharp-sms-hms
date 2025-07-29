# init.md

## 🌱 `seeders/init.seed.js`

This seeder initializes the system with the **Super Admin role**, default permissions, and a Super Admin user.

---

### 📦 Responsibilities

* Connects to MongoDB
* Seeds `permissions` using `PERMISSIONS` constant
* Creates a `Super Admin` role with all permissions
* Generates a Super Admin user if not already present

---

### 🔐 Super Admin Setup

**Email:** `superadmin@sharpHMS.com`
**Password:** `superadmin123`

```js
const superAdmin = new User({
  firstName: 'Super',
  lastName: 'Admin',
  emailAddress: 'superadmin@sharpHMS.com',
  ...
})
```

Username is auto-generated using:

```js
User.generateUsername('Super', 'Admin')
```

---

### 🔗 Role Binding

After user creation, the Super Admin role is pushed to the user's roles:

```js
superAdmin.roles.push(superAdminRole._id)
```

---

### ✅ Seeder Safety

* If Super Admin already exists, the user is **not** recreated
* Always ensures permissions and SuperAdmin role are seeded before moving on to tenant seeding

---

### 📤 Run This First

```bash
node seeders/init.seed.js
```

---

> This seeder should always run before `tenant.seed.js` to ensure role + permission structure is ready.