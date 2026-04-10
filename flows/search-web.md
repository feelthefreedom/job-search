# Flow: Web Search (Buckets 1, 4)

Used for Google, LinkedIn, Indeed queries via WebSearch tool. No browser needed.

## Process

1. Load the relevant `sources/*.md` file for search queries.
2. For each query template, adapt to WebSearch format:
   - Remove boolean operators (AND/OR/NOT) — split into simpler queries if needed.
   - Simplify `site:` operators — one site per query works best.
3. Execute independent queries in parallel when possible.
4. For each result:
   - Extract: title, company, location, URL, source, posting date.
   - **URL rule**: Save the direct job posting URL, not a search/filter page URL. If a board links through to greenhouse/lever/company site, use the final URL.
   - Check URL against existing spreadsheet rows. If exists → skip.
5. For each new URL, fetch full description via WebFetch.
   - If WebFetch blocked → immediately fall back to Chrome (navigate + get_page_text).
   - If Chrome also fails → mark `details_status` with specific reason: `timeout`, `CAPTCHA`, `login_wall`, `not_found`, `redirect`.
   - If Chrome is unavailable in this session → mark `details_status` as `no_chrome`. This means "WebFetch failed, Chrome wasn't available — retry in a session with Chrome."
6. From fetched descriptions, extract: requirements, tech stack, salary range, experience level, remote policy, Canada-eligibility signals.

## Title Variants

Load `data/title-variants.md` — always search multiple title variations where the platform allows:
"Frontend Engineer", "Front-End Engineer", "Front End Engineer" as separate queries.

## Geography Filter

If a geography override is active (e.g., "только Квебек"), filter results before collecting.
Load `data/geography.md` for salary rules and eligibility signals.

## Error Handling

- WebSearch returns no results → log, move to next query.
- WebFetch blocked → Chrome fallback → mark failure reason if both fail. If Chrome unavailable → mark `no_chrome`.
- More than 50 new results in single query → process first 30, note overflow in report.
