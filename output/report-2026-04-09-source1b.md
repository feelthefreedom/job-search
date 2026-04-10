# Source 1 (Web Search) Report — 2026-04-09

## Run Summary

- **Date**: 2026-04-09
- **Source**: Bucket 1 — Web Search (Google ATS, LinkedIn via Google, company career pages, job boards)
- **Queries executed**: ~30 search queries across Greenhouse, Lever, Ashby, LinkedIn, Indeed, WeWorkRemotely, HN Hiring, and company career pages
- **New vacancies added**: 4
- **Duplicates skipped**: 284+ (database already very comprehensive at 288 entries)
- **Auto-skipped (Staff level)**: 5 (Grafana K6, Grafana Observability, Luxury Presence, Owner.com, Remote.com)
- **Auto-skipped (geography)**: 2 (OnHires — Europe only, Vannevar — US citizens/ITAR only)
- **Auto-skipped (full-stack backend-heavy)**: 1 (Toast — Delivery Services integrations)

## New Vacancies by Match Score

| # | Score | Company | Position | Canada | Salary | Summary |
|---|-------|---------|----------|--------|--------|---------|
| 1 | **75** | OpenTable | Frontend Engineer II - Hospitality | ✅ yes | CAD 100K-125K + equity | Perfect seniority (3+ years), React/TS/Redux/GraphQL, RTL+Cypress testing, remote Canada. Strong direct match. |
| 2 | 56 | Rippling | SE II - Growth (Fullstack Frontend Leaning) | ❓ unclear | — | Good level match (SE II), well-known unicorn. LinkedIn listing only — needs review for Canada eligibility and frontend weight. |
| 3 | 50 | Gametime | Senior Frontend Engineer (Web-first, Cross-Platform) | ❓ unclear | USD 170K-201K | React + React Native cross-platform. RN experience is direct match. US Remote listing — Canada eligibility unclear. |
| 4 | 44 | DuckDuckGo | Senior Frontend Engineer, React/TypeScript | ✅ yes | USD 178.5K | Canada eligible, strong comp. But 7+ years required vs candidate's 5 is a stretch. Consumer search product ≠ data platform domain. |

## Entries with Fetch Issues

| Company | Position | Status | Reason |
|---------|----------|--------|--------|
| Rippling | SE II - Growth | Listing only | LinkedIn URL, no ATS direct link found. May be stale (originally posted Aug 2025). |

## Staff-Level Positions Noted (Auto-Skipped)

These were found during search but excluded per level rules. Noted for awareness:

- **Grafana Labs** — Staff Front End Engineer, Grafana K6 (Canada Remote, CAD 174K-209K). Only requires 2 years React experience despite Staff title.
- **Grafana Labs** — Staff Frontend Engineer, Observability Cloud (Canada Remote, CAD 174K-209K).
- **Luxury Presence** — Staff Frontend Engineer, Canada Remote. React 18/19, micro-frontends, 8+ years required.
- **Owner.com** — Staff Software Engineer, Full-Stack (US/Canada Remote, USD 190K-230K). React/Next.js.
- **Remote.com** — Staff Frontend Engineer (10+ years required).

## Notable Observations

### Market Signals
- **OpenTable is the standout find** this run — perfect seniority match (Engineer II), confirmed Canada remote (Vancouver), full React/TS/GraphQL stack, RTL+Cypress testing aligns with candidate's testing setup experience. CAD 100K-125K is in the "local Montreal" range.
- **Heavy dedup** — 284 out of ~288 search results were already tracked. Database coverage for ATS boards (Greenhouse, Lever, Ashby) is now very mature.
- **Staff-level positions dominate** Canada remote offerings at top companies (Grafana, Luxury Presence). The mid-level Canada market is thinner.

### Salary Data Points
- OpenTable: CAD 100K-125K + equity + bonus (Canada remote, mid-level) — low end of "US companies, Canadian rates" range
- Grafana: CAD 174K-209K (Canada remote, Staff) — top reference
- DuckDuckGo: USD 178.5K (remote, Senior) — strong for US remote
- Gametime: USD 170K-201K (US remote, Senior) — strong

### Search Coverage
All query groups from `sources/1-websearch.md` were executed: Core ATS, Niche ATS, LinkedIn via Google, Company-specific, Indeed Canada, Alternative Titles, Domain Expansion (compliance, healthcare, supply chain, AI tools), Workflow Products, and Job Boards (HN Hiring, WeWorkRemotely).
