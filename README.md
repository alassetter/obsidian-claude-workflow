# Obsidian + Claude Workflow System

A production-ready knowledge management and task workflow system integrating Obsidian with Claude via MCP (Model Context Protocol). Built for interrupt-driven work across multiple projects and domains.

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Obsidian](https://img.shields.io/badge/obsidian-1.5%2B-purple)
![Claude](https://img.shields.io/badge/claude-desktop-orange)

---

## 🎯 What This System Does

**Eliminate context switching pain.** This system helps you:
- 📝 **Brain dump instantly** - Capture tasks without breaking focus
- 🎯 **Organize automatically** - Claude categorizes and creates structured tasks
- 🔄 **Switch contexts seamlessly** - Save state, load new context, resume work
- 📊 **Visualize priorities** - Beautiful HTML dashboards show what needs attention
- 🤖 **Never repeat yourself** - Save prompts, load context, reuse patterns
- 🏢 **Manage multiple domains** - Client work, companies, personal projects

---

## ✨ Key Features

### Daily Workflow Commands
```bash
/inbox xyz create landing page          # Quick capture (no file opening!)
/organize                               # Process inbox → structured tasks
/dashboard                              # Beautiful HTML task overview
/load companya                          # Load full domain context
/tasks priority:high                    # Show filtered tasks
/checkpoint                             # Save work state before switching
```

### Smart Organization
- **Self-contained domains** - Each project has Planning/Tasks/Documentation
- **Cross-domain resources** - Shared knowledge organized by topic
- **Hybrid prompt system** - Category folders + domain tags for flexibility
- **Planning inbox** - Brain dump now, organize later

### Claude Desktop Integration
- **Project mapping** - Each domain maps to a Claude Desktop project
- **MCP servers** - Shopify, filesystem, Git, Obsidian integration
- **Context loading** - Claude reads your vault and provides relevant info
- **Command system** - 13+ slash commands for common workflows

---

## 🚀 Quick Start

### Prerequisites
- [Obsidian](https://obsidian.md/) 1.5+
- [Claude Desktop](https://claude.ai/download) with MCP support (⚠️ **Claude Web doesn't work - Desktop only!**)
- Node.js (for MCP)
- Git (for version control)

### Installation

1. **Clone this repository:**
```bash
git clone https://github.com/yourusername/obsidian-claude-workflow.git
cd obsidian-claude-workflow
```

2. **Open in Obsidian:**
   - Launch Obsidian
   - "Open folder as vault"
   - Select the cloned directory

3. **Set up Claude ↔ Obsidian MCP connection:** ⚡ **CRITICAL STEP**
   - See **[MCP_SETUP.md](MCP_SETUP.md)** for complete MCP configuration
   - Install Obsidian Local REST API plugin
   - Configure Claude Desktop MCP
   - **This is what powers all the slash commands!**

4. **Install recommended plugins (optional):**
   - See [PLUGINS.md](PLUGINS.md) for full list
   - Core system works without plugins!

5. **Test the system:**
```bash
# In Claude Desktop (not web!), try:
/help                    # See all commands
/inbox test task         # Quick capture
/organize                # Process inbox
/dashboard               # View tasks
```

📖 **Full guides:**
- **[MCP_SETUP.md](MCP_SETUP.md)** - Claude ↔ Obsidian connection (START HERE!)
- [SETUP.md](SETUP.md) - Complete installation guide
- [PLUGINS.md](PLUGINS.md) - Plugin recommendations

---

## 📁 Structure Overview

```
obsidian-claude-workflow/
├── 00_System/              # Templates, docs, conventions
│   ├── Templates/          # File templates
│   ├── Setup_Guide.md      # System overview
│   ├── Quick_Reference.md  # Command cheat sheet
│   └── Claude_Projects.md  # Project mapping
├── 01_Clients/             # Client work
│   └── [ClientName]/       # Self-contained per client
├── 02_Company_*/           # Your companies
├── 03_Company_*/           # (Add more as needed)
├── 04_Development/         # Learning & skills
├── 05_Prompts/             # Reusable prompts
│   ├── Analysis/
│   ├── Business/
│   ├── Coding/
│   ├── Meta/               # System commands
│   └── Writing/
├── 06_Resources/           # Cross-domain knowledge
│   ├── AI/
│   ├── Shopify/
│   ├── Development/
│   └── ...
├── 07_Personal/            # Personal notes (gitignored)
├── 09_Planning/            # Planning inbox
│   └── inbox.md            # Brain dump here!
├── README.md               # This file
├── MCP_SETUP.md            # Claude ↔ Obsidian connection
└── SETUP.md                # Full installation guide
```

---

## 🎮 Core Commands

### Most Used
| Command | What It Does |
|---------|-------------|
| `/inbox [text]` | Quick capture to planning inbox |
| `/organize` | Process inbox into structured tasks |
| `/dashboard` | Visual HTML task overview |
| `/load [domain]` | Load full context for domain |
| `/tasks [domain]` | Show active tasks |
| `/checkpoint` | Save work state |
| `/rewrite` | Rewrite content with style |

### Full Command List
See [Quick_Reference.md](00_System/Quick_Reference.md) for complete documentation.

---

## 🏷️ Domain Shortcuts

Use full names or shortcuts:
- **Company_A** → `ca`
- **Company_B** → `cb`
- **Client_XYZ** → `xyz`
- **Development** → `dev`

Example: `/load ca` = `/load companya`

---

## 💡 Typical Daily Workflow

### Morning
```bash
/dashboard              # See what's urgent, what's blocked
/load xyz              # Dive into most urgent domain
```

### Throughout Day
```bash
/inbox xyz prep meeting tomorrow
/inbox ca update content
/inbox research new AI tools
# Keep working, capture as you go
```

### Context Switching
```bash
/checkpoint            # Save Client_XYZ work state
/load companya        # Switch to Company_A
# Claude shows where you left off
```

### End of Day
```bash
/organize              # Process all captured tasks
# Claude creates tasks in proper domains
# Asks about archiving inbox
```

---

## 🔧 Customization

### Add a New Domain
1. Create folder: `0X_Company_YourCompany/`
2. Add subfolders: `Planning/`, `Tasks/`, `Documentation/`
3. Create `Project_Context.md`
4. Update domain shortcuts in conventions
5. Create corresponding Claude Desktop project

See [SETUP.md](SETUP.md) for details.

### Create Custom Prompts
```bash
# After a great interaction with Claude:
/prompt save
# Claude extracts the pattern and saves it
```

### Customize Templates
Edit templates in `00_System/Templates/` to match your workflow.

---

## 📚 Documentation

- **[MCP_SETUP.md](MCP_SETUP.md)** - ⚡ Claude ↔ Obsidian MCP connection (CRITICAL!)
- **[SETUP.md](SETUP.md)** - Detailed installation and configuration
- **[PLUGINS.md](PLUGINS.md)** - Required and recommended Obsidian plugins
- **[Quick_Reference.md](00_System/Quick_Reference.md)** - Command cheat sheet
- **[Setup_Guide.md](00_System/Setup_Guide.md)** - Complete system overview
- **[Conventions.md](00_System/Conventions.md)** - Structure rules and naming
- **[Claude_Projects.md](00_System/Claude_Projects.md)** - Claude Desktop integration

---

## 🤝 Contributing

Contributions welcome! This system can be adapted for:
- Different industries (legal, healthcare, education)
- Different work styles (deep work, agile, GTD)
- Different team sizes (solo, small team, enterprise)

**To contribute:**
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

**Ideas for contributions:**
- Domain-specific prompt libraries (legal, medical, etc.)
- Integration guides (Notion, Todoist, etc.)
- Video tutorials
- Translations
- Bug fixes and improvements

---

## 🐛 Troubleshooting

### Claude doesn't see my files
- **Most common:** MCP not configured - see [MCP_SETUP.md](MCP_SETUP.md)
- Check Obsidian Local REST API plugin is enabled
- Verify API key in Claude config
- Ensure Obsidian is running

### Commands don't work
- Ensure you're using **Claude Desktop**, not Claude Web
- Verify MCP connection is working
- Try natural language: "organize my inbox"
- Check [Quick_Reference.md](00_System/Quick_Reference.md)

### Tasks not organizing correctly
- Check frontmatter in task files
- Verify domain names match conventions
- See [Conventions.md](00_System/Conventions.md)

**More help:** See [MCP_SETUP.md](MCP_SETUP.md) and [SETUP.md](SETUP.md) troubleshooting sections

---

## 📖 Examples

### Real-World Use Cases

**Scenario 1: Freelance Consultant**
- Multiple clients in `01_Clients/`
- Personal business in `02_Company_YourBusiness/`
- Learning new skills in `04_Development/`

**Scenario 2: Startup Founder**
- Main company in `02_Company_Startup/`
- Side projects in `03_Company_SideProject/`
- Research and development in `04_Development/`

**Scenario 3: Enterprise Employee**
- Primary project in `01_Clients/Enterprise/`
- Internal tools in `04_Development/`
- Personal projects kept separate

---

## 🎓 Learning Path

**Week 1: Get Comfortable**
- Set up MCP connection ([MCP_SETUP.md](MCP_SETUP.md))
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
- Integrate Claude Desktop projects fully
- Set up domain-specific MCP servers
- Fine-tune your personal workflow

---

## 🏆 Why This System Works

### Built for Real Work
- **Interrupt-driven** - Designed for constant context switching
- **Incremental** - Capture now, organize later
- **Flexible** - Adapts to your workflow, not the other way around

### No Vendor Lock-In
- **Plain text** - Markdown files, readable anywhere
- **Local first** - Your data stays on your machine
- **Open source** - MIT license, use and modify freely

### Claude-Powered
- **Smart categorization** - Claude figures out which domain
- **Context aware** - Loads relevant info for each domain
- **Pattern learning** - Save and reuse successful prompts

---

## 📊 System Stats

- **Commands:** 13+ slash commands
- **Prompts:** 20+ reusable prompts (and growing)
- **Documentation:** 20,000+ tokens of guides and examples
- **Templates:** 6 core templates (fully customizable)
- **Domains:** Unlimited (add as many as you need)

---

## 📜 License

MIT License - see [LICENSE](LICENSE) for details.

Free to use, modify, and distribute. Attribution appreciated but not required.

---

## 🙏 Acknowledgments

Built with:
- [Obsidian](https://obsidian.md/) - The extensible knowledge base
- [Claude](https://claude.ai/) - AI assistant by Anthropic
- [MCP](https://modelcontextprotocol.io/) - Model Context Protocol
- [Obsidian Local REST API](https://github.com/coddingtonbear/obsidian-local-rest-api) - By Adam Coddington

Inspired by:
- GTD (Getting Things Done)
- PARA Method
- Zettelkasten
- Personal knowledge management community

---

## 🚀 Get Started

1. **[Set up Claude ↔ Obsidian MCP](MCP_SETUP.md)** ⚡ START HERE
2. **[Install the system](SETUP.md)**
3. **[Read the quick reference](00_System/Quick_Reference.md)**
4. **Start brain dumping!**

---

## 💬 Community & Support

- **Issues:** [GitHub Issues](https://github.com/yourusername/obsidian-claude-workflow/issues)
- **Discussions:** [GitHub Discussions](https://github.com/yourusername/obsidian-claude-workflow/discussions)
- **Questions:** Open a discussion or issue

---

**Built by knowledge workers, for knowledge workers.**

*Stop fighting your tools. Start flowing with them.* ✨