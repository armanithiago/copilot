# Copilot Command Auto-Approval Policy

## Overview
This document defines which commands Copilot CLI can execute without explicit user approval. These are non-destructive, read-safe, or development-workflow commands commonly used during software development.

## Auto-Approved Command Categories

### File Navigation & Inspection
✅ **Auto-Approved:**
- `cd`, `pwd`, `ls`, `dir` - directory navigation and listing
- `Get-ChildItem` - PowerShell file listing
- `cat`, `type`, `Get-Content` - file content reading
- `find`, `grep`, `rg` (ripgrep) - pattern searching
- `file`, `stat`, `ls -la` - file metadata inspection
- `head`, `tail`, `wc` - file inspection utilities

### Build & Development Tools
✅ **Auto-Approved:**
- `npm install`, `npm ci` - package installation
- `npm run [build|test|dev|lint]` - standard npm scripts
- `node`, `npx` - Node.js execution
- `dotnet build`, `dotnet restore`, `dotnet test` - .NET commands
- `dotnet watch` - .NET development server
- `npm list`, `npm ls` - dependency inspection
- `nvm use` - Node version switching
- `pnpm`, `yarn` - alternative package managers (standard operations)

### Git Read Operations
✅ **Auto-Approved:**
- `git status` - check repository status
- `git diff` - view changes
- `git log` - view commit history
- `git branch`, `git branch -a` - list branches
- `git tag` - list tags (viewing)
- `git remote -v` - list remote repositories
- `git show` - inspect commits
- `git --no-pager` - output formatting
- `git fetch` - retrieve from remote

### Git Operations for PR Workflow (Auto-Approved with skill: create-pr)
✅ **Auto-Approved when using `create-pr` skill:**
- `git checkout <branch>` - switch branches
- `git checkout -b <branch>` - create and switch branches
- `git pull origin <branch>` - update from remote
- `git add <files>` - stage changes
- `git add .` - stage all changes
- `git commit -m "message"` - create commits
- `git push -u origin <branch>` - push new branch
- `git push origin <branch>` - push commits
- `git push -f origin <branch>` - force push (for rebasing)
- `git rebase origin/<branch>` - rebase updates
- `git merge origin/<branch>` - merge updates
- `gh pr create` - create pull requests with GitHub CLI
- `gh pr list` - list pull requests
- `gh pr view` - view pull request details

### PowerShell System Commands
✅ **Auto-Approved:**
- `New-Item -ItemType Directory` - create directories
- `Get-ChildItem`, `Get-Item` - file operations (read)
- `Test-Path` - check file/directory existence
- `Remove-Item` (directories only, not `-Force` flag) - safe deletions
- `Copy-Item` - file copying
- `Write-Host` - console output
- `Select-Object`, `Where-Object` - PowerShell filtering

### Utilities & Diagnostics
✅ **Auto-Approved:**
- `echo`, `Write-Output` - output text
- `sleep`, `Start-Sleep` - delays
- `date`, `Get-Date` - time operations
- `whoami`, `hostname` - system info
- `curl`, `Invoke-WebRequest` (GET/HEAD only) - HTTP read operations
- `jq`, `yq` - JSON/YAML parsing (read-only)

## Explicitly Blocked Commands
❌ **Never Auto-Approved:**
- `rm -rf`, `Remove-Item -Path * -Force -Recurse` - mass deletions
- `git push`, `git commit`, `git merge` - repository mutations
- `npm publish`, `npm unpublish` - registry mutations
- `sudo`, `su` - privilege escalation
- `passwd`, `useradd`, `userdel` - system account modifications
- Database operations (DROP, DELETE, TRUNCATE)
- Commands accessing secrets or credentials
- `curl -X POST/PUT/DELETE` - mutating HTTP requests
- Any command with `--force` or `-f` flags on destructive ops

## Git Write Operations (Require Approval)
🔒 **Requires Explicit Approval** (or use `create-pr` skill):

When using the `create-pr` skill, the following operations are **auto-approved** as part of the PR workflow:
- `git checkout -b <branch>` - create feature branches
- `git add` and `git commit` - stage and commit changes
- `git push -u origin <branch>` - push new branches
- `git rebase` and `git merge` - update from main branch
- `gh pr create` - create pull requests

**Without the `create-pr` skill, these require explicit approval:**
- `git commit`, `git commit -am` - require confirmation
- `git push`, `git push origin` - require confirmation
- `git pull` - can modify local state
- `git merge`, `git rebase` - major branch operations
- `git tag` (creating new tags) - requires approval
- `git branch -d`, `git branch -D` - requires approval
- `git reset`, `git revert` - major history changes
- `git stash`, `git clean` - local state modifications

## NPM/Package Write Operations (Require Approval)
🔒 **Requires Explicit Approval:**
- `npm publish`
- `npm unpublish`
- `npm deprecate`
- `npm update` (version bumping)

## User Confirmation Points
When Copilot encounters a command not in the auto-approved or explicitly blocked lists, it should:

1. **Pause and ask**: "Can I run: `<command>`?"
2. **Show context**: Explain why the command is needed
3. **Wait for confirmation**: Require user to explicitly approve with "yes" or "y"
4. **Log the decision**: Store user's response for this session

## Common Scenarios

### ✅ Writing & Testing Code
```bash
npm install                 # Auto-approved
npm run build              # Auto-approved
npm run test               # Auto-approved
npx ts-node src/main.ts    # Auto-approved
npm run lint               # Auto-approved
```

### ✅ Viewing Changes
```bash
git status                 # Auto-approved
git diff                   # Auto-approved
git log --oneline          # Auto-approved
git show HEAD              # Auto-approved
```

### 🔒 Committing Changes
```bash
git add .                  # Requires approval
git commit -m "fix: bug"   # Requires approval
git push origin main       # Requires approval
```

### ✅ File Management
```bash
New-Item -ItemType Directory -Name "src"  # Auto-approved
Get-ChildItem -Recurse                    # Auto-approved
Copy-Item file.txt file.backup            # Auto-approved
Remove-Item -Path temp.txt                # Auto-approved (file only)
```

### ❌ Dangerous Operations (Never Auto-Approved)
```bash
rm -rf /src              # BLOCKED
git push --force         # BLOCKED
npm publish              # BLOCKED
Remove-Item * -Force     # BLOCKED
```

## Review & Update
This policy should be reviewed quarterly and updated as:
- New development tools become standard
- New dangerous patterns are discovered
- Team processes evolve
- Security requirements change

**Last Updated**: 2026-01-18
**Owner**: Development Team
