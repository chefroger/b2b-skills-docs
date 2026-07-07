# Document-Based Customer Lookup Guide

**When CRM database (`customers` table) is empty, check these sources:**

## Primary Sources

| Source | Path | Content |
|--------|------|---------|
| Priority Report | `~/Desktop/科辰/客户池-/客户池分析报告_优先开发名单.md` | 50 prioritized customers across 3 tiers (A/B/C), with country, email, website, rationale |
| Full Data Report | `~/Desktop/科辰/客户池-/客户池Excel完整数据分析报告.md` | Complete analysis of 1,472-record Excel pool |
| Daily Summaries | `~/.hermes/cron/output/*/2026-*.md` | Extracted follow-up lists from morning briefs and daily summaries |

## Key Customers from Priority Report (Top 10, Tier A)

| # | Company | Country | Email | Product Fit |
|---|---------|---------|-------|-------------|
| 1 | CTC Group | Vietnam | [contact.email] | Preformed fittings |
| 2 | Hardexo Kenya | Kenya | [contact.email] | OEM preformed |
| 3 | Al Rasikh Company | Iraq | [contact.email] | Power equipment |
| 4 | McWade Productions | South Africa | [contact.email] | Power line hardware |
| 5 | Aragón Energía | Chile | [contact.email] | Preformed + insulators |
| 6 | Kenya Power | Kenya | [contact.email] | National utility |
| 7 | Electricidad Serrano | Argentina | [contact.email] | Distribution |
| 8 | PT. Himalaya Everest Jaya | Indonesia | [contact.email] | Electrical trading |
| 9 | EVERENG | Thailand | [contact.email] | Power distribution |
| 10 | Doorisopen Nigeria | Nigeria | [contact.email] | Distribution |

## Known Existing Contacts (Avoid Duplicate Development)

| Country | Existing Contacts |
|---------|-------------------|
| South Africa | Collen K, evansmkhombo, Sipho Mabuza, Wynand |
| Philippines | Manuel Ang, Enrique Perlas, Rajeev |
| Peru | Luis Layme, Arquimedes Olarte |
| Brazil | Benjamin Oduro |
| Mexico | Freddy Altuzar Agustin |
| Egypt | Bahaa-Egypt |
| Malaysia | Albert |
| Argentina | Historical orders exist |

## Database Schema Reference

```sql
-- customers table may be empty even when document data exists
CREATE TABLE customers (
    id          INTEGER PRIMARY KEY AUTOINCREMENT,
    company_id  INTEGER REFERENCES companies(id),
    name        TEXT NOT NULL,
    contact     TEXT DEFAULT '',
    note        TEXT DEFAULT '',
    created_at  TEXT DEFAULT (datetime('now', 'localtime')),
    updated_at  TEXT DEFAULT (datetime('now', 'localtime')),
    extra1 TEXT DEFAULT '{}', extra2 TEXT DEFAULT '{}', extra3 TEXT DEFAULT '{}'
);
-- extra1/2/3 are JSON columns for flexible fields: email, phone, country, tier, website, etc.
```
