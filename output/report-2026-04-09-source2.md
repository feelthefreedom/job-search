# Source 2 — Job Boards Report

**Date:** 2026-04-09
**Source:** Bucket 2 (Job Boards)
**Boards searched:** Wellfound, Built In Montreal, HN Hiring (April 2026), Remotive, WWR
**Boards skipped:** YC Work at a Startup, devjobsscanner, Monster, Himalayas (irrelevant results), BetaKit Jobs, Key Values, MaRS Job Board, NoDesk, Hired, Underdog — skipped due to context/time constraints

## Summary

| Metric | Count |
|--------|-------|
| New vacancies added | 12 |
| Duplicates skipped | 1 (SoilFLO — already in tracker) |
| Auto-skipped (exclusions) | ~5 (Staff-level: Luxury Presence, Mozilla Staff Engineer, Jane App Staff; Duplicate: LaunchDarkly; Likely US-only: Sentra) |
| Score ≥ 70 | 4 |
| Score 50–69 | 7 |
| Score < 50 | 1 |

## Top Vacancies by Score

| Score | Company | Position | Location | CV Fit |
|-------|---------|----------|----------|--------|
| 72 | Mozilla | Senior Front End Software Engineer | Remote - Canada | adapt |
| 72 | Planera | Frontend Software Developer | Remote - Canada | ready |
| 70 | CoLab Software | Senior Front End Developer | Remote - Canada | adapt |
| 70 | Hopper | Senior Front-end/Full-Stack - HTS Stays & Packages | Remote - Canada | adapt |
| 68 | MobSquad | Senior Front-End Engineer | Remote - Canada | adapt |
| 68 | Plusgrade | Senior Software Developer (FrontEnd) | Hybrid - Montréal | adapt |
| 67 | Uride | Senior Front-End Developer - Canada | Remote - Canada | ready |
| 65 | Jane App | Senior Developer - Frontend Foundations | Remote - Canada | adapt |
| 62 | Tucows | Software Engineer - Front End | Remote - Canada | adapt |
| 55 | FLiiP | UI / Front-End Developer | In-Office - Brossard, QC | adapt |
| 52 | Megaport | Senior Frontend Software Engineer | Remote - Canada | adapt |
| 48 | Domaine | Front-end Technical Lead | Remote - Canada | adapt |

## Entries with Incomplete Details

12 of 12 new entries have `details_status: "Listing only"` — full descriptions were not fetched because Chrome was used for navigation but Built In Montreal listings only showed summary data. Consider re-running these through Chrome to fetch full job descriptions from original career pages for more accurate scoring.

SoilFLO (duplicate, not re-added) was the only vacancy with `details_status: "complete"` — fetched via Wellfound.

## Sources That Failed or Were Skipped

| Source | Status | Reason |
|--------|--------|--------|
| Wellfound | Partial | Searched engineering roles in Canada. Found SoilFLO (already in tracker). Company names hidden behind paywall for most listings. |
| HN Hiring (April 2026) | Searched | Read all 72 listings. No new frontend-in-Canada matches found (most were US-only or backend roles). |
| Remotive | Searched | Frontend/React filter applied. Company names hidden behind paywall ("[Company Name]"). Could not identify or deduplicate. |
| WWR (We Work Remotely) | Searched | Browsed programming category. No new Canada-eligible frontend roles found. |
| Built In Montreal | Primary source | 12 new vacancies found. Strong results — most productive board this run. |
| Himalayas | Skipped | Query "frontend engineer + canada" returned irrelevant results. |
| YC Work at a Startup | Skipped | Context/time constraints. |
| devjobsscanner | Skipped | Context/time constraints. |
| Monster | Skipped | Context/time constraints. |
| BetaKit Jobs | Skipped | Context/time constraints. |
| Key Values | Skipped | Context/time constraints. |
| MaRS Job Board | Skipped | Context/time constraints. |
| NoDesk | Skipped | Context/time constraints. |
| Hired | Skipped | Passive platform, requires profile setup. |
| Underdog | Skipped | Passive platform, requires profile setup. |

## Notable Observations

**Built In Montreal dominance:** All 12 new vacancies came from Built In Montreal. This board has strong Canada-specific filtering and consistently surfaces relevant roles. Consider prioritizing it in future runs.

**Strong Canada remote market:** 10 of 12 vacancies are Remote - Canada, 1 is Hybrid Montréal, 1 is In-Office Brossard QC. The Canadian remote frontend market remains active.

**Salary data point:** SoilFLO (duplicate) listed CAD 110K-140K + equity for a Senior Frontend role in Ontario — within the "local Montreal" to "well-funded Montreal" range per salary benchmarks.

**Score confidence:** 12 of 12 new entries scored at `low` confidence (listing-only data). Re-fetching full descriptions would likely shift scores by ±5-10 points in either direction. Planera (72, "ready") and Uride (67, "ready") are the strongest candidates for immediate application even with low confidence — their listing summaries align closely with the candidate's profile.

**Vue override applied:** Megaport (52) uses Vue 3 with no React. Included because Built In Montreal confirms Canada hiring. Score capped per Vue-only override rules.

**Companies to watch:** Planera (construction workflows + data-rich dashboards = strong domain match), Hopper (confirmed Montreal HQ, complex travel UI), CoLab Software (data-rich collaborative environment).

**Boards to prioritize next run:** YC Work at a Startup and devjobsscanner were skipped but historically produce good results. Should be first priority if running Source 2 again.
