---
name: b2b-cold-outreach
description: "Compose targeted B2B cold outreach emails — product promotion letters, development letters, follow-ups — using company product data, past quotations, and market intelligence from the document library."
version: 1.0.0
metadata:
  hermes:
    tags: [b2b, outreach, email, cold-mail, development-letter, product-promotion]
    category: b2b
    platforms: [all]
---

# B2B Cold Outreach — Product Promotion & Development Letters

> For B2B manufacturing and trading companies. Generates professional, data-driven outreach emails tailored to a specific target market and product category.

## Trigger

Use when the user asks to:
- Write a **development letter** (开发信) to prospective customers
- Write a **product promotion email** (产品推广信) to a specific market
- Draft a **follow-up email** to a prospect after initial contact
- Create a **catalog/email campaign** for a product line

## Language Policy

- **Match the target audience's language**, not the user's language.
  - Malaysia, UK, US, Australia, EU → English
  - Middle East (Saudi, UAE, Qatar) → English (business standard)
  - Latin America (Mexico, Brazil, Argentina) → Spanish or Portuguese per country
  - Vietnam, Thailand → English (preferred for B2B) or Vietnamese/Thai if user specifies
- **One language per email.** Never mix English and Chinese in the same email body.
- Product model numbers, SKUs, and technical terms stay in original form.

## Research Workflow

### Step 1: Survey the Document Library

List files in the company's document directory to understand available data:

```
# Find product-related files
科辰/预绞丝_副本/          ← 预绞丝产品资料
科辰/GPP_副本/             ← 电力金具产品手册
科辰/quotation_副本/       ← 历史报价单（含客户国家文件夹）
科辰/客户池-/              ← 客户名单和分析报告
科辰/科辰产品册_副本/      ← 公司宣传册
```

### Step 2: Prioritize Files to Read

| Priority | File Type | What to Extract |
|----------|-----------|-----------------|
| 1 | Product spec sheets / PDFs / XLSX | Product names, model numbers, technical specs, certifications |
| 2 | Past quotations to same region | Products previously quoted, pricing patterns, Incoterms used |
| 3 | Customer pool / competitor analysis | Target customer profiles, market insights |
| 4 | Company catalog / PPTX | Company intro, capabilities, product range overview |

### Step 3: Extract Key Information

From product files, gather:
- **Product categories** and specific models offered
- **Technical standards** (IEC, IEEE, ANSI)
- **Certifications** (ISO 9001, TIMREX, KEMA test reports)
- **Competitive advantages** (pricing vs PLP, lead time, customization)

From past quotations, gather:
- **Products already quoted** to the target region
- **Pricing structure** (EXW vs CIF, currency)
- **Payment terms** offered
- **Shipping destinations** mentioned

### Step 4: Research the Target Market

Search for:
- Local utility companies and their infrastructure projects
- Competitors operating in the market (e.g., PLP Malaysia)
- Key decision-makers or procurement channels
- Relevant technical standards adopted locally

## Email Structure

### Development Letter (首次开发信)

```
Subject: [Product Category] from [Company] — [Key Differentiator]

Dear [Title/Name],

[Intro: Who you are + how you found them + relevance to their business]

[Product Introduction: Core offerings with specific model numbers]

[Why Us: 3-5 concrete advantages with data]

[Social Proof: Past experience in the region, certifications, notable customers]

[Call to Action: Next step — catalog, samples, quote]

[Sign-off: Full contact details]
```

### Product Promotion Letter (产品推广信)

```
Subject: [Specific Product] — [Benefit/Price Point] from [Company]

Dear [Name],

[Context: Reference a specific project, standard, or need]

[Product Details: Specific models, specs, applications]

[Value Proposition: Why this product solves their problem]

[Offer: Sample, trial order, volume discount]

[CTA + Contact]
```

### Follow-Up Email (跟进信)

```
Subject: Re: [Original Subject] / Following up on [Product]

Hi [Name],

[Reference previous contact]

[New information: price update, new product, certification received, capacity]

[Soft CTA: Any questions? Need samples?]

[Sign-off]
```

## Writing Guidelines

### Tone
- Professional but approachable — not overly formal
- Confident without being pushy
- Focus on **their needs**, not just **your products**

### Specificity
- Always include **model numbers** (e.g., NL-35G, CLCS-6, FD-2428)
- Always include **standards** (e.g., IEC 61235, IEC 61371)
- Always include **concrete numbers** (lead time days, price range, quantity)
- Never use vague phrases like "competitive price" without context

### Competitive Positioning
- Reference industry benchmarks (e.g., "typically 15-30% below PLP pricing")
- Mention certifications that matter to the target market
- Highlight experience in similar markets

### Formatting
- Use bullet points for product lists
- Use tables for comparison or specification data
- Keep paragraphs short (2-4 sentences max)
- Bold key differentiators

## Common Product Categories (Power Line Hardware)

| Category | Examples | Key Specs |
|----------|----------|-----------|
| Preformed Guy Grip (预绞丝耐张线夹) | NL series, GG series | Conductor size, material (AL/Steel), tensile strength |
| Suspension Clamp (悬垂线夹) | CLCS series, XG series | Voltage rating, conductor type |
| Vibration Damper (防震锤) | FD, FFH series | Span length, conductor diameter |
| Spacer/Damper (间隔棒) | FJZ series | Bundle configuration (2/4-split), spacing |
| Earthing Clamp (接地线夹) | ALM, STG series | Conductor cross-section (mm²) |
| Parallel Groove Clamp (并沟线夹) | APG, CAPG series | Cable size range, bolt specification |
| OPGW/ADSS Fittings (光缆金具) | OPGW clamp, grounding clamp | Cable diameter, tension rating |

## Citation Format

When referencing data from source documents:
📄 `{filename} | Sheet: {sheet_name} | Row: {row_range}`

## Anti-Patterns (What NOT to Do)

- ❌ **"Dear Sir/Madam"** — always try to find a specific name or department
- ❌ **Generic product lists** — tailor to what the target market actually needs
- ❌ **Overly long emails** — keep under 400 words for cold outreach
- ❌ **Fabricated data** — if a value is unknown, omit it rather than guess
- ❌ **Mixed languages** — English email must be entirely in English
- ❌ **Placeholder text** — no "XXX", "[insert here]", or "[company name]"

## Related Skills

- `b2b-doc-generation` — Generate formal documents (PPTX, DOCX, XLSX)
- `b2b-lead-generation` — Research and identify target customers
- `b2b-customer-mgmt` — Retrieve client history and interaction records
- `file-extract` — Extract data from PDF, Excel, Word source files

## Linked Reference Files

- `references/malaysia-market.md` — Malaysia market intelligence compiled from Kechen document library
