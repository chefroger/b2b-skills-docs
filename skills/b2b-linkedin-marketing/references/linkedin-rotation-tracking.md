# LinkedIn 5-Dimension Rotation Tracking

## Problem
LinkedIn content is published daily in 5 rotating dimensions:
1. **视频/照片 (Video/Photo)** — Product showcase, factory behind-the-scenes
2. **文章 (Article)** — Thought leadership, industry analysis
3. **投票 (Poll)** — Engagement-driving questions
4. **Document** — Guides, checklists, free resources
5. **Text Post** — Quick insights, tips, opinions

Two posts per day (09:30 + 15:30). Dimensions cycle: video/photo → article → poll → document → video/photo...

## Persistent State File
Store rotation state at `~/.trade/data/linkedin_rotation.json`:
```json
{
  "dimension_index": 0,
  "last_date": "2026-06-16",
  "dimensions": ["video_photo", "article", "poll", "document", "text_post"]
}
```
- `dimension_index`: current position in the cycle (0-based)
- `last_date`: YYYY-MM-DD of last post
- After generating a post: increment index, wrap at len(dimensions), update date

## Fallback: Scan Cron Outputs
If state file missing, scan `~/.hermes/cron/output/*/` for files containing "LinkedIn 帖子" or "Dimension" in content. Parse the last generated dimension from the most recent successful cron run.

## Weekend / Missed-Day Handling (Critical!)
When the cron job runs on a day after a gap (weekend, holiday, missed run), **do NOT simply increment by 1**. Instead:
1. Count working days between `last_date` and today (exclude Saturdays and Sundays).
2. Advance the dimension index by that many steps: `next_index = (dimension_index + working_days) % len(dimensions)`.
3. Update `last_date` to today's date.
Example: last post was Thursday (index 1), today is Tuesday. Working days = Fri(1) + Mon(1) + Tue(1) = 3. Next dimension = (1+3)%5 = 4 → text_post.

## Quick Reference
- Next dimension = `(dimension_index + 1) % len(dimensions)`
- Reset on weekends/holidays: if `last_date` is Saturday/Sunday, set index to 0 (start of new cycle on Monday)
