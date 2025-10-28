# Speckit Constitution

## Core Principles

### I. High Quality & Clean Code
Code is written for humans first, machines second. Follow DRY (Don't Repeat Yourself) principle, avoid duplicate code. Adopt KISS (Keep It Simple, Stupid) principle - choose the simplest direct solution unless there's sufficient reason otherwise.

### II. Testability
All code must be testable. Adopt Test-Driven Development (TDD) approach: Write tests first → Tests fail → Implement functionality → Tests pass → Refactor. Maintain reasonable code coverage, typically at least 70-80%.

### III. Minimum Viable Product
Avoid over-engineering. Start with the simplest solution and iterate based on actual needs. Follow YAGNI (You Aren't Gonna Need It) principles.

### IV. Traditional Chinese First
All documentation, comments, and responses use Traditional Chinese. Ensure team communication consistency.

### V. Developer Execution Checklist
Developers must follow these steps when making any changes:
1. Preparation Phase: Read files to be modified and related dependencies, avoid guessing. If location search needed, use search tools first, then read files. Record key decision points and design considerations.
2. Follow Standards: Adhere to official coding standards for each programming language. Use appropriate formatting tools and Linters.
3. Change Implementation: Add annotations before changes (date/author/story/task). Use minimal edits; avoid unrelated changes. Track todos, update status when completed.
4. Verification & Consistency: Run Lint and format checks, fix identified issues.
5. Documentation Sync: Update related documentation and comments.
6. Commit Description: Use clear commit messages describing the changes.

## Coding Standards

### Style & Formatting
- Follow official coding standards and conventions for each programming language.
- Use automatic formatting tools (such as Prettier, Black, gofmt, etc.).
- Use language-specific static analysis tools (Linters) to catch potential errors.

### Naming Conventions
Maintain consistent naming conventions:

| Element | Common Convention | Example |
|---------|-------------------|---------|
| Variables | camelCase or snake_case | `userName`, `user_name` |
| Functions/Methods | camelCase or snake_case | `calculateTotal()`, `calculate_total()` |
| Classes/Types | PascalCase | `UserService`, `ProjectManager` |
| Constants | UPPER_SNAKE_CASE | `MAX_RETRY_COUNT`, `DEFAULT_TIMEOUT` |
| Private Members | Prefix underscore | `_privateField`, `_internalMethod()` |

### Documentation & Comments
- All public APIs must have complete documentation.
- Add comments for complex logic.
- Use standard documentation formats (such as JSDoc, docstrings, XML comments).

## Security
- Sensitive Information Management: All sensitive information stored in environment variables or secure configuration systems, never committed to version control.
- Input Validation: Always validate and sanitize user input to prevent injection attacks.
- Authentication & Authorization: Implement appropriate authentication and permission checking mechanisms.
- Data Encryption: Encrypt sensitive data during storage and transmission.
- Dependency Updates: Regularly update third-party dependencies to patch known security vulnerabilities.

## Testing Strategy
- Choose appropriate testing frameworks based on programming language (such as JUnit, pytest, Jest, Vitest, etc.).
- Place test files in corresponding directory structures with source code.
- Unit Tests: Test logic of individual functions, methods, or classes, using mocks to isolate external dependencies.
- Integration Tests: Test interactions and data flow between components.
- Test Coverage: Maintain 70-80% or higher coverage.

## Version Control
Adopt simplified GitFlow:
- `main`: Stable, releasable version. Only accepts merges from `develop` branch.
- `develop`: Development branch, integrates all completed features.
- `feature/<feature-name>`: New feature branches, created based on `develop`, merged back to `develop` when completed.

Practices:
- Clear, descriptive commit messages.
- Important changes undergo code review.
- Use issue tracking systems to track feature requests and bug fixes.

## Development Workflow

### Code Review
All changes must undergo code review. Review focuses include:
- Compliance with coding standards
- Test coverage
- Security considerations
- Performance impact

### Quality Gates
- All tests must pass
- Lint checks pass without errors
- Code coverage meets standards
- Security scans pass

## Governance
Constitution supersedes all other practices. All PRs/reviews must verify compliance. Complexity must be justified. Use relevant guidance documents for development guidance.

**Version**: 1.0 | **Ratified**: 2025-10-28 | **Last Amended**: 2025-10-28