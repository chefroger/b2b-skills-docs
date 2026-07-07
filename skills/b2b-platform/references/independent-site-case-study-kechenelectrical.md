# Case Study: kechenelectrical.com — Independent B2B Website Analysis

**Date**: 2026-05-13
**Site**: kechenelectrical.com (Renqiu Dingcheng Electric Equipment Manufacturing Co., Ltd.)
**Products**: Electric power fittings — clamps, insulators, connectors, brackets
**Industry**: Power transmission/distribution hardware

---

## What the Agent Found (Real Findings)

### P0 Issues
- **Company Profile page returns 404** at `/about-us`, `/About-Us`, `/company-profile` — all tried and failed. The top nav links to it but it doesn't exist.
- **Product pages have no H1 tags** — the product grid on `/products` has no heading element.
- **No meta descriptions on product category pages** — only the homepage has one (if any).

### P1 Issues
- **Product titles leak internal data**: One product card reads `STOCK CODE: NO: TYPE: Galvanize steel MATERIALR: Galvanize steel/carton steel DESCRIPTION: Suitable for spirit wiring` — raw ERP output exposed to customers.
- **Keyword-stuffed titles**: `Manufacturer Supply for Power Accessories 16-120MM2 50-240MM2 JBL16-120 Clamp Copper-Aluminum Parallel-Groove Clamp` — written for search, unreadable to humans.
- **No structured data**: No JSON-LD for Organization or Product schema.
- **URL structure unknown**: Products likely use dynamic IDs (couldn't confirm from HTML alone).
- **Image ALT unknown**: Product images likely have no ALT or filename-only.

### P2 Issues
- **Company description is generic**: "export-oriented company integrating industry and trade" — no founding year, no employee count, no certifications, no production capacity.
- **About page (when found) would be the fix**: A `/company-profile` or `/about` page with real data would solve the trust gap.
- **Footer lacks trade assurance signals**: No payment terms icons, no logistics partners, no Trade Assurance badge.
- **Social links (YouTube/Facebook/LinkedIn) exist but content unknown** — could be empty.

---

## Diagnostic Commands Used

```bash
# Check if About page exists (returns 404)
curl -s "[company-website-url]/Company-Profile"
# Result: 404 Not Found nginx

# Extract full homepage text for content analysis
curl -s "[company-website-url]/" | python3 -c "..."

# Browse product page and take annotated snapshot
browser_navigate → product page URL
browser_snapshot(full=false)
browser_vision(annotate=true, question)
```

---

## What to Always Check on an Independent B2B Site

1. **404 on /about, /about-us, /company, /company-profile** — check all common paths
2. **H1 presence** via `browser_snapshot` — look for `heading` elements with `level=1`
3. **Meta description** via raw HTML: `curl | grep meta description`
4. **Product title quality** — look for: internal stock codes, excessive ALL-CAPS, "Manufacturer Supply" keyword stuffing
5. **Company address specificity** — generic "China" vs. specific city/province/industrial zone
6. **Language consistency** — some Chinese B2B sites mix EN/CN improperly
