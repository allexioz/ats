# Swarm ATS — project notes

A minimal, Vercel/Geist-inspired applicant tracker for Swarm's internship hiring.
Single self-contained static page — no build step, no framework.

## Files
- **`index.html` — the canonical file. Make all changes here.**
- `swarm-ats.html` — older duplicate, now stale. Ignore unless asked to re-sync.
- `resumes/` — candidate résumé PDFs (exact email-attachment filenames). The in-app
  viewer loads these by relative path.
- `README.md` — public-facing readme for the GitHub repo.

## Data
Candidates are sourced from the Gmail **`Applicants`** label and embedded as the
`CANDIDATES` array in `index.html` (no live API). Each candidate object carries:
`name, email, applied, status, appliedRole, highlight, school, schoolName, year,
role, aiTools[], skills[], pitch, note, resumeFile, links[], thread[]`.
Status changes persist per-browser via `localStorage`; they are not written back to Gmail.

## Roles being hired (two distinct posts)
1. **Software Engineering Intern** (Aaron & Alexis). Hiring signal: *judgment over
   output*, showing your thinking (what broke / what you changed / why), and learning
   velocity. Default role for applicants.
2. **Design Engineer Intern** (Alexis, growth team). Hiring signal: *craft excellence
   ("your work carries your name")*, taste, curiosity, a builder's instinct, learning
   velocity. Work spans landing pages, campaigns, AI demos, design systems, and growth.

A candidate's role is `appliedRole`; if absent it defaults to "Software Engineering Intern".
- **John Yumul → Design Engineer Intern** (design/product/growth background).
- All other current applicants → Software Engineering Intern.

## Features
- Full-width sortable table: Candidate, Role, Education, Main selling point, Portfolio,
  Applied, Status. Click a column header to sort (carets show direction).
- Filters: search, role, status. Stats cards up top.
- Badges: year level, "Ivy League" (Ateneo / DLSU / UBC), and a role pill
  (SWE = blue, Design = purple).
- Stripe-style centered popover per candidate: quick actions (View résumé, Portfolio,
  Email thread), details, AI tooling, key skills, links, summary, and the full email thread.
- In-app fullscreen PDF résumé viewer (reads from `resumes/`).
- Light/dark theme. Password gate (password: `sw@rm2026`, SHA-256 checked client-side —
  cosmetic only; use Vercel password protection for real auth, especially since résumés
  contain PII).

## Deploy
Pushed to **github.com/allexioz/ats** (`main`). Static site — import the repo at
vercel.com/new and it deploys with zero config; every push redeploys.
Keep the repo **private** because the résumé PDFs contain candidate phone numbers/emails.

## Conventions
- Edit `index.html` directly; validate JS with `node --check` on the extracted `<script>`.
- Keep the design restrained (Geist/Vercel: subtle borders, minimal color, system font).
- Don't fabricate candidate facts — everything in the data traces to their email or résumé.
