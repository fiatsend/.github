# Contributing to Fiatsend

Thank you for your interest in contributing to Fiatsend. Whether you're fixing a bug, improving documentation, or proposing a new feature — we appreciate the help.

This guide covers everything you need to get started.

---

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Setup](#development-setup)
- [How to Contribute](#how-to-contribute)
  - [Reporting Bugs](#reporting-bugs)
  - [Suggesting Features](#suggesting-features)
  - [Submitting a Pull Request](#submitting-a-pull-request)
- [Coding Standards](#coding-standards)
- [Commit Messages](#commit-messages)
- [Pull Request Guidelines](#pull-request-guidelines)
- [Review Process](#review-process)
- [Community](#community)

---

## Code of Conduct

All contributors are expected to follow our [Code of Conduct](./CODE_OF_CONDUCT.md). Be respectful, constructive, and inclusive.

---

## Getting Started

### Find something to work on

- **Good first issues** — Look for issues labeled [`good first issue`](../../issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+issue%22). These are scoped, well-documented, and ideal for first-time contributors.
- **Help wanted** — Issues labeled [`help wanted`](../../issues?q=is%3Aissue+is%3Aopen+label%3A%22help+wanted%22) are open for community contributions.
- **Bug fixes** — Check the [`bug`](../../issues?q=is%3Aissue+is%3Aopen+label%3Abug) label for confirmed bugs.
- **Documentation** — Typos, unclear explanations, and missing examples are always welcome fixes.

> **Tip:** Comment on an issue before starting work so we can assign it to you and avoid duplicate effort.

---

## Development Setup

### Prerequisites

- **Node.js** >= 18.x (LTS recommended)
- **pnpm** >= 8.x (we use pnpm, not npm or yarn)
- **Git** >= 2.x
- **TypeScript** >= 5.x

For smart contract repos, you'll also need:

- **Foundry** (preferred) or **Hardhat**
- **Solidity** >= 0.8.x

### Clone and install

```bash
# Fork the repo on GitHub, then:
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>

# Install dependencies
pnpm install

# Run tests to verify setup
pnpm test
```

### Project structure (SDK repos)

```
src/
├── index.ts           # Main entry point / public exports
├── client.ts          # FiatsendClient class
├── resources/         # API resource modules (wallets, payouts, etc.)
├── types/             # TypeScript type definitions
└── errors/            # Custom error classes

tests/                 # Test files mirroring src/ structure
examples/              # Runnable usage examples
```

### Common commands

| Command | Description |
|---------|-------------|
| `pnpm install` | Install dependencies |
| `pnpm build` | Build the package |
| `pnpm test` | Run all tests |
| `pnpm test:watch` | Run tests in watch mode |
| `pnpm lint` | Run ESLint |
| `pnpm lint:fix` | Auto-fix lint issues |
| `pnpm format` | Format code with Prettier |
| `pnpm typecheck` | Run TypeScript type checking |

---

## How to Contribute

### Reporting Bugs

Use the [Bug Report](../../issues/new?template=bug_report.yml) issue template. A good bug report includes:

1. **What you expected** vs. **what actually happened**
2. **Steps to reproduce** — the more specific, the faster we can fix it
3. **Environment details** — SDK version, Node.js version, OS
4. **Code snippet** — a minimal example that demonstrates the issue
5. **Error output** — full stack trace or error message

### Suggesting Features

Use the [Feature Request](../../issues/new?template=feature_request.yml) issue template. Describe:

1. **The problem** you're trying to solve
2. **Your proposed solution** — what would the API or behavior look like?
3. **Alternatives** you've considered
4. **Use case** — how would this help you or other developers?

### Submitting a Pull Request

#### 1. Create a branch

Branch from `main` using this naming convention:

```bash
# Bug fix
git checkout -b fix/brief-description

# New feature
git checkout -b feat/brief-description

# Documentation
git checkout -b docs/brief-description

# Chore / maintenance
git checkout -b chore/brief-description
```

#### 2. Make your changes

- Keep changes focused — one PR per concern
- Add or update tests for any code changes
- Update documentation if you change public API
- Run the full test suite before pushing

#### 3. Write a clear commit message

See [Commit Messages](#commit-messages) below.

#### 4. Push and open a PR

```bash
git push origin feat/your-branch-name
```

Then open a pull request against `main` on GitHub. Fill out the PR template completely.

---

## Coding Standards

### TypeScript / JavaScript

- **Strict TypeScript** — `strict: true` in `tsconfig.json`. No `any` unless absolutely necessary (and documented with a comment explaining why).
- **ESLint + Prettier** — All code must pass linting and formatting. Run `pnpm lint` and `pnpm format` before committing.
- **Named exports** — Prefer named exports over default exports.
- **Async/await** — Use `async/await` over raw Promises. No callbacks.
- **Error handling** — Throw typed errors (`FiatsendError`, `AuthError`, `RateLimitError`). Never swallow errors silently.
- **No side effects on import** — Modules should not execute logic when imported.

```typescript
// Good
export class FiatsendClient {
  async createWallet(params: CreateWalletParams): Promise<Wallet> {
    const response = await this.request<Wallet>('POST', '/wallets', params);
    return response;
  }
}

// Bad — untyped, uses any, default export
export default class {
  createWallet(params: any) {
    return this.request('POST', '/wallets', params).then((r: any) => r);
  }
}
```

### Solidity (contracts repos)

- **Solidity** >= 0.8.x with optimizer enabled
- **NatSpec comments** on all public/external functions
- **Foundry tests** preferred (Hardhat accepted)
- Follow [Solidity Style Guide](https://docs.soliditylang.org/en/latest/style-guide.html)
- All contracts must compile with zero warnings

### Tests

- Every PR that changes functionality must include tests
- Aim for meaningful tests, not coverage numbers — test behavior, not implementation
- Use descriptive test names: `it('should return 400 when phone number is missing')`
- Mock external services (API calls, blockchain interactions) in unit tests

### Documentation

- All public functions, classes, and types must have JSDoc / TSDoc comments
- Update the README if you change installation steps, API surface, or usage examples
- Write examples that are copy-paste-runnable

---

## Commit Messages

We follow [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>(<scope>): <short summary>

<optional body>

<optional footer>
```

### Types

| Type | When to use |
|------|-------------|
| `feat` | A new feature or capability |
| `fix` | A bug fix |
| `docs` | Documentation only |
| `test` | Adding or updating tests |
| `refactor` | Code change that neither fixes a bug nor adds a feature |
| `chore` | Build process, CI, dependency updates |
| `perf` | Performance improvement |
| `style` | Formatting, white-space (no code logic change) |

### Examples

```
feat(wallets): add multi-currency wallet creation

fix(payouts): handle timeout on mobile money settlement

docs(readme): add Python SDK quickstart example

test(transfers): add edge case for zero-amount transfer

chore(deps): bump typescript to 5.4
```

### Rules

- Use **present tense** and **imperative mood** ("add feature", not "added feature")
- Keep the first line under **72 characters**
- Reference issue numbers in the footer: `Closes #42`

---

## Pull Request Guidelines

### Before opening a PR

- [ ] Code compiles without errors (`pnpm build`)
- [ ] All tests pass (`pnpm test`)
- [ ] Linting passes (`pnpm lint`)
- [ ] Types check (`pnpm typecheck`)
- [ ] Commit messages follow Conventional Commits
- [ ] You've added/updated tests for your changes
- [ ] You've updated documentation if needed
- [ ] PR targets the `main` branch

### PR size

- **Small PRs get reviewed faster.** Aim for under 400 lines of diff.
- If your change is large, break it into a stack of smaller PRs.
- Each PR should be independently mergeable and testable.

### What to include in the PR description

Use the PR template. At minimum:

1. **What** — What does this PR do?
2. **Why** — What problem does it solve? Link the issue.
3. **How** — Brief description of the approach.
4. **Testing** — How did you verify it works?

---

## Review Process

1. **Automated checks** — CI runs linting, type checking, and tests. All must pass.
2. **Maintainer review** — A Fiatsend team member will review your PR, usually within 2-3 business days.
3. **Feedback** — We may request changes. This is normal and collaborative, not adversarial.
4. **Approval and merge** — Once approved and CI is green, a maintainer will merge your PR.

### What we look for in reviews

- Correctness — Does the code do what it claims?
- Tests — Are edge cases covered?
- Types — Are TypeScript types accurate and helpful?
- Clarity — Could another developer understand this code in 6 months?
- API design — Does the public API feel consistent with the rest of the SDK?

---

## Community

- **Questions?** Open a [Discussion](../../discussions) or ask in our [Discord](https://discord.gg/fiatsend).
- **Security issues?** Do NOT open a public issue. See [SECURITY.md](./SECURITY.md) for responsible disclosure.
- **Need help with your first PR?** Tag your issue with `good first issue` and we'll provide extra guidance.

---

Thank you for contributing to Fiatsend. Every improvement — no matter how small — helps build better payment infrastructure for Africa and the world.
