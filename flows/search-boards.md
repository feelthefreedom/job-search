# Flow: Job Board Search (Buckets 2, 5)

Used for browser-based navigation of job boards and aggregators. Requires Chrome MCP tools.

## Title Variants

Load `data/title-variants.md` before searching. On each board, search using multiple title variants — not just "Frontend Engineer."

<title_variant_rules>

- **Boards with free-text search** (Wellfound, YC Work at a Startup, Monster, Himalayas, devjobsscanner): run separate searches for at least these titles from the Primary list: "Frontend Engineer", "Software Engineer Frontend", "Product Engineer", "Senior Frontend Engineer". If the board supports it, also search Alternative titles: "UI Engineer", "Design Engineer", "Full Stack Engineer", "React Developer".
- **Boards with tag/category filters** (HN Hiring, We Work Remotely, Remotive, Key Values): apply the broadest relevant filter (e.g., "Programming" or "Software Dev"), then scan results for any title matching `data/title-variants.md` — both Primary and Alternative lists.
- **Boards with limited search** (Built In Montreal, BetaKit, MaRS): scan all new engineering listings and match against the full title variants list manually.

The goal: a "Product Engineer" posting on Wellfound or a "UI Engineer" on YC should be found, not missed because the search only used "Frontend Engineer."

</title_variant_rules>

## Process

1. Load the relevant `sources/*.md` file for board list and actions.
2. For each board:
   - Navigate to the URL using Chrome `navigate` tool.
   - Apply filters as specified in the query file (category, tech, location).
   - Scan listings. Use `get_page_text` or `read_page` to extract visible postings.
   - For each relevant listing:
     - Extract: title, company, location, URL, source.
     - **URL rule**: If the board links to an external ATS (greenhouse/lever/ashby), follow through and use the final URL. If only the board URL exists, use that. Never use a generic filter/search URL.
     - Check URL against existing spreadsheet. If exists → skip.
3. For each new posting, attempt to get full description from the posting page.
   - If page loads → extract requirements, tech stack, salary, experience, remote policy, Canada signals.
   - If page fails (CAPTCHA, timeout, login wall) → mark `details_status` with specific reason.

## Chrome Unavailable

If Chrome is not available, skip all board sources. Note in report: "skipped — Chrome unavailable". Proceed with other flows.

## Common Patterns

- **Greenhouse redirect**: Closed jobs redirect to `?error=true` on company listing page → mark as `closed`.
- **Wellfound**: Personalized "Note to Founder" messages improve callback (6.4% vs 3.3% LinkedIn). Note this in report for high-score matches.
- **HN Hiring**: Monthly thread on 1st — highest-signal source. Process thoroughly.

## Error Handling

- Page timeout → log, skip that board, continue.
- CAPTCHA/JS rendering required → mark status, move on.
- Site blocked by Chrome safety → log as `blocked`, move on.
