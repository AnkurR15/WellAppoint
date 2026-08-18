# WellAppoint 🏥

A full-stack **Hospital Management System** for booking and managing patient appointments, built as an Nx monorepo with a React public website, a React admin dashboard, and a NestJS REST API.

> Group project by a team of three developers.

## ✨ Features

- **Public website** (`web`) — landing page, services, about, contact and patient login
- **Admin dashboard** (`dashboard`) — secure admin panel with role-based access (Admin / Receptionist / Doctor)
- **Appointment booking** — book, view, edit and delete patient appointments
- **Doctors & team management** — manage users, specialties and roles
- **Interactive calendar** — view and schedule events on a full-featured calendar
- **Analytics** — bar, line, pie and progress charts for appointments & specializations
- **Authentication** — JWT-based login with protected routes

## 🧱 Tech Stack

| Layer | Technology |
| ----- | ---------- |
| Monorepo | Nx |
| Frontend | React 18, Vite, MUI, FullCalendar, Chart.js / Nivo |
| Backend | NestJS 10 |
| Database | PostgreSQL + Prisma ORM |
| Auth | Passport + JWT |

## 📦 Project Structure

```
apps/
├── web/          # Public-facing website (Vite + React)
├── dashboard/    # Admin dashboard (Vite + React + MUI)
├── api/          # REST API (NestJS)
├── web-e2e/      # Cypress E2E tests for web
├── dashboard-e2e # Cypress E2E tests for dashboard
└── api-e2e/      # E2E tests for API
prisma/           # Prisma schema & migrations
```

## 🚀 Getting Started

### Prerequisites

- Node.js 18+
- PostgreSQL running locally
- npm or pnpm

### 1. Install dependencies

```bash
npm install
```

### 2. Configure environment

Create a `.env` file in the project root:

```env
DATABASE_URL="postgresql://postgres:yourpassword@localhost:5432/wellappoint?schema=public"
JWT_SECRET="your-secret"
```

> `.env` is git-ignored. Never commit real credentials.

### 3. Set up the database

```bash
npx prisma migrate dev --name init
```

### 4. Run the apps

Open three terminals:

```bash
nx serve api        # REST API on http://localhost:3000
nx serve web        # Public website on http://localhost:4200
nx serve dashboard  # Admin dashboard on http://localhost:4201
```

## 🛠 Build

```bash
nx build api        # dist/apps/api
nx build web        # dist/apps/web
nx build dashboard  # dist/apps/dashboard
```

## 🧪 Test & Lint

```bash
nx test api
nx lint web
```

## 🔌 API Overview

| Module | Endpoints |
| ------ | --------- |
| Auth | `POST /auth/login`, `POST /auth/create-user`, `GET/PATCH/DELETE /auth/*` |
| Users | `GET /users` |
| Appointment | `GET /appointment/:specialization`, `POST /appointment/create`, `GET/PATCH/DELETE /appointment/*` |
| Calendar | `GET /calendar`, `POST /calendar/create`, `DELETE /calendar/delete/:id` |
| Charts | `GET /pie`, `GET /lchart`, `GET /lchart/specializations`, `GET /lchart/gender-count` |

## ☁️ Deployment

- **API** — build with `nx build api`, run `node dist/apps/api/main.js` (set `PORT`, `DATABASE_URL`, `JWT_SECRET`). Any Node host works (Render, Railway, Fly.io).
- **Frontends** — static builds in `dist/apps/web` and `dist/apps/dashboard`; deploy to Vercel, Netlify or any static host.
- **Database** — PostgreSQL (Supabase, Neon, Render) with `npx prisma migrate deploy` on first deploy.
- Frontends must point at the deployed API URL via a `VITE_API_URL` environment variable.

## 👥 Team

- [MandavkarPranjal](https://github.com/MandavkarPranjal)
- [AnkurR15](https://github.com/AnkurR15)
- [MithilMestry](https://github.com/MithilMestry)

## 📄 License

MIT