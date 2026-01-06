# Quick Reference - Claude Commands

Your cheat sheet for working with Claude + Obsidian MCP.

## 🎯 Most Used Commands

| Command | What It Does | Example |
|---------|-------------|---------|
| `/inbox [text]` | Quick add to planning inbox | `/inbox xyz create page` |
| `/organize` | Process planning inbox into tasks | `/organize` |
| `/dashboard` | Visual HTML task overview | `/dashboard` |
| `/load [domain]` | Load full context for domain | `/load companya` |
| `/tasks [domain]` | Show active tasks | `/tasks xyz` |
| `/checkpoint` | Save current work state | `/checkpoint` |
| `/rewrite` | Rewrite content professionally | `/rewrite` |

## 📋 All Commands

### Planning & Tasks

| Command | What It Does | Example |
|---------|-------------|---------|
| `/inbox [text]` | Quick add to inbox (no file opening!) | `/inbox xyz create landing page` |
| `/plan [domain]` | Open/create planning doc | `/plan companyb` |
| `/organize` | Process inbox → tasks | `/organize` |
| `/organize [domain]` | Process inbox for specific domain | `/organize companya` |
| `/dashboard` | Visual HTML task dashboard | `/dashboard` |
| `/tasks` | Show all active tasks (text) | `/tasks` |
| `/tasks [domain]` | Show domain-specific tasks | `/tasks xyz` |
| `/task add [domain]` | Create new task | `/task add companya` |
| `/task done [name]` | Mark task complete | `/task done update-products` |

### Context & Loading

| Command | What It Does | Example |
|---------|-------------|---------|
| `/load [domain]` | Load full context | `/load companya` |
| `/switch [domain]` | Tell me which Claude project | `/switch companyb` |
| `/status [domain]` | Quick status summary | `/status xyz` |
| `/checkpoint` | Save current work state | `/checkpoint` |

### Documentation

| Command | What It Does | Example |
|---------|-------------|---------|
| `/doc [topic]` | Search documentation | `/doc shopify api` |
| `/save doc [domain]` | Save conversation as doc | `/save doc companya` |
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
| `/voice [brand]` | Apply brand voice | `/voice companya` |
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
| Company_A | ca | `/load companya` OR `/load ca` |
| Company_B | cb | `/load companyb` OR `/load cb` |
| Client_XYZ | xyz | `/load xyz` |
| Development | dev | `/load development` OR `/load dev` |

## 💡 Common Workflows

### Throughout Your Day - Quick Capture
```
/inbox xyz create landing page
/inbox ca update content
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
/tasks companya         (specific domain)
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
- "Add to inbox: create Client_XYZ page"
- "Quick capture: review analytics"

**Instead of `/dashboard`:**
- "Show my task dashboard"
- "What's on my plate?"
- "Task overview"

**Instead of `/load companya`:**
- "Load context for Company_A"
- "Switch to Company_A work"
- "What's going on with Company_A?"

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
- `companya` - Company_A brand voice

### Task Filters
- By domain: `/tasks companya`
- By status: `/tasks status:in-progress`
- By priority: `/tasks priority:high`

### Organization Options
- All domains: `/organize`
- Specific domain: `/organize companya`
- Dry run: `/organize --preview` (shows what would be created)

### Dashboard Options
- Standard: `/dashboard`
- Save snapshot: `/dashboard --save` (default)
- No save: `/dashboard --no-save`

## ⚡ Power User Tips

**Quick Capture Throughout Day:**
```
/inbox xyz urgent meeting prep
/inbox ca analyze sales data
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
/tasks companya status:todo priority:high
```
Show only high-priority todos for Company_A.

**Context Chain:**
```
/load companya
[work for a while]
/checkpoint
/load xyz
```
Seamless context switching with saved state.

**Smart Organize:**
```
/organize --split
```
For items that span multiple domains, create separate tasks in each.

**Prompt Discovery:**
```
/prompt find domain:companya category:writing
```
Find all Company_A writing prompts.

## 🔍 Finding Things

**Don't Remember Command:**
- `/help` - Shows this reference
- `/commands` - Lists all available commands

**Don't Remember Where File Is:**
- Just describe it: "Find my Client_XYZ navigation doc"
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