# Contributing to WDLE

Thank you for your interest in contributing to WDLE — the Website Development Learning Ecosystem for the Department of Computer Science at Dev Sanskriti Vishwavidyalaya. This document explains how to add new content, fix issues, and improve the platform.

## Code of Conduct

Be respectful, constructive, and inclusive. WDLE is an educational resource for students — assume good intent, give constructive feedback, and prioritise learning.

## Ways to Contribute

You do not need to be an experienced developer to contribute. Here are ways you can help:

| Contribution type | Difficulty | Impact |
|---|---|---|
| Fix a typo or content error | Easy | Improves quality |
| Add a quiz question | Easy | Builds the question bank |
| Add a practice exercise | Easy–Medium | Helps learners |
| Improve accessibility | Medium | Inclusive design |
| Add a new module | Medium–Hard | Extends curriculum |
| Add a new template | Medium–Hard | Adds reusable code |
| Add a new project | Medium–Hard | Extends project library |
| Translate content | Medium | Reaches more students |
| Improve performance | Hard | Better UX |

## Getting Started

### Prerequisites

- Node.js 18+ (recommend 20 LTS) — https://nodejs.org/
- npm 9+
- Git — https://git-scm.com/
- Visual Studio Code (recommended) — https://code.visualstudio.com/

### Fork and Clone

```bash
# Fork the repo on GitHub first (use the Fork button)
# Then clone your fork:
git clone git@github.com:your-username/wdle.git
cd wdle

# Add the upstream remote to stay in sync
git remote add upstream git@github.com:original-owner/wdle.git
```

### Install and Run

```bash
npm install
npm run dev
# Open http://localhost:5173
```

### Create a Branch

Always create a feature branch — never commit directly to main:

```bash
git switch -c feat/your-feature
```

## Conventional Commits

Use the Conventional Commits specification for commit messages:

| Type | When to use | Example |
|---|---|---|
| `feat:` | New feature or content | `feat: add TypeScript module to roadmap` |
| `fix:` | Bug fix | `fix: correct broken link in HTML module` |
| `docs:` | Documentation only | `docs: update README installation steps` |
| `style:` | Code style (whitespace, formatting) | `style: prettier reformat modules.js` |
| `refactor:` | Code restructuring (no behavior change) | `refactor: extract search helper` |
| `test:` | Adding or updating tests | `test: add quiz scoring tests` |
| `chore:` | Maintenance, dependencies | `chore: bump vite to 5.4.12` |

Format: `type: short description`

For longer commits, add a body explaining the what and why:

```
feat: add new module on TypeScript fundamentals

Adds a 15th module covering TypeScript basics, type annotations,
interfaces, and how TypeScript differs from JavaScript. Includes
9 topics, 5 exercises, knowledge-check questions, and a starter
project assignment. Aligns with the existing roadmap structure.
```

## Content Contribution Patterns

All content lives in `/src/data/` as JavaScript modules that export arrays of structured objects. The pages consume these arrays and render them automatically — you do not need to touch any component code to add new content.

### Adding a New Module

Edit `/src/data/modules.js`. Add an object to the `MODULES` array following the existing shape:

```javascript
{
  id: 'typescript-fundamentals',          // unique kebab-case id
  order: 15,                                // 1-indexed position
  title: 'TypeScript Fundamentals',
  level: 'advanced',                         // 'beginner' | 'intermediate' | 'advanced'
  estimatedHours: 10,
  prerequisites: ['Module 7: JavaScript Fundamentals'],
  objectives: [/* 5-7 strings */],
  topics: [/* 8-12 strings */],
  explanation: `A multi-paragraph beginner-friendly explanation...`,
  exercises: [/* 3-5 strings */],
  outcomes: [/* 4-6 strings */],
  resources: [
    { label: 'TypeScript Handbook', url: 'https://www.typescriptlang.org/docs/handbook/intro.html' }
  ],
  commonMistakes: [/* 4-6 strings */],
  checkQuestions: [/* 4-5 strings */],
  assignment: {
    title: 'TypeScript Todo App',
    description: 'Refactor your JavaScript todo app to TypeScript...'
  },
  checklist: [/* 5-7 strings */]
}
```

### Adding a New Chapter to the Handbook

Edit `/src/data/lessons.js`. Add to the `CHAPTERS` array:

```javascript
{
  id: 'ch-21',
  number: 21,
  title: 'TypeScript Fundamentals',
  level: 'intermediate',
  estimatedMinutes: 60,
  prerequisites: ['Chapter 10: JavaScript Fundamentals'],
  whatYouWillLearn: [/* 5 strings */],
  concepts: `Multi-paragraph explanation...`,
  tutorials: [/* 2-3 strings */],
  codeExample: {
    title: 'A TypeScript example',
    language: 'typescript',
    code: `interface User { name: string; age: number; }
const user: User = { name: 'Alice', age: 25 };`
  },
  practiceTasks: [/* 3 strings */],
  commonErrors: [/* 3-5 strings */],
  bestPractices: [/* 3-5 strings */],
  industryNotes: 'A short note on industry usage...',
  interviewQuestions: [/* 3-5 strings */],
  revision: 'A short revision summary...',
  references: ['https://www.typescriptlang.org/docs/']
}
```

### Adding a New Project

Edit `/src/data/projects.js`. The full shape includes:

```javascript
{
  id: 'unique-id',
  title: 'Project Title',
  level: 'beginner',            // 'beginner' | 'intermediate' | 'advanced'
  category: 'personal',         // 'personal' | 'business' | 'community' | 'content'
  icon: 'Briefcase',            // Lucide icon name
  estimatedHours: 12,
  skills: ['HTML5', 'CSS3'],
  overview: 'One-paragraph overview',
  problemStatement: '...',
  objective: '...',
  prerequisites: [/* strings */],
  learningOutcomes: [/* strings */],
  requiredFeatures: [/* strings */],
  optionalFeatures: [/* strings */],
  designRequirements: [/* strings */],
  folderStructure: `project-name/\n├── index.html\n└── README.md`,
  starterCode: { 'index.html': '<!DOCTYPE html>...' },
  developmentPlan: [/* ordered steps */],
  responsiveRequirements: [/* strings */],
  accessibilityRequirements: [/* strings */],
  testingChecklist: [/* strings */],
  submissionChecklist: [/* strings */],
  rubric: [
    { category: 'Functionality', marks: 25, criteria: '...' },
    // ... must total 100
  ],
  vivaQuestions: [/* 5 strings */],
  extensionIdeas: [/* 3-5 strings */]
}
```

### Adding a Practice Exercise

Edit `/src/data/exercises.js`:

```javascript
{
  id: 'unique-id',
  title: 'Exercise title',
  category: 'html',               // 'html' | 'css' | 'javascript'
  difficulty: 'beginner',         // 'beginner' | 'intermediate' | 'advanced'
  estimatedMinutes: 15,
  description: 'Short description',
  instructions: [/* ordered steps */],
  starterCode: `// starter code here`,
  expectedBehavior: 'What the solution should produce',
  hints: [/* progressive hints */],
  solution: `// complete solution`
}
```

### Adding a Quiz

Edit `/src/data/quizzes.js`:

```javascript
{
  id: 'unique-id',
  title: 'Quiz title',
  category: 'html',              // 'internet' | 'html' | 'css' | 'responsive' | 'javascript' | 'dom' | 'git' | 'deployment' | 'react'
  level: 'beginner',
  description: 'Short description',
  questions: [
    {
      id: 'q1',
      question: 'Question text?',
      options: ['A', 'B', 'C', 'D'],
      answer: 1,                 // 0-indexed correct option
      explanation: 'Why the correct answer is right'
    }
  ]
}
```

### Adding a Template

Edit `/src/data/templates.js`. The shape includes `code` as an object mapping filenames to content:

```javascript
{
  id: 'unique-id',
  title: 'Template title',
  purpose: 'Why this template exists',
  useCases: [/* strings */],
  features: [/* strings */],
  technologies: ['HTML5', 'CSS3'],
  folderStructure: `project/\n├── index.html\n└── README.md`,
  setupInstructions: [/* strings */],
  customizationInstructions: [/* strings */],
  accessibilityNotes: [/* strings */],
  responsiveNotes: [/* strings */],
  code: {
    'index.html': '<!DOCTYPE html>...',
    'css/style.css': '/* styles */'
  },
  deploymentInstructions: [/* strings */],
  improvements: [/* strings */]
}
```

### Adding a Resource

Edit `/src/data/resources.js`. For external resources, include the `url` field. For internal reference content, add an entry to `RESOURCE_DETAILS`:

```javascript
// In RESOURCES array:
{ id: 'unique-id', category: 'css', title: 'Resource title', summary: 'Summary', tags: ['tag1'] }

// In RESOURCE_DETAILS (for internal reference content):
'unique-id': {
  intro: 'Intro paragraph',
  sections: [
    { heading: 'Section', body: 'Multi-line content' }
  ]
}
```

## Code Style

### JavaScript / JSX

- Use `const` by default, `let` only when reassigning
- Use arrow functions for short callbacks
- Use template literals for string interpolation
- Use destructuring for object and array extraction
- Use 2 spaces for indentation
- Use single quotes for strings
- Use semicolons at end of statements
- Use `===` for equality, never `==`

### CSS

- Use kebab-case for class names
- Use CSS custom properties for design tokens (colors, spacing, fonts)
- Use modern units (`rem`, `em`, `%`, `vh`, `vw`, `ch`, `clamp()`)
- Use `box-sizing: border-box` globally
- Use `display: flex` for one-dimensional layouts
- Use `display: grid` for two-dimensional layouts
- Mobile-first media queries with `min-width`

### React Components

- Function components only (no class components)
- Hooks for state and side effects (`useState`, `useEffect`)
- Props destructured in the function signature
- One component per file
- File names match component names (PascalCase)

### Accessibility Checklist

Every contribution must:
- Use semantic HTML5 elements
- Provide alt text for images
- Use `<label for>` paired with `<input id>`
- Maintain heading hierarchy (one h1, then h2s, etc.)
- Have keyboard-accessible interactive elements
- Use ARIA attributes sparingly and correctly
- Pass WCAG AA color contrast (4.5:1 for body text)

## Testing Your Contribution

Before opening a pull request:

1. Run `npm run build` — must pass with no errors
2. Manually test the affected routes in the browser
3. Test on mobile (360px), tablet (768px), and desktop (1280px)
4. Run Lighthouse on the affected pages — aim for 90+ on accessibility
5. Check the console for runtime errors

## Pull Request Process

1. Push your branch to your fork: `git push -u origin feat/your-feature`
2. Open a pull request on GitHub
3. Write a clear title and description following Conventional Commits
4. Link any related issues
5. Address review feedback with new commits (do not squash)
6. Wait for the build CI to pass
7. Once approved, a maintainer will merge

## Reporting Issues

Use GitHub Issues for:
- Content errors (typos, incorrect code, broken links)
- Bugs (broken routes, console errors, accessibility issues)
- Feature requests (new modules, exercises, projects)
- Documentation improvements

Include:
- A clear title and description
- Steps to reproduce (for bugs)
- Expected vs actual behavior
- Browser and OS information
- Screenshots if applicable

## Attribution

Contributors will be acknowledged in the Credits page. When you make your first contribution, add your name to the contributors list in a separate PR.

## License

By contributing, you agree that your contributions will be licensed under the MIT License — see [LICENSE](LICENSE).

---

Thank you for helping make WDLE better for current and future Computer Science students at DSVV.
