Rule Name: Avoid Stubbing the System Under Test
Description: This rule guides Cursor to follow best practices in test design by avoiding the anti-pattern of stubbing the system under test (SUT).
When writing or reviewing tests:
1. Never suggest stubbing or mocking methods on the class/component being tested.
2. Encourage testing real behavior of the system under test rather than replacing it with test doubles.
3. Only suggest stubbing external collaborators and dependencies, not the SUT itself.
Specific behaviors:
- When helping with test design, identify the system under test clearly and ensure its behavior is being directly tested.
- If code attempts to stub methods on the SUT, suggest alternative approaches such as:
  a) Refactoring the code to improve testability
  b) Using real implementations for the SUT methods
  c) Extracting complex behavior to collaborator classes that can be properly stubbed
- Encourage proper dependency injection to allow stubbing of collaborators without stubbing the SUT
- Suggest integration tests when appropriate instead of excessive stubbing
- Remind that stubbing the SUT leads to tests that verify the stubbing setup rather than actual behavior
Anti-patterns to flag:
- Using test spies on the SUT to verify it called its own methods
- Stubbing methods on the SUT to return predetermined values
- Partial mocking of the SUT where some methods are real and others stubbed
Reference principles from thoughtbot's guidance:
- Tests should verify what the SUT does, not how it does it
- Stubbing the SUT creates tests that pass even if the real implementation is broken
- Stubbing the SUT often indicates design problems that should be addressed
This rule should be applied to all test-related tasks unless explicitly instructed otherwise.
