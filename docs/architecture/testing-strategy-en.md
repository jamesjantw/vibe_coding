# BMad Method V6 Alpha - Universal Testing Strategy

**BMad Method Version:** V6 Alpha (6.0.0-alpha.6)

## Testing Pyramid (Testing Pyramid)

```
E2E Tests
    /  \
  Integration Tests
    /    \
  Unit Tests
```

## Test Organization (Test Organization)

### Universal Test Structure

```
tests/
├── unit/                    # Unit tests
│   ├── components/          # UI component tests
│   ├── services/            # Service layer tests
│   ├── models/              # Data model tests
│   └── utils/               # Utility function tests
├── integration/             # Integration tests
│   ├── api/                 # API integration tests
│   └── workflows/           # Business process tests
├── e2e/                     # End-to-end tests
│   ├── user-journeys/       # User journey tests
│   └── critical-paths/      # Critical path tests
└── performance/             # Performance tests
```

## Test Examples (Test Examples)

### Unit Test Example (Unit Test Example)

```javascript
// JavaScript/TypeScript unit test
import { calculateTotal } from '../utils/calculator';

describe('calculateTotal', () => {
  test('should return correct sum for valid inputs', () => {
    expect(calculateTotal([1, 2, 3])).toBe(6);
  });

  test('should handle empty array', () => {
    expect(calculateTotal([])).toBe(0);
  });
});
```

### Integration Test Example (Integration Test Example)

```python
# Python integration test
import pytest
from services.user_service import UserService
from repositories.user_repository import UserRepository

def test_user_creation_flow():
    repo = UserRepository()
    service = UserService(repo)

    user = service.create_user("john@example.com", "John Doe")
    assert user.email == "john@example.com"
    assert user.name == "John Doe"
    assert user.id is not None
```

### E2E Test Example (E2E Test Example)

```typescript
// Playwright E2E test
import { test, expect } from '@playwright/test';

test('user can create and view tasks', async ({ page }) => {
  await page.goto('/tasks');

  // Create new task
  await page.click('[data-testid="new-task-button"]');
  await page.fill('[data-testid="task-title"]', 'Test Task');
  await page.click('[data-testid="save-task"]');

  // Verify task created
  await expect(page.locator('[data-testid="task-list"]')).toContainText('Test Task');
});
```

## Testing Strategy (Testing Strategy)

### Testing Goals
- **Unit Tests**: Verify correctness of individual modules and functions
- **Integration Tests**: Verify module interactions and data flows
- **E2E Tests**: Verify complete user workflows
- **Performance Tests**: Ensure system response times meet requirements

### Testing Framework Selection
Choose appropriate testing frameworks based on programming language:

| Language | Unit Testing Framework | Integration/E2E Testing | Mocking Tools |
|----------|----------------------|-------------------------|---------------|
| JavaScript/TypeScript | Jest, Vitest | Playwright, Cypress | Jest mocks |
| Python | pytest, unittest | pytest, Selenium | unittest.mock |
| Java | JUnit, TestNG | Selenium, RestAssured | Mockito |
| C# | NUnit, xUnit | Selenium, SpecFlow | Moq |
| Go | testing (standard library) | - | - |

### Test Coverage Goals
- **Unit Tests**: 80%+ code coverage
- **Integration Tests**: Cover all critical interaction paths
- **E2E Tests**: Cover main user workflows
- **Error Scenarios**: Cover common errors and exception handling

## Test Execution Environment

### Local Test Environment
Execute tests based on the testing framework used:

```bash
# JavaScript/TypeScript (Jest)
npm test                    # Execute all tests
npm test -- --watch         # Watch mode
npm test -- --coverage      # Generate coverage report

# Python (pytest)
pytest tests/               # Execute all tests
pytest tests/unit/ -v       # Verbose output
pytest --cov=src tests/     # Coverage report

# Java (Maven)
mvn test                    # Unit tests
mvn verify                  # Integration tests
mvn surefire-report:report  # Test report
```

### CI/CD Integration Testing
- **Trigger Conditions**: Code pushes, PR creation, scheduled execution
- **Test Scope**: Unit tests, integration tests, E2E tests
- **Quality Gates**: Test pass rate > 95%, coverage meets project standards
- **Report Output**: Test results, coverage reports, performance benchmarks

## Test Data Management

### Test Data Strategy
- **Mock Data**: Create realistic test data sets
- **Data Isolation**: Ensure test data doesn't interfere between tests
- **Data Cleanup**: Automatically clean test data after tests
- **Edge Cases**: Cover normal, edge, and abnormal data scenarios

### Test Database Setup
- **Development Environment**: Use in-memory databases for fast testing
- **Test Environment**: Use dedicated test databases
- **Database Migration**: Support schema migration for test environments

## Quality Assurance Process

### Code Review Standards
- **Test Requirements**: New features must include corresponding test cases
- **Test Quality**: Test cases must be clear and maintainable
- **Edge Testing**: Cover normal and abnormal scenarios
- **Performance Considerations**: Avoid test cases affecting system performance

### Continuous Integration Process
1. **Code Submission**: Trigger automatic syntax checks
2. **Test Execution**: Automatically execute complete test suite
3. **Quality Verification**: Confirm test pass rates and coverage
4. **Deployment Preparation**: Only allow deployment of code passing tests

## Test Type Detailed Description

### Unit Tests (Unit Tests)
- **Goal**: Verify correctness of individual functions and methods
- **Scope**: Isolated testing, no external resource dependencies
- **Tools**: Language-specific unit testing frameworks
- **Execution Time**: Fast, usually completed in seconds

### Integration Tests (Integration Tests)
- **Goal**: Verify module interactions and data flows
- **Scope**: Test module integration points and interface contracts
- **Tools**: Testing frameworks + test databases/services
- **Execution Time**: Medium, usually completed in tens of seconds

### End-to-End Tests (E2E Tests)
- **Goal**: Verify complete user workflows
- **Scope**: Complete flow from user operations to system responses
- **Tools**: Selenium, Playwright, Cypress, etc.
- **Execution Time**: Longer, usually takes minutes

### Performance Tests (Performance Tests)
- **Goal**: Verify system performance indicators meet requirements
- **Scope**: Response times, resource usage, load handling
- **Tools**: JMeter, k6, load testing tools
- **Execution Time**: Varies by test scale

## Test Automation

### Automated Testing Pipeline
- **Trigger Mechanisms**: Code submissions, scheduled executions, manual triggers
- **Parallel Execution**: Support multi-threaded test execution
- **Result Reporting**: Automatically generate test reports and trend analysis
- **Failure Notifications**: Automatically notify relevant personnel of test failures

### Test Environment Management
- **Environment Isolation**: Development, testing, production environments separated
- **Environment Replication**: Support quick replication and restoration of test environments
- **Resource Monitoring**: Track test environment resource usage

## Test Result Analysis

### Test Metrics Tracking
- **Pass Rate**: Overall test pass rate statistics
- **Execution Time**: Test execution time trend analysis
- **Coverage**: Code coverage tracking and improvement
- **Error Rate**: Test failure rate and cause analysis

### Test Reports
- **Detailed Reports**: Include test results, error details, performance indicators
- **Trend Analysis**: Long-term test result trend tracking
- **Improvement Suggestions**: Quality improvement suggestions based on test results

## Test Team Roles

### Development Engineers
- Responsible for writing and maintaining unit tests
- Ensure new features include corresponding test cases
- Participate in test failure issue diagnosis and resolution

### QA Engineers
- Responsible for integration test and E2E test design
- Execute test validation and quality assessment
- Provide test result analysis and improvement suggestions

### Architects
- Define test architecture and strategy direction
- Review test case design and coverage
- Guide test technology selection and tool usage

## Test Documentation Standards

### Test Case Documentation
- **Clear Description**: Clearly explain test purpose and verification points
- **Preconditions**: List necessary conditions for test execution
- **Test Steps**: Detailed operation step instructions
- **Expected Results**: Clear verification standards and success conditions
- **Test Data**: Provide test data examples and preparation methods

### Test Report Documentation
- **Execution Summary**: Test result overview and key indicators
- **Detailed Results**: Execution results and error details for each test case
- **Trend Analysis**: Long-term test result trends and improvement suggestions
- **Issue Tracking**: Records and status tracking of issues discovered during testing