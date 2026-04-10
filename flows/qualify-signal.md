# Flow: Qualify Signal (Source 6)

Load before qualifying: `data/profile.md`, `data/companies-list.md`, `data/geography.md`, `database/signals-schema.md`.

## Purpose

Evaluate each company from Source 6 and assign a qualification level (`hot`, `warm`, `cold`, `disqualified`) and a recommended action. This is NOT vacancy scoring — it's company-level assessment of "will they hire a frontend engineer I can reach in Canada?"

## Qualification Rubric

Evaluate three dimensions independently, then combine.

### Dimension 1: Sector Fit (how well does this company's product match candidate's strengths?)

<sector_fit>

**Strong fit** — company builds products where candidate has direct experience:
- Observability / monitoring dashboards
- Data platforms / data-dense operational UIs
- Developer tools / devtools
- Internal tools / admin panels / workflow builders
- Fintech dashboards / controls / backoffice

**Moderate fit** — adjacent to candidate's experience:
- Healthcare operations platforms
- Supply chain / logistics dashboards
- AI tooling / annotation / human-in-the-loop
- Compliance / risk management UIs
- B2B SaaS with complex UI (not CRUD)

**Strong fit (hardware-adjacent)** — candidate's ХНУРЭ/ХРТТ education gives domain advantage:
- EDA / schematic tools / PCB design platforms
- Robotics dashboards / fleet management / teleoperation UI
- Automotive / ADAS / connected car platforms
- Industrial automation / SCADA / HMI / factory dashboards
- IoT platforms / device management / digital twin
- Telecom / RF / network monitoring
- Embedded device management / firmware OTA dashboards
- Test & measurement / instrumentation UI

Note: These are "Strong fit" because candidate understands the domain from education, even though professional frontend experience is in data platforms. A hardware company hiring frontend is likely building dashboards/UIs where this background is a rare advantage.

**Weak fit** — far from candidate's experience:
- Consumer mobile apps
- E-commerce storefronts
- Marketing tech / CMS
- Gaming (non-tooling)
- Simple CRUD SaaS

</sector_fit>

### Dimension 2: Canada Eligibility (can the candidate actually work there?)

<canada_eligibility>

**High confidence** — strong Canada signals:
- HQ or office in Canada (Montreal, Toronto, Vancouver)
- "Remote Canada" or "Remote North America" on careers page
- RRSP, Canadian benefits mentioned
- Already in `data/companies-list.md` as confirmed Canada-hiring
- Multiple Canadian employees visible on LinkedIn

**Medium confidence** — mixed signals:
- "Remote" without geographic restriction
- US-based but known to hire internationally
- No Canada-specific signals but no US-only signals either

**Low confidence** — negative signals:
- "US only" or "US timezone only" on careers page
- Security clearance mentioned
- No evidence of non-US hiring
- Very early stage (<10 employees, all in one US city)

**Disqualified**:
- Explicitly "US citizens only"
- Government contractor requiring clearance
- Agency / consulting / body shop

</canada_eligibility>

### Dimension 3: Signal Strength (how likely is imminent frontend hiring?)

<signal_strength>

**Strong signal** — high likelihood of frontend hire within 3 months:
- Series B+ ($20M+) with public statements about team growth
- VP/Head of Engineering hired in last 60 days
- Backend + Design roles posted (frontend gap)
- Company explicitly mentions "building new frontend" or "rebuilding UI"
- Multiple engineering roles posted simultaneously

**Moderate signal** — possible frontend hire within 6 months:
- Series A ($10M+) in target sector
- Engineering leadership hire (not necessarily VP)
- One adjacent role posted (backend OR design, not both)
- New product launch that is frontend-heavy
- Headcount growth 20%+ on LinkedIn

**Weak signal** — speculative, >6 months out:
- Seed/early funding in target sector
- Product launch but no hiring signals
- Tech stack change detected but no open roles
- Vague "we're growing" statements

</signal_strength>

## Combining into Qualification

| Sector Fit | Canada Eligibility | Signal Strength | → Qualification |
|-----------|-------------------|-----------------|-----------------|
| Strong | High | Strong | **hot** |
| Strong | High | Moderate | **hot** |
| Strong | Medium | Strong | **hot** |
| Strong | Medium | Moderate | **warm** |
| Moderate | High | Strong | **warm** |
| Moderate | High | Moderate | **warm** |
| Strong | Low | Strong | **warm** |
| Moderate | Medium | Moderate | **warm** |
| Any | Low | Moderate | **cold** |
| Weak | Any | Any | **cold** |
| Any | Any | Weak | **cold** |
| Any | Disqualified | Any | **disqualified** |
| Weak | Low | Weak | **disqualified** |

When the combination doesn't exactly match the table, use judgment. The table covers the most common cases.

## Qualification → Action Mapping

| Qualification | Action | What to do |
|--------------|--------|------------|
| **hot** | `outreach_ready` | Add to `companies-list.md` + `3-companies.md`. Prepare for cold outreach — find engineering lead on LinkedIn. |
| **warm** | `research_deeper` | Investigate further: check careers page, LinkedIn headcount, tech stack. May upgrade to hot after research. |
| **cold** | `monitor` | Keep in signals.json. Re-check in 4-6 weeks. |
| **disqualified** | `no_action` | Keep in signals.json for record. Don't spend more time. |

## Writing qualification_reason

Write 1-2 sentences explaining the qualification decision. Reference specific evidence.

### Good examples:
- "Hot: Series B ($40M) fintech with Toronto office, React/TypeScript on careers page, backend engineer posted last week but no frontend yet. VP of Engineering joined 2 months ago."
- "Warm: Series A observability startup, confirmed remote-friendly, but only 15 employees and no adjacent roles yet. Sector fit is strong — monitor for backend/design hires."
- "Cold: Interesting dev tools company but US-only hiring, seed stage, no React in stack. Too many unknowns."
- "Disqualified: Government contractor, requires US security clearance."

### Bad examples (too vague):
- "Looks promising" — no evidence cited
- "Good company" — doesn't explain why
- "Not sure" — must commit to a qualification level

## Updating Existing Entries

When re-running Source 6 and a company already exists in signals.json:
1. Check for new signals (new funding, new roles posted, leadership changes).
2. Append new info to `signal_detail` and relevant arrays (`canada_signals`, `tech_signals`, `adjacent_roles`).
3. Re-evaluate qualification — it can go up or down based on new evidence.
4. Update `last_checked` to today's date.
5. If qualification changed, update `qualification_reason` to explain the change.
