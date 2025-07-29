## 🔐 Authentication Module

Handles all login, registration, token refresh, password reset, and OTP-related logic.

---

### 📌 Route Prefix

`/api/v1/auth`

| Method | Endpoint                   | Description                      |
| ------ | -------------------------- | -------------------------------- |
| POST   | `/register`                | User registration                |
| POST   | `/login`                   | Login using email + password     |
| POST   | `/logout`                  | Logout (clears refresh token)    |
| POST   | `/refresh-token`           | Get new access token via refresh |
| GET    | `/check-status`            | Basic system health              |
| GET    | `/check-auth`              | Check if access token is valid   |
| POST   | `/check-password`          | Verify password (before update)  |
| PATCH  | `/update-password`         | Change user password             |
| POST   | `/password-change-request` | Request password reset (email)   |
| POST   | `/verify-otp-token`        | OTP or token verification        |
| POST   | `/password-reset`          | Reset password (OTP/token-based) |

---

### 🧠 Token Structure

* **Access Token:** JWT, short-lived, used for authorization
* **Refresh Token:** Long-lived, saved in DB, used to renew access

---

### 🔒 Middleware

* `authGuard` — protects private routes
* `optionalAuth` — allows anonymous access if no token present

---

### 🔁 Token Rotation

1. Login issues access + refresh token
2. Refresh endpoint rotates refresh token in DB
3. Old refresh token becomes invalid

---

### 🔐 OTP Support

If `USE_OTP=true`, OTP-based password reset is enabled:

* OTP sent to email
* User verifies OTP via `/verify-otp-token`
* New password is submitted via `/password-reset`

---

> The auth module provides the full authentication flow with support for refresh tokens, OTP, and middleware-based protection.