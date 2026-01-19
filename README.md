# Copilot CLI Enhancements

Repository for managing reusable **skills**, **commands**, and **agents** for GitHub Copilot CLI.

## 📍 Key Files

| File | Purpose |
|------|---------|
| [`.github/copilot-instructions.md`](.github/copilot-instructions.md) | Core guidelines, quality standards, skill triggers |
| [`.github/command-approvals.md`](.github/command-approvals.md) | Security policies and command approval matrix |
| [`.github/tdd-instructions.md`](.github/tdd-instructions.md) | TDD best practices |
| [`.copilot/tdd-instructions.md`](.copilot/tdd-instructions.md) | TDD workflow details |

## 🎯 Available Skills

- **interview** - Deep requirement gathering interviews
- **create-pr** - Pull request creation assistance
- **prompt-enhance** - Prompt optimization
- **tidy-up** - TDD-based code refactoring
- **story-planner** - Feature decomposition into user stories
- **skill-builder** - Create/edit skills
- **remember** - Document decisions & conventions
- **powerpoint** - Create presentations

Each skill lives in `.github/skills/<skill-name>/SKILL.md`

## 🚀 Quick Start

```bash
/skills reload              # Load all skills
/skills add <skill-name>    # Load specific skill for session
/skills list                # List available skills
/save <path>               # Save work to repository
```

## 📝 Commands

Available commands in `.github/commands/`:
- `/analyze-project` - Generate project-specific development instructions
- `/save` - Save session memories to project memory
- `/review-plan` - Review plans for gaps and assumptions

## 🔧 Add a New Skill

1. Create `.github/skills/<skill-name>/SKILL.md`
2. Include skill metadata and behavior definition
3. Test: `/skills add <skill-name>`
4. Save: `/save .github/skills/<skill-name>/`

## 📋 Requirements

- GitHub Copilot CLI installed
- Git for version control
- `.github` directory structure

## 🔐 Security

Command execution follows `.github/command-approvals.md`:
- Auto-approved: File reads, npm/dotnet commands
- Pre-approved: Git writes (with `create-pr` skill)
- Blocked: Privilege escalation, credentials access

## 🤝 Contributing

### Add a New Skill
1. Create `.github/skills/<skill-name>/SKILL.md`
2. Define behavior, triggers, and usage examples
3. Test: `/skills add <skill-name>`
4. Save: `/save .github/skills/<skill-name>/`

### Add a New Command
1. Create `.github/commands/<command-name>.md`
2. Document syntax, behavior, and examples
3. Save: `/save .github/commands/<command-name>.md`

### Add Project Instructions
1. Create `.github/instructions/<project-name>-instructions.md`
2. Include architecture, patterns, naming conventions, and constraints
3. Save: `/save .github/instructions/<project-name>-instructions.md`

### Add Memories/Documentation
1. Use `store_memory` tool to save conventions and facts
2. Or create `.github/memories/<topic>.md` for shared knowledge
3. Save: `/save .github/memories/`

### Improve Existing Artifacts
1. Edit the file directly
2. Test locally if applicable
3. Commit and create a PR or use `/save` for quick additions

All contributions should follow `.github/copilot-instructions.md` guidelines.
