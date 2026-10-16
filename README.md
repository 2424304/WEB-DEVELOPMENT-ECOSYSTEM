# WDLE — Website Development Learning Ecosystem

> **A complete, structured, practical learning platform for web development — built by the Software Development Cell, Department of Computer Science, Dev Sanskriti Vishwavidyalaya (DSVV), Haridwar.**
>
> *Vision: every student of the Department of Computer Science should be able to design, develop, and deploy a professional website.*

---

## Table of Contents

- [What is WDLE?](#what-is-wdle)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Quick Start](#quick-start)
- [Project Structure](#project-structure)
- [Available Scripts](#available-scripts)
- [Learning Content](#learning-content)
- [Documentation](#documentation)
- [Local Installation](#local-installation)
- [Production Build](#production-build)
- [Deployment](#deployment)
- [Contributing](#contributing)
- [License](#license)
- [Credits and References](#credits-and-references)
- [Disclaimer](#disclaimer)

---

## What is WDLE?

WDLE is a free, open, browser-based learning ecosystem that takes Computer Science students from absolute beginner level to the ability to design, code, test, deploy, and present professional websites.

The platform brings together a structured learning roadmap, a 20-chapter handbook, interactive tutorials, a projects library with rubrics, a daily practice lab, a templates library, a complete deployment handbook, a Git/GitHub guide, a curated resource hub, an assessment system with MCQ quizzes and viva questions, and a faculty teaching guide.

It is designed as a reusable departmental learning resource for current and future batches.

## Features

- **Structured Learning Roadmap** with 14 modules (Internet fundamentals → HTML → CSS → Responsive → Flexbox → Grid → JavaScript → DOM → Forms → Git → GitHub → Deployment → Portfolio → React), each with objectives, prerequisites, topic lists, exercises, outcomes, common mistakes, knowledge-check questions, assignments, and completion checklists.
- **20-Chapter Handbook** covering every layer of modern web development with concepts, code examples, practice tasks, common errors, best practices, industry notes, interview questions, revision summaries, and references.
- **Interactive Tutorials** with code examples, copy-to-clipboard controls, knowledge check, and Previous/Next lesson navigation.
- **Projects Library** with 11 projects across beginner, intermediate, and advanced levels, each with a 100-point rubric covering functionality, design, responsiveness, code quality, accessibility, and documentation. Plus viva questions and extension ideas.
- **Practice Lab** with HTML, CSS, and JavaScript exercises (starter code, hints, reveal-when-ready solutions), plus 4 weekly mini-projects.
- **Templates Library** with 7 fully documented starter templates including complete source code, customisation guides, accessibility notes, and deployment instructions.
- **Complete Deployment Handbook** covering 22 sections from "what deployment means" through GitHub Pages, Vercel, Netlify, environment variables, custom domains, HTTPS, and troubleshooting.
- **Git & GitHub Guide** with installation, branching, merging, pull requests, conflict resolution, .gitignore, README best practices, GitHub Pages, team collaboration workflow, and a practical assignment.
- **Resource Hub** with HTML, CSS, JavaScript, Git, and tools references plus curated links to MDN, web.dev, React documentation, Vite, Vercel, Netlify, GitHub Docs, and more. Bookmarking supported.
- **Assessment System** with multiple-choice quizzes (auto-scored with explanations), practical assignments, and topic-wise viva questions with answers.
- **Faculty Teaching Guide** with proposed 12-week schedule, learning outcomes, classroom demonstration ideas, lab activities, assessment strategy, rubric usage, remedial learning recommendations, academic integrity, accessibility and inclusive teaching, and instructions for adding new content.
- **About & Credits** pages documenting vision, audience, methodology, and acknowledging all external resources.
- **Light/Dark Mode** with system-preference detection and toggle. Preference is saved to localStorage.
- **Global Search** across modules, chapters, projects, exercises, templates, resources, and quizzes.
- **Progress Tracking** for lessons, modules, exercises, quizzes, and bookmarks — all stored locally in the browser (no login required).
- **Fully Responsive** — works on mobile (360px), tablet (768px), and desktop (1280px+).
- **Accessible** — semantic HTML5, keyboard navigation, visible focus indicators, ARIA labels, WCAG AA color contrast.

## Tech Stack

- **React 18** — UI library
- **Vite 5** — build tool and dev server
- **JavaScript ES6+** — no TypeScript
- **React Router 6** — client-side routing
- **Lucide React** — consistent icons
- **localStorage** — progress tracking, bookmarks, theme preference
- **CSS3** — modular stylesheets, CSS custom properties, no CSS-in-JS

## Quick Start

```bash
# Clone the repository
git clone https://github.com/your-username/wdle.git
cd wdle

# Install dependencies
npm install

# Start the development server
npm run dev
```

The site will be available at http://localhost:5173/

## Project Structure

```
wdle/
├── public/
│   ├── assets/
│   │   └── dsvv-logo/
│   │       └── dsvv-logo.svg    # Placeholder logo - replace with official DSVV logo
│   └── favicon.svg
├── src/
│   ├── components/              # Reusable UI components
│   │   ├── Badge.jsx
│   │   ├── Breadcrumb.jsx
│   │   ├── CodeBlock.jsx
│   │   ├── Footer.jsx
│   │   ├── Navbar.jsx
│   │   ├── ProgressBar.jsx
│   │   └── ScrollToTop.jsx
│   ├── contexts/
│   │   └── ThemeContext.jsx     # Dark/light mode context
│   ├── data/                    # Learning content data modules
│   │   ├── modules.js           # 14 roadmap modules
│   │   ├── lessons.js           # 20 handbook chapters
│   │   ├── projects.js          # 11 projects
│   │   ├── exercises.js         # Practice exercises + weekly mini-projects
│   │   ├── templates.js         # 7 starter templates
│   │   ├── quizzes.js           # MCQ question bank
│   │   └── resources.js         # Resource hub entries
│   ├── hooks/
│   │   └── useProgress.jsx      # LocalStorage-backed progress hook
│   ├── layouts/
│   │   └── Layout.jsx           # Navbar + Footer wrapper
│   ├── pages/                   # Route pages
│   │   ├── Home/
│   │   ├── Roadmap/             # Roadmap + ModuleDetail
│   │   ├── Handbook/            # Handbook + ChapterDetail
│   │   ├── Learn/               # Learn + LessonDetail
│   │   ├── Projects/            # Projects + ProjectDetail
│   │   ├── Practice/            # Practice + ExerciseDetail
│   │   ├── Templates/           # Templates + TemplateDetail
│   │   ├── Deployment/
│   │   ├── GitHubGuide/
│   │   ├── Resources/           # Resources + ResourceDetail
│   │   ├── Assessments/         # Assessments + QuizRunner
│   │   ├── FacultyGuide/
│   │   ├── About/               # About + Credits
│   │   ├── NotFound.jsx
│   │   └── SearchResults.jsx
│   ├── styles/                  # CSS
│   │   ├── global.css
│   │   ├── components.css
│   │   ├── home.css
│   │   ├── page-details.css
│   │   └── page-lists.css
│   ├── utils/
│   │   └── search.js            # Unified search across all content
│   ├── App.jsx                  # Route definitions
│   └── main.jsx                 # Entry point
├── docs/                        # Markdown documentation
│   ├── WEBSITE_HANDBOOK.md
│   ├── LEARNING_ROADMAP.md
│   ├── FACULTY_GUIDE.md
│   ├── PRACTICE_WORKBOOK.md
│   ├── DEPLOYMENT_HANDBOOK.md
│   ├── GIT_GITHUB_GUIDE.md
│   ├── CHEAT_SHEETS.md
│   └── QUICK_REFERENCE.md
├── index.html
├── package.json
├── vite.config.js
├── LICENSE
├── CONTRIBUTING.md
├── CHANGELOG.md
└── README.md
```

## Available Scripts

| Command | Description |
|---------|-------------|
| `npm install` | Install all dependencies |
| `npm run dev` | Start the Vite dev server at http://localhost:5173 |
| `npm run build` | Build the production version into `dist/` |
| `npm run preview` | Preview the production build locally |

## Learning Content

The complete learning content is delivered through the website itself, but is also available as Markdown documentation in the `/docs` folder for offline reference and version control:

| Document | Content |
|----------|---------|
| [WEBSITE_HANDBOOK.md](docs/WEBSITE_HANDBOOK.md) | 20 chapters covering every layer of web development |
| [LEARNING_ROADMAP.md](docs/LEARNING_ROADMAP.md) | Complete 14-module learning roadmap |
| [FACULTY_GUIDE.md](docs/FACULTY_GUIDE.md) | Faculty teaching guide with proposed 12-week schedule |
| [PRACTICE_WORKBOOK.md](docs/PRACTICE_WORKBOOK.md) | Student practice workbook with HTML, CSS, JS exercises |
| [DEPLOYMENT_HANDBOOK.md](docs/DEPLOYMENT_HANDBOOK.md) | 22-section deployment guide |
| [GIT_GITHUB_GUIDE.md](docs/GIT_GITHUB_GUIDE.md) | Complete Git and GitHub guide |
| [CHEAT_SHEETS.md](docs/CHEAT_SHEETS.md) | Quick reference cheat sheets |
| [QUICK_REFERENCE.md](docs/QUICK_REFERENCE.md) | One-page quick reference guides |

## Documentation

See the `/docs` folder for the complete documentation suite. The documentation is maintained as Markdown files for version control, code review, and long-term maintenance.

## Local Installation

### Prerequisites

- **Node.js 18+** (recommend 20 LTS) — download from https://nodejs.org/
- **npm 9+** — comes with Node.js
- **Git** — download from https://git-scm.com/
- **A code editor** — recommend [Visual Studio Code](https://code.visualstudio.com/)

### Steps

```bash
# 1. Clone the repository (replace with the actual repo URL once published)
git clone https://github.com/your-username/wdle.git
cd wdle

# 2. Install dependencies
npm install

# 3. Start the development server
npm run dev
```

Open http://localhost:5173 in your browser.

### Verifying Installation

After installation, verify:

1. The dev server is running on http://localhost:5173
2. The home page loads with the hero, learning journey, features, projects, and resource highlights sections
3. Navigation works (Roadmap, Handbook, Learn, Projects, Practice, Templates, Deployment, Resources, Assessments, About)
4. Theme toggle (sun/moon icon in navbar) switches between light and dark mode
5. The search overlay opens with the search icon
6. Module/lesson completion buttons save progress (refresh to verify)

## Production Build

```bash
# Build the production version
npm run build

# The build output is in /dist
# Preview locally before deploying:
npm run preview
```

The build outputs to `/dist`. The build is configured with manual chunks for vendor code splitting (React, React Router, Lucide icons in separate chunks).

## Deployment

WDLE is a static site — deploy the `dist/` folder to any static host.

### Option 1: Vercel (recommended for Vite projects)

1. Push your repository to GitHub
2. Visit https://vercel.com/new
3. Import the repository
4. Vercel auto-detects Vite. Defaults:
   - Build command: `npm run build`
   - Output directory: `dist`
   - Install command: `npm install`
5. Click **Deploy**

### Option 2: Netlify

1. Push to GitHub
2. Visit https://app.netlify.com/start
3. Connect your repository
4. Configure:
   - Build command: `npm run build`
   - Publish directory: `dist`
5. Click **Deploy site**

### Option 3: GitHub Pages

1. Build: `npm run build`
2. Push the contents of `dist/` to a `gh-pages` branch, or use the GitHub Pages source setting pointing at `/docs` (after copying build output there)
3. Configure repository: Settings → Pages → Source: main branch, /root folder

See [docs/DEPLOYMENT_HANDBOOK.md](docs/DEPLOYMENT_HANDBOOK.md) for the complete guide with troubleshooting.

## Contributing

WDLE welcomes contributions from students, faculty, and the broader community. See [CONTRIBUTING.md](CONTRIBUTING.md) for the full guide.

Quick start for contributors:

1. Fork the repository
2. Create a feature branch: `git switch -c feature/your-feature`
3. Make changes following the existing patterns
4. Run `npm run build` to verify the build passes
5. Commit with a Conventional Commits message: `feat: add new module on TypeScript`
6. Push to your fork
7. Open a pull request

### Ways to contribute

- **Add a new module** to `src/data/modules.js` following the existing shape
- **Add a new chapter** to `src/data/lessons.js`
- **Add a new project** to `src/data/projects.js` with a full 100-point rubric
- **Add new exercises** to `src/data/exercises.js`
- **Add new quiz questions** to `src/data/quizzes.js`
- **Add new templates** to `src/data/templates.js`
- **Add new resources** to `src/data/resources.js`
- **Fix typos and content errors** (the easiest way to start)
- **Improve accessibility** — run Lighthouse and fix issues
- **Translate content** to Hindi or other regional languages

## License

MIT License — see [LICENSE](LICENSE) for the full text.

This project is intended for educational use within the Department of Computer Science at DSVV and the broader learning community. The original content is freely usable; third-party trademarks (React, Vite, GitHub, Vercel, Netlify, etc.) belong to their respective owners.

## Credits and References

See [About → Credits & References](https://your-deployment-url/about/credits) on the live site, or the in-app Credits page.

Major sources of curated content:
- [MDN Web Docs](https://developer.mozilla.org/)
- [web.dev](https://web.dev/)
- [W3C](https://www.w3.org/)
- [React documentation](https://react.dev/)
- [Vite documentation](https://vite.dev/guide/)
- [Git documentation](https://git-scm.com/doc)
- [GitHub Docs](https://docs.github.com/)
- [Visual Studio Code documentation](https://code.visualstudio.com/docs)
- [Vercel documentation](https://vercel.com/docs)
- [Netlify documentation](https://docs.netlify.com/)

## Disclaimer

WDLE is a student-led educational resource built by the Software Development Cell of the Department of Computer Science, Dev Sanskriti Vishwavidyalaya. It is **not** an officially launched institutional product of DSVV. The official DSVV website is https://www.dsvv.ac.in/.

The DSVV logo asset included in this repository is a placeholder. The official institutional emblem should be obtained from the official source subject to appropriate usage permissions.

All content is curated from publicly available official documentation and is intended for non-commercial educational use.
