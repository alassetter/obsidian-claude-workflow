# Prompt Dashboard

Your master index of all reusable prompts, organized by category and domain.

---

## 🎯 Quick Access - Most Used

| Command | Prompt | Category | Domain |
|---------|--------|----------|--------|
| `/inbox` | [[Inbox_Add]] | Meta | General |
| `/organize` | [[Organize_Planning]] | Meta | General |
| `/dashboard` | [[Task_Dashboard]] | Meta | General |
| `/load` | [[Load_Context]] | Meta | General |
| `/tasks` | [[Show_Tasks]] | Meta | General |
| `/rewrite` | [[Rewrite_Content]] | Meta → Writing | General |
| `/checkpoint` | [[Create_Checkpoint]] | Meta | General |
| `/help` | [[Help]] | Meta | General |

---

## 📁 By Domain

### ExampleA
*Product descriptions, brand voice, Shopify operations*

**Writing:**
- Professional_Writer (if tagged ExampleA)

**Analysis:**
- (Add Shopify analytics prompts here)

**To Be Created:**
- Product_Description_Writer
- Brand_Voice_Check
- Shopify_Analytics

### ExampleB
*Real estate software development*

**Coding:**
- Senior_Engineer (General, but used heavily here)
- Debugging (General, but used heavily here)

**To Be Created:**
- Code_Review_Checklist
- Architecture_Discussion

### ExampleC
*Enterprise intranet, IA, content*

**Writing:**
- Professional_Writer (General)

**Analysis:**
- Project_Advisor (if applicable)

**To Be Created:**
- Content_Rewriter
- IA_Advisor

### Development
*Learning, skill building*

**Coding:**
- Senior_Engineer
- Debugging

**Meta:**
- All system prompts apply

### General (Cross-Domain)
*Applicable to all work*

**Meta:**
- Inbox_Add
- Organize_Planning
- Task_Dashboard
- Load_Context
- Show_Tasks
- Create_Checkpoint
- Create_Task
- Save_Prompt
- Find_Prompt
- Rewrite_Content
- Help
- Vault_Context

**Writing:**
- Professional_Writer

**Coding:**
- Senior_Engineer
- Debugging

**Analysis:**
- Knowledge_Extractor
- Project_Advisor

**Business:**
- Client_Summary

---

## 📚 By Category

### Analysis (4 prompts)
*Data analysis, research, knowledge extraction*

- **Knowledge_Extractor** - Extract key info from conversations
- **Project_Advisor** - Provide project guidance and recommendations
- (Test Prompt - review/remove)

### Business (1 prompt)
*Client management, proposals, summaries*

- **Client_Summary** - Summarize client information and status

### Coding (3 prompts)
*Development, debugging, code review*

- **Senior_Engineer** - Senior engineer guidance on code
- **Debugging** - Debug code issues systematically
- (Untitled - review/remove)

### Meta (13 prompts) ✨ UPDATED
*Vault management, context loading, workflows*

- **Inbox_Add** → `/inbox` - Quick capture to planning inbox ✨ NEW
- **Organize_Planning** → `/organize` - Process inbox to tasks
- **Task_Dashboard** → `/dashboard` - Visual HTML task overview ✨ NEW
- **Load_Context** → `/load` - Load domain context
- **Show_Tasks** → `/tasks` - Display active tasks (text)
- **Create_Checkpoint** → `/checkpoint` - Save work state
- **Create_Task** → `/task add` - Create single task
- **Rewrite_Content** → `/rewrite` - Rewrite in various styles
- **Save_Prompt** → `/prompt save` - Save reusable prompts
- **Find_Prompt** → `/prompt find` - Search prompts
- **Help** → `/help` - Show command help
- **Vault_Context** - General vault context loading
- **Context_Load** - (May be duplicate of Load_Context - review)
- (Test Meta - review/remove)

### Writing (1 prompt)
*Content creation, copywriting, rewriting*

- **Professional_Writer** - Write professional business content
- **Rewrite_Content** - (Also in Meta) - Rewrite with style variations

---

## 🏷️ Domain Tags Reference

When adding domain tags to prompts, use these values:

- **ExampleA** (ea) - Western wear business
- **ExampleB** (eb) - Real estate software
- **ExampleC** (examplec) - Enterprise intranet client
- **Development** (dev) - Learning and skill building
- **General** - Applicable across all domains

---

## 📝 Prompts Needing Domain Tags

**Need to Review and Tag:**

From Analysis:
- [ ] Knowledge_Extractor.md - Add domain tag
- [ ] Project_Advisor.md - Add domain tag
- [ ] Test Prompt.md - Review if needed, add domain or remove

From Business:
- [ ] Client_Summary.md - Add domain tag (probably General or ExampleC)

From Coding:
- [ ] Senior_Engineer.md - Add domain tag (probably General)
- [ ] Debugging.md - Add domain tag (probably General)
- [ ] Untitled.md - Review if needed, add domain or remove

From Writing:
- [ ] Professional_Writer.md - Add domain tag (probably General)

From Meta:
- [x] All new Meta prompts have domain: General ✅
- [x] Inbox_Add.md ✅ NEW
- [x] Task_Dashboard.md ✅ NEW
- [ ] Context_Load.md - Check if duplicate, add domain
- [ ] Vault_Context.md - Add domain (General)
- [ ] Test Meta.md - Review if needed, add domain or remove

---

## 🎨 Prompt Creation Ideas

**For ExampleA:**
- Product_Description_Writer - Craft compelling product descriptions
- Brand_Voice_Check - Verify brand consistency
- Shopify_Analytics - Analyze store performance
- Marketing_Email - Product launch emails

**For ExampleB:**
- Code_Review_Checklist - Comprehensive code review
- Architecture_Discussion - Discuss technical decisions
- Feature_Spec_Writer - Document feature specifications

**For ExampleC:**
- Content_Rewriter - Enterprise content polish
- IA_Advisor - Information architecture guidance
- Meeting_Prep - Prepare for client meetings

**For Development:**
- Learning_Path - Create learning roadmaps
- Concept_Explainer - Explain complex technical concepts

---

## 🔧 Maintenance Tasks

**Regular (Monthly):**
- [ ] Review use_count on prompts
- [ ] Archive low-reuse prompts (move to Archive/ subfolder)
- [ ] Update domain tags as work evolves
- [ ] Remove test/draft prompts

**As Needed:**
- [ ] Add new prompts with `/prompt save`
- [ ] Update this dashboard with new prompts
- [ ] Refine existing prompts based on usage

---

## 📊 Statistics

**Total Prompts:** 20 ✨ UPDATED (not counting test/untitled)
- Analysis: 3
- Business: 1
- Coding: 2
- Meta: 13 (was 10, added 3: Inbox_Add, Task_Dashboard, and including others)
- Writing: 2

**By Reuse Level:**
- High: 13 (All Meta prompts)
- Medium: TBD (need to review existing)
- Low: TBD (need to review existing)

**By Domain:**
- General: 13+ (most prompts)
- ExampleA: 0 (need to create)
- ExampleB: 0 (need to create)
- ExampleC: 0 (need to create)
- Development: 0 (tagged as general)

---

## 💡 Usage Tips

**Quick Capture (NEW!):**
- `/inbox examplec create page` - Instant append to planning inbox
- No need to open files manually
- Run `/organize` when ready to process

**Visual Dashboard (NEW!):**
- `/dashboard` - Beautiful HTML task overview
- Color-coded priorities
- Shows urgent, blocked, and active tasks
- Auto-saves snapshot to 00_System/Task_Dashboard.md

**Finding Prompts:**
- Use `/prompt find [keyword]`
- Use `/prompt find domain:examplea`
- Use `/prompt find category:writing`
- Browse this dashboard

**Using Prompts:**
- Say: "Use my [prompt name] prompt"
- Say: `/prompt use [name]`
- Reference the prompt file directly

**Saving New Prompts:**
- After successful interaction, say `/prompt save`
- Claude will extract the pattern and save it

**Keeping Dashboard Updated:**
- When new prompts are saved, add them here
- Update domain tags as you learn which prompts work where
- Archive prompts you no longer use

---

## 🔗 Related Docs

- `Quick_Reference.md` - All slash commands
- `Setup_Guide.md` - System overview
- `00_System/Templates/Prompt.md` - Prompt template
- Each prompt file has detailed instructions

---

**Last Updated:** 2026-01-06 (Added /inbox and /dashboard commands)
**Next Review:** 2026-02-06