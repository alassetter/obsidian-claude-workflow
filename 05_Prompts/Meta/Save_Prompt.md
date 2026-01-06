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

You have Obsidian MCP access. Extract a reusable prompt pattern from the current conversation and save it.

**Process:**

1. **Review conversation:**
   - Look back at the current session
   - Identify the prompt pattern user just used successfully
   - Extract the core instruction/request

2. **Ask clarifying questions:**
   
   **Name:**
   - "What should I call this prompt?"
   - Suggest based on function: "Product_Description_Writer", "Code_Review_Helper"
   
   **Category:**
   - Analysis, Business, Coding, Meta, or Writing?
   - Based on what the prompt does
   
   **Domain:**
   - ExampleA, ExampleB, ExampleC, Development, or General?
   - General if applicable across domains
   
   **Reuse potential:**
   - High (use weekly), Medium (use monthly), Low (use occasionally)
   - Default to high if user is saving it

3. **Extract prompt components:**
   
   **The Prompt Text:**
   - Core instruction/request
   - Remove specific details, make it generalizable
   - Identify variables: {{product_name}}, {{deadline}}, etc.
   
   **When to Use:**
   - What scenarios trigger this prompt
   - What problems it solves
   
   **Variables:**
   - List all placeholders
   - Describe what each one is
   
   **Examples:**
   - Provide 1-2 sample usages
   - Show input and expected output
   
   **Output Format:**
   - Describe what response should look like
   - Structure, length, style

4. **Create prompt file:**
   
   **Location:** `05_Prompts/[Category]/[Prompt_Name].md`
   
   **Use Prompt template:** `00_System/Templates/Prompt.md`
   
   **Filename:** Title_Case_With_Underscores.md
   
   **Fill all fields:**
   - type: prompt
   - category: [user specified]
   - domain: [user specified]
   - reuse: [user specified or high]
   - audience: ai (default)
   - created: [today]
   - last_used: [today - just used it]
   - use_count: 1 (already used once)

5. **Update Prompt Dashboard:**
   - Add to `05_Prompts/_Prompt_Dashboard.md`
   - List under appropriate category and domain

6. **Confirm creation:**
   - Show filename and location
   - Brief summary of what prompt does
   - How to use it (command or reference)

**Important Rules:**
- Generalize the prompt - remove specifics
- Identify ALL variables clearly
- Provide concrete examples
- Make it reusable, not one-time-use
- Don't save if it's too specific to be reused
- Check if similar prompt already exists first

## When to Use

User says:
- `/prompt save`
- "Save this as a prompt"
- "I want to reuse this"
- "Remember this pattern"
- After a particularly successful interaction

## Variables

- `{{prompt_name}}`: User-specified or suggested name
- `{{category}}`: Analysis, Business, Coding, Meta, Writing
- `{{domain}}`: ExampleA, ExampleB, ExampleC, Development, General

## Examples

### Example 1: Saving Product Description Prompt

**Context:** User just had Claude write a great ExampleA product description

**User:** `/prompt save`

**Claude:** "I'll save that product description pattern. What should I call it?"

**User:** "Product Description Writer"

**Claude:** "Got it. Which category? I'm thinking Writing. Correct?"

**User:** "Yes"

**Claude:** "Domain? This seems ExampleA-specific. Correct?"

**User:** "Yes"

**Output:**
```
Created: 05_Prompts/Writing/Product_Description_Writer.md

Prompt saved for writing ExampleA product descriptions.

Use it by saying: "Use my product description prompt for [product]"
Or: /prompt use product-description

Added to Prompt Dashboard under Writing > ExampleA.
```

**Saved Prompt File:**
```yaml
---
type: prompt
category: Writing
domain: ExampleA
reuse: high
audience: ai
created: 2026-01-06
last_used: 2026-01-06
use_count: 1
---

## Prompt

Write a compelling product description for {{product_name}} that embodies ExampleA's brand voice.

Read brand guidelines from: 02_Company_ExampleA/Documentation/Brand-Voice-Guidelines.md

Include:
- Attention-grabbing opening (Western authenticity)
- Key features and materials
- Craftsmanship and quality emphasis
- Care instructions
- SEO-friendly keywords

Target length: 100-150 words

## When to Use

When adding new products to ExampleA's Shopify store or updating existing product descriptions.

## Variables

- {{product_name}}: Name of the product
- {{features}}: Key product features, materials, specs
- {{sku}}: Product SKU (optional, for reference)

## Examples

### Example 1: Hat
Input: Cattle Baron Felt Hat, premium wool felt, brown, classic western style
Output: [150-word description emphasizing craftsmanship, heritage, quality]

## Output Format

Markdown-formatted product description, 100-150 words, with SEO keywords naturally integrated.

## Related Prompts

- [[Rewrite_Content]] - For polishing existing descriptions
- [[Brand_Voice_Check]] - For verifying brand consistency

## Notes

- Always read brand guidelines before writing
- Keep SEO in mind but don't keyword stuff
- Authenticity matters more than being flowery
```

### Example 2: Saving Code Review Prompt

**Context:** User had Claude do thorough code review with specific checklist

**User:** "Save this code review pattern"

**Output:**
```
Created: 05_Prompts/Coding/Code_Review_Checklist.md

Saved your code review pattern with the comprehensive checklist.

Use: "Review this code using my checklist" or /prompt use code-review

Added to Prompt Dashboard under Coding > ExampleB.
```

### Example 3: Already Exists

**User:** `/prompt save`

**Claude:** "I found a similar prompt: Professional_Writer.md - does this work or do you need a variation?"

**User:** "That works"

**Claude:** "Great! I'll update its last_used date and increment use_count. No need for a duplicate."

## Output Format

1. Confirmation with filename and location
2. Brief description of what prompt does
3. How to invoke it
4. Dashboard update confirmation

## Related Prompts

- [[Find_Prompt]] - Search for saved prompts
- [[Prompt_Template]] - Template for prompts
- [[_Prompt_Dashboard]] - Browse all prompts

## Notes

- Don't save overly specific prompts - they won't be reusable
- DO save patterns you use weekly
- Check for duplicates first - better to update than duplicate
- Variables make prompts flexible
- Good examples make prompts easy to reuse
- Update use_count when prompt is used via this system
- Prompt Dashboard helps with discovery
- This is for YOUR benefit - save prompts YOU find useful