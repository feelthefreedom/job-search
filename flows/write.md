# Flow: Write to Spreadsheet + Generate Report (Phase 5-6)

Read before writing: `database/schema.md` (columns), `database/styling.md` (openpyxl styles).

## Phase 5: Update Database

1. **Ensure output directory exists**: `os.makedirs("output", exist_ok=True)`
2. **Backup first**: `cp output/job-tracker.xlsx output/job-tracker-backup-YYYY-MM-DD-HHMM.xlsx`
3. **Record freeze_row**: Find the actual last row with data, NOT `ws.max_row` (which may include styled-but-empty rows). Use this pattern:
   ```python
   freeze_row = 1
   for row in range(1, ws.max_row + 1):
       if any(ws.cell(row=row, column=col).value is not None for col in range(1, 21)):
           freeze_row = row
   ```
   This prevents the bug where styled empty rows inflate `max_row` to 1000+ and new data gets appended far below the actual data.
4. Append new entries sorted by match_score descending.
5. Apply styles from `database/styling.md` to every new row.
6. Save file.

### Write Safety

- ALL writes MUST target rows > `freeze_row` ONLY.
- Never `ws.cell(row=r, ...)` where `r <= freeze_row` for ANY write: `.value`, `.font`, `.fill`, `.hyperlink`, `.alignment`.
- If an existing row's vacancy is found closed via Chrome → do NOT modify that row. Log in report only.
- Follow-up updates (Chrome enrichment): may update rows > `freeze_row` created in THIS session. Pre-existing rows are permanently read-only.
- If code has `for r in range(start, ...)` where `start` could be ≤ `freeze_row` → BUG. Fix before running.
- Never change `application_status` or `notes` — candidate manages those.

### File Corruption

If spreadsheet is corrupted/unreadable: create new file with `_backup_YYYY-MM-DD` suffix, start fresh, alert in report.

## Phase 6: Generate Report

Write markdown report to: `output/report-YYYY-MM-DD.md`

### Report Contents

- Date of search run
- Buckets executed
- Number of new vacancies found
- Number of duplicates skipped
- Top 10 new vacancies by match score: title, company, score, URL, one-line summary
- List of entries where details could not be fetched (with failure reason per entry)
- Sources that failed or were skipped (with reason)
- Notable observations: new companies hiring, salary data points, emerging trends

### Salary Context in Report

When reporting salary data, compare against reference ranges:
- Local Montreal: CAD 80K-110K
- Well-funded Montreal: CAD 100K-150K
- US companies, Canadian rates: CAD 120K-180K+
- Top reference: Grafana CAD 174K-209K base, Stripe CAD 212K-485K TC, Shopify CAD 217K avg TC

## Output

After each run, candidate should find:
1. Updated spreadsheet with new rows (sorted by score within day's batch).
2. Markdown report for the day.

Prioritize signal over volume. Eight 70+ matches > forty 30-50 matches.
