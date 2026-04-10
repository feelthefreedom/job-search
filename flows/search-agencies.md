# Flow: Staffing Agency Outreach (Bucket 7)

Used for submitting resume and browsing agency job boards via Chrome. Requires Chrome MCP tools.

## How This Flow Differs

This is NOT a vacancy search flow. The primary goal is **resume submission and profile maintenance**, not finding specific job postings. Agencies match you to contracts — your job is to stay visible in their system.

## Process

1. Load `sources/7-agencies.md` for the agency list, URLs, and actions.
2. Process Wave 1 first (tech-focused agencies), then Wave 2 (general).
3. For each agency:
   - Navigate to the agency URL using Chrome `navigate`.
   - Look for "Submit Resume", "Register", "Create Profile", or "Job Seekers" section.
   - **If new**: register and upload current resume. Note any profile fields that need filling (skills, preferences, availability).
   - **If already registered**: check if resume is current. If outdated, update it.
   - **If agency has a job board**: after registration, browse for frontend/React roles using title variants from `data/title-variants.md`. Apply standard search: "frontend", "product engineer", "React", "software engineer".
   - For each relevant listing found on agency board:
     - Extract: title, company (if visible), location, URL, source = agency name.
     - **URL rule**: Use the direct job posting URL. If company name is hidden (common for agencies), use `"company": "confidential via [Agency Name]"`.
     - Check URL against existing spreadsheet. If exists → skip.
4. For new postings found on agency boards, attempt to get details:
   - Requirements, tech stack, salary, experience, remote policy, Canada signals.
   - Agency postings often have less detail — mark `details_status` accordingly.

## Output

Two types of output from this flow:

### 1. Agency Status Report (always produced)
For each agency visited, report:
- Agency name
- Status: `registered` / `profile_updated` / `already_active` / `registration_failed` / `blocked`
- Last resume update date (if visible)
- Notes (e.g., "requires phone call to activate", "profile incomplete — needs skills section")

### 2. Vacancy JSON (only if job board postings found)
Same format as other flows — standard vacancy JSON per `master.md` data contract. Use `source_bucket: 7`.

## Chrome Unavailable

If Chrome is not available, skip this entire flow. Note in report: "Bucket 7 skipped — Chrome unavailable".

## Error Handling

- Registration requires phone verification → mark `registration_failed`, note reason.
- Site requires login but credentials unknown → mark `blocked`, note for manual follow-up.
- Page timeout → log, skip that agency, continue.
- CAPTCHA/bot protection → mark `blocked`, move on.
