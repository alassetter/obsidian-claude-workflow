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

You have Obsidian MCP access. Show active tasks for a domain or all domains.

**Process:**

1. **Determine scope:**
   - `/tasks` = all domains
   - `/tasks [domain]` = specific domain only
   - Accept shortcuts: cc, ax, XYZ, dev

2. **Read task files:**
   - List all `.md` files in `[domain]/Tasks/` folders
   - Filter OUT: archived: true, ignore: true, status: completed
   - Include: todo, in-progress, blocked

3. **Group by status:**
   - **BLOCKED** - Show first with blocker reason
   - **IN PROGRESS** - Currently being worked
   - **TODO - Urgent** - priority: urgent
   - **TODO - High** - priority: high
   - **TODO - Medium** - priority: medium  
   - **TODO - Low** - priority: low

4. **For each task show:**
   - Task title (file name without .md)
   - Brief description (first line of Description section)
   - Due date if set
   - Domain (if showing all domains)

5. **Format concisely:**
   ```
   ## BLOCKED (2)
   [domain] task-name - Brief description - Blocker: reason
   
   ## IN PROGRESS (3)
   [domain] task-name - Brief description
   
   ## TODO - High (5)
   [domain] task-name - Brief description - Due: date
   ```

6. **Summary:**
   - Total task count
   - Count by status
   - Suggest next action if clear

**Important Rules:**
- Be CONCISE - just enough to identify the task
- Show domains if viewing all, hide if single domain
- Surface blockers prominently
- Sort by priority within each status
- Show due dates when present
- Max 50 tasks - if more, paginate or suggest filtering

## When to Use

User says:
- `/tasks`
- `/tasks [domain]`
- "Show my tasks"
- "What do I need to work on?"
- "List CompanyA tasks"
- "What's on my plate?"

## Variables

- `{{domain}}` (optional): Filter to specific domain
- `status:{{status}}`: Filter by status (todo, in-progress, blocked)
- `priority:{{priority}}`: Filter by priority (urgent, high, medium, low)

## Examples

### Example 1: All Domains

**User:** `/tasks`

**Output:**
```
## BLOCKED (1)
[CompanyB] user-dashboard-authentication - Build user dashboard auth system - Blocker: Waiting on OAuth config

## IN PROGRESS (2)
[CompanyA] update-product-descriptions - Update 10 fall collection products
[XYZ] prepare-ia-review-meeting - Prep IA review presentation - Due: 2026-01-10

## TODO - High (4)
[CompanyA] optimize-product-images - Optimize fall collection imagery
[XYZ] review-navigation-structure - Review and provide feedback on nav
[CompanyB] property-search-ui - Build property search interface
[CompanyA] shopify-inventory-audit - Audit inventory levels

## TODO - Medium (3)
[CompanyA] review-abandoned-carts - Analyze cart abandonment
[CompanyB] database-schema-review - Review database design
[Development] learn-claude-skills - Learn Claude skills system

---
Total: 10 tasks (1 blocked, 2 in progress, 7 todo)

Focus: Unblock CompanyB or tackle high-priority CompanyA/XYZ work?
```

### Example 2: Single Domain

**User:** `/tasks CompanyA`

**Output:**
```
## IN PROGRESS (1)
update-product-descriptions - Update 10 fall collection products

## TODO - High (2)
optimize-product-images - Optimize fall collection imagery
shopify-inventory-audit - Audit inventory levels

## TODO - Medium (1)
review-abandoned-carts - Analyze cart abandonment patterns

---
CompanyA: 4 tasks (1 in progress, 3 todo)

Next up: Finish product descriptions, then tackle imagery?
```

### Example 3: Filtered View

**User:** `/tasks priority:high`

**Output:**
```
## IN PROGRESS
[XYZ] prepare-ia-review-meeting - Due: 2026-01-10

## TODO - High
[CompanyA] optimize-product-images
[XYZ] review-navigation-structure
[CompanyB] property-search-ui
[CompanyA] shopify-inventory-audit

---
5 high-priority tasks
```

### Example 4: Clean Slate

**User:** `/tasks XYZ`

**Output:**
```
No active tasks for XYZ.

Want to:
- Check planning docs for upcoming work?
- Create new tasks from planning inbox?
- Start fresh planning?
```

## Output Format

1. Group by status (blocked, in progress, todo by priority)
2. Concise one-line per task
3. Summary stats at bottom
4. Suggest next action or ask clarifying question

## Related Prompts

- [[Load_Context]] - Full context including planning
- [[Create_Task]] - Add new task
- [[Organize_Planning]] - Convert inbox to tasks

## Notes

- This is a QUICK VIEW - not comprehensive detail
- User wants to see at-a-glance what needs doing
- Don't read full task files unless needed
- Keep it under 30 lines typically
- If too many tasks, suggest filtering
- Update last_used when executed
- If all tasks complete, celebrate briefly then ask what's next