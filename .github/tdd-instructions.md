# Test-Driven Development (TDD) Guidelines

Follow this TDD process when writing code.

## Process Indicators

Use these STARTER_CHARACTERS at the beginning of each response:
- 🔥 Red phase - test fails to compile or assertion fails
- 🦖 Green phase - test passes
- ☄️ Refactoring phase - improving code while all tests stay green

## Core Rules:

1. Think about what the code you want to write should do
2. Make a list of tests that are needed
3. Write a single-line test comment with `[TEST]` prefix for each test, then wait for confirmation before proceeding.
   - Example: `[TEST] Zero plus number returns that number`
   - Example: `[TEST] Division by zero throws exception`
   - **Important:** No other comments in production code; only `[TEST]` comments are permitted during this phase.
4. One test at a time - focus on the simplest, lowest-hanging fruit test
5. Predict failures - state what we expect to fail before running tests
6. Two-step red phase:
- First: Make it fail to compile (class/method doesn't exist)
- Second: Make it compile but fail the assertion (return wrong value)
7. Minimal code to pass - just enough to make the test green
8. No other comments in production code - keep it clean unless specifically asked
9. Run all tests every time - not just the one you're working on
10. Refactor at the first opportunity when all the tests are green, until there's nothing to refactor

## Process Flow:

1. Write test comment, succinct and single line, starting with a `[TEST] ` prefix
2. Write failing test (replacing the comment, not adding below it)
3. Predict what will fail
4. Run tests, see compilation error (if testing something new)
5. Add minimal code to compile
6. Predict assertion failure
7. Run tests, see assertion failure
8. Add minimal code to pass
9. Run tests, see green
10. Refactor when you see a way to improve code
11. Push back when something seems wrong or unclear

## Test Design:

**CRITICAL: Test behaviors, not implementation details**
- Focus on WHAT the code does, not HOW it does it
- Tests should survive refactoring of internal implementation
- Avoid testing private methods or internal state
- Use fakes and/or mock servers over mocks
- Use fluent assertion libraries where applicable
