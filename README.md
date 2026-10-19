# StudentMart

React (Vite) frontend + Express / MongoDB backend with JWT login.

```
react/
├── server/                 # backend
│   ├── middleware/auth.js  # JWT check
│   ├── models/Student.js   # Mongoose schema
│   ├── routes/auth.js      # register + login
│   ├── routes/student.js   # get/update profile, change password
│   ├── .env
│   ├── package.json
│   └── server.js
└── studentmart/            # frontend
    ├── index.html
    ├── vite.config.js
    └── src/
        ├── App.jsx  App.css  index.css  main.jsx
        └── components/
            ├── Login.jsx  Register.jsx  Dashboard.jsx
            ├── profile.jsx   # "Your Profile" page
            ├── edit.jsx      # Personal info + Change password forms
            └── Logout.jsx    # logout button
```

## Run it

You need Node.js 18+ and MongoDB (local install, or a free MongoDB Atlas cluster).

**1. Backend**
```bash
cd server
npm install
# edit .env: set MONGO_URI (Atlas string or local) and a JWT_SECRET
npm run dev          # http://localhost:5000
```

**2. Frontend** (new terminal)
```bash
cd studentmart
npm install
npm run dev          # http://localhost:5173
```

Open http://localhost:5173 → **Create Account** → you land on the Dashboard → **Edit Profile** to fill in name, phone, college, course and year, or change your password.

## API

| Method | Route | Auth | Body |
|---|---|---|---|
| POST | /api/auth/register | – | usn, email, password |
| POST | /api/auth/login | – | email, password |
| GET | /api/student/me | Bearer token | – |
| PUT | /api/student/me | Bearer token | usn, name, email, phone, college, course, year |
| PUT | /api/student/change-password | Bearer token | currentPassword, newPassword |

If the backend runs on a different port, change `API_URL` at the top of `src/App.jsx`.
