# Vault Conventions

## Structure Rules
- Clients live in `/01_Clients`
- Each domain (Clients, CompanyA, CompanyB, Development) is self-contained with Planning/Tasks/Documentation
- Projects always live under their client
- Development knowledge never lives inside a client
- Prompts live only in `/05_Prompts` - organized by category with domain tags (hybrid system)
- Cross-domain resources in `/06_Resources/` - organized by topic (AI, Shopify, Development, IA, DevOps, Design, HowTos)
- Planning inbox in `/09_Planning/` - gets organized into domains via `/organize` command

## Domain Structure
Each domain folder contains:
- **Planning/** - Future roadmaps, specs, strategy docs
- **Tasks/** - Active to-dos and action items
- **Documentation/** - Domain-specific processes, how-tos, decisions

## Naming
- Clients: ClientName
- Projects: ProjectName
- Tasks: descriptive-task-name.md (lowercase, hyphenated)
- Documentation: Descriptive_Title.md (Title_Case)
- Planning: Descriptive_Plan.md (Title_Case)
- Prompts: Descriptive_Name.md (Title_Case)
- References: Descriptive_Name.md (Title_Case)
- One topic per note

## Frontmatter
Every note uses frontmatter. Filtering and AI depend on this.

**Required fields by type:**

**Planning:**
```yaml
type: planning
domain: [CompanyA | CompanyB | XYZ | Development]
created: YYYY-MM-DD
status: active | completed | on-hold
related_tasks: []
```

**Task:**
```yaml
type: task
domain: [CompanyA | CompanyB | XYZ | Development]
status: [todo | in-progress | blocked | completed]
priority: [low | medium | high | urgent]
created: YYYY-MM-DD
due_date: YYYY-MM-DD (optional)
completed_date: YYYY-MM-DD (optional)
related_planning: (optional)
related_tasks: []
```

**Documentation:**
```yaml
type: documentation
domain: [CompanyA | CompanyB | XYZ | Development | General]
category: [AI | Shopify | Development | IA | DevOps | Design | HowTos | Process]
topic: (descriptive)
created: YYYY-MM-DD
last_updated: YYYY-MM-DD
```

**Prompt:**
```yaml
type: prompt
category: [Analysis | Business | Coding | Meta | Writing]
domain: [CompanyA | CompanyB | XYZ | Development | General]
reuse: [high | medium | low]
audience: [ai | human]
created: YYYY-MM-DD
last_used: YYYY-MM-DD (optional)
use_count: 0
```

**Project Context:**
```yaml
type: project_context
domain: [CompanyA | CompanyB | XYZ | Development]
claude_project: (name of Claude Desktop project)
status: active
last_updated: YYYY-MM-DD
```

**Reference:**
```yaml
type: reference
domain: [CompanyA | CompanyB | XYZ | Development | General]
category: [AI | Shopify | Development | IA | DevOps | Design | HowTos]
ignore: false  # or true - see Reference Materials section
created: YYYY-MM-DD
```

## Reference Materials

For cheat sheets, quick references, external documentation, and guides.

**Location:** `06_Resources/[Category]/`

**When to use `ignore: true`:**
- Personal/sensitive information (passwords, finances)
- Private notes not work-related
- Archive content (completed work you don't need anymore)
- Large datasets Claude doesn't need to process
- Content you never want Claude to reference

**When to use `ignore: false` (default):**
- Cheat sheets (Markdown, Git, Shopify API, etc.)
- Quick reference guides
- Documentation Claude might help you with
- Technical references you may ask about
- Guides relevant to your work

**How it works:**
- Reference materials are **NOT auto-loaded** by `/load` commands
- They only load when you ask: "How do I format markdown tables?"
- Using `ignore: false` makes them available when relevant
- Using `ignore: true` excludes them completely from Claude's context
- Default should be `ignore: false` unless you have a specific reason to hide it

**Examples:**

```yaml
# Markdown Cheat Sheet - you may ask Claude about this
---
type: reference
domain: General
category: HowTos
ignore: false
---
```

```yaml
# Personal Finance Notes - never want Claude to see
---
type: reference
domain: General
category: Personal
ignore: true
---
```

## Do Not
- Duplicate prompts across domains - use domain tags instead
- Mix client knowledge across domain boundaries
- Store dev patterns in client/company folders - use 04_Development/ or 06_Resources/
- Put domain-specific docs in Resources (Resources = cross-domain only)
- Archive or delete without asking Claude first (use `archived: true, ignore: true`)
- Create tasks manually without templates
- Use `/organize` on already-organized content

## Slash Commands
Use slash commands for common operations:
- `/organize` - Process planning inbox into tasks
- `/load [domain]` - Load context for domain
- `/tasks [domain]` - Show tasks for domain
- `/checkpoint` - Save current work state
- `/rewrite` - Rewrite content with proper voice
- `/help` - Show all commands

See `Quick_Reference.md` for full command list.

## Archiving
When archiving notes:
```yaml
archived: true
ignore: true
```
Claude will skip these files when loading context. Never delete - always archive for reference.

## Planning Inbox Workflow
1. Brain dump into `/09_Planning/inbox.md` throughout day
2. Run `/organize` when ready
3. Claude creates tasks in proper domain folders
4. Claude asks about archiving inbox
5. Archived inboxes kept for reference

## Domain Shortcuts
For convenience, use either full names or shortcuts:
- CompanyA → cc
- CompanyB → ax  
- XYZ → XYZ
- Development → dev

Both work in all commands: `/load CompanyA` = `/load cc`