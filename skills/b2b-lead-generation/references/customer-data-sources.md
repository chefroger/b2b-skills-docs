# Customer Data Sources — 科辰部署

> Where to find actual customer records in this deployment. Update paths when the data layout changes.

---

## Database (customers table often empty)

The `customers` table in `trade.db` is frequently empty because the agent hasn't yet saved scanned prospects back to the DB. **Do not assume the DB has data — always check.**

```
~/.trade/data/trade.db          # primary
~/Desktop/Foreign Trade Assistant/data/trade.db  # secondary (same)
```

Schema:
```sql
customers(id, company_id, name, contact, note, created_at, updated_at, extra1/2/3)
-- contact field: primary phone/email
-- email field: dedicated email column (often NULL)
```

---

## File System Sources (the real data)

The actual customer pool lives in **flat files** parsed from Excel/Word exports:

```
~/Desktop/科辰/客户池-/
├── 优先开发客户名单_可搜索版.html   # ★ Primary: parsed HTML, 50 prioritized leads
├── 客户池分析报告_优先开发名单.md  # ★ Secondary: structured analysis + 50 leads
├── 预绞丝潜在客户开发清单.md       # Africa + South America focused
├── 预绞丝亚洲客户开发清单.md       # Asia focused
├── 预绞丝竞争对手客户名单_*.md    # Iraq/Uganda/Kenya/Egypt/Philippines
├── Client POOl -[Company Name]-20240823.xlsx   # Raw: 1,000 records (binary)
├── Client POOl -[Company Name]20240830.xlsx   # Raw: 1,323 records (binary)
└── 优先开发客户名单_Top50.csv     # Empty template — ignore
```

---

## How to Extract Customer Records from HTML Priority List

```python
import re

html_path = "~/Desktop/科辰/客户池-/优先开发客户名单_可搜索版.html"
with open(html_path, 'r', errors='ignore') as f:
    content = f.read()

rows = re.findall(r'<tr>(.*?)</tr>', content, re.DOTALL)
for row in rows:
    cells = re.findall(r'<td>(.*?)</td>', row, re.DOTALL)
    if cells:
        clean = [re.sub(r'<[^>]+>', '', c).strip() for c in cells]
        # Columns: priority | company | country | website | contact | reason
        print(' | '.join(clean))
```

---

## Market Filter Reference

Target markets and their keywords in the data:

| Market | Keyword in data | Notes |
|--------|----------------|-------|
| 🇩🇪 Germany | Germany, Pfisterer | Only 1 EU customer in DB |
| 🇹🇷 Turkey | Turkey | 0 direct records |
| 🇸🇦 Saudi Arabia | Saudi | AkR Power available |
| 🇦🇪 UAE | UAE, Dubai | 4 companies (SIMMU, Emirates Electrical, Ducab, DutcoTENNAT) |
| 🇶🇦 Qatar | Qatar | 1 (Kahramaa) — no direct email, use web form |
| 🇮🇷 Iran | Iran | 0 records |
| 🇫🇷🇬🇧🇮🇹🇪🇸🇳🇱 | France/UK/Italy/Spain/Netherlands | 0 records in current DB |

---

## Priority Tier Mapping

| Tier | Meaning | Action |
|------|---------|--------|
| ★★★ | Top 10, direct request fit | Send email today |
| ★★ | Strong match, pipeline opportunity | Send within 3 days |
| ★ | Worth a try, lower urgency | Batch send in 1-2 weeks |

---

## Saving Scanned Prospects to DB

After generating outreach from file data, save results back:

```python
from trade import customer as _cust
_cust.bulk_save(
    company_id=1,   # 科辰 is always company_id=1 in this deployment
    customers=[
        {
            "name": "Pfisterer",
            "contact": "+49-XXX-XXXX",      # primary contact
            "email": "[contact.email]",
            "country": "Germany",
            "tier": "B",                      # ★★ = B
            "note": "德国电力传输专业分销",
            "company_website": "pfisterer.com",
            "source": "agent",
        },
        # ... more
    ],
    library_id=None,
)
```
