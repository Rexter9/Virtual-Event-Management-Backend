# 🎯 Virtual Event Management Backend

A RESTful API backend for managing virtual events, built with **Node.js** and **Express.js**. Supports user authentication, event creation, registration, and management.

---

## 👤 Author

**Mohd Faiz**

---

## 🛠️ Tech Stack

- **Runtime:** Node.js
- **Framework:** Express.js
- **Authentication:** JSON Web Token (JWT)
- **Password Hashing:** bcrypt
- **Email:** Nodemailer
- **Environment Variables:** dotenv
- **Dev Tool:** Nodemon

---

## 📁 Project Structure

```
virtual-event-backend-main/
├── controllers/
│   ├── authController.js      # Register & Login logic
│   └── eventController.js     # Event CRUD logic
├── middleware/
│   └── authMiddleware.js      # JWT token verification
├── routes/
│   ├── authRoutes.js          # Auth endpoints
│   └── eventRoutes.js         # Event endpoints
├── data/
│   └── store.js               # In-memory data store
├── utils/
│   └── sendEmail.js           # Email utility
├── .env                       # Environment variables
├── server.js                  # Entry point
└── package.json
```

---

## ⚙️ Installation & Setup

### Prerequisites
- [Node.js](https://nodejs.org/) installed on your machine
- [Postman](https://www.postman.com/downloads/) (for API testing)

### Steps

**1. Clone the repository**
```bash
git clone https://github.com/Rexter9/Virtual-Event-Management-Backend.git
cd virtual-event-backend-main
```

**2. Install dependencies**
```bash
npm install
```

**3. Configure environment variables**

The `.env` file is already included with:
```
JWT_SECRET=mysecretkey
```
You can change the secret key to any strong random string.

**4. Run the server**

Development mode (auto-restart on file changes):
```bash
npm run dev
```

Production mode:
```bash
npm start
```

**5. Server is running at:**
```
http://localhost:3000
```

---

## 🔌 API Endpoints

### 🔐 Auth Routes

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/api/register` | Register a new user | ❌ No |
| POST | `/api/login` | Login and get JWT token | ❌ No |

### 📅 Event Routes

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/api/events` | Get all events | ✅ Yes |
| POST | `/api/events` | Create a new event | ✅ Yes |
| PUT | `/api/events/:id` | Update an event | ✅ Yes |
| DELETE | `/api/events/:id` | Delete an event | ✅ Yes |
| POST | `/api/events/:id/register` | Register for an event | ✅ Yes |

---

## 🧪 Testing with Postman

### Step 1 — Register a User
```
POST http://localhost:3000/api/register
```
**Body (JSON):**
```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "123456"
}
```

### Step 2 — Login
```
POST http://localhost:3000/api/login
```
**Body (JSON):**
```json
{
  "email": "john@example.com",
  "password": "123456"
}
```
> 📌 Copy the **token** from the response — you'll need it for protected routes.

### Step 3 — Use Token for Protected Routes

In Postman, go to the **Authorization** tab → Select **Bearer Token** → Paste your token.

**Example — Create Event:**
```
POST http://localhost:3000/api/events
```
**Body (JSON):**
```json
{
  "title": "Tech Conference 2025",
  "description": "A virtual tech conference",
  "date": "2025-06-15",
  "location": "Online"
}
```

---

## 📝 Notes

- This project uses **in-memory storage** — data will reset when the server restarts.
- JWT tokens expire based on the configured secret — keep `JWT_SECRET` private in production.
- For email features, add your SMTP credentials to the `.env` file.

---

## 📄 License

This project is licensed under the **ISC License**.
