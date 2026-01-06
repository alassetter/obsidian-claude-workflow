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

You have Obsidian MCP access. Create a beautiful HTML task dashboard showing all active tasks across domains.

**Process:**

1. **Read all task files:**
   - List tasks in all domain Task folders
   - Filter OUT: archived: true, ignore: true, status: completed
   - Include: todo, in-progress, blocked

2. **Organize data:**
   - Group by: Urgent, Blocked, By Domain
   - Count totals
   - Extract: title, priority, due date, blocker reason

3. **Create HTML dashboard:**
   - Use modern, clean styling
   - Color-coded priority (red=urgent, orange=high, blue=medium, gray=low)
   - Icons for status (🚨 urgent, 🛑 blocked)
   - Responsive design
   - Easy to scan visually

4. **Save snapshot (optional):**
   - Also save to `00_System/Task_Dashboard.md`
   - Include timestamp
   - Note: "This is a snapshot - run `/dashboard` for live version"

5. **Display:**
   - Show HTML artifact (interactive, live)
   - Confirm snapshot saved
   - Suggest next action

**Important Rules:**
- HTML must be self-contained (CSS inline or in <style> tag)
- Use emoji for visual indicators
- Color-code priorities
- Keep it clean and scannable
- Mobile-friendly layout
- Update snapshot timestamp

## When to Use

User says:
- `/dashboard`
- "Show my task dashboard"
- "What's on my plate?"
- "Task overview"

## Variables

- `--save`: Force save snapshot to file (default: yes)
- `--no-save`: Skip saving snapshot

## Examples

### Example 1: Standard Dashboard

**User:** `/dashboard`

**Claude:**
1. Reads all tasks
2. Creates HTML artifact with:
   - Urgent section (red)
   - Blocked section (orange)
   - Domain sections (organized)
   - Summary stats
3. Saves snapshot to 00_System/Task_Dashboard.md

**Output:**
```
Dashboard created with 6 tasks.

Highlights:
- 1 urgent task (due soon!)
- 1 blocked task
- 4 active todos

Snapshot saved to: 00_System/Task_Dashboard.md
```

## Output Format

HTML with this structure:

```html
<!DOCTYPE html>
<html>
<head>
<style>
body { font-family: system-ui, -apple-system, sans-serif; max-width: 900px; margin: 40px auto; padding: 20px; background: #f5f5f5; }
.dashboard { background: white; padding: 30px; border-radius: 12px; box-shadow: 0 2px 8px rgba(0,0,0,0.1); }
h1 { color: #333; margin-bottom: 10px; }
.date { color: #666; font-size: 14px; margin-bottom: 30px; }
.section { margin-bottom: 30px; }
.section h2 { font-size: 18px; margin-bottom: 15px; border-bottom: 2px solid #e0e0e0; padding-bottom: 8px; }
.task { padding: 12px; margin-bottom: 8px; border-radius: 6px; border-left: 4px solid; }
.urgent { background: #fff5f5; border-color: #e53e3e; }
.blocked { background: #fff9f5; border-color: #ed8936; }
.high { background: #fef5ff; border-color: #9f7aea; }
.medium { background: #f0f9ff; border-color: #4299e1; }
.low { background: #f7fafc; border-color: #718096; }
.task-title { font-weight: 600; margin-bottom: 4px; }
.task-meta { font-size: 13px; color: #666; }
.domain-section { margin-left: 20px; }
.summary { background: #f7fafc; padding: 15px; border-radius: 6px; margin-top: 30px; }
.summary-stat { display: inline-block; margin-right: 20px; }
</style>
</head>
<body>
<div class="dashboard">
  <h1>📊 Task Dashboard</h1>
  <div class="date">2026-01-06</div>
  
  <div class="section">
    <h2>🚨 Urgent (1)</h2>
    <div class="task urgent">
      <div class="task-title">[ExampleC] prepare-ia-review-meeting</div>
      <div class="task-meta">Due: 2026-01-10 (Friday)</div>
    </div>
  </div>
  
  [... more sections ...]
  
  <div class="summary">
    <strong>📈 Summary</strong><br>
    <span class="summary-stat">Total: 6 tasks</span>
    <span class="summary-stat">1 urgent</span>
    <span class="summary-stat">1 blocked</span>
    <span class="summary-stat">4 active</span>
  </div>
</div>
</body>
</html>
```

## Related Prompts

- [[Show_Tasks]] - Text-based task view
- [[Load_Context]] - Load domain context
- [[Organize_Planning]] - Process inbox

## Notes

- HTML artifact is LIVE - always shows current state
- Saved snapshot goes stale immediately
- Use HTML for visual clarity and styling
- Color-coding makes priorities obvious at a glance
- This is your "morning briefing" view
- Run daily to see what needs attention
- Update last_used when executed