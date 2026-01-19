## Save your latest memories

### INSTRUCTIONS

You are working inside a Copilot-based environment.

1. Look at the files in  
   `.copilot/memory/memories`

2. Find the highest numbered markdown file  
   - Example: `memory_0119.md`

3. Increment the number by 1 and zero-pad to 4 digits  
   - Example: `memory_0120.md`

4. Create a new markdown file with that number inside  
   `.copilot/memory/memories`

5. Think carefully and write your latest memories into that new file.

---

### Title extraction

- Extract the **title** from the learning content:
  - The title is the **first markdown heading after `# `**
  - Example:
    ```md
    # Copilot Agent Planning
    ```
- If no explicit title is found, use **`Memory`** as the title.

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

### Update README with tags

1. Look at the files in  
   `.copilot/memory/project-memory.md`

2. If no file was found, create one

3. Update the file with the memory the new memory file name and add the tags related to that memory file.

