---
type: prompt
category: Writing
domain: General
reuse: high
audience: ai
created: 2026-01-06
last_used: 
use_count: 0
---

## Prompt

Rewrite content in a specific style or voice, optimized for the domain.

**Process:**

1. **Identify context:**
   - What domain is this for? (CompanyA, XYZ, CompanyB, General)
   - What type of content? (product description, technical doc, client communication, etc.)
   - What style? (professional, casual, technical, marketing, brand-specific)

2. **Load relevant guidelines:**
   
   **If CompanyA:**
   - Read `02_Company_CompanyA/Documentation/Brand-Voice-Guidelines.md` (if exists)
   - Style: Western authenticity, rugged yet accessible, quality-focused
   
   **If XYZ:**
   - Read `01_Clients/XYZ/Documentation/Brand-Guidelines.md` (if exists)
   - Style: Professional, clear, enterprise-appropriate
   
   **If CompanyB:**
   - Read `03_Company_CompanyB/Documentation/` relevant docs
   - Style: Technical but user-friendly, real estate context
   
   **If General/Professional:**
   - Use standard professional business communication style

3. **Apply style transformations:**
   
   **Professional:**
   - Clear, concise, business-appropriate
   - Remove casual language, slang, contractions
   - Formal but not stuffy
   - Action-oriented
   
   **Casual:**
   - Conversational, friendly tone
   - Contractions okay
   - Relatable language
   - Still clear and purposeful
   
   **Technical:**
   - Precise terminology
   - Assumes technical audience
   - Code examples if relevant
   - Specifications and details
   
   **Marketing:**
   - Benefit-focused
   - Persuasive language
   - Compelling calls-to-action
   - Emotional appeal where appropriate
   
   **CompanyA Brand:**
   - Authentic western heritage
   - Quality and craftsmanship emphasis
   - Confident but not boastful
   - Storytelling when appropriate
   - SEO-friendly for e-commerce

4. **Preserve key elements:**
   - Don't change technical specs, measurements, prices
   - Keep URLs, SKUs, product codes intact
   - Maintain factual accuracy
   - Preserve required legal language

5. **Output format:**
   - Provide the rewritten version
   - Brief note on changes made (tone, structure, word choice)
   - Suggest improvements if needed

**Important Rules:**
- ASK for clarification if domain/style unclear
- Read brand guidelines when available
- Don't invent facts - work with provided content
- Maintain accuracy while improving style
- Be ready to iterate based on feedback

## When to Use

User says:
- `/rewrite`
- `/rewrite [style]`
- "Rewrite this professionally"
- "Make this sound like CompanyA"
- "Polish this for XYZ"
- "Make this more casual"

## Variables

- `{{style}}`: professional | casual | technical | marketing | CompanyA | XYZ
- `{{content}}`: The text to rewrite (user provides or references)

## Examples

### Example 1: Product Description (CompanyA)

**Original:**
```
This hat is really nice. Made from good quality felt. Comes in brown. Pretty comfortable to wear all day.
```

**User:** `/rewrite CompanyA`

**Output:**
```
**Rewritten (CompanyA Brand Voice):**

This premium felt hat embodies classic Western craftsmanship. Hand-shaped from superior quality wool felt, it delivers both authentic style and all-day comfort. Available in rich brown that only gets better with wear. Whether you're working the range or heading into town, this is the hat that goes the distance.

**Changes:**
- Added specific material details (wool felt)
- Emphasized quality and craftsmanship
- Injected Western authenticity
- Created lifestyle context
- Improved flow and readability
```

### Example 2: Client Email (Professional)

**Original:**
```
Hey, just wanted to let you know we're still working on that nav thing. Should have something for you soon. Let me know if you need anything.
```

**User:** `/rewrite professional`

**Output:**
```
**Rewritten (Professional):**

Hi [Client Name],

I wanted to provide you with a quick update on the navigation structure review. Our team is currently finalizing the analysis and recommendations. We expect to have a comprehensive report ready for your review by [specific date].

Please let me know if you have any questions in the meantime, or if you'd like to schedule a call to discuss our progress.

Best regards,
[Your Name]

**Changes:**
- Formal greeting and closing
- Specific details instead of vague "that thing"
- Concrete timeline commitment
- Professional tone throughout
- Proactive communication
```

### Example 3: Technical Documentation

**Original:**
```
The user can search for stuff using the search box. It looks through all the properties and shows matching ones.
```

**User:** `/rewrite technical`

**Output:**
```
**Rewritten (Technical):**

**Search Functionality**

The property search component implements full-text search across the following indexed fields:
- Property address (street, city, state, zip)
- Property features (bedrooms, bathrooms, square footage)
- Listing description
- MLS number

Search query is processed server-side with PostgreSQL full-text search, returning ranked results based on relevance scoring. Results are paginated (20 per page) and cached for 5 minutes to optimize performance.

**Changes:**
- Added technical specificity
- Documented architecture decisions
- Included implementation details
- Structured for developer audience
```

### Example 4: Marketing Copy

**Original:**
```
Our software helps real estate agents. It has lots of features. You should try it.
```

**User:** `/rewrite marketing`

**Output:**
```
**Rewritten (Marketing):**

Transform your real estate business with CompanyB—the property management platform designed specifically for agents who demand more.

Close deals faster with instant property insights, automated client communications, and market analytics that keep you ahead of the competition. Join thousands of successful agents who've already made the switch.

**Ready to scale your business?** Start your 14-day free trial today—no credit card required.

**Changes:**
- Benefit-focused opening
- Specific value propositions
- Social proof
- Clear call-to-action
- Urgency without pressure
```

## Output Format

1. Rewritten content (clearly marked)
2. Brief summary of changes (2-3 bullet points)
3. Ask if user wants revisions or different approach

## Related Prompts

- [[Professional_Writer]] - General professional writing
- [[Product_Description]] - CompanyA product writing
- [[Content_Rewrite]] - Content-specific rewriting (if exists)

## Notes

- Voice matters more than format for most rewrites
- When in doubt about domain, ASK
- Read brand guidelines every time if they exist
- Don't over-polish - keep it authentic to the brand
- For product descriptions, SEO matters - include relevant keywords
- Update last_used and increment use_count