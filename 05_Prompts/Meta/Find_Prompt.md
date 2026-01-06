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

You have Obsidian MCP access. Search for and display saved prompts based on keywords, domain, or category.

**Process:**

1. **Parse search query:**
   
   User may search by:
   - **Keyword:** Text in prompt name or content
   - **Domain:** Company_A/ca, Company_B/cb, Client_XYZ/xyz, Development/dev, General
   - **Category:** Analysis, Business, Coding, Meta, Writing
   - **Reuse level:** high, medium, low
   - **Combination:** domain:companya category:writing
   
   Examples:
   - `/prompt find rewrite` → keyword search
   - `/prompt find domain:companya` → domain filter
   - `/prompt find category:coding` → category filter
   - `/prompt find writing companya` → combined search

2. **Search strategy:**
   
   **Method A: Use Prompt Dashboard**
   - Read `05_Prompts/_Prompt_Dashboard.md`
   - This has indexed prompts by domain and category
   - Fast lookup for filtered searches
   
   **Method B: Search Prompt Files**
   - Use Obsidian's global search for keyword searches
   - Search in `05_Prompts/` directory
   - Read frontmatter of matching files
   
   **Method C: List Directory**
   - List files in `05_Prompts/[Category]/`
   - Filter by domain tag in frontmatter

3. **Display results:**
   
   **For each matching prompt show:**
   - Name (linked if possible)
   - Category and Domain
   - Brief description (from "When to Use" section)
   - Reuse level
   - Last used (if recent)
   - Use count (if tracked)
   
   **Format:**
   ```
   ## Found X prompts
   
   **[Prompt Name]** (Category > Domain)
   Reuse: High | Last used: 2026-01-05 | Used: 10 times
   → [One-line description]
   
   Use: /prompt use [name] or "Use my [name] prompt"
   ```

4. **If too many results:**
   - Show top 10 most relevant
   - Suggest refining search
   - Offer to filter by domain or category

5. **If no results:**
   - Confirm search terms
   - Suggest similar searches
   - Offer to create new prompt

6. **If one result:**
   - Show full details
   - Ask if user wants to use it now
   - Or modify/update it

**Important Rules:**
- Search is case-insensitive
- Keyword search looks in name and content
- Domain/category filters use exact match
- Prioritize high-reuse prompts in results
- Sort by relevance or last_used date
- Don't show archived prompts

## When to Use

User says:
- `/prompt find [query]`
- "Find my [keyword] prompt"
- "Show me Company_A prompts"
- "What writing prompts do I have?"
- "Search prompts for [topic]"

## Variables

- `{{query}}`: Search keyword or filter
- `domain:{{domain}}`: Filter by domain
- `category:{{category}}`: Filter by category
- `reuse:{{level}}`: Filter by reuse level

## Examples

### Example 1: Keyword Search

**User:** `/prompt find rewrite`

**Output:**
```
## Found 2 prompts matching "rewrite"

**Rewrite_Content** (Meta > General)
Reuse: High | Last used: 2026-01-06 | Used: 15 times
→ Rewrite content in specific styles: professional, casual, technical, marketing, brand-specific

**Content_Rewrite** (Writing > Client_XYZ)
Reuse: Medium | Last used: 2026-01-02 | Used: 3 times
→ Rewrite Client_XYZ client content maintaining enterprise tone

Use: /prompt use rewrite-content or "Use my rewrite prompt"
```

### Example 2: Domain Filter

**User:** `/prompt find domain:companya`

**Output:**
```
## Found 4 prompts for Company_A

**Content_Description_Writer** (Writing > Company_A)
Reuse: High | Last used: 2026-01-06 | Used: 12 times
→ Write compelling Company_A content descriptions with brand voice

**Brand_Voice_Check** (Analysis > Company_A)
Reuse: Medium | Last used: 2025-12-28 | Used: 5 times
→ Verify content matches Company_A brand guidelines

**E-commerce_Analytics** (Analysis > Company_A)
Reuse: High | Last used: 2026-01-04 | Used: 8 times
→ Analyze e-commerce store performance and inventory

**Marketing_Email** (Writing > Company_A)
Reuse: Low | Last used: 2025-11-15 | Used: 2 times
→ Write marketing emails for product launches

Want details on any of these?
```

### Example 3: Category + Domain

**User:** `/prompt find category:coding domain:companyb`

**Output:**
```
## Found 2 prompts for Coding > Company_B

**Code_Review_Checklist** (Coding > Company_B)
Reuse: High | Last used: 2026-01-05 | Used: 7 times
→ Comprehensive code review with security, performance, and style checks

**Architecture_Discussion** (Coding > Company_B)
Reuse: Medium | Last used: 2025-12-20 | Used: 4 times
→ Discuss technical architecture decisions for Company_B features

Both are ready to use. Which one?
```

### Example 4: No Results

**User:** `/prompt find email templates`

**Output:**
```
No prompts found matching "email templates"

Did you mean:
- "Marketing_Email" (Writing > Company_A)
- "Professional_Writer" (Writing > General)

Or want to create a new prompt? Say "/prompt save" after we craft the perfect email template together.
```

### Example 5: Single Result Detail

**User:** `/prompt find senior engineer`

**Output:**
```
## Found: Senior_Engineer

**Category:** Coding > General
**Reuse:** High | Used 23 times | Last used: 2026-01-04

**What it does:**
Acts as senior engineer providing code review, architecture advice, and best practices guidance. Asks clarifying questions, considers tradeoffs, provides specific recommendations.

**Variables:**
- {{code}}: Code to review
- {{context}}: Project context
- {{focus}}: Specific concern (performance, security, maintainability)

**Recent usage:** Used frequently for Company_B code reviews

Want to use this prompt now? Just share the code and context.
```

## Output Format

1. Match count and search summary
2. List of matching prompts with key details
3. How to use them
4. Follow-up question or suggestion

## Related Prompts

- [[Save_Prompt]] - Create new prompts
- [[_Prompt_Dashboard]] - Browse all prompts
- [[Help]] - General help

## Notes

- Prompt Dashboard makes filtering fast
- Keyword search is flexible - tries hard to find matches
- If searching often, Dashboard is your friend
- Can combine multiple filters: `domain:companya category:writing reuse:high`
- Update last_used when prompts are invoked via search
- High reuse prompts float to top
- This helps with prompt discovery - you may forget what you saved!
- If user repeatedly searches for same thing, suggest saving a shortcut