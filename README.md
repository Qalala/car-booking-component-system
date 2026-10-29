# Car Booking Component System

## Brief description
A component-based full-stack web app for browsing car models, booking test drives, and managing user accounts and feedback.

## Project purpose
Practice component-based development with a NestJS API, MongoDB persistence, and a React + Vite + Tailwind client.

## Project requirements
- Node.js 18+ and npm
- MongoDB running locally (or an Atlas URI)
- Free ports for the API and Vite dev server

## How to navigate
- `backend/` — NestJS API (auth, cars, bookings, feedback)
- `frontend/` — React + Vite + Tailwind UI
- `backend/.env.example` — environment template

## How to run
### 1) Backend
```bash
cd backend
copy .env.example .env
npm install
npm run start:dev
```

### 2) Frontend
```bash
cd frontend
npm install
npm run dev
```

Open the Vite URL shown in the terminal (typically `http://localhost:5173`).