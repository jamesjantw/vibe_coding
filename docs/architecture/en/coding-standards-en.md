# BMad Method - Universal Coding Standards

**Version:** 1.0
**Applies to:** All programming languages and frameworks
**Date:** 2025-10-15

## 1. Introduction (Introduction)

This document defines the universal coding standards, style guides, and best practices for software development using BMad Method. These standards apply to all programming languages and frameworks, aiming to ensure code readability, consistency, and maintainability.

---

## 2. General Principles (General Principles)

*   **Clarity over Conciseness:** Code is written first for humans to read, second for machines to execute.
*   **Follow The Zen of Python:** In a terminal, type `import this`.
*   **DRY (Don't Repeat Yourself):** Avoid duplicate code; abstract it into reusable functions or classes wherever possible.
*   **KISS (Keep It Simple, Stupid):** Unless there's a compelling reason, choose the simplest direct solution.
*   **Please reply and write documents in Traditional Chinese**
*   **Internal tools** Use read_file instead of read_many_files, write_file instead of replace
*   **Read before modifying** Update memory to ensure existing functionality is not affected
*   **Comments** Please add date agent personnel story task
*   **OS Environment** Windows
*   **All Agent Roles** Please refer to docs/architecture/definition-of-done.md to understand & align related definitions
*   **Processing Methods & Results** Please record in detail and update file status

---

### 2.1 Developer Execution Checklist (Mandatory for Developers)

The following checklist is what developers must follow for any changes, ensuring traceability, reproducibility, and no disruption to existing functionality:

1) Preparation Phase
    - Read the files to be modified and related dependencies (avoid guessing).
    - If location lookup is needed, use search tools to locate, then read files.
    - Record key decision points and design considerations.

2) Follow Standards
    - Follow official coding standards and conventions for each programming language.
    - Use appropriate formatting tools and Linters.

3) Change Implementation
    - Add annotations before changes (date/author/Story/Task).
    - Use minimal edits; avoid unrelated changes.
    - Track pending items, update status upon completion.

4) Verification and Consistency
    - Execute Lint and format checks, correct discovered issues.

5) Documentation Synchronization
    - Update related files and annotations.

6) Submission Instructions
    - Use clear commit messages describing changes.

---

## 3. Universal Programming Language Standards

### 3.1. Style and Formatting

*   **Language-Specific Standards:** Follow official coding standards and conventions for each programming language.
*   **Automatic Formatting:** Use appropriate code formatting tools (such as Prettier, Black, gofmt, etc.).
*   **Linter:** Use language-specific static analysis tools to catch potential errors and non-compliant writing.

### 3.2. Universal Naming Conventions (Naming Conventions)

Different programming languages have different naming conventions, but consistency should be maintained:

| Element | Common Convention | Example |
|---------|-------------------|---------|
| Variables | camelCase or snake_case | `userName`, `user_name` |
| Functions/Methods | camelCase or snake_case | `calculateTotal()`, `calculate_total()` |
| Classes/Types | PascalCase | `UserService`, `ProjectManager` |
| Constants | UPPER_SNAKE_CASE | `MAX_RETRY_COUNT`, `DEFAULT_TIMEOUT` |
| Private Members | Prefix underscore | `_privateField`, `_internalMethod()` |

### 3.3. Documentation and Comments (Documentation & Comments)

*   **Public APIs:** All public functions, classes, and modules must have complete documentation.
*   **Complex Logic:** Add comments for complex business logic and algorithms.
*   **Documentation Format:** Use standard documentation formats for each language (such as JSDoc, docstrings, XML comments).

```javascript
/**
 * Validate user authentication information
 * @param {string} username - Username
 * @param {string} password - Password
 * @returns {Promise<boolean>} Validation result
 */
async function validateCredentials(username, password) {
    // Implement validation logic
}
```

---

## 4. Security (Security)

*   **Sensitive Information Management:** All sensitive information (API keys, database passwords, certificates, etc.) must be stored in environment variables or secure configuration management systems, never committed to version control.
*   **Input Validation:** Always validate and sanitize user input to prevent injection attacks.
*   **Authentication and Authorization:** Implement appropriate identity verification and permission checking mechanisms.
*   **Data Encryption:** Sensitive data should be encrypted during storage and transmission.
*   **Dependency Updates:** Regularly update third-party dependencies to patch known security vulnerabilities.

---

## 5. Testing (Testing)

*   **Testing Frameworks:** Choose appropriate testing frameworks based on programming language (such as JUnit, pytest, Jest, Vitest, etc.).
*   **Test Organization:** Place test files in corresponding directory structures alongside source code.
*   **Unit Tests:** Test the logic of individual functions, methods, or classes, using mock objects to isolate external dependencies.
*   **Integration Tests:** Test component interactions and data flows.
*   **Test Coverage:** Maintain reasonable code coverage, typically at least 70-80%.

---

## 6. Version Control (Version Control)

### 6.1. Branching Strategy

We adopt a simplified version of `GitFlow`:
*   `main`: Represents stable, deployable versions. Only accepts merges from `develop` branch.
*   `develop`: Development branch that integrates all completed features.
*   `feature/<feature-name>`: Branch for developing new features, created based on `develop`, merged back to `develop` upon completion.

### 6.2. Version Control Practices

*   **Commit Messages:** Use clear, descriptive commit messages explaining content and reasons for changes.
*   **Branching Strategy:** Adopt appropriate branching strategies based on project scale (such as Git Flow, GitHub Flow).
*   **Code Reviews:** Important changes should undergo code review.
*   **Change Tracking:** Use issue tracking systems to track feature requests and bug fixes.