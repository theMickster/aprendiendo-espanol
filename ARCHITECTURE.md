# 🏗️ Project Architecture

This document outlines the technical architecture of the Aprendiendo Español project, from current state through future phases.

## 📐 Current Architecture (Phase 1)

```
aprendiendo-espanol/
│
├── docs/                          # Content repository
│   ├── beginner/                 # A1-A2 lessons
│   ├── intermediate/             # B1-B2 lessons
│   ├── advanced/                 # C1-C2 lessons
│   ├── resources/                # Reference materials
│   ├── LESSON_TEMPLATE.md        # Template for new lessons
│   └── README.md                 # Lesson library guide
│
├── .github/                      # (Future) CI/CD workflows
│   └── workflows/                # Automated tests, deployments
│
├── README.md                     # Project homepage
├── CONTRIBUTING.md               # Contribution guidelines
├── ROADMAP.md                    # Project roadmap
├── IMPORTING.md                  # Gist import guide
├── LICENSE                       # MIT License
└── .gitignore                    # Git ignore rules

Content Format: Markdown
Version Control: Git/GitHub
Hosting: GitHub (repository + Pages ready)
```

## 🌐 Future Web Architecture (Phase 3)

### Proposed Structure

```
aprendiendo-espanol/
│
├── docs/                         # Content (same as above)
│
├── web/                          # Static website
│   ├── src/
│   │   ├── pages/               # Next.js/Astro pages
│   │   ├── components/          # Reusable UI components
│   │   ├── lib/                 # Utilities and helpers
│   │   └── styles/              # CSS/Tailwind styles
│   ├── public/                  # Static assets
│   ├── package.json             # Dependencies
│   └── README.md                # Web app documentation
│
├── apps/                        # Interactive applications
│   ├── flashcards/              # Flashcard app
│   │   ├── src/                # App source
│   │   ├── package.json        # Dependencies
│   │   └── README.md           # App documentation
│   │
│   ├── verb-conjugator/         # Verb practice tool
│   │   └── ...
│   │
│   └── quiz-generator/          # Quiz builder
│       └── ...
│
├── shared/                      # Shared code between web/apps
│   ├── content-parser/          # Parse markdown lessons
│   ├── types/                   # TypeScript types
│   └── data/                    # Shared data structures
│
├── scripts/                     # Build and utility scripts
│   ├── build-lesson-index.js   # Generate lesson metadata
│   ├── validate-markdown.js    # Content quality checks
│   └── generate-site.js        # Static site generation
│
└── ...                          # (existing files)
```

### Technology Stack Recommendations

#### Static Website (`web/`)

**Recommended: Astro**

- **Why:** Perfect for content-heavy, Markdown-based sites
- Lightning fast, SEO-friendly
- Can integrate React/Vue/Svelte components as needed
- Built-in markdown support
- Static generation perfect for GitHub Pages

**Alternative: Next.js**

- More feature-rich but heavier
- Better for dynamic features later
- Larger ecosystem

**Styling:** Tailwind CSS

- Utility-first, responsive design
- Great for rapid prototyping
- Consistent design system

**Deployment:**

- GitHub Pages (free, simple)
- Vercel (free tier, automatic deployments)
- Netlify (free tier, good DX)

#### Interactive Apps (`apps/`)

**Flashcards App**

```
Technology: React (web) or React Native (mobile)
State Management: Zustand or React Context
Storage: LocalStorage (web) or AsyncStorage (mobile)
Features:
- Spaced repetition algorithm
- Progress tracking
- Custom deck creation
- Offline support
```

**Verb Conjugator**

```
Technology: React with TypeScript
Data: JSON files with verb patterns
Features:
- All tenses and moods
- Irregular verb handling
- Practice mode with instant feedback
- Progress tracking
```

**Quiz Generator**

```
Technology: Next.js (full-stack capability)
Backend: API routes in Next.js
Database: SQLite or Supabase (if needed)
Features:
- Pull from lesson content
- Multiple quiz types (multiple choice, fill-in-blank)
- Randomized questions
- Score tracking
```

## 🔄 Data Flow Architecture

### Content Pipeline

```
┌─────────────────┐
│  Markdown Files │  (docs/)
│   (Source of    │
│     Truth)      │
└────────┬────────┘
         │
         ├──────────────────────────┐
         │                          │
         v                          v
┌─────────────────┐        ┌──────────────┐
│   Web Display   │        │  Mobile App  │
│                 │        │              │
│ • Lesson pages  │        │ • Flashcards │
│ • Search        │        │ • Offline    │
│ • Navigation    │        │ • Quizzes    │
└─────────────────┘        └──────────────┘
         │                          │
         v                          v
┌──────────────────────────────────────┐
│         Shared Content Parser        │
│                                      │
│ • Extracts lesson metadata           │
│ • Generates flashcards from content  │
│ • Creates quiz questions             │
│ • Builds vocabulary lists            │
└──────────────────────────────────────┘
```

### User Data Flow (Future)

```
User Progress
      │
      v
┌────────────────┐
│ Local Storage  │ ──────┐
└────────────────┘       │
                         │
      OR                 │ Sync
                         │
┌────────────────┐       │
│   Cloud DB     │ ◄─────┘
│  (Supabase/    │
│   Firebase)    │
└────────────────┘
```

## 📊 Content Management

### Lesson Metadata

Each lesson can include frontmatter:

```yaml
---
title: "Greetings and Introductions"
level: "beginner"
sublevel: "A1"
duration: "20 minutes"
topics: ["greetings", "introductions"]
vocabulary_count: 15
difficulty: 1
prerequisites: []
related_lessons: ["alphabet-and-pronunciation", "subject-pronouns"]
author: "theMickster"
date: "2026-02-15"
---
```

### Build-Time Processing

```javascript
// scripts/build-lesson-index.js
// Generates searchable lesson index

{
  "lessons": [
    {
      "id": "beginner-01",
      "slug": "greetings-and-introductions",
      "title": "Greetings and Introductions",
      "level": "beginner",
      "path": "/docs/beginner/01-greetings-and-introductions.md",
      "vocabulary": [...],
      "exercises": [...]
    }
  ]
}
```

## 🔐 Security & Privacy

- **No personal data collection** (initially)
- **Optional Google Analytics** for usage patterns
- **Local-first storage** for user progress
- **Optional cloud sync** with user consent
- **Open source** - all code visible and auditable

## 🚀 Deployment Strategy

### Phase 1 (Current): Content Only

```
GitHub Repository
└─> GitHub Pages (optional static site from README)
```

### Phase 2: Static Website

```
GitHub Repository
├─> Vercel/Netlify (automatic deployment on push)
└─> Custom domain (optional)
```

### Phase 3: Interactive Apps

```
GitHub Repository
├─> Web App → Vercel
├─> Mobile App → App Store / Play Store
└─> API (if needed) → Vercel Serverless Functions
```

## 🧪 Quality Assurance

### Automated Checks (Future)

```yaml
# .github/workflows/quality-check.yml

- Markdown linting
- Spell checking (Spanish + English)
- Link validation
- Frontmatter validation
- Build tests for web/apps
- Automated deployments
```

## 📱 Mobile Considerations

When building mobile apps:

- **Offline-first architecture**
- **Lightweight database** (SQLite, Realm)
- **Minimize app size** (user content updates without app updates)
- **Progressive Web App** (PWA) as first mobile experience

## 🔄 Migration Path

### From Markdown to Database (if needed)

```
Phase 1: Markdown files (human-editable)
    ↓
Phase 2: Markdown + JSON index (searchable)
    ↓
Phase 3: Markdown + Database (user data, analytics)
    ↓
Phase 4: Database + Markdown backup (scale)
```

**Recommendation:** Keep markdown as source of truth indefinitely. It's:

- Version controllable
- Human readable
- Easy to edit
- Platform independent

## 💡 Design Principles

1. **Content First:** Content in markdown, tools built around it
2. **Progressive Enhancement:** Start simple, add features incrementally
3. **Offline Capable:** Learning shouldn't require internet
4. **Open Source:** Learning should be free and accessible
5. **Mobile Friendly:** Most learning happens on phones
6. **Community Driven:** Built by learners, for learners

## 🤔 Technology Decision Matrix

| Feature        | Solution        | When to Add       |
| -------------- | --------------- | ----------------- |
| Static content | Markdown in Git | ✅ Now            |
| Website        | Astro/Next.js   | Phase 3 (Q3 2026) |
| Flashcards     | React app       | Phase 3 (Q3 2026) |
| User accounts  | Supabase        | Phase 4 (Q4 2026) |
| Mobile app     | React Native    | Phase 4 (2027)    |
| AI features    | OpenAI API      | Phase 5 (2027+)   |
| Real-time sync | Firebase        | Only if needed    |

## 📚 Resources for Developers

When you're ready to build:

- **[Astro Docs](https://docs.astro.build/)** - Static site generator
- **[Next.js Docs](https://nextjs.org/docs)** - React framework
- **[Tailwind CSS](https://tailwindcss.com/)** - Styling
- **[Supabase](https://supabase.com/)** - Backend as a service
- **[React Native](https://reactnative.dev/)** - Mobile development

---

**This is a living document.** Update as the project evolves!

_Questions about architecture? [Start a discussion](../../discussions)_
