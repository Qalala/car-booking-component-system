# Car Booking Component System

A component-based full-stack web application for browsing car models, comparing vehicles, booking **test drives**, submitting feedback, and managing authenticated user accounts.

The stack is:
- **Backend**: NestJS + TypeScript + MongoDB (Mongoose) + JWT
- **Frontend**: React + Vite + Tailwind CSS + Axios

This project focuses on clean module boundaries (cars, users, bookings, feedback) rather than a single monolithic script.

## Tech stack
- NestJS
- TypeScript
- MongoDB / Mongoose
- JWT authentication
- React
- Vite
- Tailwind CSS
- Axios

## Architecture (high level)

```
car-booking-component-system/
├─ backend/                         [NestJS API]
│  ├─ src/
│  │  ├─ main.ts
│  │  ├─ app.module.ts
│  │  ├─ user/                      [register/login + JWT strategy]
│  │  ├─ car/                       [car catalog CRUD/query]
│  │  ├─ book-test-drive/           [test-drive bookings]
│  │  └─ feedback/                  [user feedback]
│  ├─ .env.example
│  └─ package.json
└─ frontend/                        [React client]
   ├─ src/
   │  ├─ pages/
   │  │  ├─ Login.jsx / Signup.jsx
   │  │  ├─ CarList.jsx / CarDetail.jsx / CompareCars.jsx
   │  │  ├─ Booking.jsx
   │  │  └─ Feedback.jsx
   │  ├─ components/                [Navbar, ProtectedRoute, ...]
   │  └─ contexts/AuthContext.jsx
   └─ package.json
```

### Backend modules
- **user** — account creation/login, password hashing, JWT issuance/validation (`passport-jwt`)
- **car** — vehicle records used by listing/detail/compare screens
- **book-test-drive** — booking requests tied to users/cars
- **feedback** — user feedback submissions

### Frontend flows
- Public browsing of cars
- Auth-gated actions via `ProtectedRoute` + `AuthContext`
- Booking a test drive
- Submitting feedback
- Optional compare-cars view for side-by-side inspection

### Auth model
1. User signs up / logs in through the React UI
2. Backend validates credentials and returns a JWT
3. Frontend stores/sends the token on protected API calls
4. NestJS JWT strategy guards protected routes

---

## Running the project

### Prerequisites
- Node.js 18+ and npm
- MongoDB running locally **or** a MongoDB Atlas URI
- Free ports for API + Vite (commonly API `3000`, Vite `5173` — confirm in your env/config)

### 1) Backend setup

```bash
cd backend
copy .env.example .env
```

Edit `.env`:

```env
DB=mongodb://localhost:27017/car_booking
CARS_DB=mongodb://localhost:27017/car_booking
PORT=3000
JWT_SECRET=change_me_to_a_long_random_string
```

Then:

```bash
npm install
npm run start:dev
```

### 2) Frontend setup

```bash
cd frontend
npm install
npm run dev
```

Open the Vite URL printed in the terminal (typically `http://localhost:5173`).

---

## How to navigate the repo
- Backend business logic: `backend/src/<module>/`
- API bootstrap: `backend/src/main.ts`, `app.module.ts`
- UI pages: `frontend/src/pages/`
- Auth wiring: `frontend/src/contexts/AuthContext.jsx` + `ProtectedRoute.jsx`
- Env template: `backend/.env.example`

---

## Demo walkthrough
1. Start MongoDB.
2. Start backend (`npm run start:dev`) and frontend (`npm run dev`).
3. Open the web app and create an account.
4. Browse the car list and open a car detail page.
5. Book a test drive.
6. Submit feedback.
7. (Optional) Use compare-cars to inspect multiple models.

### Notes / limitations
- `.env` is gitignored — always copy from `.env.example`
- `node_modules` and upload artifacts are excluded
- Seed/sample car data depends on what is already in your MongoDB; insert documents if lists are empty

---

## Project purpose
Practice component-based full-stack development: modular NestJS services, JWT auth, and a React client for browsing cars and managing test-drive bookings/feedback.
