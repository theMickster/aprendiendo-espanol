# 🇪🇸 Aprendiendo Español - Learning Spanish with the Shawsky Family

A family-driven Spanish learning repository. Currently in **Phase 1** (content-only). All content lives in `docs/` as Markdown files. No source code exists yet—the toolchain is solely for formatting and Git hooks.

## Commands

```bash
npm install          # First-time setup (installs Prettier, Husky, lint-staged)
npm run format       # Format all .md, .json, .yml, .yaml files with Prettier
npm run format:check # Check formatting without writing changes
```

Prettier runs automatically on staged files via a Husky pre-commit hook—manual formatting is rarely needed.

## Content Architecture

```
docs/
├── beginner/          # A1-A2 lessons (numbered 01, 02, ...)
├── intermediate/      # B1-B2 lessons
├── advanced/          # C1-C2 lessons
├── driving-in-spain/  # Spain driving exam study materials
├── pimsleur-spanish-learnings/  # Notes from Pimsleur audio course
├── resources/         # Reference materials
├── LESSON_TEMPLATE.md # Canonical structure for new lessons
└── README.md          # Lesson library index
```

## Lesson File Naming

Files use zero-padded sequential numbers: `NN-descriptive-hyphenated-name.md`

- ✅ `03-building-block-verbs.md`, `17-preposition-por-vs-para.md`
- ❌ `Lesson1.md`, `spanish_stuff.md`

## Lesson Structure

Every lesson follows `docs/LESSON_TEMPLATE.md`. Key sections in order:

1. Frontmatter header (Level, Estimated Time, Topics)
2. `## 📝 Overview`
3. `## 🎯 Learning Objectives`
4. `## 📖 Lesson Content`
5. `## 💬 Common Phrases` (table with Pronunciation Tip column)
6. `## ⚠️ Common Mistakes`
7. `## 💪 Practice Exercises`
8. `## 🔑 Answer Key` (wrapped in `<details><summary>Click to reveal answers</summary>`)
9. `## 🌟 Cultural Notes`
10. `## 📚 Additional Resources`
11. `## 🗣️ Speaking Practice`

## Content Conventions

- Spanish text in **bold**: `**Hola**`
- Translations in parentheses: `**Hola** - Hi/Hello`
- Vocabulary tables use columns: `Spanish | English | Pronunciation Tip`
- Wrong/right examples: `❌ **Wrong:** ... ✅ **Right:** ... 💡 **Why:** ...`
- Gendered adjectives noted inline: `_encantado_ if male, _encantada_ if female`
- Heading hierarchy: `#` for title, `##` for major sections, `###` for sub-concepts

## Prettier Settings

`printWidth: 100`, `proseWrap: preserve` (paragraphs are not reflowed—manual line breaks are respected).
