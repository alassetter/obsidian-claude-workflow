# Structure Guidelines

## Domain Folder Structure

Each major domain (Clients, Companies, Development) follows this pattern:

```
DomainName/
  Planning/              ← Roadmaps, specs, strategy
    README.md
    [planning docs].md
  Tasks/                 ← Active to-dos
    README.md
    [task files].md
  Documentation/         ← Processes, how-tos
    README.md
    [documentation].md
  Project_Context.md     ← Master context file
  [other domain files]
```

## Complete Vault Structure

```
00_System/
  Templates/             ← File templates
  Setup_Guide.md
  Quick_Reference.md
  Claude_Projects.md
  Conventions.md
  Guidelines.md (this file)
  AI_Usage_Guide.md

01_Clients/
  Client_XYZ/
    Planning/
    Tasks/
    Documentation/
    Projects/            (optional - for sub-projects)
    Client_Overview.md
    Knowledge_Base.md
    Project_Context.md

02_Company_A/
  Planning/
  Tasks/
  Documentation/
  Finance/               (existing subfolders)
  Marketing/
  Products/
  Shopify/
  Company_Overview.md
  Project_Context.md

03_Company_B/
  Planning/
  Tasks/
  Documentation/
  Company_Overview.md
  Project_Context.md

04_Development/
  Planning/              ← Learning roadmap
  Tasks/                 ← Learning tasks
  Documentation/         ← Your learning notes
  [tech notes].md
  Project_Context.md

05_Prompts/
  Analysis/
  Business/
  Coding/
  Meta/
  Writing/
  _Prompt_Dashboard.md   ← Master index

06_Resources/            ← Cross-domain only
  AI/
  Shopify/
  Development/
  IA/
  DevOps/
  Design/
  HowTos/

07_Personal/

09_Planning/
  inbox.md               ← Active brain dump
  README.md
  [checkpoints].md
  [archived-inboxes].md
```

## Client Structure Example

```
01_Clients/Client_XYZ/
  Planning/
    2026-Q1-Intranet-Redesign.md
    Content-Migration-Plan.md
    README.md
  Tasks/
    review-navigation-structure.md
    prepare-ia-meeting.md
    update-accreditation-docs.md
    README.md
  Documentation/
    Content-Approval-Process.md
    IA-Methodology.md
    Brand-Guidelines.md
    README.md
  Projects/              (if needed for sub-projects)
    Accreditation/
    Navigation-Redesign/
  Client_Overview.md
  Knowledge_Base.md
  Project_Context.md
```

## Company Structure Example

```
02_Company_A/
  Planning/
    2026-Product-Launch.md
    Fall-Marketing-Campaign.md
    README.md
  Tasks/
    update-product-descriptions.md
    optimize-product-images.md
    shopify-inventory-audit.md
    README.md
  Documentation/
    Brand-Voice-Guidelines.md
    Product-Photography-Process.md
    Shopify-Workflow.md
    README.md
  Finance/               (existing structure)
  Marketing/
  Products/
  Shopify/
  Company_Overview.md
  Project_Context.md
```

## Development Structure Example

```
04_Development/
  Planning/
    2026-Learning-Roadmap.md
    Claude-Skills-Mastery.md
    README.md
  Tasks/
    learn-react-hooks.md
    experiment-with-mcp.md
    master-git-workflows.md
    README.md
  Documentation/
    React-Patterns-Learned.md
    MCP-Server-Setup.md
    Git-Workflow-Best-Practices.md
    README.md
  React.md               (existing)
  Project_Context.md
```

## Prompts Structure

```
05_Prompts/
  Analysis/
    Knowledge_Extractor.md
    Project_Advisor.md
    Shopify_Analytics.md
  Business/
    Client_Summary.md
    Proposal_Writer.md
  Coding/
    Senior_Engineer.md
    Code_Review.md
    Debugging.md
  Meta/
    Organize_Planning.md
    Load_Context.md
    Show_Tasks.md
    Create_Checkpoint.md
    Save_Prompt.md
    Find_Prompt.md
    Help.md
  Writing/
    Professional_Writer.md
    Product_Description.md
    Content_Rewrite.md
  _Prompt_Dashboard.md
```

## Resources Structure

```
06_Resources/
  AI/
    Claude-Commands.md
    MCP-Setup-Guide.md
    README.md
  Shopify/
    API-Authentication.md
    Product-Management.md
    README.md
  Development/
    JavaScript-Patterns.md
    React-Best-Practices.md
    README.md
  IA/
    Navigation-Patterns.md
    Content-Hierarchy.md
    README.md
  DevOps/
    Git-Workflows.md
    CI-CD-Basics.md
    README.md
  Design/
    Color-Theory.md
    Typography-Guide.md
    README.md
  HowTos/
    Running-Effective-Meetings.md
    Project-Kickoff-Checklist.md
    README.md
```

## File Naming Conventions

### Planning Documents
- Use Title Case with hyphens: `2026-Q1-Intranet-Redesign.md`
- Include dates when relevant: `2026-Product-Launch-Plan.md`
- Be descriptive: `Content-Migration-Strategy.md`

### Task Files
- Use lowercase with hyphens: `update-product-descriptions.md`
- Action-oriented: `review-navigation-structure.md`
- Specific: `shopify-inventory-audit.md`

### Documentation
- Use Title Case with hyphens: `Brand-Voice-Guidelines.md`
- Topic-focused: `Shopify-Workflow.md`
- Process-oriented: `Content-Approval-Process.md`

### Prompts
- Use Title Case with underscores: `Product_Description_Writer.md`
- Descriptive function: `Senior_Engineer.md`
- Clear purpose: `Load_Context.md`

## When to Create What

### Planning Document
Create when you need to:
- Map out a project roadmap
- Plan a feature or initiative
- Document strategy or approach
- Set goals and success criteria

### Task
Create when you need to:
- Track a specific action item
- Manage a to-do
- Break down work into chunks
- Remember to do something

**Don't manually create tasks** - use `/organize` or `/task add` instead.

### Documentation
Create when you need to:
- Document a process
- Explain how something works
- Create a how-to guide
- Capture decisions and rationale
- Record what you learned

### Prompt
Create when you have:
- A reusable conversation pattern
- A specific request you make often
- A command or workflow to save
- Instructions for Claude

Use `/prompt save` to create from conversations.

## Project Context Files

Every domain MUST have a `Project_Context.md` file. This is Claude's entry point for loading context.

**Location:** Root of each domain folder
**Examples:**
- `01_Clients/Client_XYZ/Project_Context.md`
- `02_Company_A/Project_Context.md`
- `03_Company_B/Project_Context.md`
- `04_Development/Project_Context.md`

## README Files

Every major folder should have a README.md explaining:
- What goes in this folder
- How to use it
- Links to templates
- Examples

Already created for:
- All Planning/ folders
- All Tasks/ folders
- All Documentation/ folders
- All 06_Resources/ subfolders
- 09_Planning/

## Related Documents

- `Conventions.md` - Naming and frontmatter rules
- `Setup_Guide.md` - Complete system overview
- `Quick_Reference.md` - Command cheat sheet
- `Claude_Projects.md` - Project mapping

---

**This is a living document.** Update as structure evolves.