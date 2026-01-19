# Copilot Agent: Project Exploration & Instruction Generation

## Primary Goal
Explore the repository and generate **project-specific development instructions** 
so future Copilot agents understand:
- How each project is built and organized
- What coding patterns and conventions to follow
- Constraints and legacy decisions that must be preserved

## High-Level Execution Steps

### Step 1: Explore the Solution
1. List all projects in the repository (identify project files, workspaces, or manifest files)
2. Determine project types: .NET, Node.js, Python, Java, or other
3. Identify the technology stack for each project

### Step 2: Analyze Each Project Individually
For **each project**, extract and document:

| Aspect | What to Include |
|--------|-----------------|
| **Purpose** | What does this project do? What problem does it solve? |
| **Type & Language** | Library, service, CLI tool, web app, etc. + language version |
| **Framework & Runtime** | .NET 7, Node 18, Python 3.11, etc. |
| **Build System** | How is it compiled/packaged? (dotnet, npm/webpack, Maven, etc.) |
| **Architecture** | Layered, MVC, CQRS, monolith, modular, etc. |
| **Folder Structure** | Key folders and their responsibilities |
| **Dependencies** | Major NuGet/npm/pip packages and why they're used |
| **Integrations** | Databases, APIs, message queues, cloud services |
| **Coding Patterns** | Naming conventions, error handling approach, logging strategy |
| **Testing** | How are tests organized? (unit, integration, e2e?) Testing frameworks used? |
| **Known Constraints** | Legacy code, technical debt, fragile areas to avoid |
| **Setup Requirements** | Tools, CLI versions, prerequisites needed for development |
| **Configuration** | Environment-specific configs (Dev, Staging, Prod); appsettings structure |
| **API Endpoints** | REST/gRPC routes, key entry points, health checks if applicable |
| **Database** | Schema overview, key entities, access patterns (ORM vs raw SQL) |
| **Inter-Project Dependencies** | Which projects this depends on (and WHY), which projects depend on this (and WHY) |
| **CI/CD Pipeline** | Build triggers, test suites, deployment process |
| **Error Handling** | Custom exceptions, error codes, validation patterns |
| **Monitoring & Health** | Logging sinks, health check endpoints, observability patterns |

### Step 3: Create Output Files

#### Step 3a: Create README.md (Entry Point)
**Create `.github/instructions/README.md`** as the navigation hub for all project instructions.

This README must include:
1. **Index/Table of Contents** - List all projects with brief descriptions
2. **Quick Start** - Commands to build, test, run, deploy
3. **Inter-Project Dependency Map** - Visual diagram showing dependencies and breaking change risks
4. **Finding Instructions** - How to locate docs for a specific task or component
5. **Critical Breaking Change Points** - Highlighted risks (public APIs, published libraries, HTTP endpoints)
6. **Project Checklist** - What to review before working on a project
7. **Generic Template** - Applicable to any repository structure

The README should be **completely generic** (no project-specific names like "VOAPI", "Stripe", "Aspose"). Use placeholders:
- `[SolutionName]` for repository name
- `[ProjectName]`, `[LibraryName]` for specific projects
- `[FrameworkVersion]`, `[Runtime]` for versions
- `[ExternalService]` for third-party integrations
- `[Feature]`, `[Task]` for generic activities

#### Step 3b: Create Project-Specific Instruction Files
**Create ONE `.github/instructions/<project-name>-instructions.md` per project.** Do NOT create a single solution-wide file. Each project file must stand alone and include enough context about its dependencies.

For each project file, include these **required sections (in this order):**

1. **Project Overview** - 2-3 sentences describing purpose and role in the solution
2. **Technology Stack** - Language, framework versions, runtime, build system
3. **Architecture & Structure** - Design patterns, folder layout, key components
4. **Folder Structure** - Detailed breakdown of major directories and what they contain
5. **Dependencies & Integrations** - 
   - External NuGet/npm/pip packages (list name, version, WHY it's used)
   - External services (databases, APIs, message queues)
   - Data stores and access patterns
6. **Internal Project Dependencies** - 
   - **Projects this depends on**: List each, explain the reason/purpose (e.g., "Depends on DTOs for API contracts")
   - **Projects that depend on this**: List each, explain how they use it
   - Include version compatibility notes if relevant
7. **Development Guidelines** - How to write code that fits this project, naming conventions, patterns
8. **Common Pitfalls** - What to avoid, known fragile areas, legacy constraints
9. **Setup & Prerequisites** - Required tools, versions, installation steps
10. **Configuration & Environments** - Config file locations, env-specific settings, secrets management
11. **API Endpoints & Data Flow** - Key routes, request/response patterns (N/A for libraries)
12. **Database & Data Models** - Schema overview, key entities, access patterns (N/A for UI-only projects)
13. **Testing & Quality** - Testing frameworks, test organization, coverage expectations, how to run tests
14. **Monitoring & Health Checks** - Logging strategy, health endpoints, observability patterns
15. **Dependency Diagram** - ASCII or text diagram showing how this project relates to others
16. **CI/CD & Deployment** - Build pipeline, deployment process, artifact locations, version bumping strategy

**Format Guidelines:**
- Be **clear and precise**, not verbose
- Use bullet points for lists
- Include brief code examples where patterns are unclear
- For dependencies: Explicitly state **WHY** the dependency exists (not just "uses X")
- For inter-project deps: State the exact reason for the dependency
- For projects with NO tests, explicitly state "No automated tests in this project"
- For projects with NO API endpoints, state "Console/library only, no HTTP endpoints"
- For projects with NO external dependencies, explicitly state that
- Mention platform target requirements (x86 vs AnyCPU) if relevant
- Document actual versions found in lock files or project files, not assumed versions
- **Use generic project names in examples** (e.g., "DomainModels", "ApiContracts", not "VOAPI.Domain")

### Step 4: Interview User When Uncertain
**Pause and interview if:**
- Architecture decision is unclear (e.g., "why did they choose MVC over CQRS?")
- Coding convention contradicts what the code shows
- Ambiguous patterns with multiple interpretations
- Missing context about WHY a project depends on another
- Unclear purpose of a project in the solution
- Dependency relationship rationale is non-obvious
- Uncertainty about which projects are public APIs (NuGet, HTTP endpoints)

**Interview Rules:**
- Ask **one question at a time**
- Provide **2-3 specific options**, but allow custom answers
- Ask to **clarify, not to invent** - never guess
- Resume documentation after each answer

**Example Interview Questions:**
- "Is [ProjectName] meant to be reused by external consumers, or only internally?"
- "Why does [ProjectA] depend on [ProjectB]? Is it for: (A) shared data models, (B) shared business logic, or (C) specific integration?"
- "Are there any HTTP endpoints or APIs that external services depend on?"
- "Which projects, if any, are published as NuGet packages or libraries?"

### Step 5: Validate Completion
✅ `.github/instructions/` folder exists
✅ **README.md created** as entry point and navigation guide
✅ **One `.md` file per buildable project** (not solution-wide files)
✅ Each file covers all 16 required sections (or explicitly excludes N/A sections with explanation)
✅ All inter-project dependencies explained with clear rationale
✅ Dependency diagrams included
✅ Breaking change policies documented (especially for public APIs/NuGet packages)
✅ All ambiguous decisions have been explicitly asked
✅ All sections required for code generation are documented (Setup, Testing, Config, Dependencies)
✅ No information is duplicated across project files unnecessarily
✅ Each file is self-contained and comprehensive for its project
✅ README.md includes project index, dependency map, and task checklist

## Interaction Rules

**When to Interview:**
- Code patterns contradict documentation
- Architectural decision is non-obvious
- Multiple valid interpretations exist
- Cannot infer intent from code alone
- Project lacks test coverage and reasons are unclear
- Deployment/environment strategy is ambiguous
- Database schema is not discoverable from code

**When to Infer (Don't Interview):**
- Clear code patterns visible across multiple files
- Consistent naming or structure evident
- Framework conventions are obvious
- Standard industry practices apply
- Tool versions are in package lock files or project files
- Build outputs are in standard directories (bin/, dist/, target/)

## Constraints & Guardrails

- ❌ **Do NOT create one solution-wide file** - Create one file per project
- ❌ **Do NOT include project-specific names in the README.md command** - It should be reusable for ANY repository
- ❌ **Do NOT be lazy** - Each project file must be complete and detailed
- ❌ **Do NOT skip inter-project dependency rationale** - Always explain WHY dependencies exist
- ❌ **Do NOT invent** architecture or patterns
- ❌ **Do NOT create** generic/templated instructions (be project-specific in the detailed files, but generic in README)
- ❌ **Do NOT interview unnecessarily** - infer from code first
- ❌ **Do NOT skip sections** - note "N/A: No REST API in this library" rather than omitting section
- ❌ **Do NOT assume** tool versions without verifying in lock files/project files
- ❌ **Do NOT document aspirational practices** - document actual patterns in use
- ❌ **Do NOT duplicate information** across project files (each stands alone but avoids redundancy)
- ✅ **Create one file per buildable project** in the solution
- ✅ **Create generic README.md** as entry point (reusable across repos, no project-specific names)
- ✅ **Be thorough** - Each detailed file is the single source of truth for that project
- ✅ **Prefer inference** over assumptions
- ✅ **Be precise** - practical advice only, not philosophy
- ✅ **List actual dependencies** discovered, not theoretical ones
- ✅ **Note legacy code explicitly** - do not bury it in common pitfalls
- ✅ **Explain dependency relationships clearly** - use tables or diagrams
- ✅ **Include copy-paste friendly commands** for setup and testing
- ✅ **Use generic placeholders** in README: [ProjectName], [Framework], [ExternalService], not real names

## Success Criteria

- ✅ **README.md created as entry point** (generic, reusable, not project-specific)
- ✅ **One file per project** - [Project1], [Project2], [Project3], etc. (actual project names used, not VOAPI)
- ✅ **README.md includes**:
  - Project index with brief descriptions
  - Quick start commands (build, test, run, deploy)
  - Inter-project dependency map (visual diagram)
  - Task-based navigation ("How to find docs for X")
  - Breaking change risk matrix
  - Project checklist before starting work
  - Generic structure applicable to ANY repository
- ✅ Each project instructions file covers all 16 required sections (or explicitly excludes N/A)
- ✅ Inter-project dependencies explained with clear rationale
- ✅ Dependency diagrams included in README and per-project files
- ✅ Breaking change policies crystal clear
- ✅ All ambiguous decisions explicitly asked during interview
- ✅ All code generation requirements documented
- ✅ No duplication across project files
- ✅ Each file is self-contained and comprehensive
- ✅ **Future use**: Command can be run on any [SolutionName] without modification
- ✅ Developers can load only relevant instructions for a task (e.g., "load Project1 and Project3 instructions only")
