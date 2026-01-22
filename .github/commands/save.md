## Save Your Latest Memories

### Purpose

This command captures **practical, reusable knowledge** from your conversation and stores it in a shared memory system. Future agents can access these memories to:

- Find **how to do things** (extract MemberId, query data, call APIs)
- Understand **where data lives** (which tables, which endpoints, data flow)
- Know **which methods/classes to use** for common tasks
- Discover **navigation shortcuts** (how to get from A to B in the codebase)

**What to save:**
- ✅ How to extract/access context data (claims, headers, configs)
- ✅ Which tables/APIs to use for a task
- ✅ Code patterns and method usage
- ✅ Data flows and relationships
- ✅ Where things live in the codebase

**What NOT to save:**
- ❌ Historical changes or refactoring stories
- ❌ Lessons learned about mistakes (save the solution, not the problem)
- ❌ Outdated approaches or "before/after" comparisons

**When to use:** Invoke `/save` whenever you discover or clarify **how something works** that other agents will need to know.

---

## `/save` vs `/personal-save`

| Aspect | `/save` | `/personal-save` |
|--------|---------|------------------|
| **Audience** | Shared with team/other agents | Personal only (you) |
| **Storage** | `.github/memory/` (in git) | `.github/personal-memories/` (.gitignore) |
| **Persistence** | Committed to repository | Local machine only |
| **Use Case** | Team knowledge, how-to guides, navigation tips | Personal context, debugging notes, learnings for you |
| **Examples** | "How to get MemberId", "Report tables", "API patterns" | "My debugging process", "Why I chose this approach", "Personal shortcuts" |
| **Share with team?** | Yes, for collaboration | No, private |

**Decision Rule:**
- "Will another developer or agent need this?" → `/save`
- "Is this just for me to remember?" → `/personal-save`

### INSTRUCTIONS

1. Look at the files in  
   `.github/memory/memories`

2. Find the highest numbered markdown file  
   - Example: `memory_0119.md`

3. Increment the number by 1 and zero-pad to 4 digits  
   - Example: `memory_0120.md`

4. Create a new markdown file with that number inside  
   `.github/memory/memories`

5. Think carefully and write your latest memories into that new file.

6. **Update the index:** Add an entry to `.github/memory/project-memory.md` with the memory file name and tags for quick discovery

---

### Update Project Memory Index

1. Look at the file in  
   `.github/memory/project-memory.md`

2. If no file exists, create one with:
   ```markdown
   # Project Memories Index
   
   Quick reference guide for all saved team memories.
   
   ## Memories by Topic
   
   [Memories will be listed here as they're added]
   ```

3. Add an entry with the new memory file name and tags for quick discovery

**Important:** Always update the index after creating a memory. This helps you and other agents quickly find memories later.

---

### Title extraction
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

### Example Memory Files

Here's what well-saved, reusable memories look like:

**Example 1: How-To Guide (Tactical)**

```markdown
---
title: How to Get MemberId in API Requests
tags: `#dotnet` `#authentication` `#claims` `#member-context`
date: 2026-01-22
---

## Quick Answer
To extract MemberId from the current user context:

```csharp
var memberId = User.FindFirst("memberId")?.Value;
// Or from HttpContext
var memberId = HttpContext.User.FindFirst("member_id")?.Value;
```

## Where It Comes From
- JWT token claim: `member_id`
- Set by authentication middleware in AuthenticationService
- Available on any authorized endpoint

## Fallback (if claim missing)
Check header: `X-Member-Id`

## Example Usage
```csharp
[Authorize]
public IActionResult GetOrdersByMember()
{
  var memberId = User.FindFirst("memberId")?.Value;
  var orders = _orderService.GetOrdersByMemberId(memberId);
  return Ok(orders);
}
```

## Related
- Claims extraction: See ClaimsHelper class
- Auth middleware: AuthenticationMiddleware.cs
```

**Example 2: Where-To-Look Guide (Navigation)**

```markdown
---
title: How to Create a Report - Required Tables & Data Flow
tags: `#reporting` `#database` `#data-flow` `#orders`
date: 2026-01-22
---

## Tables You'll Need
- `Orders` - main order data (OrderId, CustomerId, OrderDate, TotalAmount)
- `OrderItems` - line items (OrderItemId, OrderId, ProductId, Quantity, Price)
- `Products` - product details (ProductId, ProductName, Category)
- `Customers` - customer info (CustomerId, CustomerName, Email)

## How Data Flows
1. Start from Orders table (filtered by date range)
2. Join to OrderItems for line-level details
3. Join to Products for product info
4. Join to Customers for customer details

## Query Structure
```csharp
var reportData = dbContext.Orders
  .Where(o => o.OrderDate >= startDate && o.OrderDate <= endDate)
  .Include(o => o.Items)
    .ThenInclude(i => i.Product)
  .Include(o => o.Customer)
  .ToList();
```

## Tips
- Always use Include() to avoid N+1 queries
- Filter Orders first, then include related data
- See ReportBuilder class for aggregation patterns
```

---
