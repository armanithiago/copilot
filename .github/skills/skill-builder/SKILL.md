---
name: skill-builder
description: Guide for creating and editing GitHub Copilot CLI skills for .NET developers. Use this skill when building new skills from scratch, editing existing skills to improve clarity or reliability, or converting Claude skills into Copilot-compatible format.
---

## Creating a New Skill

When asked to create a new skill, follow these steps:

1. **Gather requirements** by asking:
   - What .NET workflow should this skill handle?
   - When should Copilot use this skill?
   - Is it project-scoped or user-scoped?
   - Does it operate on solutions, projects, or repositories?

2. **Design the skill structure**:
   - Skill directory: lowercase with hyphens (e.g., `api-testing`, `build-automation`)
   - Main file: `SKILL.md` with YAML frontmatter and instructions
   - Supporting files: Scripts, examples, with intention-revealing names

3. **Write the SKILL.md file**:
   - **Frontmatter section**: Define `name` (lowercase, hyphen-separated) and `description` (clear, action-oriented)
   - **Markdown body**: Concrete step-by-step instructions, not philosophy or explanations
   - **Instruction style**: Use imperative language ("Run X, then validate Y")
   - **Target length**: Approximately 400 lines or less

## Skill Directory Structure

For project skills (repository-specific):
```
.github/skills/skill-name/
  SKILL.md
  example-script.ps1
  README.md (optional)
```

For personal skills (shared across projects):
```
~/.copilot/skills/skill-name/
  SKILL.md
  example-script.ps1
  README.md (optional)
```

## Naming Conventions

- **Skill directories**: Lowercase, hyphens for spaces, action-oriented
- **Supporting files**: Intention-revealing names
  - Good: `debug-workflow-failure.ps1`, `solution-analyzer.md`
  - Bad: `helper.ps1`, `utils.md`, `script.ps1`

## Recommended Tools for .NET Skills

- `dotnet` (build, test, pack, publish, tool)
- PowerShell scripts (.ps1) for orchestration
- C# console tools for complex logic
- `git` and `gh` for repository operations
- MSBuild and test runners where appropriate

## Editing Existing Skills

When editing a skill:
1. Review the current SKILL.md file
2. Identify what should be clarified, removed, or improved
3. Ensure instructions remain concrete and deterministic
4. Remove any abstract or philosophical guidance
5. Keep supporting files organized with intention-revealing names

## Converting Claude Skills to Copilot

When converting Claude skills:

1. **Extract intent**: Understand the original purpose and trigger conditions
2. **Remove Claude-specific concepts**: Delete any references to allowed-tools, WebFetch, model selection, or tool permissions
3. **Rewrite instructions**: Make them shorter, more deterministic, and CLI-driven
4. **Replace Claude assumptions**: Use .NET/PowerShell equivalents instead
5. **Migrate supporting docs**: Move documentation into adjacent markdown files
6. **Validate independence**: Ensure the skill runs without Claude infrastructure

## Validation Checklist

Before finalizing any skill:
- [ ] Instructions are under ~400 lines
- [ ] No Claude-only concepts remain
- [ ] Commands are runnable and tested
- [ ] Skill name and description are clear and action-oriented
- [ ] Supporting files have intention-revealing names
- [ ] Skill is self-contained and understandable
