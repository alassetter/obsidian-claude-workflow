# Obsidian Plugins Guide

Plugin recommendations and configuration for the Obsidian + Claude workflow system.

---

## 🎯 Plugin Philosophy

**Core system works with ZERO plugins!**

Plugins enhance the experience but aren't required. The workflow system is built on:
- Plain markdown files
- Standard folder structure
- Claude MCP integration

You can use this system with vanilla Obsidian + Claude Desktop.

---

## 📊 Plugin Categories

### Required: None! ✅

The system works out of the box.

### Highly Recommended (Enhance Workflow)

These significantly improve the experience:

1. **[Obsidian Git](#obsidian-git)** - Auto-sync to GitHub
2. **[Templater](#templater)** - Advanced template functionality

### Useful (Quality of Life)

These make specific tasks easier:

3. **[Advanced Tables](#advanced-tables)** - Better table editing
4. **[Commander](#commander)** - Custom command palette
5. **[Hover Editor](#hover-editor)** - Quick preview windows

### Optional (Mentioned but not Required)

6. **[Dataview](#dataview)** - Dynamic queries (Dashboard was static HTML instead)
7. **[QuickAdd](#quickadd)** - Quick capture macros
8. **[Local REST API](#local-rest-api)** - External integrations

---

## Plugin Details

### Obsidian Git

**What it does:** Automatically commits and syncs your vault to GitHub

**Why you want it:**
- ✅ Automatic backups
- ✅ Version history
- ✅ Never lose work
- ✅ Sync across devices
- ✅ Collaborate with team

**Installation:**
1. Settings → Community plugins → Browse
2. Search "Obsidian Git"
3. Install + Enable

**Recommended Configuration:**
```
Vault backup interval: 10 minutes
Auto pull interval: 5 minutes
Commit message: "vault backup: {{date}}"
Auto commit: On
Auto push: On
Pull on startup: On
```

**Setup:**
```bash
# Initialize git in your vault (if not cloned)
cd /path/to/vault
git init
git remote add origin https://github.com/alassetter/obsidian-claude-workflow.git

# Obsidian Git will handle commits/pushes automatically
```

**⚠️ Important:** Ensure `.gitignore` is configured before enabling auto-push!

---

###

 Templater

**What it does:** Advanced template system with dynamic variables

**Why you want it:**
- ✅ Auto-insert dates
- ✅ Dynamic file names
- ✅ Template variables
- ✅ JavaScript support
- ✅ Complex workflows

**Installation:**
1. Settings → Community plugins → Browse
2. Search "Templater"
3. Install + Enable

**Recommended Configuration:**
```
Template folder location: 00_System/Templates
Trigger Templater on new file creation: On
Enable folder templates: On
```

**Example Usage:**
Create templates that auto-fill:
- Current date: `{{date}}`
- Current time: `{{time}}`
- Custom variables: `{{title}}`

**Works perfectly with our templates:**
- Task.md
- Planning.md
- Documentation.md

---

### Advanced Tables

**What it does:** Makes editing markdown tables painless

**Why you want it:**
- ✅ Auto-formatting
- ✅ Tab navigation
- ✅ Column alignment
- ✅ Quick calculations

**Installation:**
1. Settings → Community plugins → Browse
2. Search "Advanced Tables"
3. Install + Enable

**Usage:**
- Just start typing a table
- Plugin auto-formats as you type
- Tab/Shift+Tab to navigate cells
- Works in Quick_Reference.md, dashboards, etc.

---

### Commander

**What it does:** Adds custom commands to command palette and UI

**Why you want it:**
- ✅ Quick access to commands
- ✅ Custom hotkeys
- ✅ Pin frequent commands
- ✅ Faster workflow

**Installation:**
1. Settings → Community plugins → Browse
2. Search "Commander"
3. Install + Enable

**Recommended Commands to Add:**
- "Open inbox" → Quick access to `09_Planning/inbox.md`
- "Open Quick Reference" → `00_System/Quick_Reference.md`
- "Create Task" → New file in Tasks folder
- Template commands

---

### Hover Editor

**What it does:** Hover over links to see content without opening

**Why you want it:**
- ✅ Quick previews
- ✅ Less context switching
- ✅ Multi-window editing
- ✅ Better navigation

**Installation:**
1. Settings → Community plugins → Browse
2. Search "Hover Editor"
3. Install + Enable

**Usage:**
- Hold Cmd/Ctrl + hover over link
- Opens in popup window
- Can edit directly in popup
- Great for checking task details

---

### Dataview

**What it does:** Query your vault like a database

**Why it's optional:**
- Our dashboards use static HTML
- System doesn't require dynamic queries
- Useful for custom views

**Installation:**
1. Settings → Community plugins → Browse
2. Search "Dataview"
3. Install + Enable

**When you'd use it:**
```dataview
TABLE priority, status, due_date
FROM "02_Company_A/Tasks"
WHERE status != "completed"
SORT priority DESC
```

**Note:** We use `/dashboard` command for visual overview instead

---

### QuickAdd

**What it does:** Quick capture macros and templates

**Why it's optional:**
- We use `/inbox` command instead
- Useful for complex capture workflows
- Good for non-Claude workflows

**Installation:**
1. Settings → Community plugins → Browse
2. Search "QuickAdd"
3. Install + Enable

**Use case:**
If you want capture WITHOUT Claude:
- Create macro for "New Task"
- Hotkey: Cmd+Shift+T
- Auto-selects domain
- Opens template

---

### Local REST API

**What it does:** External apps can access your vault

**Why it's optional:**
- Advanced use case
- External integrations
- Not needed for core workflow

**Installation:**
1. Settings → Community plugins → Browse
2. Search "Local REST API"
3. Install + Enable
4. Generate API key

**Use cases:**
- Custom scripts
- Mobile apps
- External automations
- Integration with other tools

---

## Recommended Plugin Loadout

### Minimal Setup (Just Getting Started)
```
✅ Obsidian Git
✅ (That's it!)
```

### Standard Setup (Most Users)
```
✅ Obsidian Git
✅ Templater
✅ Advanced Tables
```

### Power User Setup
```
✅ Obsidian Git
✅ Templater
✅ Advanced Tables
✅ Commander
✅ Hover Editor
```

### Advanced Setup (Custom Workflows)
```
✅ All of the above
✅ Dataview
✅ QuickAdd
✅ Local REST API
```

---

## Plugin Installation Process

### Step 1: Enable Community Plugins

1. Open Obsidian
2. Settings (gear icon)
3. Community plugins
4. Turn off "Restricted mode"
5. Click "Browse"

### Step 2: Install Each Plugin

1. Search for plugin name
2. Click "Install"
3. Click "Enable"
4. Configure (see plugin-specific settings)

### Step 3: Configure Settings

Each plugin has settings under:
- Settings → Community plugins → [Plugin name] → Settings icon

---

## Plugin Compatibility

### Tested With:
- ✅ Obsidian 1.5.0+
- ✅ macOS 13+
- ✅ Windows 10+
- ✅ Linux (Ubuntu 22.04+)

### Known Issues:
- **Mobile:** Some plugins don't work on mobile (Templater does!)
- **Sync:** Use Obsidian Git OR Obsidian Sync, not both
- **Performance:** Too many plugins can slow Obsidian

---

## Troubleshooting Plugins

### Plugin Won't Install

**Issue:** "Failed to load plugin"

**Solutions:**
1. Check Obsidian version (must be 1.0+)
2. Update Obsidian to latest version
3. Disable other plugins temporarily
4. Restart Obsidian
5. Try Safe Mode to isolate issue

### Plugin Causes Errors

**Issue:** Error messages, crashes, slow performance

**Solutions:**
1. Disable plugin
2. Check plugin GitHub for known issues
3. Update plugin to latest version
4. Report issue to plugin developer
5. Use Safe Mode to test

### Plugins Conflict

**Issue:** Two plugins don't work together

**Solutions:**
1. Check plugin documentation
2. Disable one at a time to isolate
3. Look for alternative plugins
4. Report to both plugin developers

---

## Plugin Updates

### Automatic Updates

Obsidian can auto-update plugins:
1. Settings → Community plugins
2. Enable "Check for updates on startup"
3. Plugins update automatically

### Manual Updates

1. Settings → Community plugins
2. Click "Check for updates"
3. Update individual plugins
4. Or "Update all"

**Recommended:** Check for updates weekly

---

## Creating Your Own Plugin Loadout

### Step 1: Start Minimal

Install only:
- Obsidian Git (for backups)

Use the system for 1 week.

### Step 2: Add Based on Pain Points

**Issue: Tables are annoying**
→ Install Advanced Tables

**Issue: Templates feel manual**
→ Install Templater

**Issue: Want custom commands**
→ Install Commander

### Step 3: Experiment

Try plugins, disable if not useful.

**Rule of thumb:** If you don't use it weekly, uninstall it.

---

## Plugin Recommendations by Role

### Freelance Consultant
```
✅ Obsidian Git (client data backup)
✅ Templater (client templates)
✅ Advanced Tables (project tracking)
```

### Startup Founder
```
✅ Obsidian Git (team sync)
✅ Commander (fast access)
✅ Dataview (metrics dashboards)
```

### Content Creator
```
✅ Obsidian Git (drafts backup)
✅ Templater (content templates)
✅ QuickAdd (idea capture)
```

### Software Developer
```
✅ Obsidian Git (obvious!)
✅ Advanced Tables (API docs)
✅ Local REST API (tool integration)
```

---

## Alternative Workflows Without Plugins

### Without Obsidian Git
```
Manual git workflow:
git add .
git commit -m "Daily update"
git push
```

### Without Templater
```
Copy/paste from Templates/ folder
Manually update dates
Still works, just more manual
```

### Without Advanced Tables
```
Format tables by hand
Use online table generators
Still readable, just messier
```

**Bottom line:** Plugins enhance, they don't enable.

---

## Community Plugin Resources

- **Official Plugin Directory:** https://obsidian.md/plugins
- **Plugin Stats:** https://obsidian-plugin-stats.vercel.app/
- **Plugin Ideas:** r/ObsidianMD on Reddit
- **Plugin Development:** https://docs.obsidian.md/Plugins/Getting+started/Build+a+plugin

---

## Contributing Plugin Recommendations

Found a plugin that works great with this system?

1. Test it thoroughly
2. Document the use case
3. Submit PR to this file
4. Include configuration recommendations

**Criteria for inclusion:**
- Adds real value to workflow
- Actively maintained
- No major bugs
- Clear use case

---

## Summary

**You need:** Nothing! (System works with vanilla Obsidian)

**You should get:** Obsidian Git (backups)

**You might want:** Templater, Advanced Tables (quality of life)

**You could explore:** Commander, Hover Editor, Dataview (power users)

**Start simple. Add plugins as you discover needs.** 🚀

---

See [SETUP.md](SETUP.md) for installation instructions.