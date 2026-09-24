# ITEP Timetable Builder — Autumn 2026

A single-page, self-contained web app that lets ITEP students pick a Major, Semester, optional Minor, and (for Semesters 4/5/6) a Pedagogy Paper, then generates a personalized weekly timetable they can view, manually adjust, and download as a JPG.

**Live demo:** _add your GitHub Pages link here once deployed_

## Features

- **Major / Semester / Minor / Pedagogy Paper selection** — dropdowns build a personalized grid from the stored course data.
- **Semesters 1–8** supported (data for Semesters 2, 4, 6, 8 to be added as it becomes available).
- **Color-coded course blocks** — orange for Major, pink for Minor, purple for Pedagogy Paper.
- **Click-to-edit** — click any class block to shift it to a different day/time, or delete just that one weekly meeting (handy for one-off extra hours or cancelled sessions), without affecting the rest of the course.
- **Reset any manual shifts** — reverts back to the official schedule in one click.
- **Download as JPG** — includes an optional student name field that gets stamped onto the image before export.
- **Admin panel** (password-protected in the UI, not a real security boundary — see note below) for editing course data per department/semester, marking a course as Major/Minor/Pedagogy, manually shifting classes, and exporting/importing the full dataset as JSON.

## Tech

Plain HTML, CSS, and vanilla JavaScript. No build step, no dependencies to install.

- [html2canvas](https://html2canvas.hertzen.com/) (loaded via CDN) — powers the "Download as JPG" feature.
- Data is stored in the browser via `localStorage`, seeded from factory-default data baked into the page.

## Running locally

No server or build tools required — just open the file in a browser:

```bash
open index.html      # macOS
start index.html      # Windows
xdg-open index.html   # Linux
```

Or serve it locally if you prefer:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploying with GitHub Pages

1. Push this repo to GitHub.
2. Go to **Settings → Pages**.
3. Under **Build and deployment → Source**, choose **Deploy from a branch**, set **Branch** to `main` and folder to `/ (root)`, then **Save**.
4. Your site will be live at `https://<your-username>.github.io/<repo-name>/` within about a minute.

## Updating course data

Two ways to add or change course data:

1. **Through the app** — open the Admin Panel (password-protected), pick a Department and Semester, edit rows or add new courses, tick Major/Minor/Pedagogy as needed, and click **Save changes**. Use **Export all data (JSON)** to back up your edits, and **Import data (JSON)** to load them on another device or share with someone else.
2. **Editing the source** — the factory-default data lives inline in `index.html` inside the `DATA` object. Editing it there changes what every visitor sees by default (Admin Panel edits are saved per-browser via `localStorage` and won't affect other visitors until re-imported).
