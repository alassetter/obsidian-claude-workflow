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

You have Obsidian MCP access. Quickly append text to the planning inbox without opening the file.

**Process:**

1. **Read current inbox:**
   - Open `09_Planning/inbox.md`
   - Locate the "## Notes" section

2. **Parse user input:**
   - Extract the text to add
   - Optional domain hint (xyz, companya, companyb, dev)
   - Keep formatting simple

3. **Append to inbox:**
   - Add timestamp: `**[HH:MM]**` (optional, if helpful)
   - Add the text
   - Preserve existing content
   - Maintain organized: false in frontmatter

4. **Confirm:**
   - Brief confirmation: "Added to inbox."
   - Optionally show what was added
   - Remind: "Run `/organize` when ready to process."

**Important Rules:**
- Don't overwrite existing inbox content
- Append to the Notes section
- Keep it fast - minimal processing
- Don't organize yet - that's what `/organize` does
- Simple confirmation, no lengthy output

## When to Use

User says:
- `/inbox [text]`
- `/inbox xyz [text]`
- "Add to inbox: [text]"
- "Quick capture: [text]"

## Variables

- `{{text}}`: The content to add to inbox
- `{{domain}}`: Optional domain hint for later organization

## Examples

### Example 1: Simple Addition

**User:** `/inbox xyz create landing page and link to external resource`

**Claude reads inbox, appends:**
```
**[11:45]** xyz create landing page and link to external resource
```

**Output:**
```
Added to inbox: "xyz create landing page and link to external resource"

Run /organize when ready to process.
```

### Example 2: Multi-line Entry

**User:** `/inbox update companya content photos for seasonal collection - need professional shots`

**Claude appends:**
```
**[14:22]** update companya content photos for seasonal collection - need professional shots
```

**Output:**
```
Added to inbox.

Run /organize when ready to process your 3 items.
```

### Example 3: No Domain Hint

**User:** `/inbox research better task management tools`

**Claude appends:**
```
**[09:15]** research better task management tools
```

**Output:**
```
Added to inbox: "research better task management tools"

Run /organize to sort into appropriate domain.
```

### Example 4: Quick Succession

**User:** 
```
/inbox update companyb database schema
/inbox review xyz analytics
/inbox companya inventory audit
```

**Claude appends all three:**
```
**[10:30]** update companyb database schema
**[10:30]** review xyz analytics  
**[10:30]** companya inventory audit
```

**Output:**
```
Added 3 items to inbox.

Run /organize when ready to process.
```

## Output Format

1. Confirmation message (one line)
2. What was added (brief)
3. Reminder to run /organize

Keep it SHORT - this is a quick capture tool.

## Related Prompts

- [[Organize_Planning]] - Process inbox into tasks
- [[Show_Tasks]] - View current tasks
- [[Load_Context]] - Load domain context

## Notes

- This is for SPEED - quick brain dump without context switch
- Don't create tasks immediately - let /organize handle that
- Timestamps help track when things were added
- Can be called multiple times in quick succession
- User never needs to open the inbox file manually
- Think of it like a "quick capture" in GTD methodology
- Update last_used when executed