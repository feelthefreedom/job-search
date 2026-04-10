# Source 1 Report — 2026-04-06

## Run Summary

- **Date**: 2026-04-06
- **Source**: Bucket 1 (Web Search)
- **Queries executed**: ~25 across Google ATS (Greenhouse, Lever, Ashby), LinkedIn, Indeed Canada, WeWorkRemotely, HN Hiring, company careers pages
- **New vacancies found**: 32
- **Duplicates skipped**: 4
- **Auto-skipped (Staff level)**: 2 (Grafana Labs Staff positions)
- **Details fetch status**: All `no_chrome` — WebFetch blocked for all job board domains (greenhouse.io, lever.co, ashbyhq.com, weworkremotely.com, sentry.io, linear.app), Chrome unavailable in this session

## Top 10 New Vacancies by Match Score

1. **[87]** Grafana Labs — Full Stack Engineer, Grafana Partner Datasources
   - Location: Canada, Remote | Canada: yes | Stack: Go, React, TypeScript
   - CAD 120K-145K
   - Direct: Grafana observability ecosystem. Adjacent: Go backend is a gap but frontend part matches. Canada confirmed with CAD salary.
   - URL: https://job-boards.greenhouse.io/grafanalabs/jobs/5650614004

2. **[84]** Observe Inc. — Software Engineer: Frontend
   - Location: Remote | Canada: yes | Stack: React, TypeScript
   - Salary: not disclosed
   - Direct: observability SaaS tool = monitoring dashboards for troubleshooting. 'Powerful enough for experts' = data-dense operational UI. Strong match.
   - URL: https://jobs.ashbyhq.com/observeinc/a3cabf2e-7a45-4ec2-9441-e30475f552c8

3. **[81]** ClickHouse — Frontend Engineer - HyperDX
   - Location: Remote | Canada: yes | Stack: TypeScript, React
   - Salary: not disclosed
   - Direct: HyperDX is open-source observability — directly maps to monitoring dashboard experience. Telemetry data = data pipeline monitoring. Strong product fit.
   - URL: https://job-boards.greenhouse.io/clickhouse/jobs/5832420004

4. **[77]** WorkOS — Product Engineer - Enterprise
   - Location: Remote (US) | Canada: yes | Stack: TypeScript, React
   - USD 175K-250K
   - Direct: B2B enterprise product with complex UI. RBAC/permissions align with candidate's data platform access control experience. Strong product fit.
   - URL: https://jobs.lever.co/workos/44f9572c-8502-4e07-9627-ed8848001d15

5. **[77]** Honeycomb.io — Senior Software Engineer I - Frontend Observability
   - Location: Remote | Canada: yes | Stack: React, TypeScript
   - Salary: not disclosed
   - Direct: observability domain maps to candidate's monitoring dashboard experience. Frontend observability (Core Web Vitals) aligns with testing/performance focus.
   - URL: https://job-boards.greenhouse.io/honeycomb/jobs/4824807008

6. **[73]** Materialize — Senior Front End Engineer (React/Typescript)
   - Location: Remote | Canada: yes | Stack: React, TypeScript
   - Salary: not disclosed
   - Direct: streaming database = data platform, monitoring dashboards. Candidate's dashboard + data pipeline monitoring experience is directly relevant.
   - URL: https://boards.greenhouse.io/materialize/jobs/4964179004

7. **[73]** Veeva Systems — Senior Software Engineer - React and Typescript
   - Location: Toronto/Remote | Canada: yes | Stack: React, TypeScript
   - Salary: not disclosed
   - Adjacent: enterprise platform UI for pharma/healthcare is similar to government data platform work. Complex domain, B2B product. Toronto = Canada eligible.
   - URL: https://jobs.lever.co/veeva/75bce668-2e37-4c78-9a0d-2fc94369f256

8. **[73]** FutureHouse — Frontend Software Engineer
   - Location: Remote | Canada: yes | Stack: React, TypeScript, D3.js, Deck.gl, Three.js
   - Salary: not disclosed
   - Direct: data visualization focus matches Recharts/xyflow experience. Real-time data handling aligns with pipeline monitoring work.
   - URL: https://job-boards.greenhouse.io/futurehouse/jobs/4824588007

9. **[71]** Augment Code — Frontend Engineer, Tech Lead
   - Location: Remote | Canada: yes | Stack: TypeScript, React
   - Salary: not disclosed
   - Adjacent: devtools/IDE experience is new but candidate's testing/CI tooling knowledge transfers. 7+ years required is a stretch for 5 years experience.
   - URL: https://job-boards.greenhouse.io/augmentcomputing/jobs/4814733008

10. **[69]** Topstep — Senior Frontend Engineer
   - Location: Remote | Canada: yes | Stack: React, TypeScript, D3.js, Recharts
   - Salary: not disclosed
   - Direct: Recharts is in candidate's stack. Real-time data + charting/dashboards directly match monitoring dashboard experience.
   - URL: https://job-boards.greenhouse.io/topsteptrader/jobs/7641646003

## Entries Needing Detail Fetch (Retry with Chrome)

ALL 32 entries have `details_status: no_chrome`. WebFetch was blocked for all job board domains in this session. These should be retried in a session with Chrome browser access to:
1. Fetch full job descriptions
2. Upgrade `score_confidence` from "low" to "high"
3. Extract accurate tech stack, salary, experience, and Canada eligibility signals
4. Re-score with full description data

## Salary Data Points Found

- **Grafana Labs (Canada)**: CAD 120K-145K (Full Stack, Partner Datasources)
- **WorkOS (US)**: USD 175K-250K (Product Engineer)
- **Ocrolus Inc. (US)**: ~USD 180K + equity (Senior Frontend)
- **Branch (US)**: USD 135K-145K (Frontend Engineer)
- **Grafana Labs (Canada, Staff)**: CAD 174K-209K (auto-skipped, Staff level)

## Notable Observations

1. **Observability/monitoring cluster remains strong**: Grafana, Honeycomb, Observe Inc., ClickHouse/HyperDX, Postman all have frontend openings. This is the candidate's strongest domain match.
2. **Grafana Labs has multiple Canada-remote positions** across observability, k6, and partner datasources — including non-Staff roles.
3. **Data visualization roles increasing**: FutureHouse, Topstep, Celonis, Robinhood all specifically seek D3/charting frontend engineers.
4. **Developer tools segment growing**: ClickHouse/HyperDX, HTTPie, Augment Code, Bolt.new all building complex frontend UIs for dev audiences.
5. **WorkOS Product Engineer** at USD 175K-250K is notable B2B auth/identity platform with enterprise complexity that maps to candidate's RBAC-adjacent experience.
6. **Knack (no-code database)** is a strong product fit for schema-driven configurator experience.
7. **All job board domains blocked by egress proxy** — future runs need Chrome browser access for full description fetching.
