# Source 1 Report — Web Search (Bucket 1)
**Date:** 2026-04-09
**Bucket:** 1 (Google ATS, LinkedIn via Google, Company careers, Indeed, Job boards)

## Summary

- **Queries executed:** ~30 search queries across Google ATS (Greenhouse, Lever, Ashby), LinkedIn, company career pages, Indeed Canada, WeWorkRemotely, Remotive, HN Hiring
- **New vacancies found:** 21 (after dedup and exclusions)
- **Duplicates skipped:** ~50+ results already in database (267 existing URLs)
- **Exclusions applied:** 10 (7 pre-scoring: 4 Staff level, 1 backend-only, 1 referral/consulting, 1 UK-only; 3 at scoring: 2 agency/outsourcing, 1 non-React tech)

## Top Vacancies by Match Score

| # | Score | Position | Company | Canada | CV Fit |
|---|-------|----------|---------|--------|--------|
| 1 | 90 | Senior Software Engineer (Frontend), Core Product | Sentry | yes | ready |
| 2 | 80 | Senior Software Engineer – Data Visualization | Databricks | maybe | ready |
| 3 | 79 | Frontend Engineer, Payments and Risk | Stripe | yes | adapt |
| 4 | 71 | Software Engineer, Frontend Infrastructure (Workspace/IDE) | Replit | maybe | adapt |
| 5 | 70 | Senior Frontend Engineer | Gather AI | maybe | adapt |
| 6 | 70 | Senior Front End Engineer - International Contractor | Knack | maybe | ready |
| 7 | 68 | Senior Full-Stack Software Engineer, Codecov | Sentry | yes | adapt |
| 8 | 68 | Frontend Software Engineer (React & TypeScript) | Salsify | maybe | adapt |
| 9 | 68 | Software Engineer, Platform | Pallet | maybe | adapt |
| 10 | 67 | Software Engineer, Full-Stack | Loop | maybe | adapt |

### Quick Takes

1. **Sentry (90)** — Toronto office, observability/error monitoring product, React/TS + open-source codebase. Direct match to candidate's monitoring dashboard and real-time status tracking experience. Top priority.
2. **Databricks (80)** — Data visualization role, interactive visual experiences for data exploration. Flow diagrams + monitoring dashboards directly relevant. Check Canada hiring status.
3. **Stripe (79)** — Confirmed Canada-hiring (Toronto). Payments & Risk frontend. Enterprise-grade fintech with strong comp.
4. **Replit (71)** — IDE/workspace frontend infrastructure. Complex developer tools domain. Check Canada eligibility.
5. **Knack (70)** — No-code database/app builder. Schema-driven configurator experience is a direct match. International contractor — may hire Canada.
6. **Gather AI (70)** — Logistics/warehouse operational UIs. Adjacent to Randonizer logistics + Aker operational dashboards.

## Details Fetch Status

**All 21 vacancies marked `no_chrome`** — WebFetch was blocked for all job board domains (greenhouse.io, ashbyhq.com, lever.co, sentry.io, stripe.com, databricks.com, remotive.com). Chrome fallback was unavailable in this session. All scores have `score_confidence: "low"`.

**Recommendation:** Re-run description fetch in a session with Chrome enabled to upgrade score confidence for top candidates.

## Excluded Vacancies

### Pre-scoring exclusions (7)
- Staff Front End Engineer - Grafana K6 @ Grafana Labs — Staff level
- Staff Frontend Engineer - Observability @ Grafana Labs — Staff level
- Staff Frontend Engineer @ Databricks — Staff level
- Staff Frontend Engineer - AI Design Tooling @ Stripe — Staff level
- Senior Backend Engineer @ Prismatic — Backend role
- Lead Frontend Developer @ Thoughtworks — Referral-only board + consulting
- Senior Frontend Engineer - Grafana Incident Management @ Grafana Labs — UK-only timezone

### Scoring exclusions (3)
- Senior Full-Stack Engineer @ Provectus — Agency/outsourcing firm
- Senior Full Stack Engineer @ Smart Working Solutions — Staffing agency
- Senior Product Engineer @ Attio — Primary stack is Rust, no React

## Notable Observations

1. **Sentry has a new Frontend Core Product role** — Toronto office, open-source, React/TS. This is one of the strongest matches found in any source run to date. The Issues team (error monitoring) maps directly to candidate's monitoring dashboard experience.

2. **Databricks entering data viz hiring** — Senior-level data visualization role with React preference. Candidate's flow diagram + dashboard portfolio is uniquely suited.

3. **Stripe has a new Payments & Risk listing** (job ID 7325252, different from existing 6786210 in database). Worth checking if this is a new headcount or updated listing.

4. **Supply chain/logistics cluster** — Gather AI, Salsify, Pallet, Loop all hiring React frontend for logistics/supply chain products. This domain is growing and candidate has adjacent Randonizer experience.

5. **Design Engineer roles proliferating** — Tambo, Sierra Studio, Vetcove all listing "Design Engineer" titles. These tend to expect stronger design craft skills than candidate currently has, but Tambo's AI agent toolkit angle is interesting.

6. **No new salary data captured** this run due to egress blocking. Known reference: Kindred $170-220K USD (USA only).

7. **Knack international contractor model** — Worth investigating as alternative hiring arrangement for Canada-based candidate at US companies.

## Failed Sources

- **HN Hiring (hnhiring.com):** Blocked by egress proxy. April 2026 postings were not fetched.
- **WebFetch:** All job board domains blocked. 21/21 vacancies have `details_status: "no_chrome"`.

## Database Stats

- Rows before: 268 (including header)
- Rows after: 289
- Total unique vacancies in database: 288
