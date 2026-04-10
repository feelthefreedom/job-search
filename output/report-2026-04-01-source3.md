# Source 3 Report — 2026-04-01

## Run Summary

- **Source executed**: Bucket 3 (Target Companies)
- **New vacancies added**: 11
- **Duplicates skipped**: 0
- **Companies checked**: 17 (15 Priority + 2 Low Priority)
- **VC portfolios checked**: 2

## Top New Vacancies by Score

| # | Score | Conf | Position | Company | Canada | URL |
|---|-------|------|----------|---------|--------|-----|
| 1 | 82 | high | Senior / Staff Fullstack Engineer | Linear | unclear | [link](https://linear.app/careers/d3bc1ced-3ce4-4086-a050-555055dbb1ff) |
| 2 | 81 | high | Senior / Staff Product Engineer | Linear | unclear | [link](https://linear.app/careers/069c4628-88d7-4e4d-b393-c996fc7f3076) |
| 3 | 79 | low | Sr SWE (Mobile), Front-End Operations | Wealthsimple | yes | [link](https://jobs.lever.co/wealthsimple/aa60ba9b-62ef-454d-b813-6efeed6a04b5) |
| 4 | 76 | low | Sr FE Developer - UI Tools for DevEx | Coveo | yes | [link](https://www.coveo.com/en/company/careers/open-positions/research-and-development/senior-front-end-developer-ui-tools-for-developer-experience/5751469002) |
| 5 | 71 | low | Sr SWD, Product Engineering (Full Stack) | Wealthsimple | yes | [link](https://jobs.lever.co/wealthsimple/c2c01d96-26f6-4fb6-b10b-ee9f01cfa5a8) |
| 6 | 69 | low | Fullstack Software Developer | Coveo | yes | [link](https://www.coveo.com/en/company/careers/open-positions/research-and-development/fullstack-software-developer/4738330002) |
| 7 | 68 | low | Senior Front-End Software Developer | Coveo | yes | [link](https://www.coveo.com/en/company/careers/open-positions/research-and-development/senior-front-end-software-developer/5751530002) |
| 8 | 67 | low | Sr SWD - Product (Full Stack & Front-end) | Wealthsimple | yes | [link](https://jobs.lever.co/wealthsimple/b75a1dc5-a49f-4725-8b2f-cb76f4e47269) |
| 9 | 66 | low | Sr Fullstack SWE - Wealthsimple Tax | Wealthsimple | yes | [link](https://jobs.lever.co/wealthsimple/5cceba88-5c4c-4388-abbd-2e075f1f2d49) |
| 10 | 61 | low | Sr SWE - Growth Engineering | Wealthsimple | yes | [link](https://jobs.lever.co/wealthsimple/c3233d05-1649-42f8-bbdf-e778aeed6865) |
| 11 | 58 | high | Senior / Staff Product Engineer, AI | Linear | unclear | [link](https://linear.app/careers/b4a7764e-c680-4bdf-9956-dc78f2ca94d5) |

## Details Fetch Failures

Most company career sites were blocked by Chrome safety restrictions and network egress proxy during this run. Only Grafana Labs, Sentry, and Linear were fully accessible.

| Company | Status | Reason |
|---------|--------|--------|
| Mercury | blocked | Known blocked site |
| Ramp | blocked | Chrome safety restriction |
| Stripe | blocked | Known blocked site |
| Brex | blocked | Chrome + Greenhouse blocked |
| Coveo | no_chrome | Chrome + WebFetch blocked (3 roles found via WebSearch) |
| Shopify | blocked | Chrome + WebFetch blocked |
| 1Password | blocked | Ashby board blocked (no matching FE roles found via WebSearch) |
| Wealthsimple | no_chrome | Lever board blocked (4 roles found via WebSearch) |
| Honeycomb | blocked | No specific FE roles found via WebSearch |
| Monte Carlo | blocked | No FE roles found via WebSearch |
| LaunchDarkly | blocked | FE roles found but US-only (already have Guarded Releases in tracker) |
| Retool | blocked | FE roles exist but San Francisco / US-only |
| Datadog | blocked | Chrome blocked |
| Instacart | blocked | Chrome blocked |
| a16z Portfolio | blocked | Chrome blocked |
| Sequoia Portfolio | blocked | Chrome blocked |

## Companies Fully Checked (via Chrome)

| Company | Result |
|---------|--------|
| Grafana Labs | No frontend roles for Canada. All Canada positions are backend/infra (Staff SWE Databases, Staff SWE K8s, Sr SWE Knowledge Graph, etc.) |
| Sentry | No frontend roles. Canada jobs are Staff-level (Billing, Issue Workflow) or non-engineering (Technical Support Mgr, Android SDK, iOS SDK) |
| Linear | 3 new roles found: Product Engineer, Fullstack Engineer, Product Engineer AI. All use React/TS/GraphQL. Canada eligibility unclear — header says "North America" but body text varies between "US and Europe" vs "North America and Europe" |

## Notable Observations

1. **Linear has refreshed their job listings** — the existing Product Engineer listing (ea0b5868) has been replaced by 3 new distinct roles with different UUIDs, suggesting team restructuring or growth.

2. **Wealthsimple is hiring aggressively in 2026** — web search confirms they're "making bold investments across Engineering" with focus on Banking, Investing, and Financial Operating System. 4+ frontend-relevant roles open. All are confirmed Canada (remote-first, 1000+ employees coast to coast in North America).

3. **Coveo has multiple frontend openings in Quebec** — including a DevEx-focused role (UI Tools for Developer Experience) that aligns well with the candidate's internal tools background. Quebec location is ideal.

4. **LaunchDarkly has 7 frontend engineer openings** but all appear US-only. Worth monitoring for Canada expansion.

5. **Retool has a Frontend Engineer role** (React/TypeScript) but San Francisco-based. US-only per geography strategy (Bucket C, deprioritized).

6. **Chrome access issues were severe this run** — only 3 out of 17+ companies were accessible. Consider running blocked companies via a manual browser session or trying at different times.

## Action Items

- **High priority**: Verify Linear Canada eligibility — reach out or check if they have Canadian employees on LinkedIn
- **Medium priority**: Access Wealthsimple Lever listings and Coveo career pages manually to get full descriptions and improve score confidence
- **Monitor**: LaunchDarkly for Canada expansion, Retool for remote policy changes
