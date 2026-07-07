# Skill Auto-Detection — Trigger Architecture

> How the Foreign Trade Assistant automatically routes user queries to the correct b2b-* skill, even from vague, abbreviated, or multilingual input.

---

## Problem

Users do not naturally say "load skill b2b-email-intel and call email_background_check()". They say:

- `"帮我查一下这个邮箱"` (vague, no explicit skill name)
- `"lead gen"` (English abbreviation)
- `"背景调查"` (single keyword, no email address yet)
- `"用 b2b-email-intel 查一下"` (explicit skill name in Chinese)

The system must bridge this gap without requiring the user to know the skill names.

---

## Solution: Two-Tier Matching

### Tier 1 — Explicit Skill Invocation

Regex: `/(?:用|使用|调用|加载|load?\s*(?:skill)?)\s*b2b-[\w-]+/i`

Matches:
- `"用 b2b-email-intel 查一下"`
- `"load skill b2b-document"`
- `"使用 b2b-lead-generation 找客户"`

Direct lookup by name — no fuzzy logic needed.

### Tier 2 — Keyword / Phrase Fuzzy Matching

Each skill registers a list of trigger phrases. Matching uses two strategies:

1. **Word-boundary match** — `\b{kw}\b` — catches exact phrase occurrences
2. **Substring match** — bare keyword — catches suffixes/prefixes and partial input

Example triggers for `b2b-lead-generation`:
```
找客户, 开发客户, 客户开发, lead generation, 
lead gen, leadgen, cold email, outreach, 
prospect, prospecting, find buyers, help me find buyers, ...
```

---

## Augmentation Prompt Pattern

When a skill matches, the router injects a structured block:

```
[SKILL AUGMENTATION]
## 技能触发：b2b-email-intel

你是 b2b-email-intel 技能。当用户需要调查某个邮箱的背景时...
1. 从对话中提取邮箱地址（格式：[email@domain].com）
2. 加载 skill: b2b-email-intel
3. 调用 email_background_check(邮箱地址)
4. 返回结构化报告：...
## 用户原始问题
帮我查一下这个邮箱
[SKILL AUGMENTATION]
```

The LLM receives: **role definition + step-by-step instructions + original query**.

This means even if the user gave a partial/abbreviated query, the LLM knows:
- Which function to call
- What parameters to extract from the conversation
- How to format the output
- What to do if the input is incomplete (ask the user)

---

## Key Design Decisions

### 1. No tool calls in the router itself
`skill_router.py` does zero tool execution — only regex matching and string injection.
This keeps it fast, stateless, and zero-dependency (no FastAPI, no external APIs).

### 2. Aliases map related skills to each other
`b2b-lead-generation` and `b2b-customer-mgmt` are aliases of each other.
This handles overlap: a "客户分级" query triggers `b2b-customer-mgmt`,
but `b2b-lead-generation` is also relevant — the router returns the first match.

### 3. `company_id` passed through for path-dependent skills
Only `b2b-data-directory` needs runtime paths. The router accepts `company_id`
and resolves `~/.trade/companies/{slug}/` before injecting the augmentation.

### 4. Fast no-match path
`augment_query()` returns the original query unchanged when no skill matches.
This means the no-match case adds zero latency — just one dict lookup.

---

## All 12 Registered Skills

| Skill | Primary Triggers (sample) |
|-------|--------------------------|
| `b2b-email-intel` | 背景调查, email intel, email lookup, 查邮箱 |
| `b2b-lead-generation` | 找客户, lead gen, 开发信, cold email, find buyers |
| `b2b-document` | moq是多少, 这是什么产品, read quote, analyze doc |
| `b2b-doc-generation` | 帮我生成, generate doc, 做一份报价, make a presentation |
| `b2b-platform` | 阿里店铺, platform diagnosis, 关键词排名, seo |
| `b2b-linkedin-marketing` | 领英, linkedin content, linkedin post, InMail |
| `b2b-social-media` | FB发帖, TikTok内容, content calendar, ins营销 |
| `b2b-customs-data` | 海关数据, customs data, import data, 找买家 |
| `b2b-onboarding` | 新公司, first time setup, 部署, 全套方案 |
| `b2b-daily-automation` | 早报, morning brief, 每日任务, cron |
| `b2b-customer-mgmt` | 客户列表, customer profile, vip客户, 订单跟踪 |
| `b2b-data-directory` | 数据目录, data directory, trade目录, 公司信息 |

---

## Adding a New Skill

1. Add entry to `_SKILLS` list in `trade/skill_router.py`:
   ```python
   {
       "name": "b2b-my-skill",
       "triggers": [
           "primary trigger phrase",
           "secondary trigger",
           ...
       ],
       "aliases": ["other-skill-that-overlaps"],
       "input_fmt": "what the user must provide",
       "output_fmt": "what the user gets back",
       "augment_prompt": "role definition + step-by-step instructions",
   }
   ```

2. Pre-compiled at import time — no runtime regex compilation.

3. Update this reference doc with the new skill entry.

---

## Code Location

`trade/skill_router.py` — `match_skill()`, `augment_query()`, `get_skill_by_name()`
`trade/helpers.py` — `build_query()` calls `skill_router.augment_query()` before assembly
