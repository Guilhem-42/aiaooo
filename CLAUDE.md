# CLAUDE.md - AI Assistant Guide for aiaooo

**Last Updated:** 2025-12-08
**Project Status:** Pre-seed Prototype
**Repository:** Guilhem-42/aiaooo

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Repository Structure](#repository-structure)
3. [Development Workflow](#development-workflow)
4. [Git Conventions](#git-conventions)
5. [Code Conventions](#code-conventions)
6. [AI Assistant Guidelines](#ai-assistant-guidelines)
7. [Common Tasks](#common-tasks)

---

## Project Overview

**aiaooo** is a pre-seed prototype project currently in its initial development phase.

### Current State
- **Status:** Initial repository setup
- **Files:** Minimal structure with README.md
- **Last Commit:** 84b52ce - Initial commit
- **Active Branch:** `claude/claude-md-mixq0x4lflr1n73l-01Hyh6fFXyE7oet35HhqauWT`

### Key Information
- This is a greenfield project - no established codebase yet
- All development decisions should be made with scalability and maintainability in mind
- Follow industry best practices unless explicitly directed otherwise

---

## Repository Structure

```
aiaooo/
├── .git/                 # Git version control
├── README.md            # Project description
└── CLAUDE.md           # This file - AI assistant guide
```

### Expected Future Structure

As the project develops, follow these organizational principles:

```
aiaooo/
├── src/                 # Source code
├── tests/              # Test files
├── docs/               # Documentation
├── config/             # Configuration files
├── scripts/            # Build and utility scripts
├── .github/            # GitHub workflows and templates
├── package.json        # Dependencies (if Node.js)
├── requirements.txt    # Dependencies (if Python)
├── Cargo.toml         # Dependencies (if Rust)
└── [language-specific files]
```

---

## Development Workflow

### Branch Strategy

**Current Branch:** `claude/claude-md-mixq0x4lflr1n73l-01Hyh6fFXyE7oet35HhqauWT`

#### Branch Naming Conventions
- **Feature branches:** `claude/[descriptive-name]-[session-id]`
- **All Claude Code branches MUST:**
  - Start with `claude/`
  - End with the matching session ID
  - Use kebab-case for descriptive names

#### Git Operations

**Push Operations:**
```bash
# Always use -u flag for new branches
git push -u origin <branch-name>

# CRITICAL: Branch must match pattern: claude/*-<session-id>
# Otherwise push will fail with 403 HTTP error
```

**Retry Logic for Network Issues:**
- Retry up to 4 times with exponential backoff: 2s, 4s, 8s, 16s
- Applies to: push, fetch, pull operations

**Fetch/Pull Operations:**
```bash
# Prefer specific branch fetches
git fetch origin <branch-name>

# For pulls
git pull origin <branch-name>
```

### Commit Message Guidelines

Follow conventional commits format:

```
<type>(<scope>): <subject>

<body>

<footer>
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, etc.)
- `refactor`: Code refactoring
- `test`: Adding or updating tests
- `chore`: Maintenance tasks
- `perf`: Performance improvements

**Examples:**
```
feat(auth): add user authentication module

Implements JWT-based authentication with refresh tokens.
Includes middleware for protected routes.

Closes #123
```

```
fix(api): handle null responses in user endpoint

Added null checks to prevent crashes when user data is incomplete.
```

### Code Review Checklist

Before committing:
- [ ] Code follows project conventions
- [ ] Tests pass (when test suite exists)
- [ ] No security vulnerabilities introduced
- [ ] Documentation updated if needed
- [ ] No debugging code or console.logs left in
- [ ] Dependencies are necessary and documented

---

## Git Conventions

### Commit Best Practices

1. **Atomic Commits:** Each commit should represent a single logical change
2. **Meaningful Messages:** Focus on "why" not just "what"
3. **Security:** Never commit secrets, API keys, or sensitive data
4. **No Force Push:** Avoid `--force` unless explicitly necessary
5. **Hook Compliance:** Never skip hooks with `--no-verify` unless required

### Files to Never Commit

- `.env` and `.env.*` files
- `credentials.json` or similar
- API keys and secrets
- Large binary files (use Git LFS if needed)
- IDE-specific files (add to .gitignore)
- `node_modules/`, `__pycache__/`, build artifacts

---

## Code Conventions

### General Principles

1. **Simplicity First:** Avoid over-engineering
2. **No Premature Optimization:** Optimize only when needed
3. **No Premature Abstraction:** Don't create helpers for one-time use
4. **Security Conscious:** Prevent OWASP top 10 vulnerabilities
5. **Clean Code:** Self-documenting code is preferred over comments

### Security Guidelines

**Always Guard Against:**
- Command injection
- XSS (Cross-Site Scripting)
- SQL injection
- CSRF (Cross-Site Request Forgery)
- Insecure deserialization
- Path traversal attacks
- Authentication/authorization bypasses

**Validation Rules:**
- Validate at system boundaries (user input, external APIs)
- Trust internal code and framework guarantees
- Don't add error handling for impossible scenarios

### Error Handling

- Handle errors at appropriate levels
- Provide meaningful error messages
- Log errors with context
- Don't swallow exceptions silently
- Use language-specific best practices

### Testing Approach

When implementing tests:
- Write tests for public APIs and critical paths
- Use descriptive test names
- Follow AAA pattern: Arrange, Act, Assert
- Mock external dependencies
- Aim for meaningful coverage, not 100% coverage

---

## AI Assistant Guidelines

### Before Making Changes

1. **Read First:** Never propose changes to code you haven't read
2. **Understand Context:** Review related files and dependencies
3. **Plan Complex Tasks:** Use TodoWrite for multi-step tasks
4. **Ask Questions:** Clarify ambiguous requirements

### During Development

1. **Stay Focused:** Only make requested changes
2. **Avoid Scope Creep:** Don't add unrequested features
3. **Track Progress:** Update TodoWrite as tasks complete
4. **Test Changes:** Verify changes work as expected

### After Changes

1. **Review Security:** Check for vulnerabilities
2. **Update Documentation:** Keep docs in sync with code
3. **Clean Up:** Remove debugging code and unused imports
4. **Commit Properly:** Follow commit message guidelines

### Communication Style

- Be concise and direct
- Focus on technical accuracy
- Avoid unnecessary superlatives
- Provide objective guidance
- Don't use emojis unless requested

### Tool Usage Priorities

1. **File Operations:** Use Read/Edit/Write tools, not bash commands
2. **Searching:** Use Grep for content, Glob for file patterns
3. **Exploration:** Use Task tool for broad codebase exploration
4. **Parallel Execution:** Run independent operations concurrently

---

## Common Tasks

### Setting Up Development Environment

Since this is a pre-seed project, the tech stack isn't yet established. When setting up:

1. Document all dependencies in appropriate manifest files
2. Create setup scripts if needed
3. Include environment variable templates
4. Document system requirements

### Adding New Features

```bash
# 1. Ensure you're on the correct branch
git status

# 2. Create necessary directories/files
# 3. Implement feature
# 4. Test thoroughly
# 5. Commit with clear message
git add <relevant-files>
git commit -m "feat(scope): description"

# 6. Push to remote
git push -u origin <branch-name>
```

### Debugging Workflow

1. Reproduce the issue
2. Add logging/debugging to understand root cause
3. Fix the issue
4. Remove debugging code
5. Add tests to prevent regression
6. Commit the fix

### Updating Documentation

- Keep CLAUDE.md updated as project evolves
- Document architectural decisions
- Update README.md for user-facing changes
- Add inline docs for complex logic only

---

## Project Evolution

As this project grows, update this document to reflect:

- Chosen tech stack and frameworks
- Established coding patterns
- Testing strategies
- Build and deployment processes
- Team conventions
- Architecture decisions

### Regular Maintenance

This file should be reviewed and updated:
- When major architectural changes occur
- When new conventions are established
- When dependencies or tooling change
- At minimum, quarterly

---

## Questions or Issues?

For questions about this codebase or to report issues:
- Check existing documentation first
- Review commit history for context
- Ask the repository owner for clarification
- Document new patterns as they emerge

---

## Version History

| Date | Version | Changes |
|------|---------|---------|
| 2025-12-08 | 1.0 | Initial CLAUDE.md creation for pre-seed phase |

---

**Note for AI Assistants:** This document is your primary reference for working with this codebase. Always consult it before making significant changes. Keep it updated as the project evolves.
