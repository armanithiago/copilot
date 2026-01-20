---
name: remember
description: Guide for documenting important insights to persist across sessions. Use this skill when asked to save codebase facts, conventions, project knowledge, or architectural decisions to CLAUDE.md.
---

## Documenting Important Facts

When asked to remember or document something important, follow these steps:

1. **Identify the fact type**:
   - Codebase conventions (naming, structure, patterns)
   - User preferences (coding style, tools, workflows)
   - Project knowledge (architecture, dependencies, technical decisions)
   - Bootstrap and build commands
   - File-specific information

2. **Check CLAUDE.md first**:
   - Read the current CLAUDE.md file
   - Avoid duplicating information already documented
   - Group related facts together

3. **Write the fact entry**:
   - **Subject**: 1-2 words identifying the topic (e.g., "naming conventions", "testing practices")
   - **Fact**: Clear, actionable statement under 200 characters
   - **Category**: bootstrap-and-build, user-preferences, general, or file-specific
   - **Citations**: Reference specific files or user input that established this fact
   - **Reason**: Explain why this fact is important for future tasks

4. **Format for persistence**:
   ```
   ## [Subject]
   
   **Fact**: [Clear statement of the convention or pattern]
   
   **Category**: [bootstrap-and-build | user-preferences | general | file-specific]
   
   **Citations**: [File paths or "User input: [description]"]
   
   **Reason**: [Why this matters for future tasks]
   ```

5. **Update CLAUDE.md**:
   - Add or update the documented fact
   - Keep entries organized by subject
   - Remove outdated information
   - Request user approval before making changes

## What to Document

**Document these**:
- Build/test commands that work (`npm run build`, `cargo build`, etc.)
- Naming conventions observed across the codebase
- Testing frameworks or practices in use
- Authentication or sanitization patterns
- Architecture decisions that constrain future work
- User-stated preferences (tabs vs spaces, single vs double quotes, language choices)

**Don't document**:
- Transient details (file paths, temporary states)
- Information already in code comments
- Facts easily inferred from codebase inspection
- Duplicates of existing CLAUDE.md entries

## Examples

**Good facts to remember**:
- "Use JWT for authentication in API endpoints"
- "Test files in `/tests` directory follow Jest conventions"
- "Sanitize user input with html_escape to prevent XSS"
- "Build with `npm run build`, test with `npm run test`"

**Bad facts** (too vague or redundant):
- "The project uses TypeScript" (easily inferred)
- "Fix bugs" (not actionable)
- "Important file" (unclear what matters about it)
---
**Sub-agent invocation:** Use the command `#runSubagent` to invoke sub-agents; include a unique `subAgentInvocationId` string (e.g., a UUID) to correlate nested calls and avoid ambiguity.
