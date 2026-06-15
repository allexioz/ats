# Swarm · Applicant Tracker

A minimal, Vercel-inspired ATS for the Software Engineering Intern role.
Static single-page app (`index.html`) that lists candidates labeled **Applicants**
in Gmail, with status pipeline, main selling point, portfolio column,
Ivy League flag, a Stripe-style candidate popover, and the full email thread.

## Deploy
Zero-config static site. Import this repo at [vercel.com/new](https://vercel.com/new)
and Vercel will deploy `index.html` automatically on every push.

## Local preview
Open `index.html` in a browser, or run `npx serve`.

## Resumes
Résumé links open the original Gmail message. To view PDFs inline instead,
drop the attachments into `resumes/` keeping their exact filenames.
