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

You have Obsidian MCP access. Read `09_Planning/inbox.md` and organize its contents into structured tasks.

**Process:**

1. **Read the inbox:**
   - Open `09_Planning/inbox.md`
   - Identify all task items, ideas, and notes

2. **Categorize by domain:**
   - Company_A (ca) - E-commerce business operations
   - Company_B (cb) - SaaS platform development
   - Client_XYZ (xyz) - Enterprise project client work
   - Development (dev) - Learning and skill building
   - If unclear, ASK the user which domain

3. **For each item, determine if it's:**
   - A single task → Create one Task file
   - Multiple tasks → Create multiple Task files
   - A planning doc → Create Planning file
   - Cross-domain → Create separate tasks in EACH domain, link them

4. **Create task files:**
   - Use the Task template from `00_System/Templates/Task.md`
   - Place in appropriate domain: `[domain]/Tasks/[descriptive-name].md`
   - Fill in all frontmatter fields
   - Extract clear description, context, acceptance criteria
   - Set priority based on urgency cues (default: medium)
   - Link related tasks if applicable

5. **After organizing:**
   - Summarize what was created (count by domain)
   - List all new task files created
   - ASK: "Should I archive the inbox note, keep it active, or delete it?"
   - If archive: Add `archived: true` and `ignore: true` to frontmatter, move to archive section

**Important Rules:**
- NEVER delete without asking first
- Use lowercase-hyphenated naming for task files
- Extract enough context so task is clear standalone
- Don't create duplicate tasks - check if similar task exists
- Link cross-domain tasks together
- Set created date to today

## When to Use

User says:
- `/organize`
- `/organize [domain]` (only process items for specific domain)
- "Organize my planning notes"
- "Process my inbox"
- "Create tasks from my brain dump"

## Variables

- `domain` (optional): If specified, only create tasks for that domain
- `--preview` flag: Show what would be created without actually creating

## Examples

### Example 1: Mixed Domain Inbox

**Inbox content:**
```
Need to update 10 content descriptions for seasonal collection
Client_XYZ wants IA review meeting prep by Friday
Continue Company_B user dashboard - authentication is blocking
Research new tools for memory management
```

**Output:**
```
Created 4 tasks:
- 02_Company_A/Tasks/update-content-descriptions.md (priority: high, due: none)
- 01_Clients/Client_XYZ/Tasks/prepare-ia-review-meeting.md (priority: high, due: 2026-01-10)
- 03_Company_B/Tasks/user-dashboard-authentication.md (priority: medium, blocked)
- 04_Development/Tasks/research-memory-tools.md (priority: low)

Should I archive the inbox note, keep it active, or delete it?
```

### Example 2: Domain-Specific

**Command:** `/organize companya`

**Result:** Only creates tasks for Company_A items, leaves others in inbox

### Example 3: Cross-Domain Task

**Inbox:** "Integrate e-commerce data into Company_B for Company_A analytics"

**Output:**
```
Created 2 linked tasks:
- 02_Company_A/Tasks/ecommerce-data-export.md
  (Extract e-commerce data for Company_B integration)
- 03_Company_B/Tasks/integrate-ecommerce-data.md
  (Build integration to receive Company_A e-commerce data)
Both tasks linked via related_tasks field.
```

## Output Format

1. Confirmation message with count
2. List of created files with brief description
3. Question about archiving
4. Wait for user response before archiving

## Related Prompts

- [[Create_Task]] - Single task creation
- [[Load_Context]] - Loading domain context
- [[Show_Tasks]] - Viewing tasks

## Notes

- Priority inference: "urgent", "asap", "today" → urgent; "soon", "this week" → high; specific dates → set due_date
- Blocker detection: "waiting on", "blocked by", "need to" → note in blockers field
- If user frequently forgets to organize, suggest they run `/organize` at end of each day
- Keep archived inboxes for reference - they're useful for weekly reviews