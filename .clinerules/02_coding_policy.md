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

---

## Summary

By following this policy, we ensure that the codebase remains robust, maintainable, and ready for future development. All contributors are expected to adhere to these practices for every code change.
