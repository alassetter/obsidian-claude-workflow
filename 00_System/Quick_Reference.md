# Quick Reference - Claude Commands

Your cheat sheet for working with Claude + Obsidian MCP.

## 🎯 Most Used Commands

| Command | What It Does | Example |
|---------|-------------|---------|
| `/inbox [text]` | Quick add to planning inbox | `/inbox XYZ create page` |
| `/organize` | Process planning inbox into tasks | `/organize` |
| `/dashboard` | Visual HTML task overview | `/dashboard` |
| `/load [domain]` | Load full context for domain | `/load CompanyA` |
| `/tasks [domain]` | Show active tasks | `/tasks XYZ` |
| `/checkpoint` | Save current work state | `/checkpoint` |
| `/rewrite` | Rewrite content professionally | `/rewrite` |

## 📋 All Commands

### Planning & Tasks

| Command | What It Does | Example |
|---------|-------------|---------|
| `/inbox [text]` | Quick add to inbox (no file opening!) | `/inbox XYZ create employment page` |
| `/plan [domain]` | Open/create planning doc | `/plan CompanyB` |
| `/organize` | Process inbox → tasks | `/organize` |
| `/organize [domain]` | Process inbox for specific domain | `/organize CompanyA` |
| `/dashboard` | Visual HTML task dashboard | `/dashboard` |
| `/tasks` | Show all active tasks (text) | `/tasks` |
| `/tasks [domain]` | Show domain-specific tasks | `/tasks XYZ` |
| `/task add [domain]` | Create new task | `/task add CompanyA` |
| `/task done [name]` | Mark task complete | `/task done update-products` |

### Context & Loading

| Command | What It Does | Example |
|---------|-------------|---------|
| `/load [domain]` | Load full context | `/load CompanyA` |
| `/switch [domain]` | Tell me which Claude project | `/switch CompanyB` |
| `/status [domain]` | Quick status summary | `/status XYZ` |
| `/checkpoint` | Save current work state | `/checkpoint` |

### Documentation

| Command | What It Does | Example |
|---------|-------------|---------|
| `/doc [topic]` | Search documentation | `/doc shopify api` |
| `/save doc [domain]` | Save conversation as doc | `/save doc CompanyA` |
| `/howto [topic]` | Find how-to guide | `/howto git workflow` |

### Prompts

| Command | What It Does | Example |
|---------|-------------|---------|
| `/prompt find [keyword]` | Search prompts | `/prompt find rewrite` |
| `/prompt save` | Save current as prompt | `/prompt save` |
| `/prompt use [name]` | Load and apply prompt | `/prompt use product-description` |

### Content & Writing

| Command | What It Does | Example |
|---------|-------------|---------|
| `/rewrite` | Rewrite content | `/rewrite professional` |
| `/rewrite [style]` | Rewrite in specific style | `/rewrite casual` |
| `/voice [brand]` | Apply brand voice | `/voice CompanyA` |
| `/analyze` | Analyze content/data | `/analyze` |

### Help & Navigation

| Command | What It Does | Example |
|---------|-------------|---------|
| `/help` | Show this reference | `/help` |
| `/commands` | List all commands | `/commands` |

## 🏷️ Domain Shortcuts

You can use full names OR shortcuts:

| Full Name | Shortcut | Use Either |
|-----------|----------|------------|
| CompanyA | cc | `/load CompanyA` OR `/load cc` |
| CompanyB | ax | `/load CompanyB` OR `/load ax` |
| XYZ | XYZ | `/load XYZ` |
| Development | dev | `/load development` OR `/load dev` |

## 💡 Common Workflows

### Throughout Your Day - Quick Capture
```
/inbox XYZ create employment page
/inbox CompanyA update product photos
/inbox research new framework
```
Instant capture without opening files!

### Start Your Day
```
/dashboard               (visual overview)
/load [domain]          (load context)
```
See what's urgent, what's blocked, then dive in.

### Switch Context Mid-Day
```
/checkpoint              (save current work)
/load [new domain]       (switch context)
```

### End of Day
```
/organize                (process your brain dump)
```
Claude creates tasks in proper domains, asks about archiving.

### Check What's On Your Plate
```
/dashboard              (visual HTML overview)
/tasks                  (text list, all domains)
/tasks CompanyA       (specific domain)
```

### Need to Remember How to Do Something
```
/doc [topic]             (search your docs)
/howto [topic]           (find how-to guides)
```

### Reuse a Good Prompt
```
/prompt find [keyword]   (search prompts)
/prompt use [name]       (apply the prompt)
```

### Save a New Prompt
```
[have great conversation with Claude]
/prompt save
```
Claude extracts the prompt pattern and saves it.

## 📝 Natural Language Also Works

You don't HAVE to use slash commands. These also work:

**Instead of `/inbox`:**
- "Add to inbox: create XYZ page"
- "Quick capture: review analytics"

**Instead of `/dashboard`:**
- "Show my task dashboard"
- "What's on my plate?"
- "Task overview"

**Instead of `/load CompanyA`:**
- "Load context for CompanyA"
- "Switch to CompanyA work"
- "What's going on with CompanyA?"

**Instead of `/organize`:**
- "Organize my planning notes"
- "Process my inbox"
- "Create tasks from my brain dump"

**Instead of `/checkpoint`:**
- "Create a checkpoint"
- "Save my progress"
- "Save where I'm at"

The slash commands are just faster! Use whatever feels natural.

## 🎨 Command Options

### Rewrite Styles
- `professional` - Business/corporate tone
- `casual` - Friendly, relaxed
- `technical` - Developer/technical audience
- `marketing` - Persuasive, benefit-focused
- `CompanyA` - CompanyA brand voice

### Task Filters
- By domain: `/tasks CompanyA`
- By status: `/tasks status:in-progress`
- By priority: `/tasks priority:high`

### Organization Options
- All domains: `/organize`
- Specific domain: `/organize CompanyA`
- Dry run: `/organize --preview` (shows what would be created)

### Dashboard Options
- Standard: `/dashboard`
- Save snapshot: `/dashboard --save` (default)
- No save: `/dashboard --no-save`

## ⚡ Power User Tips

**Quick Capture Throughout Day:**
```
/inbox XYZ urgent meeting prep
/inbox cc analyze sales data
/inbox research competitor pricing
```
No context switching - just capture and move on!

**Morning Routine:**
```
/dashboard              (visual overview)
/load [urgent domain]   (dive into urgent work)
```

**Batch Operations:**
```
/tasks CompanyA status:todo priority:high
```
Show only high-priority todos for CompanyA.

**Context Chain:**
```
/load CompanyA
[work for a while]
/checkpoint
/load XYZ
```
Seamless context switching with saved state.

**Smart Organize:**
```
/organize --split
```
For items that span multiple domains, create separate tasks in each.

**Prompt Discovery:**
```
/prompt find domain:CompanyA category:writing
```
Find all CompanyA writing prompts.

## 🔍 Finding Things

**Don't Remember Command:**
- `/help` - Shows this reference
- `/commands` - Lists all available commands

**Don't Remember Where File Is:**
- Just describe it: "Find my XYZ navigation doc"
- Claude will search and find it

**Don't Remember Exact Prompt Name:**
- `/prompt find [keyword]`
- Claude searches by name, content, and domain

## 📚 More Info

- `Setup_Guide.md` - Complete system overview
- `Conventions.md` - Structure rules
- `Claude_Projects.md` - Project mapping
- `09_Planning/README.md` - Inbox system details

---

**Pro Tip:** Bookmark this file in Obsidian for quick access!