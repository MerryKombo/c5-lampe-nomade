# Coding Policy

## Introduction

To ensure high code quality, maintainability, and reliability, this project follows a strict Test-Driven Development (TDD) approach. All code contributions must include comprehensive automated tests, including both unit and end-to-end (E2E) tests.

---

## Test-Driven Development (TDD)

- All new features and bug fixes must be developed using TDD.
- Write failing tests before implementing new code.
- Refactor code only after tests are passing.

---

## Unit Testing

- Every module, function, and component should have corresponding unit tests.
- Aim for high code coverage (recommended: 90% or higher).
- Use an appropriate unit testing framework for the language/stack (e.g., `pytest` for Python, `Jest` for JavaScript/TypeScript, etc.).
- Organize unit tests alongside or within a dedicated `tests/unit` directory.

---

## End-to-End (E2E) Testing

- Major user flows and critical paths must be covered by E2E tests.
- Use a suitable E2E testing tool (e.g., `Cypress`, `Playwright`, `Selenium`, etc.).
- Place E2E tests in a dedicated `tests/e2e` directory.
- E2E tests should simulate real user interactions and verify the system as a whole.

---

## Code Review & Continuous Integration

- All pull requests must include passing unit and E2E tests.
- Tests are required for merge approval.
- Automated tests must run in Continuous Integration (CI) for every PR (e.g., via GitHub Actions).
- PRs without adequate test coverage or with failing tests will not be merged.

## Git Workflow Requirements

**IMPORTANT**: For every user request, you MUST:

1. **Categorize the request** by asking the user to classify it as one of:
   - "new feature" - Adding completely new functionality
   - "feature improvement" - Enhancing existing functionality 
   - "bug fix" - Fixing broken or incorrect behavior
   - "foundation" - Configuration changes, repository setup, or technical debt work

2. **Create a feature branch** based on the classification:
   - Branch naming: `feature/description-of-change`, `improvement/description-of-change`, `bugfix/description-of-change`, or `foundation/description-of-change`
   - Always work on the branch, never directly on master
   - Output the branch name so the user knows which branch to test

3. **Commit all changes** on the feature branch with descriptive commit messages

4. **Wait for user approval** before merging to master
   - User will test the changes on the feature branch
   - Once approved, merge the branch and delete it
   - If rejected, make additional changes on the same branch

5. **Branch and commit output format**: 
   - Always clearly state "Working on branch: `branch-name`" when making changes
   - After committing, output the commit hash and message
   - Format: "Committed on `branch-name`: `commit-hash` - commit message"
   
---

## Summary

By following this policy, we ensure that the codebase remains robust, maintainable, and ready for future development. All contributors are expected to adhere to these practices for every code change.
