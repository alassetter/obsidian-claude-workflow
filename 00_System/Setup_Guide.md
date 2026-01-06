# Obsidian + Claude MCP Setup Guide

Welcome to your Obsidian knowledge base integrated with Claude via MCP (Model Context Protocol).

## 🎯 What This System Does

This vault is designed for your **interrupt-driven, multi-context workflow** where you:
- Work across multiple projects (XYZ, CompanyA, CompanyB)
- Switch contexts frequently throughout the day
- Need Claude to remember decisions, tech stacks, and project state
- Want to brain dump now, organize later
- Never want to repeat yourself to Claude

## 📁 Folder Structure

### Self-Contained Domains
Each major project area has its own Planning/Tasks/Documentation:

**01_Clients/** - Client work
- `XYZ/` - Enterprise intranet project
  - Planning/ - Project roadmaps
  - Tasks/ - Active to-dos
  - Documentation/ - Client-specific processes

**02_Company_CompanyA/** - Your western wear business
- Planning/ - Product/marketing roadmaps
- Tasks/ - Daily operations
- Documentation/ - Brand guidelines, processes

**03_Company_CompanyB/** - Real estate software
- Planning/ - Dev roadmap
- Tasks/ - Development tasks
- Documentation/ - Architecture, tech decisions

**04_Development/** - Your learning & skills
- Planning/ - Learning roadmap
- Tasks/ - "Learn X", "Try Y"
- Documentation/ - Your notes on patterns

### Cross-Domain Resources
**06_Resources/** - General knowledge (not project-specific)
- AI/ - Claude commands, MCP, AI tools
- Shopify/ - Shopify API, technical refs
- Development/ - JavaScript, Python, React
- IA/ - Information Architecture, UX
- DevOps/ - Git, CI/CD, deployment
- Design/ - UI/UX, color theory, tools
- HowTos/ - General process guides

### System Folders
**00_System/** - Templates, conventions, guides
**05_Prompts/** - Reusable prompts (organized by category + domain tags)
**07_Personal/** - Personal stuff
**09_Planning/** - Your inbox for brain dumps

## 🚀 Daily Workflow

### Morning: Load Context
```
You: /load CompanyA
Claude: [Reads context, tells you where you left off, asks what to focus on]
```

### Throughout Day: Brain Dump
As tasks and ideas come up, dump them in `09_Planning/inbox.md`:
```
Need to update 10 product descriptions
XYZ wants IA review meeting prep
Continue CompanyB user dashboard
Research letta.com
```
No formatting needed - just dump and move on.

### Context Switch: Checkpoint
```
You: /checkpoint
Claude: [Saves current work state]

You: /load XYZ
Claude: [Switches context, loads XYZ info]
```

### End of Day: Organize
```
You: /organize
Claude: [Processes inbox, creates tasks in proper domains, asks about archiving]
```

### Check Tasks
```
You: /tasks CompanyA
Claude: [Shows CompanyA tasks by priority/status]
```

## 🎮 Slash Commands

See `Quick_Reference.md` for complete command list. Most used:

- `/organize` - Process planning inbox into tasks
- `/load [domain]` - Load full context for domain
- `/tasks [domain]` - Show active tasks
- `/checkpoint` - Save current work state
- `/rewrite` - Content rewriting with proper voice
- `/help` - Show all commands

## 📝 Using Templates

Templates are in `00_System/Templates/`. To use:

1. Copy the template content
2. Paste into new note in the right location
3. Fill in the frontmatter and content
4. Claude can help with this - just say "create a task for CompanyA"

**Key Templates:**
- Planning.md - Roadmaps, feature specs
- Task.md - Individual to-dos
- Documentation.md - How-tos, processes
- Project_Context.md - Master context for each domain
- Prompt.md - Reusable prompts

## 🔗 Claude Desktop Projects

You have Claude Desktop projects set up. See `Claude_Projects.md` for mapping.

When Claude says "Switch to: CompanyA Shopify", switch to that project in Claude Desktop. This ensures proper MCP context and tools are available.

## 🧠 How Claude Uses This Vault

**When you say `/load CompanyA`:**
1. Claude reads `02_Company_CompanyA/Project_Context.md`
2. Reads recent Planning docs
3. Reads active Tasks
4. Reads relevant Documentation
5. Summarizes where you are
6. Asks what you want to focus on

**When you say `/organize`:**
1. Claude reads `09_Planning/inbox.md`
2. Identifies which domain each item belongs to
3. Creates Task files in proper domain folders
4. For cross-domain tasks, creates separate tasks in each domain
5. Asks if you want to archive the inbox

**When you say `/checkpoint`:**
1. Claude reviews your conversation
2. Extracts what you worked on
3. Lists decisions made
4. Notes next steps
5. Saves to `09_Planning/YYYY-MM-DD-[project]-checkpoint.md`

## 💡 Best Practices

### Brain Dumping
- Don't format - just write naturally
- Don't categorize - Claude will figure it out
- Don't prioritize yet - that comes during organize
- Do capture everything - better too much than too little

### Task Management
- Tasks are "mix" granularity - some big, some small
- Update status as you work (todo → in-progress → completed)
- Link related tasks together
- Use blockers field when stuck

### Documentation
- Document as you learn, not after
- Domain-specific docs stay WITH the domain
- General resources go in 06_Resources/
- One topic per note

### Prompts
- Save good prompts immediately (use `/prompt save`)
- Tag with domain even if general (helps find later)
- Update use_count and last_used (or let Claude do it)
- Don't duplicate - search first

## 🔧 Troubleshooting

**"Claude doesn't remember X"**
- Check if it's in Project_Context.md for that domain
- If not, add it there
- Use `/load [domain]` to reload context

**"Tasks not showing up"**
- Check frontmatter: status should be `todo`, `in-progress`, or `blocked`
- Check domain field matches what you're searching
- Check if accidentally archived (archived: true)

**"Claude can't find my docs"**
- Check file is in right domain folder
- Check frontmatter type and domain fields
- Try searching by title or content

**"Inbox getting huge"**
- Run `/organize` more frequently (daily is good)
- Archive old organized content
- Start fresh inbox if needed

## 🎓 Learning Path

**Week 1: Get Comfortable**
- Use inbox for brain dumping
- Run `/organize` daily
- Use `/load` when switching contexts

**Week 2: Add Context**
- Fill in Project_Context.md files
- Document recurring processes
- Start using `/checkpoint`

**Week 3: Optimize**
- Save frequently-used prompts
- Refine task workflow
- Add documentation as you learn

**Week 4: Advanced**
- Integrate Claude Desktop projects
- Set up domain-specific MCP servers
- Fine-tune your personal workflow

## 📚 Related Docs

- `Quick_Reference.md` - Command cheat sheet
- `Conventions.md` - Structure rules
- `Claude_Projects.md` - Project mapping
- `09_Planning/README.md` - Inbox system details

---

**Questions?** Ask Claude! Say `/help` for command list.