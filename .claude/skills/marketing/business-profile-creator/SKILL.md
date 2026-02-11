---
name: business-profile-creator
description: Creates comprehensive business profile documenting offerings, positioning, values, and methodology. Can extract from existing documents (website, sales pages) or use guided questionnaire. Use when user wants to create business profile, mentions "document my business", "what I offer", or needs to capture business context for AI writing.
---

# Business Profile Creator

**Purpose:** Create a comprehensive business profile that documents offerings, positioning, philosophy, and terminology for accurate AI-generated content.

## When to Activate

Use this skill when:
- User wants to create a business profile
- User mentions "document my business" or "business context"
- User says "what I offer" or "my products/services"
- User needs business information for AI writing
- User asks "create business profile"

## Core Principle

**Business profiles ensure accuracy:**
- AI references products correctly
- Pricing is accurate
- Positioning is consistent
- Methodology is properly described
- Terminology matches brand language

**This isn't marketing copy - it's structured data for AI to reference.**

## Reference Materials

- `references/questionnaire.md` - Complete 17-question interview guide with examples and probes

## Workflow

### Step 1: Choose Creation Method

**Present options to user:**

```
I'll help you create a comprehensive business profile that captures your offerings, positioning, and philosophy.

How would you like to provide this information?

Option 1: Extract from existing documents
   "I have website copy, sales pages, or about pages"
   → I'll read and synthesize from your existing materials

Option 2: Guided questionnaire
   "I'll answer questions about my business"
   → I'll guide you through structured questions

Option 3: Hybrid approach
   "Read my documents AND ask clarifying questions"
   → Best of both worlds

Which works best for you?
```

---

## Method 1: Extract from Documents

### Ask for Documents

```
Great! Point me to your business documents and I'll extract the key information.

What documents should I read?

Examples:
- Website pages: "Read website-copy.md"
- Sales pages: "Read sales-page.md"
- About page: "Read about.md"
- Multiple files: "Read business-docs/*.md"

Provide file paths:
```

### Read and Analyze

1. Read all specified documents
2. Extract information for each section
3. Identify gaps in information
4. If hybrid approach, ask follow-up questions for missing pieces

**Extract:**
- Business name and mission
- Products/services offered
- Pricing (if mentioned)
- Positioning and differentiation
- Core beliefs and values
- Terminology and language
- Target market mentions
- Methodology descriptions

**If gaps exist:**
```
I've extracted most information from your documents. I need clarification on:

[Ask specific questions about missing information]
```

---

## Method 2: Guided Interview

**Read the interview guide first:**
```
Read references/questionnaire.md
```

### Conduct Interactive Interview

**Interview approach:**
- Conduct as **conversational interview**, not a form
- Ask **ONE question at a time**
- **Wait for response** before moving on
- **Probe for specifics** especially for offerings
- **Verify accuracy** on pricing, names, details

**The 6 sections (17 questions):**

| Section | Questions | Focus |
|---------|-----------|-------|
| 1. Business Basics | Q1-Q4 | Name, mission, value prop, positioning |
| 2. Offerings | Q5-Q7 | Products, entry offers, services (critical) |
| 3. Philosophy | Q8-Q11 | Beliefs, values, stand for/against |
| 4. Methodology | Q12-Q13 | Framework, teaching approach |
| 5. Terminology | Q14-Q15 | Key terms, language to avoid |
| 6. Market Position | Q16-Q17 | Target market, differentiation |

**Critical: Offerings section requires precision.** Get exact product names, prices, and details.

---

## Method 3: Hybrid Approach

1. **First, extract from documents**
2. **Show user what was extracted**
3. **Ask clarifying questions for gaps**
4. **Verify accuracy** of extracted information

---

### Step 2: Generate Business Profile JSON

```json
{
  "_meta": {
    "title": "Business Profile",
    "type": "business_profile",
    "updated_at": "[Today's date YYYY-MM-DD]"
  },
  "data": {
    "business_overview": {
      "name": "[From Q1]",
      "mission": "[From Q2]",
      "core_value_proposition": "[From Q3]",
      "positioning": "[From Q4]"
    },
    "offerings": {
      "flagship_products": [
        {
          "name": "[Product name]",
          "description": "[What it is]",
          "price_point": "[Price]",
          "target_audience": "[Who it's for]",
          "key_outcomes": ["[Outcome 1]", "[Outcome 2]"],
          "delivery_format": "[Format]",
          "duration": "[If applicable]"
        }
      ],
      "entry_products": [
        {
          "name": "[Product name]",
          "description": "[Brief description]",
          "price_point": "[Price]",
          "relationship_to_flagship": "[How it connects]"
        }
      ],
      "services": [
        {
          "name": "[Service name]",
          "description": "[What's included]",
          "pricing_structure": "[Pricing model]"
        }
      ]
    },
    "brand_philosophy": {
      "core_beliefs": ["[From Q8]"],
      "values": ["[From Q9]"],
      "what_you_stand_for": "[From Q10]",
      "what_you_stand_against": "[From Q11]"
    },
    "methodology": {
      "framework": "[From Q12]",
      "key_principles": ["[Principle 1]", "[Principle 2]"],
      "teaching_approach": "[From Q13]"
    },
    "terminology": {
      "key_terms": {
        "[term_1]": "[Definition]",
        "[term_2]": "[Definition]"
      },
      "signature_concepts": ["[Concept 1]", "[Concept 2]"],
      "avoid": ["[From Q15]"]
    },
    "market_position": {
      "target_market_overview": "[From Q16]",
      "competitive_positioning": "[From Q17]",
      "differentiation": "[What makes you different]"
    },
    "content_philosophy": {
      "content_types": ["[Types you create]"],
      "quality_standards": "[Standards you maintain]"
    }
  }
}
```

### Step 3: Save the File

**Save to:** `/context/core/business-profile.json`

**Confirm success:**
```
✓ Business Profile Created!

File saved: /context/core/business-profile.json

Your business profile captures:
- Business: [Name]
- Mission: [Brief mission]
- Flagship offering: [Main product name and price]
- Key differentiation: [Main differentiator]
- Core values: [List 2-3]

This profile ensures AI will:
- Reference your products accurately
- Use correct pricing and terminology
- Maintain brand positioning
- Describe methodology properly

Would you like me to:
1. Generate test content using this profile?
2. Refine any specific sections?
```

## Quality Guidelines

### For Offerings Section

This is critical - AI will reference these details in content.

**Get exact:**
- Product names (spelled correctly)
- Prices (current and accurate)
- What's included
- Target audience
- Key outcomes

**Verify:** "Just to confirm, the price is $X and it includes [details]?"

### For Extracted Information

- **Be precise:** Extract exact product names, prices, descriptions
- **Capture tone:** How they describe themselves matters
- **Note gaps:** What's missing that needs clarifying?

### Common Pitfalls

| Pitfall | Problem | Solution |
|---------|---------|----------|
| Vague descriptions | "We help people with AI" | Get specific transformation |
| Missing pricing | No price info | AI needs this for sales content |
| Generic positioning | "We're the best" | Define actual differentiation |
| Inconsistent terms | Different words for same concept | Define once, use consistently |

## Updating Business Profile

When offerings change:

1. Read existing `/context/core/business-profile.json`
2. Ask what needs updating
3. Show current values for those sections
4. Get new information
5. Update JSON and `updated_at` date

---

**Remember:** This isn't marketing copy - it's structured data that ensures AI accurately represents your business in all generated content.
