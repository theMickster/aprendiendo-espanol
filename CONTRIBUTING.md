# Contributing to Aprendiendo Español

Thank you for your interest in contributing! This guide will help you get started.

## 🤝 How to Contribute

### Contributing Lessons

1. **Choose the right level**: Place your content in the appropriate folder

   - `docs/beginner/` - A1-A2 level (basic phrases, present tense, essential vocabulary)
   - `docs/intermediate/` - B1-B2 level (past tenses, subjunctive, extended vocabulary)
   - `docs/advanced/` - C1-C2 level (complex grammar, idiomatic expressions, nuanced language)

2. **Use the lesson template**: See `docs/LESSON_TEMPLATE.md` for structure

3. **Follow naming conventions**: Use descriptive, lowercase, hyphenated filenames
   - ✅ Good: `present-tense-verbs.md`, `ordering-at-restaurants.md`
   - ❌ Avoid: `Lesson1.md`, `spanish_stuff.md`

### Content Guidelines

- **Clarity first**: Write for learners at the target level
- **Include examples**: Real-world usage helps understanding
- **Add translations**: Provide English translations for new content
- **Cultural context**: Share insights about Spanish culture when relevant
- **Pronunciation notes**: Include pronunciation guides for tricky words
- **Practice exercises**: Add exercises when possible (with answer keys!)

### Markdown Standards

- Use proper heading hierarchy (`#`, `##`, `###`)
- Format Spanish text in **bold** and translations in (parentheses)
- Use tables for verb conjugations and structured data
- Include emoji sparingly for visual interest 🎯
- Add horizontal rules `---` to separate major sections

### Code Formatting

This project uses [Prettier](https://prettier.io/) to ensure consistent formatting across all markdown and JSON files.

**Automatic formatting:**

- When you commit, Prettier automatically formats your staged files via a pre-commit hook
- You don't need to manually format—just write and commit!

**Manual formatting:**

- Format all files: `npm run format`
- Check formatting: `npm run format:check`
- First time setup: `npm install` (installs Prettier, Husky, and lint-staged)

**Configuration:**

- Prettier settings: `.prettierrc.json`
- Ignored files: `.prettierignore`
- Pre-commit hook: `.husky/pre-commit`

### Submitting Changes

1. **Fork** the repository
2. **Create a branch**: `git checkout -b add-lesson-name`
3. **Install dependencies**: `npm install` (first time only)
4. **Make your changes**: Add or edit lesson files
5. **Test**: Review your markdown rendering
6. **Commit**: Use clear commit messages (Prettier will auto-format on commit!)
   - `Add lesson on present tense AR verbs`
   - `Fix typo in restaurant vocabulary`
7. **Push** and create a **Pull Request**

### Reporting Issues

Found a mistake? Have a suggestion? [Open an issue](../../issues/new) with:

- Clear title describing the problem
- Location of the issue (file and section)
- Suggested correction or improvement

## 🎨 Lesson Structure Example

```markdown
# Topic Title

## 📝 Overview

Brief introduction to the topic

## 🎯 Learning Objectives

- What you'll learn
- Key concepts covered

## 📖 Lesson Content

Main teaching content with examples

## 💪 Practice

Exercises and activities

## 🔑 Answer Key

Solutions to exercises

## 📚 Additional Resources

Links to related lessons or external resources
```

## ✨ Code of Conduct

- Be respectful and constructive
- Assume good intentions
- Help create an inclusive learning environment
- Celebrate mistakes as learning opportunities

## 🙋 Questions?

Not sure about something? Ask in [Discussions](../../discussions) or open an issue. We're all learning together!

---

**¡Gracias por contribuir!** | Thank you for contributing!
