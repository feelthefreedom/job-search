# Signals Database Schema

## File

`output/signals.json` — flat JSON array of company objects.

## Schema

```json
{
  "company": "",
  "website": "",
  "sector": "",
  "hq": "",
  "size": "",
  "funding_stage": "",
  "funding_amount": "",
  "funding_date": "",
  "investors": [],
  "signal_type": "",
  "signal_detail": "",
  "signal_date": "",
  "signal_url": "",
  "canada_signals": [],
  "tech_signals": [],
  "adjacent_roles": [],
  "qualification": "",
  "qualification_reason": "",
  "action": "",
  "status": "new",
  "notes": "",
  "added": "",
  "last_checked": ""
}
```

## Field Rules

### Identity
- `company`: company name as commonly known (e.g., "Temporal", not "Temporal Technologies Inc.")
- `website`: main website URL
- `sector`: one of: `fintech`, `observability`, `devtools`, `data_platform`, `internal_tools`, `healthcare`, `logistics`, `compliance`, `ai_tooling`, `workflow`, `other`
- `hq`: city + country (e.g., "Toronto, Canada", "San Francisco, US", "Remote-first")
- `size`: approximate headcount if known, otherwise `"unknown"`

### Funding
- `funding_stage`: e.g., `"Series A"`, `"Series B"`, `"Series C"`, `"Growth"`, `"unknown"`
- `funding_amount`: string with currency (e.g., `"$45M"`, `"$120M CAD"`). Use `""` if unknown.
- `funding_date`: YYYY-MM-DD of the round. Use `"unknown"` if approximate.
- `investors`: array of investor names. Use `[]` if unknown.

### Signal
- `signal_type`: one of: `funding`, `leadership_hire`, `adjacent_role`, `product_launch`, `tech_stack_change`, `headcount_growth`, `office_expansion`
- `signal_detail`: 1-2 sentence description of what was detected (e.g., "Raised $60M Series B led by a16z. CEO mentioned 'tripling engineering team' in TechCrunch interview.")
- `signal_date`: YYYY-MM-DD when the signal was observed
- `signal_url`: source URL where the signal was found

### Qualification
- `canada_signals`: array of strings — evidence for/against Canada hiring (e.g., `"Toronto office on LinkedIn"`, `"RRSP in benefits page"`, `"US-only on careers page"`, `"3 Canadian employees found"`)
- `tech_signals`: array of strings — evidence of tech stack fit (e.g., `"React listed on careers page"`, `"TypeScript repos on GitHub"`, `"Vue.js only in job descriptions"`, `"Wappalyzer shows Next.js"`)
- `adjacent_roles`: array of strings — related roles already posted (e.g., `"Backend Engineer posted 2026-03-25"`, `"Product Designer posted 2026-04-01"`)
- `qualification`: one of: `hot`, `warm`, `cold`, `disqualified`
- `qualification_reason`: 1-2 sentence explanation (see `flows/qualify-signal.md` for criteria)

### Action
- `action`: one of: `monitor`, `research_deeper`, `outreach_ready`, `added_to_source3`, `reached_out`, `no_action`
- `status`: one of: `new`, `watching`, `outreach_sent`, `responded`, `no_fit`, `converted_to_vacancy`
- `notes`: freeform, managed manually

### Timestamps
- `added`: YYYY-MM-DD when the record was created
- `last_checked`: YYYY-MM-DD when the record was last updated/verified

## Dedup

Dedup by `company` name (case-insensitive). If a company already exists in the array, UPDATE the existing entry with new signal info — don't create a duplicate. Append new signals to `signal_detail`, update `signal_date` to the latest, and update `last_checked`.

## Cross-reference with companies-list.md

When a company reaches `qualification: "hot"` and `action: "outreach_ready"` or higher, it should also be added to `data/companies-list.md` and `sources/3-companies.md` so Source 3 monitors its careers page. Set `action: "added_to_source3"` after doing this.

Companies already in `data/companies-list.md` should still be tracked in signals.json if a new signal is detected — this enriches existing data.
