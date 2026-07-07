# Customer Follow-Up Templates (Generated 2026-06-18)

Reusable email templates for the `📧 邮件处理与跟进` cron job outputs.

## Template 1: A-Level Urgent Follow-Up (ICC Togo)

**Use when:** Critical customer hasn't been contacted in >30 days, raw material prices changed.

```
Subject: Updated Quotation — Togo 27 Mini-Grid Project (Preformed Fittings + Poles + LED)

Dear [Contact Name],

I hope this email finds you well.

Following up on our previous discussion regarding the Togo 27 Mini-Grid project,
I would like to provide you with an updated quotation reflecting the latest
raw material cost changes:

• LME Aluminum has decreased to $3,097/t — down 17.7% from June peak ($3,795/t). Peak was ~$3,795/t in early June; current $3,097/t is the lowest in months.
• This presents an opportunity for us to offer more competitive pricing

Could you please confirm:
1. Current project phase and expected tender deadline
2. Updated quantity requirements
3. Any specification changes since our last discussion

We remain committed to delivering quality preformed fittings, poles, and LED
solutions for your mini-grid infrastructure.

Best regards,
Nancy Wu
Tianjin [Company Name] International Trade Co., Ltd.
📧 [contact.email]
📱 WhatsApp/WeChat: +86 1*** **** 7380
```

## Template 2: A-Level Second Touch (CTC Group Vietnam)

**Use when:** Customer was sent initial materials but hasn't replied after 5+ days.

```
Subject: [Company Name] ISO Certification + Preformed Product Catalog + FOB Quotation

Dear [Contact Name],

Following up on our earlier conversation about preformed line hardware solutions
for the Vietnamese market.

Attached please find:
1. [Company Name] ISO 9001:2015 Certificate
2. Complete Preformed Product Catalog (CLCS, NL, GG series)
3. Preliminary FOB Quotation

Key advantages for Vietnamese buyers:
• 15-20 day lead time (vs. industry average 30-45 days)
• IEC 61235 / IEC 61371 certified products
• Competitive pricing — 15-30% below Western brands like [Competitor Name]
• Experience supplying to Southeast Asian utility projects

Would you be available for a brief call this week to discuss your requirements?

Best regards,
Nancy Wu
Tianjin [Company Name] International Trade Co., Ltd.
```

## Template 3: B-Level Price-Opportunity Notification

**Use when:** Raw material prices drop significantly (>5%) and you want to notify B-level prospects.

```
Subject: Market Update — LME Aluminum Price Drop 17.7%, Opportunity to Revise Quotation

Dear [Name],

I wanted to share a timely market update that may benefit your procurement planning:

LME Aluminum cash price has dropped to $3,097/t — down 17.7% from June peak ($3,795/t).
This is the lowest aluminum price in months and directly impacts preformed line hardware costs.

Given this favorable movement, we would like to:
1. Review any pending quotations and offer revised pricing
2. Discuss how this cost reduction can be passed on to accelerate your projects

This is an ideal window to lock in lower material costs for upcoming tenders
and projects.

Looking forward to your thoughts.

Best regards,
Nancy Wu
Tianjin [Company Name] International Trade Co., Ltd.
```

## Template 4: WhatsApp Quick Follow-Up (Bangladesh/South Asia)

**Use when:** Following up with South Asian contacts via WhatsApp (abpower, energypac, psdc, etc.)

```
Hi [Name], this is Nancy from Tianjin [Company Name]. Following up on my earlier message 
about power transmission hardware.

We're currently offering updated pricing on preformed guy grips and suspension 
clamps — competitive rates for Bangladesh grid projects.

Do you have any active tenders or projects we can support? Happy to send a quote 
within 24 hours.

Thanks,
Nancy
[Company Name] Electrical | kechenelectrical.com
```

## Usage Notes

- Replace bracketed placeholders `[Contact Name]` before sending
- Always attach relevant documents (certificates, catalogs, quotes)
- For ICC Togo: attach the updated quotation spreadsheet
- For CTC Group: attach ISO certificate PDF + product catalog PDF
- For price notification: include LME price chart screenshot if available
- Send during recipient's business hours (check timezone)
- **ALWAYS refresh commodity price figures** (LME aluminum, copper, gold, WTI crude) before sending price-related emails — stale data undermines credibility. Use the latest values from the morning brief cron output as the baseline.
- **Price-drop notifications should include the % decline from peak**, not just the absolute price, so the buyer understands the magnitude of savings.
- **For A-level urgent follow-ups (100+ days no contact)**, reference the specific project name (e.g. "Togo 27 Mini-Grid") and attach a revised quotation — don't just send a market update.
- **Template 1 (ICC Togo)**: Also update the subject line aluminum price to $3,097/t, down 17.7% from June peak ($3,795/t). This is the lowest aluminum price in months.