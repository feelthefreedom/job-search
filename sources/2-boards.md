# Bucket 2: Job Boards

Method: Chrome | ~20-30 min

## Title Variants Rule

Every board with free-text search MUST run the full Primary list from `data/title-variants.md` as separate searches:

1. Frontend Engineer
2. Front-End Engineer
3. Front End Engineer
4. Software Engineer - Frontend
5. Software Engineer, Frontend
6. Senior Frontend Engineer
7. Frontend Engineer II
8. Software Engineer II, Frontend
9. Product Engineer
10. Senior Product Engineer

If the platform allows additional searches without significant time cost, also run the Alternative list:

11. Full Stack Engineer (frontend-leaning)
12. Data Visualization Engineer
13. Application Engineer
14. Web Application Engineer
15. React Developer
16. Software Engineer, Frontend Platform
17. Frontend Platform Engineer
18. Frontend Engineer, UI Platform
19. UI Engineer
20. Design Engineer
21. Design Systems Engineer
22. Software Engineer (filter for React in description)
23. Frontend Developer

**No board gets a custom subset.** If a board has free-text search, it gets the full list. If a board only has tag/category filters, scan results against the full list manually.

## Board Types

Boards fall into two categories based on how they support search:

- **Free-text search** → run each title variant as a separate search query
- **Browse/filter only** → apply broadest relevant filter, then scan all results against the full title variants list

## Boards

| Board | URL | Type | Filters | Notes |
|-------|-----|------|---------|-------|
| Wellfound | wellfound.com | Free-text search | B2B, Remote, Canada, Series B+. For Primary titles 1-10 also try filter: 51-200 employees | — |
| YC Work at a Startup | workatastartup.com | Free-text search | B2B, devtools, developer tools, data, infrastructure | — |
| Himalayas | himalayas.app | Free-text search | Timezone EST/Americas | — |
| devjobsscanner | devjobsscanner.com | Free-text search | Montreal + Remote, React | — |
| Monster | monster.ca | Free-text search | Canada / Remote | — |
| HN Hiring | hnhiring.com | Browse/filter | Filter by "react" tag | Scan all results against full title variants list. Also look for domain keywords: dashboard, visualization, observability, B2B, Canada, remote, TypeScript, compliance, healthcare, logistics, workflow, internal tools, AI tools |
| We Work Remotely | weworkremotely.com | Browse/filter | Programming category | Scan all results against full title variants list |
| Remotive | remotive.com/remote-jobs/software-dev | Browse/filter | Software Dev category | Scan all results against full title variants list |
| Built In Montreal | builtinmontreal.com | Browse/filter | Front End Engineering + Software Engineering categories | Scan all results against full title variants list |
| BetaKit Jobs | betakit.com/jobs | Browse/filter | Engineering roles | Scan all results against full title variants list |
| Key Values | keyvalues.com | Browse/filter | "Complex Problems" + "React" + "Remote" | Scan all results against full title variants list |
| MaRS Job Board | techjobs.marsdd.com/jobs?q=frontend | Browse/filter | — | Scan all engineering roles against full title variants list |
| Hired.com | hired.com | Passive | — | If account active: check for new inbound interview requests |
| Underdog.io | underdog.io | Passive | — | If account active: check weekly batch matches |
| NoDesk | nodesk.co | Free-text search | Remote, Engineering/Development category | — |
