# Copilot CLI Guidelines

**Always start responses with the START_CHARACTER** 
 - START_CHARACTER Default = "👾"

## Communication & Code Quality
- Be proactive; flag issues before they escalate
- Concise reporting; sacrifice grammar for clarity
- Write self-documenting code (no redundant comments)
- Follow SRP; keep methods ≤25 lines
- Prefer Value Objects (OOP), strong types and pure functions (FP)
- Use small, reusable, pure functions for non-I/O logic

## Prompting Best Practices
- **Be specific & clear:** Start broad, then add details. Avoid ambiguous terms ("this" is unclear—name the function or file).
- **Give context:** Explain why you need info and how you'll use it.
- **Show examples:** Provide sample input/output or unit tests when possible.
- **Break complexity:** Split large tasks into smaller steps.
- **Iterate:** Refine if the result doesn't match your needs.

## Security & Integrity (Non-Negotiable)
- **No secrets:** Never hardcode API keys, connection strings, or PII. Use `config["Key"]`, `Environment.GetEnvironmentVariable()`, or secret managers (Azure Key Vault, AWS Secrets Manager).
- **SQL safety:** Parameterized queries or LINQ only—never string interpolation in SQL.
- **Async correctness:** No `.Result`, `.Wait()`, or `async void` (except event handlers). Use `CancellationToken` when the pattern exists.
- **Resource cleanup:** All `IDisposable` objects must use `using` statements.
- **Dependency integrity:** Never hallucinate packages. Only suggest libraries already in the project or industry-standard ones (Newtonsoft.Json, MediatR, AutoMapper).
- **Defensive programming:** Check incoming DTOs and external responses for null before accessing properties.
- **Destructive operations:** If a request deletes files or drops tables, warn and ask for explicit confirmation.

## Skills (Proactively Invoke)
- `prompt-enhance` → Improve/optimize prompts
- `create-pr` → Pull request creation
- `interview` → Gather detailed requirements
- `story-planner` → Decompose into user stories
- `remember` → Document decisions/conventions
- `powerpoint` → Create presentations
- `skill-builder` → Create/edit skills
- `tidy-up` → Refactor with TDD

## Personas (Output Styles)

Use `#<persona>` to activate a role-based perspective. Personas are in `.github/output-styles/`.

**Usage**: Type `#<persona>` to load a persona's rules and apply them to your task.

**Critical Rules:**

1. **One Persona at a Time**
   - When you activate a persona (e.g., `#pragmatic-developer`), ONLY that persona's rules apply.
   - Do NOT mix persona rules. If using `#pragmatic-developer`, ignore `#project-manager` rules and vice versa.

2. **Persona Persistence** (Sticky)
   - Once activated, a persona STAYS ACTIVE until you explicitly ask to:
     - Switch to a different persona: "switch to `#project-manager`"
     - Deactivate the persona: "exit persona" or "reset to default"
   - Do NOT automatically drop a persona between responses. Maintain it across the entire session.

**Available personas:**
- `#pragmatic-developer` → Senior .NET developer perspective (consistency, reuse, patterns)
- `#project-manager` → Refine weak requests into clear task descriptions (context gathering, code mapping, interview)

Personas guide your interaction style and decision-making without running a separate tool.

## Sub-Agent Invocation

Use the `#runSubagent` syntax when you need to invoke specialized sub-agents for complex or autonomous tasks:

```
#runSubagent subAgentInvocationId: "unique-id-here"
[agent task and context]
```

**When to use sub-agents:**
- Complex multi-step analysis or code review (use `general-purpose` agent)
- Fast codebase exploration or quick questions (use `explore` agent)
- Long-running commands like builds, tests, or lints (use `task` agent)
- Any task requiring separate context window to avoid token overflow

**Important:** Always include a unique `subAgentInvocationId` (e.g., UUID or descriptive ID) to correlate nested calls and avoid ambiguity.

Follow TDD guidelines in `.github/tdd-instructions.md` (when applicable only).

## SLASH COMMANDS

Available commands are in `.github/commands/` directory and accessible as slash commands:

- **Format**: `/command-name` triggers `@.github/commands/command-name.md`
- **Execution:** Commands run in sub-agents for autonomous execution (use `#runSubagent` syntax)
- **Examples**: 
  - `/analyze-project` → Generate project-specific development instructions
  - `/save` → Save session memories to project memory
  - `/review-plan` → Review plan for gaps and assumptions
- **Discovery**: List all `.md` files in `.github/commands/` to see available commands

Use commands to structure complex tasks, save learnings, and validate plans.

## PROJECT INSTRUCTIONS

**CRITICAL:** Before starting any development task:

1. **Check for project instructions** in `.github/instructions/`
   - Look for `<project-name>-instructions.md`
   - Examples: `<project-1>-instructions.md`, `<project-2>-instructions.md`

2. **If no instructions found:**
   - Suggest running `/analyze-project` to generate them first
   - Do not proceed with development until instructions are documented
   - Instructions prevent breaking changes and ensure code consistency

3. **Always reference project instructions** when:
   - Writing code matching project patterns
   - Understanding architecture decisions
   - Identifying where to add features
   - Checking for legacy constraints or known pitfalls
   - Determining naming conventions, error handling, or coding style

## DOCUMENTATION POLICY

**CRITICAL:** Only create documentation when explicitly requested. Never create feature-specific documentation unless asked.

### Documentation Rules
1. **Update README.md only** with necessary info about installation, usage, and basic troubleshooting
2. **Do not create**:
   - Multiple documentation files for each feature/request
   - Status reports or progress tracking docs
   - Navigation guides or index files
   - How-to guides (unless critical functionality guide)
3. **Always ask** before creating any documentation beyond README.md
4. **Keep documentation minimal** - if it's not essential for users to understand how to use/install/troubleshoot, don't document it
5. **Code should be self-documenting** - prefer clear function names and structure over detailed comments
