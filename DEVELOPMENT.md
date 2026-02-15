# Development Setup Guide

This guide explains the development tools and workflows for working on the Aprendiendo Español project.

## 📋 Prerequisites

- **Node.js** (v16 or higher)
- **npm** (comes with Node.js)
- **Git**

## 🚀 First Time Setup

When you first clone the repository or want to start contributing:

```bash
# Clone the repository (if you haven't already)
git clone https://github.com/theMickster/aprendiendo-espanol.git
cd aprendiendo-espanol

# Install development dependencies
npm install
```

This installs:

- **Prettier** (3.2.5) - Code formatter
- **Husky** (9.0.11) - Git hooks manager
- **lint-staged** (15.2.2) - Run linters on staged files

After installation, Husky automatically sets up Git hooks.

## 🎨 Code Formatting with Prettier

### What Gets Formatted?

Prettier automatically formats:

- Markdown files (`*.md`)
- JSON files (`*.json`)
- YAML files (`*.yml`, `*.yaml`)

### Automatic Formatting (Recommended)

When you commit files, Prettier **automatically formats** your staged files:

```bash
git add docs/beginner/my-new-lesson.md
git commit -m "Add new lesson"
# ✨ Prettier formats your files automatically before committing!
```

### Manual Formatting

Format all files in the project:

```bash
npm run format
```

Check if files need formatting (without changing them):

```bash
npm run format:check
```

## 📝 Prettier Configuration

### Settings (`.prettierrc.json`)

```json
{
  "printWidth": 100,
  "tabWidth": 2,
  "useTabs": false,
  "proseWrap": "preserve"
}
```

**Key settings:**

- **printWidth: 100** - Lines wrap at 100 characters (wider for readability)
- **proseWrap: preserve** - Don't reflow markdown paragraphs (preserves manual line breaks)
- **tabWidth: 2** - Use 2 spaces for indentation

### Ignored Files (`.prettierignore`)

Prettier skips:

- `node_modules/`
- `package-lock.json`
- Build outputs (`dist/`, `build/`, etc.)
- Log files

## 🪝 Git Hooks with Husky

### Pre-commit Hook

Located at: `.husky/pre-commit`

**What it does:**

1. Runs before each commit
2. Triggers `lint-staged`
3. Formats only the files you're committing
4. Prevents commits if formatting fails

**Flow:**

```
git commit
    ↓
.husky/pre-commit runs
    ↓
lint-staged runs Prettier on staged files
    ↓
Files are formatted and added to commit
    ↓
Commit succeeds ✅
```

## 🔧 Troubleshooting

### Hook Not Running?

If the pre-commit hook doesn't run:

```bash
# Make sure the hook is executable
chmod +x .husky/pre-commit

# Reinstall Husky
npm run prepare
```

### Prettier Not Installed?

```bash
# Reinstall dependencies
rm -rf node_modules package-lock.json
npm install
```

### Want to Skip the Hook? (Not Recommended)

Only in emergencies:

```bash
git commit --no-verify -m "Emergency commit"
```

### Format Check Failing?

Run format to fix all issues:

```bash
npm run format
```

## 📚 Writing Markdown Lessons

### Best Practices

1. **Write naturally first** - Don't worry about formatting while writing
2. **Commit when ready** - Prettier will format automatically
3. **Keep lines readable** - Prettier won't reflow paragraphs, so feel free to break lines manually
4. **Use consistent headers** - `#`, `##`, `###` (Prettier ensures consistency)

### Example Workflow

```bash
# 1. Create a new lesson
vim docs/beginner/new-lesson.md

# 2. Write your content (don't worry about formatting)

# 3. Stage your changes
git add docs/beginner/new-lesson.md

# 4. Commit (Prettier formats automatically)
git commit -m "Add lesson on Spanish verbs"

# 5. Push to GitHub
git push origin your-branch
```

## 🎯 NPM Scripts Reference

| Script                 | Command                                      | Purpose                               |
| ---------------------- | -------------------------------------------- | ------------------------------------- |
| `npm install`          | Install dependencies                         | First-time setup                      |
| `npm run format`       | `prettier --write "**/*.{md,json,yml,yaml}"` | Format all files                      |
| `npm run format:check` | `prettier --check "**/*.{md,json,yml,yaml}"` | Check formatting without changing     |
| `npm run prepare`      | `husky install`                              | Set up Git hooks (runs automatically) |

## 🔄 Updating Dependencies

To update Prettier, Husky, or lint-staged:

```bash
# Check for updates
npm outdated

# Update all dependencies
npm update

# Update specific package
npm install prettier@latest --save-dev
```

## 🌟 VS Code Integration (Optional)

For an even better experience, install the Prettier extension:

1. Install: [Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
2. Settings → Format On Save: ✅ Enable
3. Settings → Default Formatter: Prettier

Now your files format on save!

**`.vscode/settings.json` (optional):**

```json
{
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true,
  "[markdown]": {
    "editor.wordWrap": "on"
  }
}
```

## 📖 Resources

- [Prettier Documentation](https://prettier.io/docs/en/)
- [Husky Documentation](https://typicode.github.io/husky/)
- [lint-staged Documentation](https://github.com/okonet/lint-staged)

## 🆘 Getting Help

- **Questions?** Ask in [Discussions](../../discussions)
- **Issues?** Report in [Issues](../../issues)
- **Want to improve this guide?** Submit a Pull Request!

---

**Happy coding! 🎉**
