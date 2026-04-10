# Database Schema — 20 Columns

Spreadsheet: `output/job-tracker.xlsx` (relative to working directory)
Dedup key: `url` (column 7)

| # | Column | Type | Description |
|---|--------|------|-------------|
| 1 | id | auto-increment | Unique row number |
| 2 | date_found | date | YYYY-MM-DD when agent found this |
| 3 | date_posted | date or "unknown" | Posting date if available |
| 4 | position | string | Job title as listed |
| 5 | company | string | Company name |
| 6 | location | string | E.g., "Montreal", "Remote - Canada", "Remote - US/Canada" |
| 7 | url | string | Direct URL to job posting (dedup key) |
| 8 | source | string | E.g., "Google ATS", "Wellfound", "grafana.com/careers" |
| 9 | source_bucket | number 1-8 | 1=Web Search, 2=Job Boards, 3=Target Companies, 4=Exploratory, 5=Monthly Research, 6=Signals, 7=Agencies, 8=Domain Deep Dive |
| 10 | tech_stack | string | E.g., "React, TypeScript, GraphQL, D3" |
| 11 | salary_range | string or empty | E.g., "CAD 174K-209K", "USD 152K-190K" |
| 12 | experience_required | string | E.g., "3-5 years", "5+ years" |
| 13 | match_score | number 0-100 | Per scoring rubric |
| 14 | score_confidence | "high" / "low" | "high" = full description, "low" = title/snippet only |
| 15 | details_status | string | "complete" / "timeout" / "CAPTCHA" / "login_wall" / "not_found" / "redirect" / "closed" / "Listing only" / "blocked" / "SPA" / "no_chrome" (WebFetch failed, Chrome unavailable — retry in session with Chrome) |
| 16 | application_status | string | "new" / "reviewing" / "applied" / "interview" / "rejected" / "offer" (default: "new") |
| 17 | canada_eligible | string | "yes" / "no" / "unclear" / "Likely" |
| 18 | key_requirements | string | Brief summary of main requirements |
| 19 | notes | string | Candidate's personal notes (never modify) |
| 20 | cv_fit | "ready" / "adapt" / "rewrite" | How well current CV covers the vacancy's key requirements. "ready" = CV already matches, send as-is. "adapt" = tweak emphasis/keywords. "rewrite" = significant gaps, needs creative framing or skip. |

## Header Row

Row 1. Dark blue background (`002F5496`), white bold font. **Never modify.**
