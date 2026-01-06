# Claude ↔ Obsidian MCP Integration

Complete guide for connecting Claude Desktop to Obsidian using the Model Context Protocol (MCP).

---

## 🎯 What This Does

Connects Claude Desktop to your Obsidian vault so Claude can:
- ✅ List files and folders in your vault
- ✅ Read existing notes
- ✅ Create new notes
- ✅ Update or append content
- ✅ Work with your real knowledge base (not hallucinated context)

**This is what powers all the slash commands!** (`/inbox`, `/organize`, `/dashboard`, etc.)

---

## ⚠️ Important Requirements

### What Works:
- ✅ **Claude Desktop** (macOS / Windows)
- ✅ **Obsidian Desktop**
- ✅ **Local connection** (no data leaves your machine)

### What Doesn't Work:
- ❌ **Claude Web** (browser) - MCP not supported
- ❌ **Obsidian Mobile** - REST API plugin unavailable
- ❌ **Remote connections** - Local only for security

---

## 📦 Components (Exact Names)

### Obsidian Plugin
- **Name:** Obsidian Local REST API
- **Author:** Adam Coddington
- **Plugin ID:** `obsidian-local-rest-api`
- **Version Tested:** 3.x
- **Purpose:** Exposes your Obsidian vault over local HTTP API

### MCP Server
- **Package:** `@modelcontextprotocol/server-http`
- **Purpose:** Bridges Claude MCP ↔ HTTP APIs
- **Used With:** Obsidian Local REST API

### Client
- **Claude Desktop** with MCP enabled
- **Requires:** Claude Pro or Team subscription

---

## 🔧 Prerequisites

Before starting, ensure you have:

1. **Obsidian Desktop** installed
   - Download: https://obsidian.md/

2. **Claude Desktop** installed
   - Download: https://claude.ai/download
   - Requires: Claude Pro/Team subscription

3. **Node.js** available
   - Test: Open terminal and run `npx --version`
   - If not installed: https://nodejs.org/

4. **This vault** cloned and open in Obsidian
   - See [SETUP.md](SETUP.md) for installation

---

## 📝 Step-by-Step Setup

### Step 1: Enable Obsidian Local REST API

**In Obsidian:**

1. Open **Settings** (gear icon)
2. Navigate to **Community Plugins**
3. If not enabled: Turn off **Restricted Mode**
4. Click **Browse**
5. Search for **"Obsidian Local REST API"**
6. Click **Install**
7. Click **Enable**

**Get your API key:**

1. Settings → Community Plugins → Obsidian Local REST API → Settings icon
2. **Copy the API Key** (long string like `abc123...`)
3. Keep this secure - it grants full vault access

**Confirm server is running:**

Open terminal and test:
```bash
curl http://127.0.0.1:27123/
```

Expected response:
```json
{
  "service": "Obsidian Local REST API",
  "versions": {...}
}
```

✅ If you see this, the plugin is working!

---

### Step 2: Configure Claude Desktop MCP

**Locate config file:**

**macOS:**
```bash
~/Library/Application Support/Claude/claude_desktop_config.json
```

**Windows:**
```
%APPDATA%\Claude\claude_desktop_config.json
```

**Create the file if it doesn't exist:**

macOS:
```bash
mkdir -p ~/Library/Application\ Support/Claude/
touch ~/Library/Application\ Support/Claude/claude_desktop_config.json
```

Windows: Use File Explorer to create the file in `%APPDATA%\Claude\`

---

**Add this configuration:**

```json
{
  "mcpServers": {
    "obsidian": {
      "command": "npx",
      "args": [
        "@modelcontextprotocol/server-http",
        "http://127.0.0.1:27123"
      ],
      "env": {
        "HTTP_HEADERS": "{\"Authorization\":\"Bearer YOUR_OBSIDIAN_API_KEY\"}"
      }
    }
  }
}
```

🔴 **IMPORTANT:** Replace `YOUR_OBSIDIAN_API_KEY` with the actual API key from Step 1

**Example (with fake key):**
```json
{
  "mcpServers": {
    "obsidian": {
      "command": "npx",
      "args": [
        "@modelcontextprotocol/server-http",
        "http://127.0.0.1:27123"
      ],
      "env": {
        "HTTP_HEADERS": "{\"Authorization\":\"Bearer abc123def456ghi789jkl012mno345\"}"
      }
    }
  }
}
```

⚠️ **Keep this file minimal** - Extra fields can break MCP loading

---

### Step 3: Restart Claude Desktop

**Complete restart required:**

1. **Quit** Claude Desktop completely
   - macOS: Cmd+Q or Claude → Quit
   - Windows: File → Exit or close all windows
2. **Verify** Claude is not running (check Activity Monitor/Task Manager)
3. **Reopen** Claude Desktop
4. **Check** for errors on startup

**No errors = Success!** ✅

If you see MCP-related errors, check:
- Config file syntax (valid JSON?)
- API key correct?
- Obsidian is running?
- REST API plugin enabled?

---

### Step 4: Test the Connection

**In Claude Desktop, try these commands:**

**Test 1: Read Access**
```
List the files in my Obsidian vault root.
```

Expected: Claude lists your vault files

**Test 2: Write Access**
```
Create a note called MCP_Test.md in my vault root with the text "MCP is working."
```

Expected: New note appears in your Obsidian vault

**Test 3: Slash Commands**
```
/help
```

Expected: Claude shows the command reference

✅ **If all three work, you're ready to use the system!**

---

## 🔧 Advanced Configuration

### Multiple MCP Servers

You can add more MCP servers alongside Obsidian:

```json
{
  "mcpServers": {
    "obsidian": {
      "command": "npx",
      "args": [
        "@modelcontextprotocol/server-http",
        "http://127.0.0.1:27123"
      ],
      "env": {
        "HTTP_HEADERS": "{\"Authorization\":\"Bearer YOUR_API_KEY\"}"
      }
    },
    "filesystem": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-filesystem",
        "/Users/you/Documents"
      ]
    },
    "git": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-git",
        "/Users/you/repos"
      ]
    }
  }
}
```

### Domain-Specific Configurations

For different Claude Desktop projects, you can limit filesystem access:

**Company A Project:**
```json
{
  "mcpServers": {
    "obsidian": {
      "command": "npx",
      "args": [
        "@modelcontextprotocol/server-http",
        "http://127.0.0.1:27123"
      ],
      "env": {
        "HTTP_HEADERS": "{\"Authorization\":\"Bearer YOUR_API_KEY\"}"
      }
    },
    "filesystem": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-filesystem",
        "/path/to/vault/02_Company_A"
      ]
    }
  }
}
```

This restricts filesystem access to only the Company_A folder.

---

## 🐛 Troubleshooting

### Issue: Claude can't see vault

**Symptoms:**
- "I don't have access to files"
- Commands don't work
- File operations fail

**Solutions:**

1. **Check Obsidian is running**
   ```bash
   curl http://127.0.0.1:27123/
   ```
   Should return service info

2. **Verify REST API plugin enabled**
   - Obsidian → Settings → Community Plugins
   - "Obsidian Local REST API" should be ON

3. **Check API key in config**
   - Open `claude_desktop_config.json`
   - Verify API key matches Obsidian
   - Check for typos in JSON

4. **Restart both applications**
   - Quit Obsidian completely
   - Quit Claude Desktop completely
   - Start Obsidian first
   - Then start Claude Desktop

5. **Check MCP server logs**
   - macOS: `~/Library/Logs/Claude/mcp*.log`
   - Windows: `%APPDATA%\Claude\Logs\mcp*.log`

---

### Issue: "npx command not found"

**Solution:**

Install Node.js:
1. Visit https://nodejs.org/
2. Download LTS version
3. Install
4. Restart terminal/computer
5. Test: `npx --version`

---

### Issue: Config file errors

**Symptoms:**
- Claude Desktop won't start
- Error messages on launch
- MCP servers not loading

**Solutions:**

1. **Validate JSON syntax**
   - Use https://jsonlint.com/
   - Check for:
     - Missing commas
     - Extra commas
     - Unclosed quotes
     - Unclosed brackets

2. **Use minimal config**
   - Remove all extra fields
   - Use only the exact config shown above
   - Add complexity slowly

3. **Check file encoding**
   - Save as UTF-8
   - No BOM (Byte Order Mark)

---

### Issue: API key keeps changing

**Symptoms:**
- Works after setup, breaks later
- Need to re-enter API key frequently

**Cause:**
- Obsidian regenerates key on plugin reinstall/update

**Solution:**
1. Pin the REST API plugin version
2. Don't auto-update plugins
3. Keep API key documented securely
4. Update `claude_desktop_config.json` when key changes

---

### Issue: Permissions errors

**Symptoms:**
- Can read but not write
- Can list but not create files

**Solutions:**

1. **Check Obsidian permissions**
   - Obsidian → Settings → Local REST API
   - Verify write operations enabled

2. **Check filesystem permissions**
   - Vault folder writable?
   - Not in protected location?

---

## 🔒 Security Notes

### Data Privacy

**All data stays local:**
- ✅ No network connections outside your machine
- ✅ API only accessible on `127.0.0.1` (localhost)
- ✅ No data sent to Anthropic except your prompts
- ✅ Your vault contents stay on your device

**API Key Security:**
- 🔐 Keep API key private
- 🔐 Don't commit to public repos
- 🔐 Rotate if exposed
- 🔐 Each vault can have unique key

### Best Practices

1. **Don't expose REST API to network**
   - Keep on 127.0.0.1 only
   - Don't change bind address

2. **Regenerate API key if exposed**
   - Obsidian → Settings → REST API → Regenerate
   - Update Claude config

3. **Use .gitignore**
   - Never commit `claude_desktop_config.json`
   - Keep API keys out of version control

---

## 📊 Status & Compatibility

### ✅ Confirmed Working With:

- **Obsidian:** 1.10.x, 1.11.x
- **Obsidian Local REST API:** 3.x
- **Claude Desktop:** Latest (MCP enabled)
- **Node.js:** 18.x, 20.x
- **Operating Systems:**
  - macOS 13+ (Ventura, Sonoma, Sequoia)
  - Windows 10, 11
  - Linux (Ubuntu 22.04+, untested but should work)

### Known Limitations:

- ❌ Mobile not supported (REST API plugin unavailable)
- ❌ Claude Web not supported (no MCP)
- ❌ Remote access not supported (security by design)

---

## 🔄 Maintenance

### Regular Tasks

**Monthly:**
- Check for Obsidian updates
- Check for REST API plugin updates
- Verify MCP still working
- Review API key security

**After Updates:**
- Test MCP connection
- Verify API key still valid
- Check config file unchanged

**If Moving to New Computer:**
1. Install Obsidian
2. Clone vault
3. Install REST API plugin
4. Get new API key
5. Install Claude Desktop
6. Configure MCP
7. Test connection

---

## 🆘 Getting Help

**If stuck:**

1. **Check logs:**
   - Obsidian: Settings → REST API → View Logs
   - Claude: `~/Library/Logs/Claude/` or `%APPDATA%\Claude\Logs\`

2. **Test components separately:**
   - Obsidian REST API with curl
   - Claude Desktop basic functionality
   - MCP config syntax

3. **Search issues:**
   - This repo's issues
   - Obsidian REST API plugin issues
   - MCP documentation

4. **Ask for help:**
   - Open issue on this repo
   - Include error messages
   - Include OS/version info
   - Include config (remove API key!)

---

## 🎓 Technical Details

### How It Works

```
Your Prompt
    ↓
Claude Desktop (with MCP)
    ↓
MCP HTTP Server (@modelcontextprotocol/server-http)
    ↓
HTTP Request with Authorization header
    ↓
Obsidian Local REST API (plugin)
    ↓
Your Obsidian Vault
```

### Why This Approach

**Advantages:**
- ✅ Stable and maintained
- ✅ Uses official MCP tooling
- ✅ Tool-agnostic
- ✅ Explicit configuration
- ✅ Easy to troubleshoot
- ✅ Future-proof

**Alternatives considered:**
- Custom MCP server (more brittle)
- File-based integration (slower, no real-time)
- Obsidian plugin calling Claude (wrong direction)

---

## 📚 Related Documentation

- [SETUP.md](SETUP.md) - Overall system setup
- [Quick_Reference.md](00_System/Quick_Reference.md) - Command reference
- [Obsidian REST API Docs](https://github.com/coddingtonbear/obsidian-local-rest-api)
- [MCP Documentation](https://modelcontextprotocol.io/)

---

## 📝 License

This integration guide is part of obsidian-claude-workflow.
MIT License - see [LICENSE](LICENSE)

---

**Ready to connect?** Follow the steps above and you'll be running slash commands in minutes! 🚀