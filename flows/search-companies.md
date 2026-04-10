# Flow: Target Company Search (Bucket 3)

Used for direct career page checks via Chrome. Requires Chrome MCP tools.

## Title Variants

Load `data/title-variants.md` before searching. On each company's careers page, search using multiple title variants — not just "frontend."

<title_variant_rules>

- **ATS with free-text search** (Greenhouse, Lever, Ashby, Workday): run separate searches for "frontend", "product engineer", "UI engineer", "software engineer." These ATS systems often return different results per query — a "Product Engineer" role will not appear in a "frontend" search if the title doesn't contain that word.
- **ATS with category/department filters**: select the "Engineering" department, then scan all listed roles against the full title variants list from `data/title-variants.md` (both Primary and Alternative).
- **Simple career pages** (no search, just a list): scan the full list and match any title from `data/title-variants.md`.

The goal: a "Product Engineer" at Linear or a "Design Engineer" at Vercel should be found, not missed because the search only used "frontend."

</title_variant_rules>

## Process

1. Load `sources/3-companies.md` for the company list, URLs, and actions.
2. Process Priority group first. If running low on context, skip Low Priority group.
3. For each company:
   - Navigate to careers/jobs page using Chrome `navigate`.
   - Search/filter using title variants per the rules above. At minimum search: "frontend", "product engineer", "UI engineer", "software engineer."
   - Scan results for React/TypeScript roles at mid or senior level.
   - For each relevant listing:
     - Extract: title, company, location, URL.
     - **URL rule**: Use the direct job posting URL from the ATS, not the search page.
     - Check URL against existing spreadsheet. If exists → skip.
4. For new postings, extract full description from the posting page:
   - Requirements, tech stack, salary, experience, remote policy, Canada signals.

## ATS Detection Patterns

Different ATS systems have different URL patterns and behaviors:

| ATS | URL Pattern | Notes |
|-----|-------------|-------|
| Greenhouse | `boards.greenhouse.io/company/jobs/ID` or `job-boards.greenhouse.io/company/jobs/ID` | Closed jobs redirect to `?error=true` |
| Lever | `jobs.lever.co/company/UUID` | Clean single-page listings |
| Ashby | `jobs.ashbyhq.com/company/UUID` | Similar to Lever |
| Workday | `company.wd5.myworkdaysite.com/...` | Complex SPAs, harder to parse |
| Custom | company.com/careers/... | Varies widely |

## Known Blocked Sites

These sites are blocked by Chrome safety restrictions — cannot be verified:
- stripe.com (use direct_url for manual check)
- mercury.com
- emplois.bnc.ca

For blocked sites: log as `blocked` in details_status, note in report for manual follow-up.

## Chrome Unavailable

If Chrome is not available, skip this entire flow. Note in report: "Bucket 3 skipped — Chrome unavailable".

## Error Handling

- Career page is JavaScript SPA that won't render → mark `SPA`, move on.
- Page timeout (>60s) → mark `timeout`.
- Redirect to generic careers page → mark `redirect`.
- Cloudflare/bot protection → mark `blocked`.
