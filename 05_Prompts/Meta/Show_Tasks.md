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
   - Accept shortcuts: ca, cb, xyz, dev

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
- "List Company_A tasks"
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
[Company_B] user-dashboard-authentication - Build user dashboard auth system - Blocker: Waiting on OAuth config

## IN PROGRESS (2)
[Company_A] update-content-descriptions - Update 10 seasonal collection items
[Client_XYZ] prepare-ia-review-meeting - Prep IA review presentation - Due: 2026-01-10

## TODO - High (4)
[Company_A] optimize-content-images - Optimize seasonal collection imagery
[Client_XYZ] review-navigation-structure - Review and provide feedback on nav
[Company_B] feature-search-ui - Build feature search interface
[Company_A] inventory-audit - Audit inventory levels

## TODO - Medium (3)
[Company_A] review-abandoned-carts - Analyze cart abandonment
[Company_B] database-schema-review - Review database design
[Development] learn-claude-skills - Learn Claude skills system

---
Total: 10 tasks (1 blocked, 2 in progress, 7 todo)

Focus: Unblock Company_B or tackle high-priority Company_A/Client_XYZ work?
```

### Example 2: Single Domain

**User:** `/tasks companya`

**Output:**
```
## IN PROGRESS (1)
update-content-descriptions - Update 10 seasonal collection items

## TODO - High (2)
optimize-content-images - Optimize seasonal collection imagery
inventory-audit - Audit inventory levels

## TODO - Medium (1)
review-abandoned-carts - Analyze cart abandonment patterns

---
Company_A: 4 tasks (1 in progress, 3 todo)

Next up: Finish content descriptions, then tackle imagery?
```

### Example 3: Filtered View

**User:** `/tasks priority:high`

**Output:**
```
## IN PROGRESS
[Client_XYZ] prepare-ia-review-meeting - Due: 2026-01-10

## TODO - High
[Company_A] optimize-content-images
[Client_XYZ] review-navigation-structure
[Company_B] feature-search-ui
[Company_A] inventory-audit

---
5 high-priority tasks
```

### Example 4: Clean Slate

**User:** `/tasks xyz`

**Output:**
```
No active tasks for Client_XYZ.

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