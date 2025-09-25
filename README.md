# Minimal Template

A minimal Node.js template with modern development tooling for rapid project initialization. This template provides a solid foundation with pre-configured linting, formatting, git hooks, and CI/CD pipelines.

## 🚀 Features

- **Modern JavaScript** - ES Modules support with Node.js 20+
- **Code Quality**
  - ✅ ESLint v9 with flat config for modern linting
  - ✅ Prettier for consistent code formatting
  - ✅ EditorConfig for cross-editor consistency
- **Git Workflow**
  - ✅ Husky for Git hooks automation
  - ✅ lint-staged for pre-commit checks
  - ✅ Conventional Commits enforcement
- **CI/CD**
  - ✅ GitHub Actions for automated testing
  - ✅ Dependabot for dependency updates
  - ✅ PR title validation
- **Developer Experience**
  - ✅ Codex configuration for AI-assisted development
  - ✅ IntelliJ IDEA configuration included
  - ✅ Issue and PR templates

## 📋 Prerequisites

- **Node.js** 20.0.0 or higher (LTS recommended)
- **npm** 9.0.0 or higher
- **Git** 2.30.0 or higher (for hooks)

## 🏁 Quick Start

### Using as a Template

1. **Create a new repository from this template**:

- Click the "Use this template" button on GitHub
- Or use GitHub CLI:

```bash
gh repo create my-project --template pillowstack/minimal-template
```

2. **Clone your new repository**:

   ```bash
   git clone https://github.com/YOUR-USERNAME/YOUR-PROJECT.git
   cd YOUR-PROJECT
   ```

3. **Install dependencies**:

   ```bash
   npm ci
   ```

4. **Initialize Git hooks**:

   ```bash
   npm run prepare
   ```

5. **Start developing**:

- Create your source files in `src/`
- Add tests in `tests/` or as `*.test.js` files
- Customize configuration files as needed

## 📁 Project Structure

```
minimal-template/
├── .codex/                    # AI development assistant configuration
│   ├── .codex.json            # Codex rules and branching config
│   └── prompts/               # Task prompt templates
├── .github/                   # GitHub specific files
│   ├── ISSUE_TEMPLATE/        # Issue templates
│   ├── workflows/             # GitHub Actions workflows
│   │   ├── ci.yml             # Main CI pipeline
│   │   └── pr-title-check.yml # PR title lint
│   ├── copilot/               # GitHub Copilot workspace guidance
│   │   └── copilot-instructions.md
│   ├── PULL_REQUEST_TEMPLATE.md
│   ├── CODEOWNERS             # Code ownership rules
│   └── dependabot.yml         # Dependency updates
├── .husky/                    # Git hooks
│   └── pre-commit             # Runs lint-staged
├── .idea/                     # IntelliJ IDEA configuration
├── .editorconfig              # Editor configuration
├── .gitignore                 # Git ignore patterns
├── .nvmrc                     # Node version specification
├── .prettierignore            # Prettier ignore patterns
├── .prettierrc.json           # Prettier configuration
├── AGENTS.md                  # Repository guidelines for AI agents
├── CONTRIBUTING.md            # How to contribute
├── SECURITY.md                # Security policy
├── eslint.config.js           # ESLint v9 flat configuration
├── LICENSE                    # MIT license
├── package.json               # Dependencies and scripts
└── README.md                  # This file
```

## 📜 Available Scripts

| Command                | Description                              | When to Use                    |
| ---------------------- | ---------------------------------------- | ------------------------------ |
| `npm ci`               | Install exact dependencies from lockfile | Initial setup, CI environments |
| `npm install`          | Install and update dependencies          | Adding new packages            |
| `npm run lint`         | Check for linting errors                 | Before committing              |
| `npm run lint:fix`     | Auto-fix linting errors                  | During development             |
| `npm run format`       | Format all files with Prettier           | Before committing              |
| `npm run format:check` | Check formatting without changes         | CI validation                  |
| `npm run prepare`      | Install Husky Git hooks                  | After cloning                  |
| `npm run clean`        | Clean install dependencies               | Troubleshooting                |

## 🔧 Configuration

### ESLint Configuration

Located in `eslint.config.js`:

- Modern ESLint v9 flat configuration
- JavaScript recommended rules
- Import ordering and validation
- Prettier integration to avoid conflicts
- Configured for `.js` and `.jsx` files

### Prettier Configuration

Located in `.prettierrc.json`:

```json
{
  "semi": true, // Semicolons required
  "trailingComma": "es5", // Trailing commas where valid
  "singleQuote": false, // Double quotes
  "printWidth": 100, // Line width limit
  "tabWidth": 2, // 2-space indentation
  "useTabs": false // Spaces over tabs
}
```

### Git Hooks (Husky + lint-staged)

Pre-commit hook automatically:

1. Formats staged files with Prettier
2. Lints staged JavaScript files with ESLint
3. Prevents commits if errors are found

### EditorConfig

Ensures consistent coding styles:

- 2-space indentation
- LF line endings
- UTF-8 encoding
- Final newline required
- Trailing whitespace trimmed

## 🤖 AI Development Support

This template includes Codex configuration (`.codex/`) for AI-assisted development:

- **Branching Strategy**: Automatically creates `codex/<task>` branches
- **Rules Enforcement**: Ensures AI agents follow project guidelines
- **Task Templates**: Predefined prompts for common tasks

When using AI assistants, they will:

1. Read configuration files before making changes
2. Follow the guidelines in `AGENTS.md`
3. Create appropriate feature branches
4. Run formatting and linting before completing tasks

## 🚢 CI/CD Pipeline

### GitHub Actions Workflow

The CI pipeline (`.github/workflows/ci.yml`) runs on:

- Push to `main` branch
- Pull requests targeting `main`

Pipeline steps:

1. **Checkout** - Clone repository
2. **Setup Node** - Install Node.js 20 with npm caching
3. **Install** - Run `npm ci` for exact dependencies
4. **Lint** - Check code with ESLint
5. **Format Check** - Verify Prettier formatting

### Pull Request Requirements

- PR titles must follow [Conventional Commits](https://www.conventionalcommits.org/)
- Valid types: `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `build`, `ci`, `chore`, `revert`
- Automated validation via `pr-title-check.yml`

### Dependency Management

Dependabot configured for:

- Weekly npm dependency updates
- Automatic pull request creation
- Security vulnerability alerts

## 🎯 Development Workflow

1. **Create a feature branch**:

   ```bash
   git checkout -b feat/your-feature
   # or for Codex: codex/your-feature
   ```

2. **Make your changes**:

- Write code following the style guide
- Add tests for new functionality
- Update documentation as needed

3. **Commit your changes**:

   ```bash
   git add .
   git commit -m "feat: add amazing feature"
   ```

   Pre-commit hooks will automatically format and lint your code.

4. **Push and create PR**:
   ```bash
   git push origin feat/your-feature
   ```

- Fill out the PR template
- Ensure CI passes
- Request review from CODEOWNERS

## 🏗️ Extending the Template

### Adding TypeScript Support

```bash
npm install --save-dev typescript @types/node tsx
```

Create `tsconfig.json`:

```json
{
  "compilerOptions": {
    "target": "ES2022",
    "module": "NodeNext",
    "moduleResolution": "NodeNext",
    "strict": true,
    "esModuleInterop": true,
    "skipLibCheck": true,
    "forceConsistentCasingInFileNames": true,
    "outDir": "./dist",
    "rootDir": "./src"
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules", "dist"]
}
```

### Adding Testing Framework

For Vitest:

```bash
npm install --save-dev vitest @vitest/ui
```

Add to `package.json`:

```json
{
  "scripts": {
    "test": "vitest",
    "test:ui": "vitest --ui",
    "test:coverage": "vitest --coverage"
  }
}
```

### Adding Build Process

For a build step:

```bash
npm install --save-dev esbuild
```

Add to `package.json`:

```json
{
  "scripts": {
    "build": "esbuild src/index.js --bundle --platform=node --outfile=dist/index.js",
    "start": "node dist/index.js"
  }
}
```

## 🐛 Troubleshooting

### Common Issues

**Issue**: Husky hooks not running

```bash
# Solution: Reinstall hooks
rm -rf .husky
npm run prepare
```

**Issue**: ESLint import errors

```bash
# Solution: Clear cache and reinstall
npm run clean
```

**Issue**: Prettier conflicts with ESLint

```bash
# Solution: Ensure eslint-config-prettier is last in config
# Check eslint.config.js includes prettier at the end
```

**Issue**: Node version mismatch

```bash
# Solution: Use nvm to switch to correct version
nvm use
# Or install the required version
nvm install
```

## 🤝 Contributing

We welcome contributions! Please follow these steps:

1. **Fork the repository**
2. **Create a feature branch** following our naming convention
3. **Make your changes** following the code style guide
4. **Write/update tests** as needed
5. **Update documentation** if applicable
6. **Submit a pull request** using our PR template

See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines.

### Code Style Guide

- **Files/Folders**: kebab-case (`my-component.js`)
- **Classes/Types**: PascalCase (`MyClass`)
- **Functions/Variables**: camelCase (`myFunction`)
- **Constants**: SCREAMING_SNAKE_CASE (`MAX_RETRIES`)
- **Imports**: Group and sort (builtin → external → internal)

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Built with modern JavaScript tooling best practices
- Inspired by community standards and conventions
- Maintained by [Pillowstack](https://github.com/pillowstack)

## 📚 Resources

- [Node.js Documentation](https://nodejs.org/docs)
- [ESLint Documentation](https://eslint.org/docs/latest/)
- [Prettier Documentation](https://prettier.io/docs/en/)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)

## 💬 Support

- **Issues**: [GitHub Issues](https://github.com/pillowstack/minimal-template/issues)
- **Discussions**: [Pillowstack](https://github.com/pillowstack/.github/discussions)
- **Security**: See [SECURITY.md](SECURITY.md) for reporting vulnerabilities

---

[![CI](https://github.com/pillowstack/minimal-template/actions/workflows/ci.yml/badge.svg)](https://github.com/pillowstack/minimal-template/actions/workflows/ci.yml)
[![Node Version](https://img.shields.io/badge/node-%3E%3D20.0.0-brightgreen)](https://nodejs.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)

---
