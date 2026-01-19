# Copilot Skills and Agents - Presentation Guide

## Overview

A comprehensive presentation explaining all GitHub Copilot CLI skills and agents in the `.github` directory.

**Location**: `copilot-presentation.json`  
**Format**: JSON structure for PowerPoint generation  
**Slides**: 16 slides covering architecture, skills, and workflow

---

## Presentation Structure

### Slide 1: Title Slide
**Title**: Copilot Skills & Agents  
**Subtitle**: GitHub Copilot CLI Extension Architecture

---

### Slide 2: What Are Skills?
Foundational concepts:
- Skills are reusable instruction sets for Copilot
- Located in `.github/skills/` directory
- Each skill is a folder with `SKILL.md` file
- Define when and how Copilot should assist
- Enable Copilot to specialize in specific workflows

---

### Slide 3: Available Skills
Complete list of 6 skills:
1. **story-planner** - Break features into user stories
2. **skill-builder** - Create and edit Copilot skills
3. **powerpoint** - Generate presentations and slides
4. **interview** - Conduct structured interviews
5. **remember** - Document persistent knowledge
6. **tidy-up** - TDD refactoring process

---

### Slide 4: Project Structure
Directory organization:
- `.github/` - Root directory for Copilot configuration
- `copilot-instructions.md` - Global guidelines for Copilot
- `tdd-instructions.md` - Testing best practices
- `skills/` - Collection of specialized agent skills
- `commands/` - Custom command definitions

---

### Slide 5-10: Skill Details

#### Slide 5: Story Planner
- Breaks applications into vertical slices
- Creates user stories with acceptance criteria
- Uses Gherkin Given/When/Then format
- Focuses on user outcomes (WHAT/WHY not HOW)
- Generates manual testing procedures

#### Slide 6: Skill Builder
- Guide for creating new Copilot skills
- Documents proper SKILL.md format
- Explains naming conventions and structure
- Covers converting Claude skills to Copilot
- Provides validation checklist for skills

#### Slide 7: PowerPoint Skill
- Creates .pptx files programmatically
- Supports multiple slide types and layouts
- Generates tables, charts, and visualizations
- Accepts JSON structure for presentation design
- Enables quick pitch deck and report creation

#### Slide 8: Interview
- Conducts structured deep interviews
- Gathers comprehensive requirements
- Asks clarifying questions progressively
- Collects information for specifications
- Ensures complete understanding before design

#### Slide 9: Remember
- Documents important project facts
- Persists knowledge across sessions
- Stores codebase conventions
- Records technical decisions and rationales
- Maintains in CLAUDE.md file

#### Slide 10: Tidy Up
- TDD-based refactoring process
- Maintains code quality during changes
- Follows test-driven development practices
- Safely refactors production code
- Ensures tests pass throughout refactoring

---

### Slide 11: Skill Invocation
How skills are used:
- User mentions skill name in chat
- Copilot detects relevant skill context
- Skill instructions are automatically loaded
- Copilot follows skill's step-by-step process
- Skill helps structure the response

---

### Slide 12: SKILL.md Format
Standard structure:
- YAML frontmatter: name and description
- Clear when Copilot should use the skill
- Actionable step-by-step instructions
- Examples and templates
- Quality checks or validation rules

---

### Slide 13: Creating Skills
Best practices:
- Use lowercase hyphenated names
- Write clear, action-oriented descriptions
- Focus on user outcomes, not implementation
- Include examples and templates
- Keep instructions under 400 lines

---

### Slide 14: Skill Location
File organization:
- Project skills: `.github/skills/skill-name/`
- Personal skills: `~/.copilot/skills/skill-name/`
- Each skill gets its own directory
- SKILL.md is the main file
- Optional supporting files with clear names

---

### Slide 15: Planning Workflow
Complete workflow example:
1. Use interview skill to gather requirements
2. Use story-planner to break into user stories
3. Use remember skill to document decisions
4. Use tidy-up skill for refactoring
5. Use powerpoint to present findings

---

### Slide 16: Key Takeaways
Summary points:
- Skills extend Copilot's specialized capabilities
- Located in `.github/skills/` for project use
- Each skill has clear SKILL.md format
- Skills help structure complex workflows
- Easy to create, share, and maintain

---

## How to Generate the PowerPoint

### Method 1: Using PowerPoint Skill (Recommended)
```bash
# Navigate to project directory
cd C:\Projects\copilot

# Run PowerPoint generation
npx pptxgenjs create copilot-presentation.json Copilot_Skills_and_Agents.pptx
```

### Method 2: Using ts-node Tool
```bash
ts-node src/tools/powerpoint-tool.ts create './Copilot_Skills_and_Agents.pptx' "$(cat copilot-presentation.json)"
```

### Method 3: Manual PowerPoint Library
Install and use pptxgenjs library:
```bash
npm install pptxgenjs
# Then use library to parse copilot-presentation.json
```

---

## Key Takeaways

### What This Presentation Covers
- **Architecture**: How skills fit into Copilot CLI ecosystem
- **Available Skills**: What each skill does and when to use it
- **Best Practices**: How to create and maintain skills
- **Workflow**: How skills work together in real scenarios
- **Structure**: File organization and SKILL.md format

### Skills Covered
1. **Story Planner** - User story and feature planning
2. **Skill Builder** - Creating new skills
3. **PowerPoint** - Presentation generation
4. **Interview** - Requirement gathering
5. **Remember** - Knowledge persistence
6. **Tidy Up** - Code refactoring

### Main Concepts
- Skills are reusable instruction sets
- Located in `.github/skills/` for projects
- Each skill has a `SKILL.md` file with clear format
- Copilot loads skills automatically when relevant
- Skills help structure complex tasks

---

## Files Referenced

- `.github/copilot-instructions.md` - Global guidelines
- `.github/tdd-instructions.md` - Testing practices
- `.github/skills/story-planner/SKILL.md` - Story planning
- `.github/skills/skill-builder/SKILL.md` - Skill creation
- `.github/skills/powerpoint/SKILL.md` - Presentation creation
- `.github/skills/interview/SKILL.md` - Requirement gathering
- `.github/skills/remember/SKILL.md` - Knowledge documentation
- `.github/skills/tidy-up/SKILL.md` - Code refactoring

---

## Notes

This presentation is generated from `copilot-presentation.json`, which contains:
- 16 slides total
- Title slides and content slides
- Bullet-point format for readability
- Focus on user-facing benefits
- Clear structure and navigation

The JSON structure is compatible with:
- pptxgenjs (Node.js library)
- PowerPoint skill for Copilot
- Other presentation generation tools

---

**Generated**: 2026-01-18  
**Status**: Ready for PowerPoint generation
