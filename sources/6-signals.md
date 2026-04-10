# Bucket 6: Hiring Signals (Pre-Vacancy Detection)

Method: WebSearch + WebFetch + Chrome | Manual trigger only
Budget: Free tools only

## Purpose

Find companies that are likely to hire a frontend engineer in the next 2-6 months, BEFORE the job post exists. The output is companies with evidence, not vacancies.

## Signal Chain Logic

Funding announcement → leadership hires → adjacent roles (backend, design) → IC frontend role.
Each stage is 4-12 weeks apart. We want to detect stages 1-3.

## Phase 1: Funding Signals (~10 min)

Search for recent funding rounds in target sectors.

### Crunchbase via Google (free workaround)

```
site:crunchbase.com "Series A" fintech 2026
site:crunchbase.com "Series B" fintech 2026
site:crunchbase.com "Series B" "developer tools" 2026
site:crunchbase.com "Series B" observability 2026
site:crunchbase.com "Series A" OR "Series B" "data platform" 2026
site:crunchbase.com "Series B" OR "Series C" healthcare tech 2026
site:crunchbase.com "Series A" OR "Series B" workflow automation 2026
site:crunchbase.com "Series B" compliance fintech 2026
site:crunchbase.com "Series A" OR "Series B" logistics "supply chain" 2026
site:crunchbase.com "Series A" OR "Series B" "AI" "machine learning" tooling 2026
site:crunchbase.com "Series A" OR "Series B" "internal tools" OR "admin" OR "operations platform" 2026
site:crunchbase.com "Series A" OR "Series B" Canada tech 2026
site:crunchbase.com "Series B" OR "Series C" Montreal OR Toronto 2026
site:crunchbase.com "Series A" OR "Series B" robotics 2026
site:crunchbase.com "Series A" OR "Series B" "autonomous" OR "self-driving" 2026
site:crunchbase.com "Series A" OR "Series B" IoT OR "connected devices" 2026
site:crunchbase.com "Series A" OR "Series B" "industrial automation" OR manufacturing 2026
site:crunchbase.com "Series A" OR "Series B" "embedded" OR "firmware" OR "hardware" 2026
site:crunchbase.com "Series A" OR "Series B" EDA OR "electronic design" OR semiconductor 2026
```

Replace `2026` with current year. Focus on Series A ($10M+) and Series B ($20M+) — these are the rounds where engineering hiring scales.

### TechCrunch / BetaKit via Google

```
site:techcrunch.com "raises" OR "raised" fintech frontend 2026
site:techcrunch.com "raises" OR "raised" "developer tools" 2026
site:techcrunch.com "raises" OR "raised" observability OR monitoring 2026
site:techcrunch.com "raises" OR "raised" logistics OR "supply chain" 2026
site:techcrunch.com "raises" OR "raised" "AI tools" OR "annotation" OR "labeling" 2026
site:betakit.com "raises" OR "raised" OR "funding" Montreal OR Toronto OR Canada 2026
site:betakit.com "series" Montreal OR Toronto 2026
```

### General funding news

```
"series B" fintech Canada hiring 2026
"series B" "developer tools" remote hiring 2026
"raised" "$" million "data platform" OR "observability" OR "workflow" 2026
startup funding Montreal OR Toronto engineering 2026
```

### For each funding result:
1. Note company name, amount, stage, investors, date.
2. WebFetch the funding article — look for quotes about hiring plans ("tripling the team", "expanding engineering", "opening Toronto office").
3. WebFetch the company's About/Careers page — check for tech stack signals (React, TypeScript on site or in existing postings).
4. Record in signals.json per `database/signals-schema.md`.

## Phase 2: Leadership Hire Signals (~10 min)

New engineering leaders = team expansion incoming.

### LinkedIn via Google

```
site:linkedin.com "VP of Engineering" OR "Head of Engineering" started fintech 2026
site:linkedin.com "VP of Engineering" OR "Head of Engineering" started "developer tools" 2026
site:linkedin.com "VP of Engineering" OR "Director of Engineering" started observability 2026
site:linkedin.com "VP of Engineering" started Montreal OR Toronto 2026
site:linkedin.com "Head of Frontend" OR "Frontend Lead" started 2026 fintech OR devtools
```

### Company blog / Twitter via Google

```
"joined as" "VP of Engineering" OR "Head of Engineering" fintech 2026
"welcome" "engineering" "VP" OR "Director" site:twitter.com OR site:x.com 2026
```

### For each leadership hire result:
1. Identify the company and the hire's role.
2. Check if the company is in a target sector.
3. WebFetch the company careers page — are there already open engineering roles?
4. Record in signals.json with `signal_type: "leadership_hire"`.

## Phase 3: Adjacent Role Signals (~10 min)

Backend + design roles without frontend = frontend is next.

### Google ATS — backend/design without frontend

```
site:greenhouse.io "backend engineer" OR "product designer" fintech -"frontend" 2026
site:lever.co "backend engineer" OR "product designer" "developer tools" -"frontend" 2026
site:greenhouse.io "backend engineer" React OR TypeScript fintech 2026
site:ashbyhq.com "software engineer" "backend" fintech Canada 2026
```

### LinkedIn adjacent roles

```
site:linkedin.com/jobs "backend engineer" OR "product designer" fintech Montreal OR Toronto OR "remote Canada"
site:linkedin.com/jobs "backend engineer" "developer tools" OR observability remote
site:linkedin.com/jobs "product designer" data platform OR workflow
```

### Hardware-adjacent role signals (Source 8 cross-feed)

These job titles indicate a hardware/embedded/robotics company is actively building. If they're hiring these roles but have NO frontend posting — frontend is often next (they'll need dashboards, control UIs, monitoring panels).

**Title triggers** — if a company posts any of these, it's a signal:

```
"embedded software engineer" OR "junior embedded software" OR "firmware developer"
"hardware integration specialist" OR "systems integration specialist"
"automation engineer" OR "controls engineer"
"test engineer" hardware OR embedded OR "validation engineer"
"avionics" OR "safety software" OR "safety-critical"
"robotics integration" OR "robot software" OR "ROS engineer"
"FPGA engineer" OR "ASIC designer" OR "hardware engineer"
```

**Google ATS — hardware roles as signals**

```
site:greenhouse.io "embedded software" OR "firmware" OR "hardware engineer" Canada 2026
site:lever.co "controls engineer" OR "automation engineer" OR "robotics" Canada 2026
site:greenhouse.io "systems integration" OR "test engineer" hardware Canada 2026
site:linkedin.com/jobs "embedded software engineer" Montreal OR Toronto OR "remote Canada"
site:linkedin.com/jobs "firmware developer" OR "hardware engineer" Montreal OR Toronto OR Quebec
site:linkedin.com/jobs "automation engineer" OR "controls engineer" OR "robotics" Montreal OR Toronto
site:linkedin.com/jobs "avionics" OR "safety software" Montreal OR Toronto OR Canada
```

**Processing**: These are NOT vacancies for the candidate — do NOT add to job-tracker.xlsx. Instead:
1. Identify the company.
2. Check if they also have frontend roles → if yes, Source 1-5/8 will handle it.
3. If no frontend role → record as signal with `signal_type: "adjacent_role"` and note the hardware role in `adjacent_roles` array.
4. These companies are strong candidates for proactive outreach — they need UI but may not know it yet.

### For each adjacent role result:
1. Check company — do they already have a frontend posting? If yes, skip (Sources 1-5 will handle it).
2. If no frontend posting — this is a signal. The company is building but hasn't posted frontend yet.
3. WebFetch company careers page to confirm no frontend role exists.
4. Record in signals.json with `signal_type: "adjacent_role"`.

## Phase 4: Product Launch / Tech Stack Signals (~5 min)

### Product Hunt

```
site:producthunt.com fintech dashboard 2026
site:producthunt.com "developer tools" 2026
site:producthunt.com workflow automation 2026
site:producthunt.com data platform analytics 2026
```

### GitHub trending (for target companies)

```
site:github.com grafana OR temporal OR retool OR sentry new repository 2026
```

### Hacker News Show HN

```
site:news.ycombinator.com "Show HN" fintech dashboard
site:news.ycombinator.com "Show HN" "developer tool" OR devtool
site:news.ycombinator.com "Show HN" workflow OR automation
```

### For each product launch result:
1. Is the company in a target sector?
2. Does the product involve frontend-heavy work (dashboards, workflows, data visualization)?
3. WebFetch careers page — are they hiring?
4. Record in signals.json with `signal_type: "product_launch"`.

## Phase 5: Canada-Specific Signals (~5 min)

### Office expansions and Canadian hiring

```
"opening office" Montreal OR Toronto tech 2026
"expanding to Canada" startup engineering 2026
"hiring in Canada" fintech OR "developer tools" OR observability 2026
site:betakit.com hiring OR "new office" OR expanding Montreal OR Toronto 2026
```

### For each Canada signal:
1. If company is already in signals.json, update `canada_signals` array.
2. If new company, create full entry.

## Processing Rules

1. **Dedup**: Check `output/signals.json` before adding. If company exists, update — don't duplicate.
2. **Cross-check companies-list.md**: If company is already monitored in Source 3, still add to signals.json but note it in `notes` field.
3. **Sector filter**: Skip companies outside target sectors unless the signal is very strong (e.g., Montreal company, Series B+, React stack confirmed).
4. **Minimum signal strength**: Don't add companies with only vague signals. Need at least: known funding stage OR confirmed adjacent role OR leadership hire with date.
5. **After all phases**: Run `flows/qualify-signal.md` on every new/updated entry to set `qualification` and `action`.

## Report

After completing all phases, output a summary:
- New companies added: [count]
- Existing companies updated: [count]
- Hot leads: [list company names with qualification = "hot"]
- Recommended actions: [list companies with action = "outreach_ready" or "research_deeper"]
