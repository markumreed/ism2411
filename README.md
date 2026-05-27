# ISM2411 — Python for Business

Course website for **ISM2411: Python for Business**, USF Muma College of Business.

A static, multi-page site built for GitHub Pages. No build step required for visitors — every page is plain HTML + one shared CSS + one shared JS file.

[**View the live site →**](#deploy-to-github-pages)

---

## Repository layout

```
ism2411/
├── index.html                 ← course hub (landing page)
├── 404.html                   ← fallback for missing pages
├── robots.txt
├── sitemap.xml
├── .nojekyll                  ← tells GH Pages: don't run Jekyll
├── README.md                  ← (you are here)
├── LICENSE                    ← MIT
├── .gitignore
│
├── assets/
│   ├── css/
│   │   └── site.css           ← shared theme, nav, layout
│   └── js/
│       └── site.js            ← nav injection, dark/light toggle, font controls
│
└── pages/                     ← every page that isn't the landing page
    ├── syllabus.html
    ├── ai_policy.html
    ├── datacamp.html
    ├── precourse.html
    │
    ├── unit_1_overview.html   …  unit_5_overview.html
    ├── unit_all_overview.html
    ├── unit_1_cheatsheet.html …  unit_4_cheatsheet.html
    │
    ├── week01_reading.html    week01_lecture.html    week01_lab.html
    ├── week02_reading.html    week02_lecture.html    week02_lab.html
    │   …
    ├── week08_reading.html    week08_lecture.html    week08_lab.html
    ├── week09_midterm.html
    ├── week10_reading.html    week10_lecture.html    week10_lab.html
    │   …
    ├── week15_reading.html    week15_lecture.html    week15_lab.html
    ├── week16_capstone.html
    └── capstone_rubric.html
```

**63 HTML pages total.** No build pipeline, no Node modules, no compilation.

## Course structure

| Unit | Weeks | Focus |
|------|-------|-------|
| 1 — Foundations | W1–5 | What is a computer, command line, variables, operators, conditionals |
| 2 — Control Flow & Structure | W6–8 | Loops, functions+debugging+AI literacy, Git/GitHub |
| Midterm | W9 | Closed-resource exam covering Units 1–2 |
| 3 — Data Structures | W10–12 | Lists/tuples, dictionaries, files & CSVs |
| 4 — Data Analysis with pandas | W13–15 | DataFrames, cleaning, grouping, visualization |
| 5 — Capstone | W16 | Retail sales analysis + presentations |

## Grading

| Component | Weight |
|-----------|-------:|
| Weekly labs & quizzes | 35% |
| DataCamp courses (8 required) | 15% |
| Midterm exam | 20% |
| Capstone project | 25% |
| Participation | 5% |

## Features

- **Dark / light theme toggle** — top-right nav, preference saved to `localStorage`
- **Font-size controls** — A− / A+ buttons in the nav
- **Sticky navigation** — dropdown menus per unit, every week linked
- **Skip-to-content link** for keyboard accessibility
- **Color-coded units** — green (U1), blue (U2), purple (U3), gold (U4), pink (U5)
- **Inline self-check quizzes** at the bottom of each reading — marked ★ Midterm-Eligible (W1–8) or ★ Capstone-Eligible (W10–15)
- **Quick-jump bar** between reading / lecture / lab on every weekly page
- **No tracking, no analytics, no external dependencies** — single CSS + JS file, served from the same origin

## Deploy to GitHub Pages

### Option 1 — Default branch / root folder (recommended)

1. Create a new GitHub repository (e.g. `ism2411`)
2. Push the contents of this folder to the `main` branch (not the `ism2411/` folder itself — its contents)
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/ism2411.git
   git push -u origin main
   ```
3. On GitHub: **Settings → Pages**
   - Source: **Deploy from a branch**
   - Branch: **main** / **/ (root)**
   - Click **Save**
4. Wait 30–60 seconds. Your site is live at `https://YOUR-USERNAME.github.io/ism2411/`

### Option 2 — User/organization site

If the repo is named `YOUR-USERNAME.github.io`, the site publishes to `https://YOUR-USERNAME.github.io/` (no subfolder). Same steps as above.

### Option 3 — Custom domain

1. Add a file named `CNAME` to the repo root containing only your domain (e.g. `ism2411.usf.edu`)
2. In your DNS provider, create a `CNAME` record pointing your domain to `YOUR-USERNAME.github.io`
3. On GitHub: **Settings → Pages → Custom domain** — enter the domain, click **Save**, then check **Enforce HTTPS** once the cert provisions

## Local preview

Any static server works. The simplest:

```bash
# Python 3 (built into Mac/Linux, easy to install on Windows)
python3 -m http.server 8000

# or Node.js
npx serve

# or PHP
php -S localhost:8000
```

Then open <http://localhost:8000> in your browser.

> **Why a server, not file://?** The shared JS file uses path detection that relies on the URL. Opening `index.html` directly via `file://` may cause nav links to break.

## Editing content

The site has no build pipeline — each HTML file is the final, served-as-is file. To edit a week's content, open the corresponding HTML file in `pages/` and edit it directly.

If you want to make bulk changes, the original generator scripts (Python) used to produce this site are not included in the repo. Direct HTML editing is the supported workflow for ongoing maintenance.

### Common edits

- **Change a week's quiz** — open `pages/weekNN_reading.html`, find the `<details>` blocks near the bottom
- **Update grading weights** — `pages/syllabus.html`, the grade table
- **Modify the AI policy** — `pages/ai_policy.html`
- **Add a new nav link** — `assets/js/site.js`, find the section building the dropdown menus
- **Adjust the color theme** — `assets/css/site.css`, the `:root` and `[data-theme="light"]` CSS variables

## Browser support

Tested in current Chrome, Firefox, Safari, and Edge. Uses CSS variables and ES6 — no support for IE11 or any browser more than ~5 years old.

## Accessibility

- Semantic HTML with proper heading hierarchy
- Skip-to-content link on every page
- Dark *and* light themes; system preference respected on first visit
- Adjustable font sizes via `localStorage`
- Color contrast meets WCAG AA at the standard font size
- Quiz answers are inside `<details>` elements (native screen-reader support)

## License

MIT. See [LICENSE](LICENSE).

## Credits

USF Muma College of Business. Site structure modeled after the ISM3232 course site.
