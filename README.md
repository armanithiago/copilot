# Copilot CLI Enhancements

A repository for saving, managing, and improving reusable **skills**, **commands**, **prompts**, and **agents** for GitHub Copilot CLI. This project enables collaborative development and improvement of Copilot capabilities through shared markdown-based definitions.

## 📁 Project Structure

```
.github/
├── skills/                    # Reusable specialized agents/skills
│   ├── interview/            # Deep requirement gathering interviews
│   ├── create-pr/            # Pull request creation assistance
│   ├── prompt-enhance/       # Prompt optimization and improvement
│   ├── tidy-up/              # TDD-based code refactoring
│   ├── story-planner/        # User story decomposition
│   ├── skill-builder/        # Create/edit skills
│   ├── remember/             # Document decisions & conventions
│   └── powerpoint/           # Presentation creation
├── commands/                 # CLI commands and handlers
│   ├── save.md              # Save work/artifacts
│   ├── review.md            # Code review commands
│   └── exploratory-testing.md # Testing commands
├── projects/                 # Project configurations
├── output-styles/            # Custom output formatting
├── copilot-instructions.md   # Core Copilot guidelines
├── command-approvals.md      # Security & execution policies
└── tdd-instructions.md       # TDD best practices
```

## 🚀 Getting Started

### Basic Commands

#### Skills Management

**Load/Reload All Skills**
```bash
/skills reload
```
This reloads all skill definitions from `.github/skills/` directory, ensuring you have the latest versions.

**Add a Skill for Current Session Only**
```bash
/skills add <skill-name>
```
Loads a specific skill (e.g., `interview`, `create-pr`, `prompt-enhance`) for the current session without permanently modifying configurations.

**List Available Skills**
```bash
/skills list
```
Shows all available skills in the repository.

#### Saving & Managing Artifacts

**Save Work**
```bash
/save <file-or-directory>
```
Saves completed work, improvements, or new skill/prompt definitions to the repository for team reuse.

**Review Code Changes**
```bash
/review <file-or-branch>
```
Initiates an interactive code review session.

**Exploratory Testing**
```bash
/test explore <target>
```
Run exploratory testing on features or code.

---

## 📚 Available Skills

### 1. **interview**
Conduct structured interviews to gather deep requirements for plans, designs, or ideas.
- Asks one non-obvious question at a time
- Covers technical, UX, risks, and tradeoffs
- Produces implementation-ready specifications

### 2. **create-pr**
Assists with creating well-structured pull requests.
- Generates PR titles and descriptions
- Ensures commit messages are clear
- Pre-approved for git write operations

### 3. **prompt-enhance**
Optimizes and improves Copilot prompts.
- Analyzes prompt clarity and completeness
- Suggests improvements for better outputs
- Tests prompts iteratively

### 4. **tidy-up**
Refactors code using TDD (Test-Driven Development) principles.
- Maintains existing functionality
- Improves code quality
- Runs tests at each step

### 5. **story-planner**
Decomposes features into user stories.
- Creates acceptance criteria
- Estimates complexity
- Identifies dependencies

### 6. **skill-builder**
Create new skills or improve existing ones.
- Generates SKILL.md templates
- Validates skill definitions
- Tests skills before publishing

### 7. **remember**
Document important decisions, conventions, and best practices.
- Stores knowledge for team reuse
- Prevents duplicate work
- Builds institutional memory

### 8. **powerpoint**
Create and manage presentations.
- Generates presentation structures
- Converts content to slides
- Exports in standard formats

---

## 💡 Usage Examples

### Example 1: Improving a Feature Specification
```
You: I have an idea for a new authentication system. Can you interview me about it?

Copilot: /interview
↳ Loads the interview skill and starts asking structured questions about your design
```

### Example 2: Creating a Custom Prompt
```
You: I want to optimize this prompt for better outputs

Copilot: /prompt-enhance my-prompt.md
↳ Analyzes your prompt and suggests improvements
```

### Example 3: Refactoring Code with Tests
```
You: Can you clean up this function while keeping tests passing?

Copilot: /tidy-up src/utils.js
↳ Uses TDD to refactor while maintaining all functionality
```

### Example 4: Saving a New Skill
```
You: I created a useful skill for validating schemas. Save it.

Copilot: /save .github/skills/schema-validator/
↳ Saves your skill definition for team reuse
```

---

## 📖 Core Guidelines

### Copilot Instructions
Located in `.github/copilot-instructions.md`:
- Guidelines for code quality (SRP, method length limits, strong types)
- Skill activation triggers
- Command execution policies
- Documentation best practices

### Command Approvals
Located in `.github/command-approvals.md`:
- **Auto-approved**: File navigation, npm/dotnet, git reads
- **Pre-approved with skills**: Git write operations (when using `create-pr` skill)
- **Requires approval**: Destructive operations, npm publish
- **Blocked**: Privilege escalation, credential access

### TDD Instructions
Located in `.github/tdd-instructions.md`:
- Test-driven development practices
- Red-green-refactor cycle
- Best practices for this codebase

---

## 🤝 Contributing

### Adding a New Skill

1. Create a directory under `.github/skills/<skill-name>/`
2. Create a `SKILL.md` file with the skill definition (use the `skill-builder` skill to help)
3. Include metadata at the top:
   ```markdown
   ---
   name: skill-name
   description: >
     Clear description of what this skill does.
   ---
   ```
4. Save your skill using `/save .github/skills/<skill-name>/`
5. Test it with `/skills add <skill-name>`

### Adding a New Command

1. Create a markdown file under `.github/commands/<command-name>.md`
2. Document the command syntax and behavior
3. Save using `/save .github/commands/<command-name>.md`

### Improving Existing Skills/Prompts

1. Modify the skill or prompt file
2. Test locally with the skill: `/skills add <skill-name>`
3. Save improvements: `/save <path-to-file>/`
4. Push to your branch and create a PR for review

---

## 🔧 Workflow

### Typical Workflow

1. **Load skills** for your task: `/skills reload` or `/skills add <skill-name>`
2. **Work on improvements**: Ask Copilot to use relevant skills
3. **Save artifacts**: Use `/save` when you want to preserve work
4. **Create PR**: Push to a feature branch and create a pull request
5. **Review & merge**: Team reviews and merges to master

### Session-Based Skill Loading

If you only want to test a skill for the current session:
```bash
/skills add interview    # Add just this skill
# Use it in your conversation
# It's automatically removed when session ends
```

---

## 📋 Requirements

- **GitHub Copilot CLI** installed and configured
- **Git** for version control
- **.github directory structure** as defined above
- **Markdown knowledge** for creating/editing skills and prompts

---

## 🔐 Security & Policies

All command execution follows policies in `.github/command-approvals.md`. Copilot will:
- Auto-approve safe file operations and reads
- Ask for confirmation on destructive operations
- Block privilege escalation attempts
- Require skill-based pre-approval for git writes

---

## 📝 License

This repository is for internal GitHub Copilot CLI improvements and enhancements.

---

## 🤔 FAQ

**Q: Can I use a skill without loading it globally?**  
A: Yes! Use `/skills add <skill-name>` to load it for the current session only.

**Q: How do I save my improvements?**  
A: Use `/save <file-or-directory>` to save changes. This adds them to git staging.

**Q: Do all commands require approval?**  
A: No. Read `.github/command-approvals.md` for the approval matrix. Most safe operations are auto-approved.

**Q: Can I create a custom skill?**  
A: Yes! Use the `skill-builder` skill or follow the structure in existing skills. Test with `/skills add` before saving.

---

## 🚀 Quick Start Checklist

- [ ] Clone the repository
- [ ] Run `/skills reload` to load all skills
- [ ] Read `.github/copilot-instructions.md` for guidelines
- [ ] Check `.github/command-approvals.md` for allowed commands
- [ ] Try a skill: `/skills add interview`
- [ ] Save your first improvement: `/save <your-file>`
- [ ] Create a PR and merge to master

---

**Happy collaborating! 🎉**
