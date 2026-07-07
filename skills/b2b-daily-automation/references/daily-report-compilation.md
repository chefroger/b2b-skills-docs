# Daily Follow-Up Report Compilation

**When to use:** Generating daily email/follow-up reports for the user, especially when the CRM `customers` table is empty or sparse.

## Data Sources (in priority order)

1. **Morning Brief** (`~/.hermes/cron/output/2026-MM-DD-morning-brief.md` or latest cron output)
   - Contains A/B/C priority customer follow-up lists
   - Includes currency/commodity data that can inform pricing emails
   - Has specific action items per customer

2. **Cron Output Directory** (`~/.hermes/cron/output/*/`)
   - Search for files dated yesterday and today: `find ~/.hermes/cron/output -name "*.md" -mtime -2`
   - Each cron job (morning brief, daily summary, LinkedIn post) produces output files
   - Daily summary cron outputs contain interaction summaries

3. **Conversation Logs** (SQLite `conversations` table)
   ```sql
   SELECT id, query, substr(response, 1, 200) as preview, created_at
   FROM conversations
   WHERE company_id = {CURRENT_COMPANY_ID}
   ORDER BY created_at DESC LIMIT 20;
   ```
   - Look for customer names, website diagnoses, email drafts in queries/responses

4. **Audit Logs** (`~/.trade/audit/YYYY-MM-DD.jsonl`)
   - Company switches, task executions
   - Shows what actions were taken on which company

5. **Document-Based Sources** (when CRM is empty)
   - `~/Desktop/科辰/客户池-/客户池分析报告_优先开发名单.md` — 50 prioritized customers
   - `~/.trade/daily-plans/YYYY-MM-DD-*.md` — Daily development plans with customer targets

## Compilation Steps

1. Load skill `b2b-daily-automation`
2. Read the latest morning brief for customer follow-up priorities
3. Cross-reference with yesterday's conversation logs for any new interactions
4. Check cron output directory for daily summary data
5. If CRM `customers` table is empty, fall back to document-based sources
6. Organize by A/B/C priority tier
7. Generate email templates using the tiered template approach

## Email Template Generation Rules

- **A-level**: Urgent, specific, time-sensitive (price drops, overdue follow-ups)
- **B-level**: Value-add, market-driven (commodity price changes, industry news)
- **C-level**: Nurturing, introductory (catalogs, company profiles, market insights)
- **Saturday rule**: Only send to North American/Latin American contacts (Asia/Africa on weekend)
- **Always reference**: Real data from search results, never fabricate prices or dates

## Known Issue: Empty CRM Table

The `customers` SQLite table frequently has 0 rows despite active customer follow-ups tracked in morning briefs and conversation logs. **Always check alternative sources before reporting "no customers to follow up."**

## Known Issue: Weekend Gap

If today is Monday, the last cron output may be from Friday (3 days ago). Explicitly note the gap and use the latest available data, not stale data. When generating the email follow-up report, acknowledge any multi-day gaps in customer communications.

## Data Discovery Workflow (When Sources Are Unknown)

When the cron job prompt asks for customer follow-ups but the path to data isn't obvious, use this discovery sequence:

1. **Check cron output directory** — `ls -lt ~/.hermes/cron/output/` to find job folders, then `ls -lt ~/.hermes/cron/output/{JOB_ID}/` for the latest run files
2. **Read the latest morning brief** — `~/.hermes/cron/output/101d1ba6032c/2026-MM-DD_*.md` contains A/B/C priority lists
3. **Read the latest email-processing output** — `~/.hermes/cron/output/14c586a6a716/2026-MM-DD_*.md` if it exists (may be stale over weekends)
4. **Query trade.db** — `sqlite3 ~/.trade/data/trade.db "SELECT * FROM companies;"` and `"SELECT COUNT(*) FROM customers;"` to know what's in the CRM
5. **Check conversation logs** — `sqlite3 ~/.trade/data/trade.db "SELECT id, company_id, substr(query,1,100), substr(response,1,200), created_at FROM conversations ORDER BY created_at DESC LIMIT 20;"`
6. **Check daily plans** — `find ~/.trade -name "*-customer-development-plan.md" -o -name "*daily-plan*" 2>/dev/null`
7. **Check for weekend gaps** — If today is Monday, the last cron output may be from Friday (3 days ago). Explicitly note the gap and use the latest available data, not stale data

### Cron Job IDs Reference

| Job ID | Name | Schedule | Latest Output Path |
|--------|------|----------|-------------------|
| `101d1ba6032c` | 🌅 早安简报 | 08:50 M-F | `~/.hermes/cron/output/101d1ba6032c/` |
| `14c586a6a716` | 📧 邮件处理与跟进 | 09:00 M-F | `~/.hermes/cron/output/14c586a6a716/` |
| `a3a9aa67ab70` | 🔍 精准加人 (LinkedIn) | 10:00 M-F | `~/.hermes/cron/output/a3a9aa67ab70/` |
| `cbf626c498ab` | 💬 评论互动与私信致谢 | 11:30 M-F | `~/.hermes/cron/output/cbf626c498ab/` |
| `02aa9b1b519f` | 📢 LinkedIn 内容发布 | 15:30 M-F | `~/.hermes/cron/output/02aa9b1b519f/` |
| `4a9ba3ab0e47` | 👥 客户开发 | 13:30 M-F | `~/.hermes/cron/output/4a9ba3ab0e47/` |
| `1f4c761266e2` | 📊 每日工作总结 | 16:00 M-F | `~/.hermes/cron/output/1f4c761266e2/` |
| `0c081b0cfd58` | 📋 每周复盘报告 | Fri 09:30 | `~/.hermes/cron/output/0c081b0cfd58/` |

### Weekly Report Reference

For generating the Friday weekly review report, see `references/weekly-report-compilation.md` (referenced in main SKILL.md Phase 3). It covers: data source aggregation from cron outputs, KPI extraction, plan-vs-execution gap analysis, and next-week action planning.
