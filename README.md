# Placement_management_System
# Placement Management System

A complete full-stack web application for college placement cells — managing students, recruiters, job postings, applications, interviews, notifications, and placement analytics with role-based access for **Admin**, **Placement Officer**, and **Student**.

## 🚀 Demo Accounts

| Role | Email | Password |
|------|-------|----------|
| Admin | admin@college.edu | admin123 |
| Placement Officer | officer@college.edu | officer123 |
| Student | aarav.sharma@student.edu | student123 |

## ✨ Features

- **Auth & RBAC** — secure login/registration, hashed passwords, signed tokens, protected routes
- **Admin dashboard** — total students, companies, openings, applications, selections, placement %
- **Officer console** — review queue, post jobs, add companies, schedule interviews, shortlist/select
- **Student portal** — browse eligible jobs, one-click apply, track pipeline, interviews, resume upload
- **CRUD** — full create/read/update/delete for students, companies, jobs, applications, interviews, users
- **Search, filter & pagination** across all data tables
- **Reports & analytics** — funnel charts, monthly trends, department-wise & company-wise reports, CSV export
- **Notifications** — in-app bell with real-time updates on applications and interviews
- **Validation** — client + server: required fields, email/phone/CGPA formats, unique emails, eligibility checks
- **Responsive UI** — sidebar + topbar, cards, charts, modals, confirm dialogs, toasts, loading states

## 🛠 Tech Stack

- **Frontend:** React 19 + TypeScript + Tailwind CSS v4 + React Router + Framer Motion + Lucide icons
- **Backend:** Vercel serverless functions (Node.js) exposing REST APIs with JSON
- **Database:** Supabase (Postgres) — tables: `users`, `students`, `companies`, `jobs`, `applications`, `interviews`, `notifications`
- **Storage:** Supabase Storage bucket `resumes` for student resume uploads

## 📁 Project Structure

```
api/                  # REST API routes (serverless)
  auth.js             # login, register, session verify
  users.js            # user CRUD (admin)
  students.js         # student CRUD + search/filter
  companies.js        # company CRUD
  jobs.js             # job CRUD + applicant counts
  applications.js     # apply, status workflow, eligibility
  interviews.js       # scheduling + results
  notifications.js    # in-app notifications
  reports.js          # dashboard + analytics aggregates
  upload.js           # resume upload to Supabase Storage
  db-client.js        # shared Supabase service client
src/
  components/         # Layout, Charts, StatCard, UI kit, Toast
  contexts/           # AuthContext (token session)
  lib/                # api client, validators, formatters
  pages/              # Home, Login, Register, dashboards,
                      # Students, Companies, Jobs, Applications,
                      # Interviews, Reports, Users, Profile
```

## 🔌 REST API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | /api/auth `{"action":"login"}` | Login, returns token + user |
| POST | /api/auth `{"action":"register"}` | Student registration |
| GET | /api/auth | Verify token → current user |
| GET/POST/PUT/DELETE | /api/users | User management |
| GET/POST/PUT/DELETE | /api/students | Student records (search, dept, year, status, paging) |
| GET/POST/PUT/DELETE | /api/companies | Companies (+ open job counts) |
| GET/POST/PUT/DELETE | /api/jobs | Jobs (+ company, applicant counts) |
| GET/POST/PUT/DELETE | /api/applications | Apply, shortlist/select/reject, tracking |
| GET/POST/PUT/DELETE | /api/interviews | Schedule interviews, mark results |
| GET/POST/PUT/DELETE | /api/notifications | Notify + read state |
| GET | /api/reports | Totals, funnel, dept/company-wise, monthly trends |
| POST | /api/upload | Resume upload (base64 → public URL) |

## 🧪 Validation Rules

- Required fields enforced on client and server
- Email format checked; duplicate emails rejected (409)
- Phone: 7–15 digits/`+ -` spaces
- CGPA: numeric 0–10
- Job apply: job must be open; CGPA ≥ min_cgpa; department must match; no duplicate applications

## ⚙️ Setup

```bash
npm install
npm run build
```

Deploy to Vercel — the `api/` directory is auto-wired as serverless functions and Supabase env vars are pre-configured.

## 📊 Sample Data

Seeded with 15 users (1 admin, 2 officers, 12 students), 16 student profiles, 8 companies, 12 jobs, 38 applications across 6 months, 10 interviews, and 8 notifications — so dashboards, charts, and reports render immediately.
