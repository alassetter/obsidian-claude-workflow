---
type: prompt
category: Meta
domain: General
reuse: high
audience: ai
created: 2026-01-06
last_used: 
use_count: 0
---

## Prompt

You have Obsidian MCP access. Save current work state as a checkpoint for resuming later.

**Process:**

1. **Review the conversation:**
   - Look back at the current session
   - Identify what domain/project was being discussed
   - Extract key activities and progress

2. **Determine domain:**
   - If clear from context (Company_A, Company_B, Client_XYZ, Development), use that
   - If multi-domain session, create one checkpoint with all contexts
   - If unclear, ASK user which domain

3. **Extract key information:**
   
   **What Was Worked On:**
   - Main topic or task
   - Specific activities (coding, writing, planning, etc.)
   - Files created or modified
   
   **Decisions Made:**
   - Technical choices
   - Architecture decisions
   - Content direction
   - Process decisions
   
   **Progress Summary:**
   - What got completed
   - What's partially done
   - What was started but not finished
   
   **Next Steps:**
   - What logically comes next
   - Immediate next actions
   - Open questions to resolve
   
   **Blockers/Questions:**
   - What's stuck or unclear
   - What needs external input
   - What requires research or decision

4. **Create checkpoint file:**
   - Name: `YYYY-MM-DD-[domain]-[brief-topic]-checkpoint.md`
   - Location: `09_Planning/`
   - Use proper frontmatter with type: checkpoint
   - Include session_duration estimate if obvious
   - Set status based on completion (in-progress, completed, blocked)

5. **Format:**
   ```yaml
   ---
   type: checkpoint
   date: YYYY-MM-DD
   project: [domain/project name]
   session_duration: [estimated time]
   status: [in-progress | completed | blocked]
   ---
   
   # [Domain/Project] - [Brief Topic]
   
   ## What I Worked On
   [Summary]
   
   ## Decisions Made
   [Key choices]
   
   ## Progress
   - [x] Completed item
   - [ ] Partially done item
   
   ## Next Steps
   1. [Immediate next action]
   2. [Follow-up action]
   
   ## Questions/Blockers
   [What's stuck or unclear]
   
   ## Context for Next Session
   [Anything important to remember when picking this up]
   ```

6. **Confirm creation:**
   - Tell user checkpoint was saved
   - Give filename
   - Brief one-line summary
   - Ask if ready to switch context or done for now

**Important Rules:**
- Be SPECIFIC about progress, not vague
- Include enough detail to resume work without re-explaining
- Capture decisions so they're not forgotten
- Link to created files when relevant
- Don't duplicate info that's already in task/planning files
- Time estimate is rough - don't obsess over accuracy

## When to Use

User says:
- `/checkpoint`
- "Create a checkpoint"
- "Save my progress"
- "Save where I'm at"
- "I need to switch to [other domain]" (suggest checkpoint first)

## Variables

- `{{domain}}`: Optional - explicitly specify domain
- `{{topic}}`: Optional - brief topic for filename

## Examples

### Example 1: Development Session

**Session:** Working on Company_B authentication for 2 hours

**User:** `/checkpoint`

**Output:**
```
Checkpoint saved: 09_Planning/2026-01-06-companyb-auth-system-checkpoint.md

Summary: Built user authentication flow, decided on JWT approach, blocked on OAuth configuration.

Ready to switch context or done for the day?
```

**Checkpoint File:**
```yaml
---
type: checkpoint
date: 2026-01-06
project: Company_B
session_duration: 2 hours
status: blocked
---

# Company_B - Authentication System

## What I Worked On
Building user authentication for Company_B platform. Focused on login flow, session management, and password reset functionality.

## Decisions Made
- Using JWT tokens for session management (instead of server-side sessions)
- Storing tokens in httpOnly cookies for security
- Implementing refresh token rotation
- Password reset via email with time-limited tokens

## Progress
- [x] Login form UI component
- [x] Password hashing with bcrypt
- [x] JWT token generation
- [ ] OAuth integration (blocked)
- [ ] Session refresh endpoint
- [ ] Password reset email template

## Next Steps
1. Get OAuth credentials from client for third-party auth
2. Complete session refresh endpoint
3. Build password reset flow
4. Add rate limiting to auth endpoints
5. Write authentication tests

## Questions/Blockers
🚨 **BLOCKED:** Need OAuth app credentials (Google, GitHub) from client to proceed with social login integration. Sent email requesting these on 2026-01-06.

Can work on password reset flow while waiting, or pivot to property search UI.

## Context for Next Session
- JWT library: jsonwebtoken v9.0.0
- Middleware: auth.middleware.js handles token validation
- Database: users table has email, password_hash, refresh_token columns
- Branch: feature/auth-system (not yet merged)
```

### Example 2: Content Work

**Session:** Writing Company_A content descriptions

**User:** `/checkpoint`

**Output:**
```
Checkpoint saved: 09_Planning/2026-01-06-companya-content-descriptions-checkpoint.md

Summary: Completed 6 of 10 seasonal collection content descriptions using brand voice guidelines.

Continue with remaining 4 items or switch context?
```

**Checkpoint File:**
```yaml
---
type: checkpoint
date: 2026-01-06
project: Company_A
session_duration: 1.5 hours
status: in-progress
---

# Company_A - Seasonal Collection Content Descriptions

## What I Worked On
Writing optimized content descriptions for seasonal 2026 collection launch. Applied brand voice guidelines and SEO keywords.

## Decisions Made
- Focus on craftsmanship and quality in descriptions
- Include care instructions for each item
- SEO keywords: "premium", "handcrafted", "authentic"
- Keep descriptions 100-150 words for optimal e-commerce display

## Progress
- [x] Item 001 (SKU: ITM-001)
- [x] Item 003 (SKU: ITM-003)
- [x] Item 015 (SKU: ITM-015)
- [x] Item 022 (SKU: ITM-022)
- [x] Item 041 (SKU: ITM-041)
- [x] Item 008 (SKU: ITM-008)
- [ ] Item 009 (SKU: ITM-009)
- [ ] Item 014 (SKU: ITM-014)
- [ ] Item 031 (SKU: ITM-031)
- [ ] Item 019 (SKU: ITM-019)

## Next Steps
1. Complete remaining 4 content descriptions
2. Have descriptions reviewed for brand consistency
3. Upload to e-commerce platform
4. Add content images (separate task)
5. Set up product collections

## Questions/Blockers
None - workflow is smooth

## Context for Next Session
- Brand voice doc: 02_Company_A/Documentation/Brand-Voice-Guidelines.md
- Target word count: 100-150 words
- Format: Brief hook → Features → Craftsmanship → Care
- All products in "Fall 2026" collection
```

### Example 3: Multi-Domain Session

**Session:** Worked on multiple projects

**User:** `/checkpoint`

**Output:**
```
Checkpoint saved: 09_Planning/2026-01-06-multi-domain-checkpoint.md

Summary: Client_XYZ meeting prep (done), Company_A descriptions (6/10), Company_B planning started.

Typical interrupt-driven day! Where do you want to focus next?
```

## Output Format

1. Confirm checkpoint saved with filename
2. One-line summary of session
3. Ask about next steps (switch or done)

## Related Prompts

- [[Load_Context]] - Resume from checkpoint
- [[Organize_Planning]] - Process inbox
- [[Show_Tasks]] - View current tasks

## Notes

- This is for YOUR benefit - capture what helps YOU resume
- Don't overthink structure - just capture essentials
- Progress checklist is super helpful for partially-done work
- Blockers should be SPECIFIC with context
- Link to created files using full paths
- Checkpoints are reference material - never delete them
- These help with weekly reviews too
- Update last_used when executed