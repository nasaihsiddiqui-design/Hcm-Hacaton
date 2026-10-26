# HCM Lite (Next.js)
**Stack:** Next.js 14 (App Router, API routes) · SQLite (better-sqlite3) · JWT + bcrypt · any OpenAI-compatible LLM API.

## Run
1. `npm install`
2. Edit `.env` (already pre-set for Gemini): paste your key in `AI_API_KEY=` (get one free at https://aistudio.google.com/apikey). Never commit `.env`.
3. `npm run dev` → http://localhost:3000
4. First visit shows **first-run setup**: company + Admin account. Database starts empty (no dummy data).

## Flow
Admin → Settings, creates HR login → HR registers employees (temp password shown once, must change on first login) → Employee checks in, applies leave (or types it in plain words) → HR approves, runs payroll draft → Admin finalizes (locks month) → Admin sees audit log.

## Done
Auth + 3 roles with server-side role/scope checks · setup · settings · HR users · employees (search/paging) · check-in/out (server time, late/half-day rules, 409 on duplicate) · leave (working days, holidays, quota, overlap = 422, approval) · payroll (gross 1.5×basic, absent/unpaid/half-day deductions, tax slab, finalize lock) · dashboards · announcements · audit log · AI chat with tools (scoped by role), dashboard summary, smart leave, policy Q&A, 20/hour limit, 15s timeout, ai_logs.

## Not done (next steps)
Departments/designations/leave-type CRUD screens · CSV import/export · attendance corrections · payslip PDF · date/department filters & charts · notifications · camera attendance · tests.
Note: SQLite needs a persistent disk; for Vercel-style hosting swap `lib/db.js` for Postgres/Mongo, or deploy on Render/Railway with a disk.
