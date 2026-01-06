# Planning Folder

This is your **planning inbox** - the central place where you brain dump everything before it gets organized.

## 📥 The Inbox System

### How It Works

**During Your Day:**
1. Work gets interrupted (normal for you!)
2. Ideas, tasks, and notes pile up
3. Dump everything into `inbox.md` - no organization needed
4. Keep working

**End of Day (or anytime):**
1. Say: `/organize`
2. Claude reads your inbox
3. Creates proper task files in the right domains:
   - CompanyA tasks → `02_Company_CompanyA/Tasks/`
   - XYZ tasks → `01_Clients/XYZ/Tasks/`
   - CompanyB tasks → `03_Company_CompanyB/Tasks/`
   - Dev learning → `04_Development/Tasks/`
4. Claude asks if you want to archive the inbox

### What Goes in the Inbox

**Everything! Examples:**
- "Need to update 10 product descriptions for CompanyA"
- "XYZ wants IA review meeting prep"
- "Continue CompanyB user dashboard"
- "Research letta.com for memory management"
- "Review that Shopify analytics report"
- "Learn how to use Claude skills"

**Don't worry about:**
- Formatting
- Which domain it belongs to
- Breaking it into subtasks
- Priority or dates

Claude will figure all that out when you run `/organize`.

## 📝 Files in This Folder

### inbox.md
- Your active brain dump file
- Always append to this (don't delete old content until organized)
- Use `/organize` to process it

### Checkpoints
- Files like `2026-01-05-obsidian-setup-checkpoint.md`
- Saves progress on longer work sessions
- Created with `/checkpoint` command
- Don't delete these - they help you resume work

### Organized Archives
- After `/organize` processes your inbox, old content can be archived here
- Named by date: `2026-01-05-inbox-archive.md`
- Safe to keep for reference

## 🎯 Commands You'll Use

- `/organize` - Process inbox into tasks
- `/checkpoint` - Save current work state
- `/plan [domain]` - Create a planning doc for specific domain

## 💡 Tips

**Brain Dump Format:**
Just write naturally! These all work:
```
Tomorrow: CompanyA product descriptions, XYZ nav review

Need to:
- Update product photos
- Review CompanyB auth system
- Schedule XYZ meeting

Random thoughts: Maybe integrate Shopify data into CompanyB?
```

**Cross-Domain Tasks:**
If something involves multiple domains, just write it once. Claude will ask you how to split it or create separate tasks in each domain.

**Don't Overthink:**
The inbox is meant to be FAST. Just dump and move on. Organization happens later.