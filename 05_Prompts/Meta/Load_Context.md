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

You have Obsidian MCP access. Load complete context for a domain so user can start working.

**Process:**

1. **Identify domain:**
   - User says `/load [domain]` or "load context for [domain]"
   - Accept full names OR shortcuts: CompanyA/cc, CompanyB/ax, XYZ/XYZ, Development/dev

2. **Read these files in order:**
   
   **A. Project Context (ALWAYS READ FIRST):**
   - `[domain]/Project_Context.md`
   - This has tech stack, current state, key decisions, constraints
   
   **B. Recent Planning (READ NEXT):**
   - List all files in `[domain]/Planning/`
   - Read files with status: active or in-progress
   - Focus on most recently updated
   
   **C. Active Tasks (IMPORTANT):**
   - List all files in `[domain]/Tasks/`
   - Filter: status NOT completed, NOT archived
   - Group by priority (urgent, high, medium, low)
   - Note any blocked tasks
   
   **D. Key Documentation (AS NEEDED):**
   - List `[domain]/Documentation/`
   - Don't read all - just show what's available
   - Read if user asks or if relevant to recent work

3. **Synthesize into brief summary:**
   
   ```
   ## Current State
   [Where we are - from Project_Context]
   
   ## Active Work
   [What's in progress - from Planning + Tasks]
   
   ## Today's Priority
   [High/urgent tasks]
   
   ## Blockers
   [Anything stuck]
   
   ## Available Context
   [List key docs available]
   ```

4. **Suggest Claude Desktop Project:**
   - Read `00_System/Claude_Projects.md`
   - Tell user: "Switch to Claude Desktop project: '[ProjectName]'"
   - Explain what MCP servers are available there

5. **Ask what to focus on:**
   - "What do you want to work on?"
   - Be ready to load specific docs or dive deeper

**Important Rules:**
- Be CONCISE - this is a briefing, not a full read
- Prioritize recent activity over old
- Don't read completed tasks unless asked
- Don't read archived content
- Surface blockers immediately
- Make it easy to jump into work

## When to Use

User says:
- `/load [domain]`
- `/load` (ask which domain)
- "Load context for CompanyA"
- "Switch to XYZ work"
- "Where were we on CompanyB?"
- "What's going on with [domain]?"

## Variables

- `{{domain}}`: Required - CompanyA/cc, CompanyB/ax, XYZ/XYZ, Development/dev
- `--deep` flag: Read all documentation too (more comprehensive)
- `--tasks-only` flag: Just show tasks, skip planning

## Examples

### Example 1: Load CompanyA

**User:** `/load CompanyA`

**Output:**
```
Switch to Claude Desktop project: 'CompanyA Shopify'

## Current State
- B2C/B2B western wear business via Shopify
- Fall collection launching soon
- Focus: Product descriptions + inventory optimization

## Active Work
Planning:
- Fall-2026-Product-Launch.md (in progress)
- Q1-Marketing-Strategy.md (active)

## Today's Priority
HIGH:
- update-product-descriptions.md (10 products need copy)
- optimize-product-images.md (fall collection)

MEDIUM:
- shopify-inventory-audit.md
- review-abandoned-carts.md

## Blockers
None currently

## Available Context
- Brand-Voice-Guidelines.md
- Product-Photography-Process.md
- Shopify-Workflow.md

What do you want to work on?
```

### Example 2: Load with Blocker

**User:** `/load CompanyB`

**Output:**
```
Switch to Claude Desktop project: 'company-b'

## Current State
- Real estate software in active development
- Tech: React, Node.js, PostgreSQL
- Phase: Building user authentication system

## Active Work
Planning:
- User-Auth-Implementation.md (in progress)

## Today's Priority
BLOCKED:
- user-dashboard-authentication.md
  Blocker: Need OAuth configuration from client

MEDIUM:
- property-search-ui.md
- database-schema-review.md

## Blockers
🚨 Authentication work blocked on OAuth config

## Available Context
- Authentication-Architecture.md
- Database-Schema.md
- React-Component-Library.md

Should we work on the unblocked tasks while waiting, or address the blocker?
```

### Example 3: Clean Slate

**User:** `/load development`

**Output:**
```
Switch to Claude Desktop project: 'ClaudeKit'

## Current State
- Learning roadmap active
- Focus: Claude skills, MCP, React patterns

## Active Work
No active planning docs

## Today's Priority
LOW:
- learn-claude-skills.md
- experiment-with-mcp.md

## Blockers
None

## Available Context
- React.md (existing notes)

Looks pretty quiet here. Want to start a new learning project or continue something?
```

## Output Format

1. Claude Desktop project switch instruction
2. Concise summary (not more than 15 lines typically)
3. Clear priority grouping
4. Immediate flag for blockers
5. Question to guide next action

## Related Prompts

- [[Show_Tasks]] - Just view tasks without full context
- [[Create_Checkpoint]] - Save state before switching
- [[Organize_Planning]] - Process inbox first

## Notes

- This is called FREQUENTLY - keep it fast and concise
- User has interrupt-driven workflow - they need to reload context often
- Don't lecture or explain - they know the system
- Assume they want to START WORKING, not read documentation
- If nothing is active, say so clearly and ask what to start
- Update last_used timestamp when executed