## Testing frameworks and versions:

    - Jest:Version 29.6.1
    - React Testing Library:Version 14.0.0
    - Pytest:Version 7.4.0
    - Suggest addition for testing frameworks if needed.

## Playwright E2E Testing Guidelines

1.  Test Structure and Organization

    - Store all tests under the tests/ folder.
    - Name test files based on the system component being tested (not React components) using kebab-case (e.g., checkout-flow.spec.ts).
    - Group related tests within a single file using test.describe blocks.
    - Use descriptive test names that clearly explain the functionality being tested.
    - Use test.use({storageState: ...}) for setting authentication state across all tests.

2.  Locator Strategy

    - Prefer accessibility-friendly locators:
    - Use getByRole for best accessibility and resilience.
    - Use getByText, getByLabel, or getByPlaceholder when appropriate.
    - Avoid test IDs unless absolutely necessary (e.g., for highly dynamic elements where other locators fail).

3.  Writing Tests

    - Focus on testing user-visible behavior, not implementation details.
    - Ensure tests are reproducible and isolated:
    - Use test.beforeEach() for common setup steps.
    - Avoid sharing state between tests.
    - Minimize use of page.evaluate() – favor Playwright’s built-in methods.

4.  Assertions & Reliability

    - Use web-first assertions (e.g., expect(locator).toBeVisible()).
    - Prefer assertions that automatically wait and retry (e.g., toHaveText() over textContent()).
    - Use soft assertions for non-critical checks that shouldn't fail the entire test.

5.  Handling Asynchronous Operations

    - Always use await with Playwright’s async methods.
    - Rely on Playwright’s auto-waiting instead of explicit time-based waits.
    - Use waitFor functions for handling complex conditions.

6.  Database & Test Data Management

    - Use a dedicated test database (never run tests against production).
    - Use Kysely with PostgresDialect for database queries.
    - Always reset test data between runs using migrations or fixtures.
    - Use dynamic test data generation where possible instead of hardcoded values.
    - Store database migrations for testing under src/lib/migrations/ and follow existing naming conventions.

7.  Performance & Stability

    - Keep tests focused and concise (avoid unnecessary actions).
    - Use test.slow() for inherently slow tests.
    - Implement retry logic for potentially flaky tests (retries in playwright.config.js).
    - Use parallel execution but ensure no race conditions with the database or shared resources.

8.  Cross-Browser & CI/CD Integration

    - Enable cross-browser testing for critical workflows (chromium, firefox, webkit).
    - Use test.describe.configure({ mode: 'parallel' }) for parallel execution.
    - Ensure Playwright tests integrate with CI/CD pipelines (e.g., GitHub Actions, Jenkins).
    - Store test reports, logs, and screenshots in a dedicated test output directory.

9.  Debugging & Maintenance
    - Use test.only() to focus on specific tests during development.
    - Leverage Playwright’s tracing and video recording for debugging failures.
    - Add structured logging for better debugging insights.
    - Document complex test scenarios with comments.
