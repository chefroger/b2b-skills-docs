# Trade Database Schema Notes

## Dual Database Locations

| Location | Purpose | Status |
|----------|---------|--------|
| `~/.trade/data/trade.db` | Production database | ✅ Always query first |
| `~/Desktop/Foreign Trade Assistant/data/trade.db` | Legacy/Dev database | ⚠️ Stale or test data |

## Customers Table Schema

```sql
CREATE TABLE customers (
    id          INTEGER PRIMARY KEY AUTOINCREMENT,
    company_id  INTEGER REFERENCES companies(id),
    name        TEXT    NOT NULL,
    contact     TEXT    DEFAULT '',
    note        TEXT    DEFAULT '',
    created_at  TEXT    DEFAULT (datetime('now', 'localtime')),
    updated_at  TEXT    DEFAULT (datetime('now', 'localtime')),
    extra1      TEXT    DEFAULT '{}',   -- JSON: customer metadata
    extra2      TEXT    DEFAULT '{}',   -- JSON: contact details
    extra3      TEXT    DEFAULT '{}'    -- JSON: reserved
);
```

### extra1 (JSON) — Customer Metadata

| Field | Type | Description | Example |
|-------|------|-------------|---------|
| `country` | string | Customer country | `"Italy"` |
| `tier` | string | Priority tier | `"A"`, `"B"`, `"C"` |
| `linkedin_url` | string | LinkedIn company/person URL | `"https://linkedin.com/company/..."` |
| `company_website` | string | Official website | `"https://example.com"` |
| `social_media` | object | Social media links | `{}` |
| `buyer_type` | string | Buyer category | `"品牌商"`, `"进口商"`, `"经销商"` |
| `main_category` | string | Main product category | `"宠物用品"` |
| `match_score` | integer | Match score (1-5) | `5` |

### extra2 (JSON) — Contact Details

| Field | Type | Description | Example |
|-------|------|-------------|---------|
| `title` | string | Job title | `"采购经理"` |
| `email` | string | Primary email | `"[user.name]@example.com"` |
| `backup_email` | string | Secondary email | `""` |
| `phone` | string | Phone number | `"+39 123 4567890"` |
| `whatsapp` | string | WhatsApp | `"+39 123 4567890"` |
| `wechat` | string | WeChat ID | `"example_wechat"` |
| `source` | string | Lead source | `"agent"`, `"manual"`, `"import"` |
| `follow_up_note` | string | Follow-up reminder | `""` |

## Companies Table

```sql
CREATE TABLE companies (
    id          INTEGER PRIMARY KEY AUTOINCREMENT,
    name        TEXT    NOT NULL,
    slug        TEXT    DEFAULT '',
    website     TEXT    DEFAULT '',
    contact_person TEXT DEFAULT '',
    contact_email TEXT DEFAULT '',
    current_company INTEGER DEFAULT 1,
    created_at  TEXT    DEFAULT (datetime('now', 'localtime')),
    updated_at  TEXT    DEFAULT (datetime('now', 'localtime')),
    extra1-3    TEXT    DEFAULT '{}'
);
```

## Query Patterns

### Get all A-tier customers across all companies
```sql
SELECT c.id, c.name, c.extra1, c.extra2
FROM customers c
WHERE c.extra1 LIKE '%"tier": "A"%'
ORDER BY c.created_at DESC;
```

### Get customers with follow-up notes
```sql
SELECT c.id, c.name, c.extra1, c.extra2
FROM customers c
WHERE c.extra2 LIKE '%"follow_up_note":"%' ESCAPE '\\';
```

### Get customers by country
```sql
SELECT c.id, c.name, c.extra1, c.extra2
FROM customers c
WHERE c.extra1 LIKE '%"country": "%Italy"%'
   OR c.extra1 LIKE '%"country": "%Germany"%'
   OR c.extra1 LIKE '%"country": "%Malaysia"%';
```
