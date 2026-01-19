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

## COMMAND EXECUTION POLICY

**CRITICAL:** Follow `.github/command-approvals.md` for all shell/CLI commands:
- **Auto-approved**: File navigation, npm/node, dotnet, git reads, safe PowerShell
- **Auto-approved with `create-pr` skill**: Git write ops (branch, add, commit, push, PR creation)
- **Requires approval**: Git destructive ops (reset, revert), npm publish, force-delete
- **Blocked**: Privilege escalation, credential access, registry mutations

When executing commands:
1. Check the approvals policy before running
2. When using `create-pr` skill, git PR workflow commands are pre-approved
3. Ask for confirmation on any command not in the approved lists
4. Never attempt commands in the Blocked category
5. Always explain WHY you're running a command before executing it

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
