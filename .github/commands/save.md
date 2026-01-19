## Save your latest learnings

### INSTRUCTIONS

You are working inside a Copilot-based environment.

1. Look at the files in  
   `.copilot/learnings/`

2. Find the highest numbered markdown file  
   - Example: `0119.md`

3. Increment the number by 1 and zero-pad to 4 digits  
   - Example: `0120.md`

4. Create a new markdown file with that number inside  
   `.copilot/learnings/`

5. Think carefully and write your latest learnings into that new file.

---

### Title extraction

- Extract the **title** from the learning content:
  - The title is the **first markdown heading after `# `**
  - Example:
    ```md
    # Copilot Agent Planning
    ```
- If no explicit title is found, use **`Learnings`** as the title.

---

### Tag extraction

Analyze the learning content and extract **3–7 relevant tags** based on:

- **Technologies / frameworks**
  - Examples: `dotnet`, `csharp`, `powershell`, `copilot`, `mcp`
- **Key concepts**
  - Examples: `architecture`, `refactoring`, `token-usage`, `agent-context`
- **Patterns / methodologies**
  - Examples: `agent-architecture`, `event-driven`, `observability`
- **Tools / platforms**
  - Examples: `github-copilot`, `powershell`, `dotnet-cli`

Rules:
- Convert all tags to **lowercase**
- Replace spaces with **hyphens**
- Format tags as **backtick-wrapped hashtags**
  - Example: `` `#dotnet` `#agent-architecture` ``

---

### Update README

Update the file:

