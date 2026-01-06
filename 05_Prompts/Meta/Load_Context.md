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
   - Accept full names OR shortcuts: Company_A/ca, Company_B/cb, Client_XYZ/xyz, Development/dev

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
- "Load context for Company_A"
- "Switch to Client_XYZ work"
- "Where were we on Company_B?"
- "What's going on with [domain]?"

## Variables

- `{{domain}}`: Required - Company_A/ca, Company_B/cb, Client_XYZ/xyz, Development/dev
- `--deep` flag: Read all documentation too (more comprehensive)
- `--tasks-only` flag: Just show tasks, skip planning

## Examples

### Example 1: Load Company_A

**User:** `/load companya`

**Output:**
```
Switch to Claude Desktop project: 'Company A Project'

## Current State
- B2C/B2B e-commerce business
- Seasonal collection launching soon
- Focus: Content creation + inventory optimization

## Active Work
Planning:
- Seasonal-2026-Product-Launch.md (in progress)
- Q1-Marketing-Strategy.md (active)

## Today's Priority
HIGH:
- update-content-descriptions.md (10 items need copy)
- optimize-content-images.md (seasonal collection)

MEDIUM:
- inventory-audit.md
- review-abandoned-carts.md

## Blockers
None currently

## Available Context
- Brand-Voice-Guidelines.md
- Content-Photography-Process.md
- E-commerce-Workflow.md

What do you want to work on?
```

### Example 2: Load with Blocker

**User:** `/load companyb`

**Output:**
```
Switch to Claude Desktop project: 'Company B Project'

## Current State
- SaaS platform in active development
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