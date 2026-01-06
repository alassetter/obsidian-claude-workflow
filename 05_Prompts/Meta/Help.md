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

You have Obsidian MCP aeaess. Show the user available commands and how to use the system.

**Process:**

1. **Display Quick Reference:**
   - Read `00_System/Quick_Reference.md`
   - Extract the "Most Used Commands" table
   - Show it formatted clearly

2. **Provide context-sensitive help:**
   
   If user just asked:
   - `/help` → Show general command list
   - `/help [command]` → Show details for specific command
   - `/help [topic]` → Show relevant commands for topic
   
   Examples:
   - `/help organize` → Details on /organize command
   - `/help tasks` → All task-related commands
   - `/help examplea` → Commands relevant to ExampleA work

3. **Core help content:**
   
   **Always show:**
   ```
   ## 🎯 Most Used Commands
   
   /organize        → Process planning inbox into tasks
   /load [domain]   → Load full context for domain
   /tasks [domain]  → Show active tasks
   /checkpoint      → Save current work state
   /rewrite         → Rewrite content professionally
   
   ## 📚 More Commands
   
   Planning & Tasks:
   /plan, /task add, /task done
   
   Context & Loading:
   /switch, /status
   
   Documentation:
   /doc, /save doc, /howto
   
   Prompts:
   /prompt find, /prompt save, /prompt use
   ```

4. **Point to detailed docs:**
   - `Quick_Reference.md` - Full command list
   - `Setup_Guide.md` - Complete system guide
   - `Conventions.md` - Structure rules
   - `Claude_Projects.md` - Project mapping

5. **Provide quick start:**
   ```
   ## 🚀 Getting Started
   
   1. Brain dump into 09_Planning/inbox.md
   2. Run /organize to create tasks
   3. Use /load [domain] to start working
   4. Use /checkpoint before switching contexts
   ```

6. **Offer specific help:**
   - "What do you need help with?"
   - If user seems stuck, ask what they're trying to do

**Important Rules:**
- Keep it CONCISE - this is quick reference, not full docs
- Point to detailed docs for deep dives
- Be context-aware - help with what they're working on
- Show examples where helpful
- Don't overwhelm - progressive disclosure
- Natural language alternatives work too

## When to Use

User says:
- `/help`
- `/help [command]`
- `/help [topic]`
- "How do I...?"
- "What commands are available?"
- "I'm stuck"
- "Show me the commands"

## Variables

- `{{command}}`: Optional specific command for detailed help
- `{{topic}}`: Optional topic area (tasks, prompts, planning, etc.)

## Examples

### Example 1: General Help

**User:** `/help`

**Output:**
```
## 🎯 Most Used Commands

| Command | What It Does |
|---------|-------------|
| /organize | Process planning inbox into tasks |
| /load [domain] | Load full context for domain |
| /tasks [domain] | Show active tasks |
| /checkpoint | Save current work state |
| /rewrite | Rewrite content professionally |

## 📚 More Commands

**Planning & Tasks:** /plan, /task add, /task done
**Context:** /switch, /status
**Documentation:** /doc, /save doc, /howto
**Prompts:** /prompt find, /prompt save, /prompt use

## 🏷️ Domain Shortcuts
ExampleA→ea, ExampleB→eb, ExampleC→examplec, Development→dev

## 📖 Detailed Docs
- Quick_Reference.md - All commands with examples
- Setup_Guide.md - Complete system guide  
- Conventions.md - Structure and naming rules

## 🚀 Quick Start
1. Dump tasks in 09_Planning/inbox.md
2. Run /organize
3. Use /load [domain] to work
4. Use /checkpoint before switching

What do you need help with?
```

### Example 2: Specific Command

**User:** `/help organize`

**Output:**
```
## /organize Command

**What it does:**
Reads your planning inbox (09_Planning/inbox.md) and creates structured task files in the appropriate domain folders.

**Usage:**
- `/organize` → Process everything in inbox
- `/organize examplea` → Process only ExampleA items

**What it does for you:**
1. Reads your brain dump
2. Figures out which domain each item belongs to
3. Creates task files in correct folders
4. Handles cross-domain tasks
5. Asks if you want to archive the inbox

**Example:**
Inbox: "Update 10 product descriptions, prep ExampleC meeting, continue ExampleB auth"

Result: Creates 3 separate task files:
- 02_Company_ExampleA/Tasks/update-product-descriptions.md
- 01_Clients/ExampleC/Tasks/prepare-meeting.md
- 03_Company_ExampleB/Tasks/continue-auth-system.md

**Tips:**
- Run daily at end of day
- Don't overthink inbox format - just dump
- Claude handles categorization
- Archives keep history

More details: 05_Prompts/Meta/Organize_Planning.md
```

### Example 3: Topic Area

**User:** `/help tasks`

**Output:**
```
## Task Commands

**View tasks:**
- `/tasks` → Show all active tasks
- `/tasks [domain]` → Show domain-specific tasks
- `/tasks priority:high` → Filter by priority

**Create tasks:**
- `/task add` → Create single task (asks for details)
- `/task add [domain]` → Create for specific domain
- `/organize` → Batch create from inbox

**Manage tasks:**
- `/task done [name]` → Mark complete
- Edit task file directly to update

**Files:**
Tasks live in: [domain]/Tasks/[task-name].md
Template: 00_System/Templates/Task.md

**Quick tip:** 
Use /organize for multiple tasks, /task add for single tasks.

More help needed?
```

### Example 4: Context-Sensitive

**User:** "I'm trying to switch from ExampleC work to ExampleA"

**Output:**
```
To switch contexts:

1. **Save current state:**
   `/checkpoint`
   
2. **Load new context:**
   `/load examplea` or `/load ea`
   
3. **Switch Claude Desktop project:**
   When prompted, switch to "ExampleA Shopify" project

That's it! Claude will load all ExampleA context and you're ready to work.

**Pro tip:** The checkpoint helps you pick up ExampleC work later exactly where you left off.

Try it now?
```

### Example 5: Getting Started

**User:** "I just set this up, where do I start?"

**Output:**
```
Welcome! Here's your workflow:

## Day 1: Brain Dump
Throughout today, dump ALL tasks/ideas into:
📝 09_Planning/inbox.md

Don't organize, just dump. Like this:
"Update ExampleA products
ExampleC meeting prep
ExampleB auth work
Research new framework"

## End of Day: Organize
Say: `/organize`

Claude will:
✅ Create task files in right domains
✅ Set priorities
✅ Ask about archiving

## Tomorrow: Load & Work
Say: `/load examplea`

Claude shows:
- Where you left off
- Active tasks
- What to focus on

## When Switching Contexts
Say: `/checkpoint` (saves progress)
Then: `/load [new domain]`

## Questions?
- `/help` → This guide
- Quick_Reference.md → All commands
- Setup_Guide.md → Complete walkthrough

Try dumping some tasks in the inbox now!
```

## Output Format

1. Concise command reference
2. Context-appropriate detail
3. Examples where helpful
4. Links to deeper documentation
5. Follow-up question or next step

## Related Prompts

All prompts! This is the entry point to discovering them.

## Notes

- Help should be HELPFUL not overwhelming
- Progressive disclosure - show basics, offer more
- Context matters - help with what they're doing NOW
- Point to docs for deep dives - don't duplicate them
- Natural language works - user doesn't have to remember exact syntax
- This is used by people who are stuck - be patient and clear
- Update last_used when invoked