## 🧱 Auth, Permission & Body Validation Middleware

Custom Express middleware functions used across the app to secure routes and validate requests.

---

### 🔐 `authGuard`

Protects routes by verifying JWT token.

```js
router.get('/protected', authGuard, handler)
```

If the token is missing or invalid, returns a 401 Unauthorized.

---

### 🔓 `optionalAuth`

Allows token if present, but doesn’t fail if missing.

```js
router.get('/public-or-auth', optionalAuth, handler)
```

Used for semi-protected or hybrid routes.

---

### 🛡️ `checkPermission(resource, action)`

Enforces RBAC using assigned user roles.

```js
router.post('/create', authGuard, checkPermission('user', 'create'), handler)
```

Checks if any of the user’s roles has the permission `{ resource, action }`.

---

### 📋 `validateBody(schema)`

Validates incoming request body using a Joi schema. Typically placed inline inside the route file:

```js
router.post('/create', validateBody(schema), handler)
```

#### Joi Validation Logic

```js
export const validateBody = (schema) => (req, res, next) => {
  const { error } = schema.validate(req.body, { abortEarly: false });

  if (error) {
    return res.status(400).json({
      success: false,
      message: 'Validation error',
      details: error.details.map(d => d.message)
    });
  }

  next();
};
```

* Combines well with custom validators like `createUserSchema`
* Captures all validation errors (not just the first)

---

### 🧠 Notes

* Middleware stack order is important
* All protected routes include `authGuard` + `checkPermission`
* Validation middleware is route-local and schema-driven
* Middleware returns consistent JSON response on failure

---

> These middleware utilities ensure API security, role enforcement, and input validation are handled declaratively.