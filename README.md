# laxport
# Online Quiz Application

A beginner-friendly full-stack quiz app using Node.js, Express, and MongoDB.

## Features
- User registration/login with bcrypt + JWT
- Session handling with `express-session` + MongoDB store
- Timed quizzes with auto-submit
- Score calculation and results history
- Admin dashboard for managing questions and viewing scores
- Security: Helmet, CORS, rate limiting, validation, and NoSQL injection protection

## Folder Structure
```
.
├─ config/
│  └─ db.js
├─ middleware/
│  ├─ auth.js
│  └─ validate.js
├─ models/
│  ├─ Question.js
│  ├─ Result.js
│  └─ User.js
├─ public/
│  ├─ css/
│  │  └─ styles.css
│  ├─ js/
│  │  ├─ admin.js
│  │  ├─ login.js
│  │  ├─ quiz.js
│  │  ├─ register.js
│  │  └─ results.js
│  ├─ admin.html
│  ├─ index.html
│  ├─ login.html
│  ├─ quiz.html
│  ├─ register.html
│  └─ results.html
├─ routes/
│  ├─ admin.js
│  ├─ auth.js
│  ├─ quiz.js
│  └─ results.js
├─ .env.example
├─ package.json
└─ server.js
```

## Getting Started (VS Code)
1. Open the project folder in VS Code.
2. Create a `.env` file by copying `.env.example` and updating values.
3. Install dependencies:
   ```bash
   npm install
   ```
4. Start MongoDB locally, or update `MONGO_URI` to a hosted MongoDB instance.
5. Run the server:
   ```bash
   npm run dev
   ```
6. Open `http://localhost:3000` in your browser.

## Admin Setup
By default, all registrations are regular users. To create an admin:
- Open MongoDB and update a user’s `role` to `admin`.
- Example MongoDB shell command:
  ```js
  use quizapp
  db.users.updateOne({ email: "admin@example.com" }, { $set: { role: "admin" } })
  ```
Then log in with that user and open `/admin.html`.

## API Routes
- `POST /auth/register`
- `POST /auth/login`
- `POST /auth/logout`
- `GET /quiz/start`
- `POST /quiz/submit`
- `GET /admin/questions`
- `POST /admin/questions`
- `PUT /admin/questions/:id`
- `DELETE /admin/questions/:id`
- `GET /results`

## Production Notes
- Set strong `JWT_SECRET` and `SESSION_SECRET`.
- Set `NODE_ENV=production` to enable secure cookies.
- Consider configuring `CORS` to your real frontend domain.
- Add HTTPS and a persistent session store for production.
