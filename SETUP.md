# Setup Guide - Obsidian + Claude Workflow

Complete installation and configuration guide for the Obsidian + Claude workflow system.

---

## 📋 Table of Contents

1. [Prerequisites](#prerequisites)
2. [Obsidian Installation](#obsidian-installation)
3. [Vault Setup](#vault-setup)
4. [Plugin Installation](#plugin-installation)
5. [Claude Desktop Setup](#claude-desktop-setup)
6. [MCP Server Configuration](#mcp-server-configuration)
7. [Testing Your Installation](#testing-your-installation)
8. [Troubleshooting](#troubleshooting)
9. [Next Steps](#next-steps)

---

## Prerequisites

### Required Software

1. **Obsidian** (v1.5.0 or later)
   - Download: https://obsidian.md/
   - Free for personal use
   - Available: Windows, macOS, Linux

2. **Claude Desktop** (with MCP support)
   - Download: https://claude.ai/download
   - Requires Claude Pro or Team subscription for MCP
   - Available: Windows, macOS

3. **Git** (for version control)
   - Download: https://git-scm.com/
   - Required for cloning repository
   - Available: All platforms

### System Requirements

- **OS:** Windows 10+, macOS 11+, or modern Linux
- **RAM:** 4GB minimum, 8GB recommended
- **Storage:** 100MB for vault + your content
- **Internet:** Required for Claude Desktop, optional for Obsidian

---

## Obsidian Installation

### Step 1: Download Obsidian

1. Visit https://obsidian.md/
2. Click "Download"
3. Choose your operating system
4. Run the installer

### Step 2: Complete First Launch

1. Launch Obsidian
2. Skip the "Create new vault" step (we'll open existing)
3. You'll see the vault picker

---

## Vault Setup

### Step 1: Clone the Repository

**Option A: Using Git (Recommended)**

```bash
# Navigate to where you want the vault
cd ~/Documents/

# Clone the repository
git clone https://github.com/yourusername/obsidian-claude-workflow.git

# Navigate into the vault
cd obsidian-claude-workflow
```

**Option B: Download ZIP**

1. Go to https://github.com/yourusername/obsidian-claude-workflow
2. Click "Code" → "Download ZIP"
3. Extract to your desired location
4. Rename folder if needed

### Step 2: Open Vault in Obsidian

1. Launch Obsidian
2. Click "Open folder as vault"
3. Navigate to the cloned/downloaded folder
4. Select `obsidian-claude-workflow`
5. Click "Open"

### Step 3: Trust the Vault

Obsidian will ask if you trust this vault:
- **Click "Trust author and enable plugins"**
- This is safe for this repository
- Required for custom settings to work

---

## Plugin Installation

### Core System (No Plugins Required!)

The system works out of the box with vanilla Obsidian + Claude MCP.

### Recommended Plugins (Optional)

See [PLUGINS.md](PLUGINS.md) for the full list and installation instructions.

**Quick install:**
1. Settings → Community plugins
2. Browse and search for each plugin
3. Install + Enable

**Most useful:**
- **Obsidian Git** - Auto-sync to GitHub
- **Advanced Tables** - Better table editing
- **Templater** - Advanced templates

---

## Claude Desktop Setup

### Step 1: Install Claude Desktop

1. Download from https://claude.ai/download
2. Install the application
3. Launch and sign in
4. Verify you have Claude Pro/Team (MCP requires paid plan)

### Step 2: Enable MCP

1. Open Claude Desktop settings (gear icon)
2. Navigate to "Developer" section
3. Ensure "Enable MCP" is checked
4. Note the MCP configuration directory:
   - **macOS:** `~/Library/Application Support/Claude/`
   - **Windows:** `%APPDATA%\Claude\`

### Step 3: Create Claude Desktop Projects

You'll create multiple Claude Desktop projects, one per domain:

**For each domain (CompanyA, CompanyB, XYZ, Development):**

1. In Claude Desktop, click "New Project"
2. Name it according to domain:
   - `CompanyA Shopify` (for CompanyA)
   - `company-b` (for CompanyB)
   - `XYZ` (for XYZ)
   - `ClaudeKit` (for Development)
3. Add custom instructions (see next section)
4. Configure MCP servers (see MCP section)

---

## MCP Server Configuration

### Understanding MCP Servers

MCP (Model Context Protocol) allows Claude to interact with external tools:
- **Obsidian MCP** - Read/write vault files
- **Filesystem MCP** - Access local files
- **Git MCP** - Version control
- **Shopify MCP** - For e-commerce work (optional)

### Step 1: Install Obsidian MCP Server

The Obsidian MCP server allows Claude to interact with your vault.

**Installation varies by platform - see official docs:**
- https://github.com/anthropics/obsidian-mcp

**Quick start (macOS/Linux):**
```bash
# Install via npm
npm install -g @anthropic-ai/obsidian-mcp

# Or via pip
pip install obsidian-mcp
```

### Step 2: Configure MCP Servers Per Project

**Location of config file:**
- **macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`
- **Windows:** `%APPDATA%\Claude\claude_desktop_config.json`

**Example configuration:**

```json
{
  "mcpServers": {
    "obsidian": {
      "command": "obsidian-mcp",
      "args": ["/path/to/obsidian-claude-workflow"],
      "env": {}
    },
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/path/to/obsidian-claude-workflow"]
    },
    "git": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-git", "/path/to/obsidian-claude-workflow"]
    }
  }
}
```

### Step 3: Configure Domain-Specific Contexts

For each Claude Desktop project, set the working directory to the appropriate domain folder:

**CompanyA Shopify:**
```json
"filesystem": {
  "command": "npx",
  "args": ["-y", "@modelcontextprotocol/server-filesystem", 
           "/path/to/obsidian-claude-workflow/02_Company_CompanyA"]
}
```

**XYZ:**
```json
"filesystem": {
  "command": "npx",
  "args": ["-y", "@modelcontextprotocol/server-filesystem",
           "/path/to/obsidian-claude-workflow/01_Clients/XYZ"]
}
```

**This ensures:**
- Claude can only see relevant files per project
- Better security (client isolation)
- Faster file operations (smaller scope)

### Step 4: Add Shopify MCP (Optional)

If you have a Shopify store:

```json
"shopify": {
  "command": "shopify-mcp",
  "env": {
    "SHOPIFY_STORE_URL": "your-store.myshopify.com",
    "SHOPIFY_ACCESS_TOKEN": "your-access-token"
  }
}
```

Only add to relevant projects (e.g., "CompanyA Shopify")

### Step 5: Restart Claude Desktop

After configuring MCP servers:
1. Completely quit Claude Desktop
2. Relaunch
3. MCP servers should now be available

---

## Testing Your Installation

### Test 1: Obsidian Vault

1. Open Obsidian vault
2. Navigate to `09_Planning/inbox.md`
3. Verify you see the planning inbox template
4. Try creating a note - it should save successfully

✅ **Success:** You can read and write notes

### Test 2: Claude Desktop Connection

1. Open Claude Desktop
2. Open any project
3. Type: "Can you see my Obsidian vault?"
4. Claude should respond affirmatively

✅ **Success:** MCP connection working

### Test 3: File Operations

In Claude Desktop:
```
List files in the 00_System folder
```

Claude should list:
- Templates/
- Setup_Guide.md
- Quick_Reference.md
- etc.

✅ **Success:** Filesystem MCP working

### Test 4: Command System

In Claude Desktop:
```
/help
```

Claude should show the command reference.

✅ **Success:** Command system working

### Test 5: Full Workflow

```
/inbox test task for testing setup
/organize
/dashboard
```

Should:
1. Add to inbox
2. Create task in appropriate domain
3. Show HTML dashboard

✅ **Success:** System fully operational!

---

## Troubleshooting

### Issue: Claude can't see vault

**Symptoms:**
- Claude says "I don't have access to files"
- File operations fail

**Solutions:**
1. Check MCP server configuration in `claude_desktop_config.json`
2. Verify vault path is correct (use absolute paths)
3. Restart Claude Desktop completely
4. Check MCP server logs

**Logs location:**
- macOS: `~/Library/Logs/Claude/`
- Windows: `%APPDATA%\Claude\Logs\`

### Issue: Obsidian plugins not loading

**Symptoms:**
- Plugins show as "Not loaded"
- Features don't work

**Solutions:**
1. Settings → Community plugins → Enable Community Plugins
2. Trust the vault author
3. Disable "Restricted mode"
4. Restart Obsidian

### Issue: Commands don't work

**Symptoms:**
- `/organize` does nothing
- Claude doesn't recognize commands

**Solutions:**
1. Make sure you're in a Claude Desktop PROJECT (not just chat)
2. Verify prompt files exist in `05_Prompts/Meta/`
3. Check if Obsidian MCP is running
4. Try natural language: "organize my planning inbox"

### Issue: Git sync problems

**Symptoms:**
- Can't push/pull
- Merge conflicts

**Solutions:**
1. Check `.gitignore` is working (personal files shouldn't be tracked)
2. Pull before pushing: `git pull origin main`
3. Resolve conflicts manually
4. Consider using Obsidian Git plugin for auto-sync

### Issue: Dashboard not rendering

**Symptoms:**
- `/dashboard` shows text instead of HTML
- No colors or styling

**Solutions:**
1. Make sure Claude is creating an HTML artifact
2. Check browser opens the HTML file
3. Verify file saved to `/mnt/user-data/outputs/`
4. Try opening the file directly

### Still Having Issues?

1. Check [README.md](README.md) for common issues
2. Search [GitHub Issues](https://github.com/yourusername/obsidian-claude-workflow/issues)
3. Create new issue with:
   - Your OS
   - Obsidian version
   - Claude Desktop version
   - Error messages
   - Steps to reproduce

---

## Next Steps

### 1. Customize for Your Workflow

**Add your domains:**
```
05_Company_YourCompany/
  Planning/
  Tasks/
  Documentation/
  Project_Context.md
```

**Create corresponding Claude Desktop project**

**Update domain shortcuts in:**
- `00_System/Conventions.md`
- `00_System/Quick_Reference.md`

### 2. Fill in Project Context Files

For each domain, edit `Project_Context.md`:
- Current state
- Tech stack
- Key decisions
- Active work
- MCP servers available

See [00_System/Templates/Project_Context.md](00_System/Templates/Project_Context.md)

### 3. Start Using the System

**Morning routine:**
```
/dashboard              # See what's urgent
/load [domain]         # Load context
```

**Throughout day:**
```
/inbox capture tasks as they come up
```

**End of day:**
```
/organize              # Process everything
```

### 4. Customize Templates

Edit templates in `00_System/Templates/` to match your needs:
- Task.md
- Planning.md
- Documentation.md
- Prompt.md

### 5. Create Custom Prompts

After successful interactions:
```
/prompt save
```

Claude will extract the pattern and save for reuse.

### 6. Set Up Git Sync (Optional)

**Using Obsidian Git plugin:**
1. Install Obsidian Git plugin
2. Configure auto-commit interval
3. Set up pull on startup
4. Never lose work!

**Manual Git workflow:**
```bash
git add .
git commit -m "Update tasks"
git push origin main
```

### 7. Join the Community

- Star the repository on GitHub
- Share your customizations
- Report bugs
- Suggest improvements
- Help others get started

---

## Security & Privacy

### What's Tracked in Git

✅ **Tracked (safe to share):**
- Folder structure
- Templates
- Documentation
- Prompts
- System files

❌ **Not tracked (private):**
- Your actual tasks
- Client data
- Personal notes
- Company information
- `.obsidian/workspace*` (your layout)

### Keeping Data Private

The `.gitignore` file excludes:
```
# Personal data
01_Clients/*/Tasks/*.md
01_Clients/*/Documentation/*.md
02_Company_*/Tasks/*.md
03_Company_*/Tasks/*.md
07_Personal/
09_Planning/inbox.md

# Obsidian workspace
.obsidian/workspace*
.obsidian/plugins/*/data.json
```

**Before pushing to public repo:**
1. Review what's staged: `git status`
2. Check `.gitignore` is working
3. Never commit sensitive data

---

## Updating the System

### Pulling Updates

```bash
# Save your work first
git stash

# Pull latest changes
git pull origin main

# Reapply your changes
git stash pop
```

### Handling Conflicts

If you customized system files:
1. Review conflicts carefully
2. Keep your customizations
3. Integrate new features manually

**Recommended:** Fork the repo and customize your fork

---

## Advanced Configuration

### Multiple Vaults

You can run multiple instances:
- Personal vault
- Work vault
- Client-specific vaults

Each gets its own:
- Claude Desktop project configuration
- MCP server setup
- Git repository

### Team Usage

**Scenario:** Small team sharing workflows

1. Fork the repository
2. Customize for your team
3. Each team member clones
4. Personal data stays local
5. Shared prompts/templates in repo

**Use separate Claude Desktop projects per team member**

### Integration with Other Tools

**Notion:** Export to markdown, import to Obsidian
**Todoist:** Create tasks via API, sync to Obsidian
**Google Calendar:** Reference in planning docs
**Jira/Linear:** Link tickets in task files

---

## Getting Help

1. **Documentation:** Read all files in `00_System/`
2. **Search issues:** Someone may have same problem
3. **Ask Claude:** Within your vault, Claude can help!
4. **Community:** GitHub Discussions
5. **Create issue:** Provide details and steps to reproduce

---

**You're all set! Start building your workflow.** 🚀

See [README.md](README.md) for daily workflow examples.