# Source 3 Mode C Report — 2026-04-08

## Run Summary
- **Source**: Bucket 3 Mode C (user-provided company list)
- **Companies searched**: 34 (user's list minus Datadog)
- **New vacancies added**: 12
- **Duplicates skipped**: 0
- **Companies with NO relevant openings**: 22

## Top Vacancies by Match Score

| # | Score | Position | Company | Location | CV Fit |
|---|-------|----------|---------|----------|--------|
| 1 | 83 | Frontend Software Development Engineer | Samsara | Remote - Canada | ready |
| 2 | 80 | Senior Frontend Software Engineer | Samsara | Remote - Canada | ready |
| 3 | 74 | Senior Frontend Engineer | d1g1t | Toronto, ON | adapt |
| 4 | 65 | Kibana - Sr SWE, Platform Security | Elastic | Canada (Distributed) | adapt |
| 5 | 61 | Software Developer (Full Stack React/TS) | Geotab | Oakville / Toronto | adapt |
| 6 | 57 | Senior Front End Developer | Edgecom Energy | Toronto (Hybrid) | adapt |
| 7 | 57 | Senior Front-End Developer | BrainBox AI | Montreal (Hybrid) | adapt |
| 8 | 55 | Sr Full Stack Developer (Build Viewing) | CoLab Software | Remote - Canada | adapt |
| 9 | 50 | Senior FullStack Software Developer | Prevu3D | Montreal (Hybrid) | adapt |
| 10 | 48 | Senior Full Stack Software Engineer | Brickeye | Toronto, ON | adapt |
| 11 | 38 | Senior Software Developer | VEERUM | Calgary, AB | rewrite |
| 12 | 37 | Senior Full Stack Developer (Blazor) | dcbel | Montreal, QC | rewrite |

## Auto-Skipped Vacancies (not added)

| Company | Position | Reason |
|---------|----------|--------|
| Samsara | Staff Front-End Engineer (React) | Staff level — auto-skip |
| FLO (AddÉnergie) | Staff Front-End Software Developer | Staff level — auto-skip |
| CrowdStrike | Frontend Engineer Intern | Intern level — auto-skip |
| Neo Financial | Junior Software Developer | Junior level — auto-skip |
| Shakepay | Senior Software Engineer | Backend-focused (Node.js/Postgres), no frontend markers |
| Shakepay | Senior SWE, Internal Tooling | Internal tooling, backend-leaning |
| Shakepay | Senior SWE, Risk | Risk/fraud backend, no frontend |

## Positions Found Closed

| Company | Position | Status |
|---------|----------|--------|
| Mappedin | Software Developer - Front-End Web | Closed (no positions at Mappedin) |
| Mappedin | Full Stack Developer | Closed |
| Mappedin | Senior Software Developer | Closed |
| Float Financial | Senior Front End Developer | Workable portal closed, no openings |
| Survalent | Software Developer (.NET/React) | No longer accepting applications |

## Companies with No Relevant Frontend Openings

Affirm (backend only in Canada), Auvik Networks (no dev roles found), Mogo (analytics/fraud roles only), Opus One Solutions (generic SWE reference), Mojio (no specific roles), NDAX (blockchain/DevOps/QA only), Vessel (no openings found), GitLab (frontend roles exist generally but no specific current Canada opening confirmed), SWTCH Energy (old posting from 2020), Blockstream (firmware/C/Python only), Peak Power (data analyst only), Waabi (SWE roles are backend/ML focused, no frontend), CrowdStrike (no full-time frontend in Canada), Sanctuary AI (SWE roles not frontend-specific), ChargeLab (Senior SWE posted but insufficient details to confirm frontend).

## Details Fetch Failures

| Company | URL | Failure Reason |
|---------|-----|----------------|
| Samsara | samsara.com/careers | SPA — career page does not render individual job listings via direct URL navigation |
| Edgecom Energy | applytojobs.ca | Egress blocked for WebFetch; Chrome not tested |
| BrainBox AI | builtinmontreal.com | Egress blocked; listing only from WebSearch |
| d1g1t | d1g1t.com/careers | Career page URL only, no direct ATS link found |
| VEERUM | veerum.com/careers | Career page URL only |
| dcbel | dcbel.energy/careers | Career page URL only |

All 12 added vacancies have `score_confidence: "low"` and `details_status: "SPA"` or `"Listing only"` — recommend Chrome enrichment in a follow-up session for the top 5 vacancies (Samsara x2, d1g1t, Elastic, Geotab).

## Salary Data Points

| Company | Range | Context |
|---------|-------|---------|
| Shakepay | CAD 170K-220K + equity | Senior SWE (backend), Remote Canada |
| d1g1t | CAD 75K-135K (Glassdoor est.) | Senior Frontend, Toronto — below market if accurate |
| CrowdStrike | CAD 130K-210K + equity | Senior SWE Auth, Remote Canada |

## Notable Observations

1. **Samsara is the standout** — two active Canada-remote frontend roles with React/TypeScript/GraphQL stack. Perfect profile match for IoT dashboards. Both scored 80+.

2. **Several positions closed since user's research**: Mappedin (all 3 roles), Float Financial (portal closed), Survalent .NET/React role. Research may be 2-4 weeks stale for some companies.

3. **Shakepay disappointing for frontend**: All 3 Senior SWE roles are backend/full-stack (Node.js, Postgres). No dedicated frontend positions despite being a consumer-facing app company.

4. **d1g1t is a hidden gem** for the candidate — entire product is financial analytics dashboards, which maps directly to monitoring dashboard experience. Salary seems low for Toronto.

5. **Montreal cluster weakened**: BrainBox AI and Prevu3D have openings but both are full-stack roles with mentoring/leadership expectations that are candidate gaps. dcbel uses Blazor (not React).

6. **Full-stack backend weight** is a recurring issue: Geotab (C#/ASP.NET), Brickeye (Python FastAPI), CoLab (cross-platform), Prevu3D (Unity/Python/C++) all expect significant backend work. Candidate should carefully evaluate backend expectations before applying.

7. **Recommended immediate actions**: Apply to Samsara (both roles — highest match). Research d1g1t to confirm tech stack and salary. Monitor Elastic for Kibana-specific frontend roles beyond security team.
