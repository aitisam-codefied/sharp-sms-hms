# ENV

```env
# Server Configuration
PORT=your-port-number
NODE_ENV=your-environment-name
APP_NAME=your-app-name

# Email Configuration
EMAIL_SENDER=your-sender-address
SMTP_USER=your-smtp-user
SMTP_PASS=your-smtp-password
SMTP_HOST=your-smtp-host
SMTP_PORT=your-smtp-port

# OTP Support
USE_OTP=true

# Frontend & API Origins
FRONTEND_ORIGIN=your-frontend-origin
SOCKET_ORIGIN=your-socket-origin
API_ORIGIN=your-api-base-url

# Authentication Secrets
JWT_SECRET=your-jwt-secret
REFRESH_SECRET=your-refresh-secret
EMAIL_TOKEN_SECRET=your-email-token-secret
PASSWORD_RESET_SECRET=your-password-reset-secret
SESSION_SECRET=your-session-secret

# Database
DATABASE_URI=your-mongodb-uri
```

---

### 📌 Notes

* `USE_OTP` must remain `true` to enable OTP/password-reset logic.
* Replace all `your-...` placeholders with actual values.
* Never commit `.env` to Git.
* Use `.env.production`, `.env.staging`, or `.env.test` for respective environments.

> This file is referenced in [Installation & Setup](setup.md) and is critical for app launch.