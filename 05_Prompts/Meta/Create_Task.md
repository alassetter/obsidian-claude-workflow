---
type: prompt
category: Meta
domain: General
reuse: high
audience: ai
created: 2026-01-06
last_used: 
use_count: 0
---

## Prompt

You have Obsidian MCP access. Create a single task file in the appropriate domain.

**Process:**

1. **Gather information:**
   
   If user provides all details, proceed. Otherwise ASK:
   - Which domain? (Company_A/ca, Company_B/cb, Client_XYZ/xyz, Development/dev)
   - What needs to be done? (task description)
   - Priority? (urgent, high, medium, low) - default: medium
   - Due date? (optional)
   - Any blockers? (optional)

2. **Create task file:**
   
   **File location:** `[domain]/Tasks/[descriptive-name].md`
   
   **File naming:**
   - Lowercase with hyphens: `update-product-descriptions.md`
   - Descriptive but concise: 3-5 words typical
   - Action-oriented: start with verb when possible
   
   **Use Task template:** `00_System/Templates/Task.md`
   
   **Fill frontmatter:**
   ```yaml
   type: task
   domain: [actual domain]
   status: todo
   priority: [user specified or medium]
   created: [today's date]
   due_date: [if provided]
   completed_date: 
   related_planning: [if applicable]
   related_tasks: []
   ```
   
   **Fill content:**
   - Clear description of what needs to be done
   - Why it matters (context)
   - How to know it's done (acceptance criteria)
   - Any steps if needed
   - Note blockers if any

3. **Confirm creation:**
   - Show filename and location
   - Brief summary of task
   - Ask if user wants to add to related planning doc

**Important Rules:**
- ALWAYS use the template - consistency matters
- Create in correct domain folder
- Use descriptive but brief filenames
- Set reasonable defaults (medium priority, no due date)
- Don't create duplicate tasks - check if similar exists first
- Link to related planning docs if obvious

## When to Use

User says:
- `/task add`
- `/task add [domain]`
- "Create a task for Company_A"
- "Add this to my tasks"
- "Remind me to [do something]"
- "I need to [task description]"

## Variables

- `{{domain}}`: Company_A/ca, Company_B/cb, Client_XYZ/xyz, Development/dev
- `{{description}}`: What needs to be done
- `{{priority}}`: urgent, high, medium, low
- `{{due_date}}`: Optional due date

## Examples

### Example 1: Quick Task Creation

**User:** `/task add companya`

**Claude:** "What needs to be done for Company_A?"

**User:** "Update 10 content descriptions for seasonal collection"

**Claude:** "Priority? (urgent/high/medium/low - default is medium)"

**User:** "high"

**Output:**
```
Created: 02_Company_A/Tasks/update-content-descriptions.md

Task: Update 10 content descriptions for seasonal collection
Priority: High
Status: Todo

Added to your Company_A tasks. Want to link this to a planning doc?
```

### Example 2: Full Details Provided

**User:** "Create an urgent task for Client_XYZ to prepare IA review meeting by Friday"

**Output:**
```
Created: 01_Clients/Client_XYZ/Tasks/prepare-ia-review-meeting.md

Task: Prepare IA review meeting presentation
Priority: Urgent
Due: 2026-01-10 (Friday)
Status: Todo

Task created with all details. Ready to start or need anything else?
```

### Example 3: With Blocker

**User:** `/task add companyb - build user dashboard, blocked on oauth config`

**Output:**
```
Created: 03_Company_B/Tasks/build-user-dashboard.md

Task: Build user dashboard
Priority: Medium
Status: Blocked
Blocker: Waiting on OAuth configuration

This task is blocked. Want to create an unblocked task to work on instead?
```

### Example 4: Learning Task

**User:** "Remind me to learn Claude skills"

**Output:**
```
Created: 04_Development/Tasks/learn-claude-skills.md

Task: Learn how to use Claude skills system
Priority: Low (learning task)
Status: Todo

Added to Development learning tasks. Want to create a learning roadmap for this?
```

## Output Format

1. Confirmation with filename and location
2. Brief task summary (title, priority, due date, blockers)
3. Follow-up question if relevant

## Related Prompts

- [[Organize_Planning]] - Batch create tasks from inbox
- [[Show_Tasks]] - View all tasks
- [[Load_Context]] - See tasks in context

## Notes

- This creates ONE task - for multiple tasks, use `/organize`
- Check for duplicates by listing tasks first
- If task is part of larger planning, suggest linking it
- If creating many tasks for same domain, suggest using planning inbox instead
- Default to medium priority unless urgency is clear
- Use natural language parsing - don't require perfect syntax
- Update last_used when executed