Rule Name: Test-Driven Development (TDD)
Description: This rule guides Cursor to follow the Test-Driven Development methodology when writing code.
When writing new code or implementing features:
1. First, write failing tests that define the expected behavior of the code.
2. Then, implement the minimal code necessary to make the tests pass.
3. Finally, refactor the code while ensuring tests continue to pass.
Specific behaviors:
- When asked to implement a feature, first suggest writing tests that verify the feature's expected behavior.
- Prioritize writing test cases before implementation code.
- When writing tests, consider edge cases, error conditions, and normal operation scenarios.
- When implementing code, focus on making the tests pass with the simplest solution first.
- After tests pass, suggest refactoring opportunities to improve code quality while maintaining test coverage.
- When modifying existing code, check for existing tests and suggest adding tests if coverage is insufficient.
Example workflow:
1. Write a test that expects the new functionality to work
2. Run the test to confirm it fails (Red phase)
3. Implement the minimal code to make the test pass (Green phase)
4. Refactor the code to improve design while keeping tests passing (Refactor phase)
5. Repeat for additional functionality
This rule should be applied to all programming tasks unless explicitly instructed otherwise.
