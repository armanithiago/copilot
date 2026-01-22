## Save Personal Memories

### Purpose

This command captures **personal insights, learnings, and context** that are specific to you and not meant to be shared across the team. These memories stay local and are excluded from version control.

Use `/personal-save` for:

- Personal debugging notes or troubleshooting steps you've discovered
- Context about why certain decisions were made (from your perspective)
- Learnings specific to your workflow or preferences
- Questions or uncertainties you want to remember for later
- Personal patterns or shortcuts you use
- Technical exploration notes

**Difference from `/save`:**
- `/save` → Team/project knowledge (shared, in git)
- `/personal-save` → Personal context (local only, in .gitignore)

**When to use:** Whenever you discover something useful that only you need to remember, or want to preserve context for your own future reference.

### INSTRUCTIONS

You are working inside a Copilot-based environment.

1. Look at the files in  
   `.github/personal-memory/memories`

2. Find the highest numbered markdown file  
   - Example: `memory_0119.md`

3. Increment the number by 1 and zero-pad to 4 digits  
   - Example: `memory_0120.md`

4. Create a new markdown file with that number inside  
   `.github/personal-memories/memories`

5. Think carefully and write your personal memory into that new file.

6. **Update the index:** Add an entry to `.github/personal-memories/index.md` with the memory file name and tags for quick discovery

---

### Update Personal Memory Index

1. Look at the file in  
   `.github/personal-memories/index.md`

2. If no file exists, create one with:
   ```markdown
   # Personal Memories Index
   
   Your personal reference guide for session learnings and discoveries.
   
   ## Memories by Topic
   
   [Memories will be listed here as they're added]
   ```

3. Add an entry with the new memory file name and tags for quick discovery

**Important:** Always update the index after creating a memory. This helps you quickly find your personal memories later.

---

### Title extraction

- Extract the **title** from the learning content:
  - The title is the **first markdown heading after `# `**
  - Example:
    ```md
    # My Debugging Pattern for Async Issues
    ```
- If no explicit title is found, use **`Personal Memory`** as the title.

---

### Tag extraction

Analyze the learning content and extract **3–7 relevant tags** based on:

- **Technologies / frameworks**
  - Examples: `dotnet`, `csharp`, `debugging`, `copilot`
- **Key concepts**
  - Examples: `async-patterns`, `debugging-technique`, `workflow`
- **Personal workflow**
  - Examples: `personal-pattern`, `shortcut`, `tip`
- **Tools / context**
  - Examples: `vs-code`, `terminal`, `powershell`

Rules:
- Convert all tags to **lowercase**
- Replace spaces with **hyphens**
- Format tags as **backtick-wrapped hashtags**
  - Example: `` `#async-patterns` `#personal-debugging` ``



**Folder Structure:**
```
.github/personal-memory/
├── index.md                    (the only file here - your memory index)
└── memories/
    ├── memory_0001.md
    ├── memory_0002.md
    └── memory_XXXX.md          (your numbered memories)
```

**Note:** This entire folder (`.github/personal-memory/`) is in `.gitignore` and stays local to your machine. Never committed to the repository.
