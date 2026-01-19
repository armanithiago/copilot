---
name: create-pr
description: Create a well-structured pull request following best practices from popular companies. Use this skill when asked to create, open, or submit a pull request with proper branching, commits, and description.
---

## Pull Request Creation Workflow

When asked to create or submit a pull request, follow this step-by-step process to ensure a professional, review-ready PR.

### 1. Validate Repository State

Before creating a PR:

```powershell
# Check current branch
git branch

# Verify clean working directory
git status

# Update from remote
git pull origin main --no-edit
```

If changes exist:
- Ask: "Should I stash these changes before creating the feature branch?"
- If YES: `git stash`
- If NO: Stop and ask user to handle

### 2. Create Feature Branch

Use conventional branch naming:

```powershell
# Create branch from main/master
git checkout main
git pull origin main
git checkout -b <branch-name>
```

**Branch Naming Convention** (follow one):
- `feature/short-description` - New features
- `fix/short-description` - Bug fixes
- `refactor/short-description` - Code refactoring
- `docs/short-description` - Documentation changes
- `chore/short-description` - Maintenance, dependencies
- `perf/short-description` - Performance improvements
- `test/short-description` - Test additions/fixes

Examples:
- ✅ `feature/user-authentication`
- ✅ `fix/null-pointer-exception`
- ✅ `refactor/database-queries`
- ❌ `my-branch`, `temp`, `feature1`

### 3. Make Code Changes

As user makes changes:
- Periodically verify branch status: `git status`
- Ensure changes are focused and cohesive
- Do NOT stage/commit yet—wait for user confirmation

### 4. Stage and Commit Changes

**Stage changes:**

```powershell
# Review what will be staged
git diff

# Stage changes
git add <files>

# Or stage all changes
git add .

# Verify staging
git status
```

**Create meaningful commits** using Conventional Commits format:

```
<type>(<scope>): <subject>

<body>

<footer>
```

**Types** (first word):
- `feat` - New feature
- `fix` - Bug fix
- `refactor` - Code reorganization (no feature/bug change)
- `docs` - Documentation updates
- `test` - Test additions/modifications
- `chore` - Build, dependencies, tooling
- `perf` - Performance improvements
- `style` - Code style (formatting, missing semicolons, etc.)

**Subject Rules**:
- Use imperative mood: "add feature" not "added feature"
- Don't capitalize first letter
- No period at end
- 50 characters or less

**Body Rules** (optional but recommended):
- Explain WHAT and WHY, not HOW
- Wrap at 72 characters
- Separate from subject with blank line

**Footer** (optional):
- Link to related issues: `Closes #123` or `Fixes #456`
- Note breaking changes: `BREAKING CHANGE: description`

**Examples**:

Good commit:
```
feat(auth): add two-factor authentication

Add support for TOTP-based two-factor authentication. Includes
QR code generation, backup codes, and account recovery options.

Closes #234
```

Good fix:
```
fix(api): handle null responses from external service

The payment API occasionally returns null instead of error codes.
Wrap calls with fallback handler and retry logic.

Fixes #567
```

**Commit instruction:**

```powershell
git commit -m "type(scope): subject" -m "body" -m "footer"

# Or for simple commits
git commit -m "type(scope): subject line"
```

### 5. Verify Changes Before Push

```powershell
# View all commits in feature branch vs main
git log main..<current-branch> --oneline

# Review final diff
git diff main..<current-branch>

# Check commit messages
git log --oneline -n 5
```

Ask user: "Do these commits and changes look correct?" 
- If NO: Allow user to amend or revert
- If YES: Proceed to push

### 6. Push Changes to Remote

```powershell
# Push feature branch
git push -u origin <branch-name>

# Verify push succeeded
git log origin/<branch-name> -n 1
```

### 7. Create Pull Request Description

Now craft the PR description. Gather information:

**Ask user these questions:**

1. **What's the title?**
   - Format: `[type] Short description` or just `Short description`
   - Examples: `[Feature] Add two-factor authentication`, `Fix payment processing error`

2. **What's the description/motivation?**
   - Why was this change made?
   - What problem does it solve?
   - What context should reviewers have?

3. **What are the changes?**
   - Brief bullet list of key changes
   - What files/modules are affected?

4. **Are there breaking changes?**
   - Yes/No?
   - If YES, describe them clearly

5. **Testing performed:**
   - Manual testing steps?
   - Test coverage added?
   - Related issues/ticket numbers?

**Build PR Description Template:**

```markdown
## Description
[User's explanation of why and what]

## Type of Change
- [ ] Bug fix (non-breaking change fixing an issue)
- [ ] New feature (non-breaking change adding functionality)
- [ ] Breaking change (fix or feature causing existing functionality to change)
- [ ] Documentation update

## Changes Made
- [Change 1]
- [Change 2]
- [Change 3]

## Testing
- [ ] Manual testing completed on [environment]
- [ ] New tests added
- [ ] All tests passing

## Related Issues
Closes #[issue-number]

## Screenshots (if applicable)
[Optional: add screenshots for UI changes]

## Checklist
- [ ] Code follows style guidelines
- [ ] Comments added for complex logic
- [ ] Documentation updated
- [ ] No breaking changes introduced
- [ ] Tests pass locally
```

### 8. Create the Pull Request

Provide the PR information for creation:

**Using GitHub CLI** (recommended):

```powershell
# Create PR with title and description
gh pr create --title "Your PR Title" --body "Your PR description"

# Create PR with file description
gh pr create --title "Your PR Title" --body-file pr-description.txt

# Create PR with auto-generated template
gh pr create --fill
```

**Manual GitHub Web Creation:**

If `gh` CLI unavailable:
1. Navigate to repository on GitHub
2. Click "New Pull Request"
3. Select:
   - Base: `main` (or appropriate base branch)
   - Compare: `<your-feature-branch>`
4. Add title and description from above
5. Add labels (bug, feature, documentation, etc.)
6. Request reviewers if appropriate
7. Click "Create Pull Request"

### 9. Verify PR Created

```powershell
# List recent PRs
gh pr list --state open --limit 5

# View your newly created PR
gh pr view <branch-name>
```

Output should show:
- PR number
- Title
- Description
- Status: OPEN
- Linked issues (if any)

## Best Practices by Company

### Google-Style PRs
- Small, focused PRs (50-200 lines)
- Clear, detailed description with rationale
- Comprehensive tests included
- Address all code review comments before merge

### Facebook/Meta-Style PRs
- Stack multiple PRs for large features
- Early posting for visibility (before completion)
- Frequent updates to incorporate feedback
- Automated testing and linting required

### Microsoft-Style PRs
- Include linked work items/tasks
- Security and accessibility checks documented
- Clear "why" in description
- Separate concern: design PRs, implementation PRs

### AWS-Style PRs
- Comprehensive documentation
- Backward compatibility guaranteed
- Extensive testing (unit, integration, load)
- Change logs updated
- Migration guides if breaking changes

### GitHub-Style PRs
- Minimal, surgical changes
- Great commit messages
- Responsive to feedback
- Clear review expectation in description

## Common Review Readiness Checklist

Before announcing PR ready for review:

- [ ] Branch name is descriptive and follows conventions
- [ ] Commit messages follow Conventional Commits format
- [ ] PR title is clear and concise
- [ ] Description explains WHAT and WHY
- [ ] Related issues are linked
- [ ] No merge conflicts with base branch
- [ ] All tests passing (CI/CD green)
- [ ] Code follows project style guide
- [ ] No debug code or temporary files
- [ ] Documentation updated if needed
- [ ] Screenshots/demos for UI changes

## Troubleshooting

**PR has conflicts with main:**
```powershell
# Update from main
git fetch origin
git rebase origin/main

# Or merge if rebasing not preferred
git merge origin/main

# Resolve conflicts, then
git add .
git rebase --continue
git push -f origin <branch-name>
```

**Forgot to add files to recent commit:**
```powershell
git add <forgotten-files>
git commit --amend --no-edit
git push -f origin <branch-name>
```

**Need to reword commit message:**
```powershell
git commit --amend -m "new message"
git push -f origin <branch-name>
```

**Want to split one commit into multiple:**
```powershell
git rebase -i origin/main
# Mark commit as 'edit'
git reset HEAD~1
git add <file1>
git commit -m "first commit"
git add <file2>
git commit -m "second commit"
git rebase --continue
```

## After PR Creation

- [ ] Share PR link with team
- [ ] Monitor for review comments
- [ ] Respond promptly to feedback
- [ ] Make requested changes on the same branch
- [ ] Push updates (CI/CD will re-run)
- [ ] Request re-review when ready
- [ ] Merge when approved and tests pass
