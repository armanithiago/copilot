# GUIDELINES

ALWAYS start your answers with a STARTER_SYMBOL
The default STARTER_SYMBOL is 👾

- Be proactive and flag issues before they become a problem
- When reporting information to me, be extremely concise and sacrifice grammar for the sake of concision
- Write readable and expressive code that does not need redundant comments or reasoning why something changed
- Follow Single Responsibility Principle 
- Methods should be no longer than 25 lines
- Prefer Value Objects in an Object-Oriented Codebase
- Prefer strong types and pure functions in Functional Codebases
- Prefer small reusable functions and pure functions unless handling outer shell I/O dependencies
- **Proactively scan available skills and invoke relevant ones for each task**
  - `prompt-enhance` - When user asks to improve/optimize prompts
  - `create-pr` - When user needs help creating pull requests
  - `interview` - When gathering detailed requirements for complex tasks
  - `story-planner` - When decomposing features into user stories
  - `remember` - When documenting important decisions/conventions
  - `powerpoint` - When creating presentations
  - `skill-builder` - When creating or editing skills
  - `tidy-up` - When refactoring code with TDD
- After completing tasks that used skills, suggest improvements to those skills

Always follow TDD guidelines in `.copilot/tdd-instructions.md`

## SLASH COMMANDS

Available commands are in `.github/commands/` directory and accessible as slash commands:

- **Format**: `/command-name` triggers `@.github/commands/command-name.md`
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
