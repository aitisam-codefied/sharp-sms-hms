# Setup

## ⚙️ Installation & Setup

Follow these steps to run SharpHMS locally or on a development server.

---

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/your-org/sharp-hms.git
cd sharp-hms
```

---

### 2️⃣ Install Dependencies

Using npm (preferred):

```bash
npm install
```

---

### 3️⃣ Configure Environment Variables

Copy and rename the example file:

```bash
cp .env.example .env
```

Edit `.env` and provide required values:

```env
PORT=your-port-number
USE_OTP=true
NODE_ENV=your-environment-name
APP_NAME=your-app-name
EMAIL_SENDER=your-email-address
SMTP_USER=your-smtp-user
SMTP_PASS=your-smtp-pass
SMTP_HOST=your-smtp-host
SMTP_PORT=your-smtp-port
FRONTEND_ORIGIN=your-frontend-origin
SOCKET_ORIGIN=your-socket-origin
API_ORIGIN=your-api-url
JWT_SECRET=your-jwt-secret
REFRESH_SECRET=your-refresh-secret
EMAIL_TOKEN_SECRET=your-email-token-secret
PASSWORD_RESET_SECRET=your-password-reset-secret
SESSION_SECRET=your-session-secret
DATABASE_URI=your-mongodb-uri
```

See full reference in [`env.md`](env.md).

---

### 4️⃣ Run the Server

```bash
npm dev
```

You should see:

```bash
🚀 Server running in development environment on port 5001
🔗 MongoDB connected...
```

---

### 5️⃣ Seed Initial Data

```bash
node seeders/init.seed.js       # Super Admin, Roles, Permissions
node seeders/tenant.seed.js     # Demo Tenant + Admin
```

To truncate database:

```bash
node seeders/truncate.seed.js   # ⚠️ Use with caution
```

---

### ✅ Ready to Use

* Base URL: `http://localhost:5001/api/v1`
* Frontend Origin: `http://localhost:5174`

> Your API and client should now be connected and ready for development.