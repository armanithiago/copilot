---
name: prompt-enhance
description: Optimize and refine prompts using GitHub Copilot prompt engineering best practices. Use this skill when asked to improve, enhance, or optimize a prompt for better AI-generated results.
---

## Prompt Enhancement Workflow

When asked to "improve this prompt", "enhance this prompt", "optimize this input", or similar variations, follow this systematic process to refine the prompt using proven prompt engineering techniques.

### 1. Analyze the Current Prompt

Review the provided prompt and assess:

**Quality Indicators - Check for:**
- ✅ Clear goal or objective stated?
- ✅ Specific vs. vague language?
- ✅ Constraints or requirements mentioned?
- ✅ Examples provided?
- ✅ Context or background given?
- ✅ Expected output format specified?
- ✅ Ambiguous terms that need clarification?

**Ask Clarifying Questions if Needed:**

If the prompt is:
- **Vague or ambiguous** → Ask what specific output is desired
- **Missing context** → Ask about the problem domain, constraints, target language
- **Overly broad** → Ask to focus on one specific aspect
- **Complex/multi-part** → Ask to clarify interdependencies
- **Unclear requirements** → Ask for examples of desired vs. undesired output

### 2. Identify Improvement Areas

Based on GitHub Copilot Prompt Engineering best practices, evaluate:

**Strategy 1: Start General, Then Get Specific**
```
BEFORE: "How do I validate emails?"
AFTER:  "Write a JavaScript function that validates email addresses
         
         The function should:
         - Accept a string parameter
         - Return true for valid emails, false otherwise
         - Support standard email formats (name@domain.com)
         - Reject emails without @ symbol or domain extension"
```

**Strategy 2: Give Examples**
```
BEFORE: "Generate a regex pattern for phone numbers"
AFTER:  "Generate a regex pattern that matches these phone number formats:
         
         Valid examples:
         - (555) 123-4567
         - 555-123-4567
         - 5551234567
         
         Invalid examples:
         - 123-4567 (missing area code)
         - (555) 1234 (incomplete)"
```

**Strategy 3: Break Complex Tasks into Simpler Steps**
```
BEFORE: "Build a file upload system"
AFTER:  "Help me build a file upload system by:
         1. First, create a form component that accepts file input
         2. Then, validate file size (max 5MB) and type (PDF, DOCX)
         3. Next, send to backend API endpoint
         4. Finally, display success/error messages to user"
```

**Strategy 4: Avoid Ambiguity**
```
BEFORE: "Make this function better"
AFTER:  "Improve the `calculateTax()` function for:
         - Performance: reduce computation time
         - Readability: add comments explaining tax calculation logic
         - Error handling: handle edge cases like negative amounts"
```

**Strategy 5: Indicate Relevant Context**
```
BEFORE: "Write a component"
AFTER:  "Write a React component that displays a user profile card
         
         Technology stack:
         - React 18 with TypeScript
         - Tailwind CSS for styling
         - Should accept userId prop
         - Should fetch user data from /api/users/:id"
```

### 3. Conduct Interview if Needed

**When to Interview:**
- Prompt has multiple interdependencies
- Request could have many valid interpretations
- User hasn't specified constraints/requirements
- Output format is unclear
- Missing crucial context

**Interview Questions Template:**

**For Any Prompt:**
1. "What is the **primary goal** of this prompt?"
2. "Who is the **target audience** for the output?"
3. "What **programming language** or **technology**?"
4. "What are the **key constraints or requirements**?"
5. "Should I provide any **examples** of desired output?"

**For Code Prompts:**
6. "What **framework or library** are you using?"
7. "Should the output be **simple** or **production-ready**?"
8. "Do you need **error handling**, **logging**, or **comments**?"
9. "Are there **performance** or **security** considerations?"
10. "What **input/output format** do you expect?"

**For Documentation/Writing:**
11. "What **tone/style** should the output use?" (technical, beginner-friendly, etc.)
12. "Should it include **examples**, **diagrams**, **code snippets**?"
13. "What **length** are you expecting?" (short, comprehensive, etc.)
14. "Who is the **audience**?" (engineers, managers, non-technical)

**For Data/Analysis:**
15. "What **format** should the output be?" (JSON, CSV, markdown table, etc.)
16. "Should I **filter, sort, or aggregate** the data?"
17. "Are there **specific metrics** or **calculations** needed?"
18. "Should results include **explanation** or **just data**?"

### 4. Apply Enhancement Techniques

Use GitHub Copilot's proven strategies to rewrite:

**Technique 1: Progressive Disclosure**
```
Start broad, then add details:

1. Main goal statement
2. Specific requirements (bulleted)
3. Constraints or boundaries
4. Examples of input/output
5. Special considerations
```

**Technique 2: Structured Format**
```
[Action/Verb] [Object/Target]

[Specific requirements]:
- Requirement 1
- Requirement 2
- Requirement 3

[Example input/output]:
Input: ...
Output: ...

[Constraints]:
- Constraint 1
- Constraint 2
```

**Technique 3: Context Layering**
```
Context: [Domain/problem space]
Goal: [What we're trying to achieve]
Tool/Language: [Technology stack]
Requirements: [Must-haves]
Examples: [Show, don't tell]
```

**Technique 4: Breaking Down Complexity**
```
If asking for complex task:

"Break this into steps:
1. [Step 1] - brief description
2. [Step 2] - brief description
3. [Step 3] - brief description

For step 1: [Detailed requirements]"
```

### 5. Validate Enhancement

Check improved prompt against criteria:

**Clarity** ✓
- [ ] Goal is explicitly stated
- [ ] No ambiguous pronouns ("this", "it", "that")
- [ ] Technical terms defined
- [ ] No jargon without context

**Completeness** ✓
- [ ] Constraints listed
- [ ] Input/output format specified
- [ ] Examples provided
- [ ] Target technology mentioned

**Conciseness** ✓
- [ ] Unnecessary words removed
- [ ] Structure is clear and scannable
- [ ] Multi-part tasks are separated
- [ ] One clear request per paragraph

**Actionability** ✓
- [ ] AI can understand intent
- [ ] Enough details to avoid guessing
- [ ] Success criteria are measurable
- [ ] Output format is specified

### 6. Present Enhanced Prompt

Format the improved prompt clearly:

**Structure:**
```markdown
## Original Prompt
> [User's original request]

## Enhancement Analysis
[Brief explanation of what was improved]

## Enhanced Prompt
[Improved version with best practices applied]

## Why This Works Better
- [Reason 1]
- [Reason 2]
- [Reason 3]

## Additional Tips
[Any follow-up recommendations]
```

**Example Enhancement:**

```markdown
## Original Prompt
> "How do I make a login page in React?"

## Enhancement Analysis
The original prompt is too broad and lacks specifics. The enhanced version:
- Specifies React version and styling approach
- Includes clear requirements (validation, error handling)
- Provides context about form layout
- Breaks down complex requirements into discrete features

## Enhanced Prompt
"Build a React login form component using React 18 and Tailwind CSS with:

**Form Fields:**
- Email input with email format validation
- Password input with show/hide toggle
- Remember me checkbox (optional)

**Validation:**
- Email: must contain @ and domain
- Password: minimum 8 characters
- Show validation errors below each field in red

**Functionality:**
- Submit button disabled until both fields are valid
- Show loading spinner during authentication
- Display error message if login fails
- Redirect to dashboard on successful login

**Styling:**
- Clean, centered layout
- Responsive design (mobile + desktop)
- Professional appearance suitable for SaaS application"

## Why This Works Better
- **Specific framework and version** → Copilot generates compatible code
- **Detailed requirements** → Less ambiguity, better output
- **Clear constraints** → Avoids unnecessary features
- **Structured sections** → Easier for AI to follow

## Additional Tips
After getting the component, you might ask:
- "Add OAuth login options (Google, GitHub)"
- "Add password reset functionality"
- "Add unit tests using Jest"
```

## Quick Reference: 7 Golden Rules

1. **Start with the goal** - State what you want first
2. **Be specific** - Avoid vague terms like "good", "better", "nice"
3. **Provide examples** - Show input/output or code samples
4. **Break it down** - For complex tasks, list steps separately
5. **Avoid ambiguity** - Define "this", "that", use actual names
6. **Add context** - Mention tech stack, constraints, audience
7. **Specify format** - Tell Copilot what format you want

## Common Enhancement Patterns

**Pattern 1: Vague → Specific**
```
❌ "Generate a function"
✅ "Generate a TypeScript function that filters an array of User objects"
```

**Pattern 2: Missing Examples → With Examples**
```
❌ "Create a sorting algorithm"
✅ "Create a sorting algorithm that sorts an array of numbers in ascending order
    Example input: [5, 2, 8, 1, 9]
    Example output: [1, 2, 5, 8, 9]"
```

**Pattern 3: Broad → Layered**
```
❌ "Build an API"
✅ "Build a Node.js Express API that:
    - Has a GET /users endpoint returning user objects
    - Has a POST /users endpoint creating new users
    - Uses MongoDB for persistence
    - Includes basic error handling"
```

**Pattern 4: Single Request → Broken Down**
```
❌ "Make a web application"
✅ "Build a React web app in phases:
    1. Create a Header component with navigation
    2. Create a Hero section with call-to-action
    3. Create a Footer with social links
    4. Style with Tailwind CSS"
```

## Iterative Refinement

If the enhanced prompt still needs work:

1. **Test it** - Use the enhanced prompt with Copilot
2. **Evaluate output** - Does Copilot produce what you expected?
3. **Identify gaps** - What was missing or incorrect?
4. **Refine further** - Apply techniques again
5. **Document learnings** - Note what works for future prompts

**Iteration Loop:**
```
Original Prompt → Enhance → Test → Evaluate → Refine → Done
```

## Resources Referenced

- [GitHub Docs: Prompt Engineering](https://docs.github.com/en/copilot/concepts/prompting/prompt-engineering)
- [GitHub Blog: How to Write Better Prompts](https://github.blog/developer-skills/github/how-to-write-better-prompts-for-github-copilot/)

### Key Strategies from Official Docs:
1. **Start general, then get specific** - Broad goal first, then specific requirements
2. **Give examples** - Use input/output examples to clarify intent
3. **Break complex tasks into simpler tasks** - Divide and conquer
4. **Avoid ambiguity** - Be specific with terminology
5. **Indicate relevant code** - Provide context about your project
6. **Experiment and iterate** - Refine prompts based on results
7. **Keep history relevant** - In Copilot Chat, maintain focused conversation

## When to Use This Skill

Copilot should automatically invoke this skill when user:
- Says "improve this prompt"
- Says "enhance this prompt"
- Says "optimize this request"
- Says "make this prompt better"
- Says "help me refine this prompt"
- Says "this prompt isn't working, help"
- Provides a prompt and asks "how can I improve this?"

## Skill Boundaries

**This skill helps with:**
- ✅ Refining unclear prompts
- ✅ Adding structure and specificity
- ✅ Identifying missing context
- ✅ Breaking down complex requests
- ✅ Creating examples and test cases
- ✅ Explaining why changes improve results

**This skill doesn't:**
- ❌ Execute the refined prompt (user does that)
- ❌ Generate content based on prompt (that's for content skills)
- ❌ Modify user's actual code (that's other skills)
- ❌ Assume missing information (interviews instead)
---
**Sub-agent invocation:** Use the command `#runSubagent` to invoke sub-agents; include a unique `subAgentInvocationId` string (e.g., a UUID) to correlate nested calls and avoid ambiguity.
