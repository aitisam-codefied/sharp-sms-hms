## 🛡️ Passport JWT Strategy

SharpHMS uses **Passport.js** to implement stateless authentication via JSON Web Tokens (JWT).

---

### 📌 Strategy File

`strategies/local.strategy.js`

---

### 🔐 What It Does

* Extracts token from `Authorization` header (Bearer)
* Verifies JWT using secret from `.env`
* Loads user from DB
* Attaches user to `req.user` for route access

---

### 🔗 Used In

```js
passport.use(jwtStrategy);
app.use(passport.initialize());
```

---

### 🧠 Token Requirements

* Token must be signed using `JWT_SECRET`
* Must include a `sub` field for user ID
* Optionally includes tenant/role/branch info

---

### 🔒 Example Token Payload

```json
{
  "sub": "userId",
  "email": "user@example.com",
  "iat": 1694500000,
  "exp": 1694503600
}
```

---

### 🔄 Token Refresh Flow

* `/login` issues access + refresh token
* `/refresh-token` issues a new access token if refresh is valid

---

### 🧪 Testing

Use the following header in Postman:

```http
Authorization: Bearer <access_token>
```

---

> Passport JWT strategy ensures secure access to protected routes using stateless identity embedded inside JWTs.