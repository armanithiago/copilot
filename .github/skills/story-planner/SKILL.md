---
name: story-planner
description: Break applications into thin vertical slices with clear acceptance criteria. Use this skill when asked to plan features, create user stories, or decompose requirements into implementable increments.
---

## Story Planning Process

When asked to plan stories or decompose features, follow this workflow:

### 1. Gather Context

Review available documentation:
- Requirements documents and specifications
- Event models, workflow diagrams, or business process flows
- Existing user stories, issues, or issue templates
- Architecture decisions or technical constraints
- Style guides, design patterns, or UX conventions

Ask clarifying questions:
- What user workflows or capabilities should these stories enable?
- What are the primary user personas and their needs?
- What technical constraints or dependencies exist?
- What's the priority order for delivery?

### 2. Identify Vertical Slices

Break features into thin vertical slices where each:
- Delivers complete end-to-end user value (from UI to outcome)
- Results in user-observable behavior (not internal state changes)
- Is cohesively complete (no crashes, no partial implementations)
- Aligns with natural workflow boundaries
- Represents the smallest implementable change enabling user function

### 3. Write User Stories

Use this format for each story:

**Story Title**: [User-focused capability, action-oriented]

**Description**: What this enables and why it matters (focus on user outcomes, not implementation)

**Acceptance Criteria (Gherkin)**:
```gherkin
Scenario: [User-focused scenario name]
  Given [initial user context - not technical state]
  When [user action or business event]
  Then [observable user outcome - not code behavior]
```

**Integration**: How the user accesses this feature (from which screen, through which workflow)

**Manual Testing**: Step-by-step instructions user can follow to verify the feature works

### 4. Apply Quality Checks

Before finalizing each story, verify:

- [ ] Is it a thin vertical slice delivering observable user value?
- [ ] Does the Gherkin follow Given/When/Then format correctly?
- [ ] Does it focus on WHAT/WHY, not HOW?
- [ ] Are all implementation details removed?
- [ ] Is there a clear integration point and user access path?
- [ ] Is it cohesively complete (no missing pieces)?
- [ ] Are manual testing steps clear and user-focused?

### 5. Prioritize Stories

Rank stories by:
- **User impact**: How many users benefit? How urgent is their need?
- **Business value**: Does it reduce risk or enable revenue?
- **Dependencies**: Does it block other stories?
- **Technical complexity**: Can it be completed quickly?

Document priority order with brief rationale.

## Writing Good Acceptance Criteria

**DO**:
- Focus on user outcomes: "Response appears in conversation history"
- Use clear Given/When/Then: "Given user has started session, When they send message, Then response appears"
- Write observable behaviors: "User sees success confirmation"
- Include business context: "User can reset forgotten password"

**DON'T**:
- Include implementation details: "SessionHandle<Ready> state changes to SessionHandle<Active>"
- Describe code behavior: "MessageSent event stored in database"
- Use technical jargon: "API call returns 200 status code"
- Write acceptance tests: "Run npm test to verify"

## Example Story

**Story: User can reset forgotten password**

**Description**: Users who forget their password can reset it by verifying their email, allowing them to regain account access without contacting support.

**Acceptance Criteria**:
```gherkin
Scenario: User resets password via email
  Given user is on login screen and forgot password
  When they click "Forgot Password" and enter email
  Then reset link appears in their email inbox

Scenario: User completes password reset
  Given user has reset link in email
  When they click link and enter new password
  Then they can log in with new password
```

**Integration**: "Forgot Password" link on login screen → Email with reset link → Password reset form accessible from link

**Manual Testing**:
1. Go to login screen and click "Forgot Password"
2. Enter email address
3. Check email inbox for reset link
4. Click link and enter new password
5. Return to login and verify login works with new password

## What to Remove

- Implementation details from stories (database, APIs, internal state)
- Technical jargon and code references
- HOW the system does something (that's for design docs, not stories)
- Stories without clear user-observable value
- Stories without access path through main application

## When to Stop

Stop story planning when:
- User has thin vertical slices delivering observable value
- Each story has clear acceptance criteria
- Integration path and manual testing steps are documented
- Stories can be prioritized and estimated
- User understands the breakdown and agrees with priority
