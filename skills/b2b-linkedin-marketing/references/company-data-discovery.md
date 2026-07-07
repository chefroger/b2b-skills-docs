# Company Data Discovery for LinkedIn Content Generation

## Problem
When generating LinkedIn posts or marketing content, the agent needs company/product data. The `.md` template files under `~/.trade/companies/{slug}/` are often **unfilled** — they contain only headers and placeholders.

## Solution: Multi-Source Data Retrieval

### 1. SQLite Database (Primary)
```bash
sqlite3 ~/.trade/data/trade.db "SELECT * FROM companies;"
# Also check trade_companies: sqlite3 ~/.trade/data/trade.db "SELECT * FROM trade_companies;"
# Join with customers: SELECT c.*, comp.name FROM customers c JOIN companies comp ON c.company_id = comp.id
# Check conversations for product context: SELECT * FROM conversations WHERE company_id=1 ORDER BY created_at DESC LIMIT 5
```
**Note:** The `companies` table contains company metadata (name, website, contact person). The `trade_companies` table stores file paths to company folders. The `conversations` table often contains product context, target markets, and past generated content that reveals terminology.

### 2. Desktop Local Folders
Product catalogs, spec sheets, and presentation files are often stored on Desktop:
- `~/Desktop/{company-slug}/` — look for `.pptx`, `.pdf`, `.xlsx` files
- Examples: `科辰产品册_副本/`, `电力相关产品清单_副本.xlsx`

### 3. Cron Output History
Past generated content (emails, posts, reports) reveals product terminology and company context:
- `~/.hermes/cron/output/*/` — scan for files mentioning the company name

### 4. .md Template Files (Secondary)
Only use as fallback. Check if files contain real data vs placeholders.

## Pattern
Always check sources in order: DB → Desktop → Cron outputs → .md files. The first source with real data wins.
