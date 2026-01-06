# Claude Desktop Projects

Mapping between your Obsidian vault domains and Claude Desktop projects.

## 🎯 Why This Matters

Each Claude Desktop project has:
- Its own custom instructions
- Specific MCP servers configured
- Separate conversation context

When you switch domains in your work, you should switch Claude Desktop projects to get the right tools and context.

## 📊 Project Mapping

| Vault Domain | Claude Desktop Project | Purpose |
|--------------|----------------------|---------|
| 02_Company_ExampleA | **ExampleA Shopify** | Shopify operations, products, B2C/B2B |
| 01_Clients/ExampleC | **ExampleC** | Enterprise intranet, IA, content |
| 03_Company_ExampleB | **exampleb** | Real estate software development |
| 04_Development | **ClaudeKit** | Learning, experiments, skill building |

*Note: ExampleA Shopify project handles Shopify operations for ExampleA.*

## 🔄 Switching Workflow

### When Claude Tells You to Switch

```
You: /load examplea

Claude: "Switch to Claude Desktop project: 'ExampleA Shopify'
         
         Context loaded:
         - Last worked on: Product descriptions
         - 10 products need updating
         - Focus: Western wear fall collection
         
         What do you want to work on?"

You: [Switch to "ExampleA Shopify" project in Claude Desktop]
     [Continue conversation with full context + Shopify MCP]
```

### Manual Switching

When you start working on a specific domain:
1. Check which Claude project to use (see table above)
2. Switch to that project in Claude Desktop
3. Say `/load [domain]` to load vault context
4. Start working

## 🔧 MCP Servers Per Project

### ExampleA Shopify
**Available MCP Servers:**
- Shopify MCP - Product management, orders, inventory
- Filesystem MCP - Access to ExampleA files
- Git MCP - Version control
- Obsidian MCP - This vault

**Common Tasks:**
- Product description updates
- Inventory analysis
- Order management
- Marketing copy generation

### ExampleC
**Available MCP Servers:**
- Filesystem MCP - Access to ExampleC files
- Obsidian MCP - This vault
- (Add Google Drive MCP if needed for ExampleC docs)

**Common Tasks:**
- Content rewriting
- IA and navigation structure
- Meeting prep
- Documentation organization

### exampleb (ExampleB)
**Available MCP Servers:**
- Filesystem MCP - Access to code repositories
- Git MCP - Version control
- Obsidian MCP - This vault
- (Add relevant dev tools MCP)

**Common Tasks:**
- Code review and development
- Architecture discussions
- Feature specification
- Technical documentation

### ClaudeKit (Development/Learning)
**Available MCP Servers:**
- Filesystem MCP - Access to learning projects
- Git MCP - Version control
- Obsidian MCP - This vault

**Common Tasks:**
- Learning new technologies
- Experimenting with frameworks
- Creating tutorials/documentation
- Skill development

## 📋 Project Setup Checklist

For each Claude Desktop project, ensure:

- [ ] Custom instructions include slash command reference
- [ ] MCP servers are configured and working
- [ ] Access to relevant file directories
- [ ] Obsidian MCP connected to this vault
- [ ] Test `/load [domain]` works correctly

## 🔗 Quick Links

### ExampleA Shopify
- Vault: `02_Company_ExampleA/`
- Context: `02_Company_ExampleA/Project_Context.md`
- Tasks: `02_Company_ExampleA/Tasks/`
- Docs: `02_Company_ExampleA/Documentation/`

### ExampleC
- Vault: `01_Clients/ExampleC/`
- Context: `01_Clients/ExampleC/Project_Context.md`
- Tasks: `01_Clients/ExampleC/Tasks/`
- Docs: `01_Clients/ExampleC/Documentation/`

### exampleb (ExampleB)
- Vault: `03_Company_ExampleB/`
- Context: `03_Company_ExampleB/Project_Context.md`
- Tasks: `03_Company_ExampleB/Tasks/`
- Docs: `03_Company_ExampleB/Documentation/`

### ClaudeKit (Development)
- Vault: `04_Development/`
- Context: `04_Development/Project_Context.md`
- Tasks: `04_Development/Tasks/`
- Docs: `04_Development/Documentation/`

## 💡 Best Practices

**Start of Day:**
1. Decide which domain you're tackling first
2. Switch to that Claude Desktop project
3. Say `/load [domain]`
4. Start working

**Mid-Day Context Switch:**
1. Say `/checkpoint` to save current work
2. Switch Claude Desktop projects
3. Say `/load [new domain]`
4. Continue with new context

**Working Across Multiple Domains:**
- Keep separate Claude Desktop windows/tabs open
- Each project maintains its own conversation thread
- Checkpoints help you resume in each context

**MCP Server Issues:**
- If Claude can't access Shopify: Check you're in "ExampleA Shopify" project
- If Claude can't see files: Check filesystem MCP is configured
- If Obsidian isn't working: Check MCP connection in all projects

## 🚧 To Be Configured

These items need setup (circle back later):
- [ ] Confirm which ExampleA project is for what
- [ ] Document specific MCP servers in each project
- [ ] Add Google Drive MCP for ExampleC if needed
- [ ] Test context loading in each project
- [ ] Add custom instructions to each project

## 📚 Related Docs

- `Setup_Guide.md` - Overall system guide
- `Quick_Reference.md` - Command cheat sheet
- Each domain's `Project_Context.md` - Detailed context per domain

---

**Note:** This is a living document. Update as you configure projects and discover what works best.