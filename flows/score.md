# Flow: Score and Classify (Phase 4)

Load before scoring: `data/profile.md`, `data/companies-list.md`, `data/geography.md`.
`data/exclusions.md` should already be in context from the search phase. If running Score standalone, load it too.

## Scoring Rubric (0–100)

Sum points from each category. Cap at 100.

<scoring_rubric>

### Tech Stack (max 30)
- React as primary framework: +15
- TypeScript required or preferred: +10
- GraphQL mentioned: +5
- Vue/Angular only (no React): skip by default. **Override**: if company is confirmed Canada-hiring (from `data/companies-list.md`), do NOT skip — cap Tech Stack at +10 max (TypeScript +10, no React bonus, no GraphQL bonus). Candidate is open to non-React frameworks at strong companies.

### Product Domain (max 25)
- Observability / monitoring / APM: +10
- EDA / schematic tools / PCB design UI: +10
- Robotics UI / fleet management / device control dashboards: +9
- Automotive / ADAS / connected car / vehicle dashboards: +9
- Industrial automation / SCADA / PLC / HMI panels: +9
- Embedded systems management / firmware OTA / device lifecycle UI: +8
- Design tools / collaborative editors / canvas products (Figma-like, Miro-like): +10
- Developer tools / devtools / developer platforms: +9
- Low-code / no-code / visual builder platforms: +9
- Pipeline / workflow builder UI (DAG editors, orchestration): +9
- Data visualization / dashboards / analytics: +8
- IoT platform / connected device management / digital twin: +8
- Telecom / RF / network monitoring / signal visualization: +8
- Test & measurement / lab equipment UI / instrumentation: +7
- Fintech / payments / banking UI: +7
- Internal tools / admin panels / platform UI: +7
- B2B / enterprise product: +5
- Simple marketing site / landing pages / CMS: -20

### Complexity Signals (max 20)
- "Complex UI" / "data-dense" / "real-time" / "performance-sensitive": +5
- RBAC / permissions / multi-tenant: +5
- Design system / component library: +4
- Graph visualization / node editor / canvas / custom rendering: +7
- CRDT / real-time collaboration / multiplayer editing: +6
- Schema-driven / dynamic forms / config-driven UI / visual config: +6
- Custom layout algorithms / hit testing / drag-and-drop architecture: +5
- Undo/redo stack / command pattern / state machine: +4
- "Own features end-to-end": +3
- Simple CRUD / basic forms only: -10

### Seniority Fit (max 15)
- Mid-level (3-6 years, SWE II, "Engineer II"): +15
- Senior (4-7 years, candidate can attempt): +12
- Junior (0-2 years): AUTO-SKIP
- Staff / Principal / 8+ years required: AUTO-SKIP (no exceptions)

### Geography and Eligibility (max 10)
- Montreal office or "Remote - Canada": +10
- Toronto / Vancouver office: +8
- "Remote" with confirmed Canada hiring (RRSP, CAD salary, known entity): +9
- "Remote" unspecified but no US-only signals: +5
- "US citizens only" / clearance / US relocation: 0, skip

### Company Signals (max 10)
- Confirmed Canada-hiring company (from `data/companies-list.md`): +8
- Series B+ startup: +5
- Well-known tech company: +4
- Unknown/early-stage: +2
- Agency / consulting / outsourcing: -10

### Domain Quality Tiebreakers
Observability: "trillions of data points", "real-time" → strong. "Marketing analytics" → weak.
Data viz: "D3.js", "interactive charts", "canvas" → strong. "Chart.js pie chart" → weak.
Devtools: "developer experience", "OSS" → strong. "WordPress plugin" → weak.
Internal tools: "admin panel", "workflow builder", "operations platform" → strong. "Agency work" → weak.
Fintech: "complex financial UI", "banking", "controls", "approval flows" → strong. "Crypto/NFT" → weak.
Workflow/automation: "workflow engine", "orchestration", "visual builder", "node editor", "pipeline builder" → strong. "Simple form wizard" → weak.
Healthcare ops: "clinical workflows", "EHR integration", "patient data platform", "operational dashboards" → strong. "Marketing site for clinic" → weak.
Supply chain/logistics: "real-time tracking", "fleet management", "inventory dashboards", "shipment visibility" → strong. "E-commerce storefront" → weak.
AI tooling: "annotation UI", "human-in-the-loop", "model evaluation", "labeling platform", "review interface" → strong. "ChatGPT wrapper" → weak.
EDA/hardware design: "schematic editor", "PCB viewer", "netlist", "component library browser", "design rule check UI", "interactive canvas" → strong. "Marketing site for hardware company" → weak.
Robotics: "robot fleet dashboard", "mission control", "teleoperation UI", "sensor visualization", "real-time device status" → strong. "Landing page for robotics startup" → weak.
Automotive: "ADAS visualization", "vehicle telemetry dashboard", "diagnostic UI", "fleet analytics", "connected car platform", "sensor fusion display" → strong. "Car dealership website" → weak.
Industrial automation: "SCADA dashboard", "PLC programming UI", "HMI panel", "factory floor monitoring", "process control visualization", "OPC-UA browser" → strong. "CRM for manufacturing company" → weak.
Embedded systems: "firmware update console", "device provisioning dashboard", "OTA management", "embedded diagnostics UI", "device lifecycle management" → strong. "Marketing site for chip company" → weak.
IoT/connected devices: "device management console", "firmware OTA dashboard", "sensor data visualization", "digital twin", "fleet provisioning" → strong. "Smart home marketing site" → weak.
Telecom/RF: "network topology visualization", "spectrum analyzer UI", "NOC dashboard", "signal monitoring", "cell tower management" → strong. "Telco billing portal" → weak.
Test & measurement: "instrument control panel", "waveform viewer", "test results dashboard", "lab automation UI" → strong. "QA tool for web apps" → weak.

</scoring_rubric>

## Phase 2: Resume Overlay (modifier −15 to +15)

After computing the rubric score, compare the vacancy's specific requirements against the candidate's actual experience from `data/profile.md`. This step adds nuance that a static checklist cannot capture.

<resume_overlay>

### Process

1. Extract the vacancy's top 3-5 concrete requirements (not generic "React experience" — look for specific tasks: "build dashboards", "design system ownership", "real-time data pipelines", "mobile app development", etc.).
2. For each requirement, check if the candidate has **direct experience** (did this exact thing), **adjacent experience** (did something similar), or **no experience** (gap).
3. Compute the modifier and write a 2-3 sentence `resume_match_summary` explaining what matched and what didn't.

### Modifier rules

- **Direct experience match**: the candidate's resume describes doing the same thing the vacancy asks for. Each direct match: +3 to +5.
- **Adjacent experience**: the candidate did something related but not identical. Each adjacent match: +1 to +2.
- **Experience gap**: the vacancy requires something the candidate has never done and cannot reasonably learn quickly (e.g., native iOS, ML engineering, backend-heavy infrastructure). Each significant gap: −3 to −5.
- **Full-stack backend weight**: if a full-stack role passed exclusion filtering but the description reveals significant backend expectations (>40% of responsibilities are backend), apply an additional −5 to −10 penalty. The candidate has no backend architecture experience and will not be competitive against full-stack candidates with backend depth.
- **Cap**: total modifier is capped at −15 to +15. Apply conservatively.

### What counts as direct experience (reference `data/profile.md`)

<candidate_strengths>

- Built frontend architecture from scratch (first commit → production)
- Schema-driven configurator reducing manual work from hours to minutes
- Interactive flow diagrams with @xyflow/react (data lineage, dependency tracking, real-time status)
- Monitoring dashboards (execution status, record volumes, error rates, multiple data sources)
- Automated testing setup (React Testing Library, Playwright, MSW, visual regression, CI)
- Cross-platform mobile app with React Native (interactive maps, 200+ locations)
- B2B/enterprise interfaces for government and private sector clients
- Data-dense operational UIs and internal tools

</candidate_strengths>

### What counts as experience gaps

<candidate_gaps>

- Backend-heavy roles (API design, database architecture, microservices)
- Machine learning / AI / data science
- Native iOS / Android (non-React-Native)
- DevOps / infrastructure / SRE
- Design system creation from scratch (used existing systems, didn't build one)
- Leadership / management / mentoring teams
- Performance engineering at massive scale (CDN, edge computing)

</candidate_gaps>

</resume_overlay>

## Phase 3: CV Fit Assessment

After computing the resume overlay, determine `cv_fit` — how much CV adaptation is needed for this vacancy. This is derived from the same resume overlay analysis but stored as a separate actionable field.

<cv_fit_rules>

### Decision logic

Use the resume overlay findings (direct matches, adjacent matches, gaps) to assign one of three values:

- **"ready"** — CV already covers the vacancy's key requirements well. The candidate's listed experience directly maps to what the job asks for. No keyword or emphasis changes needed. Typical when resume overlay is +5 or higher and no significant gaps.
- **"adapt"** — CV covers most requirements but needs tweaks: reorder bullet points to highlight relevant experience first, add domain-specific keywords from the job description, emphasize certain projects over others. Typical when resume overlay is −5 to +4, or when there are adjacent matches that need better framing.
- **"rewrite"** — CV has significant gaps relative to what the vacancy asks for. Would require creative reframing of experience or the gaps are too large to bridge with formatting alone. Consider whether the effort is worth it given the match_score. Typical when resume overlay is below −5 or when key requirements fall into `candidate_gaps`.

### Edge cases

- `score_confidence: "low"` → default to `"adapt"` (not enough info to judge precisely).
- Vue/Angular override vacancies → at least `"adapt"` (need to reframe React experience as transferable).
- If match_score < 40 and cv_fit would be "rewrite" → the combination signals "probably skip unless there's a specific reason to apply".

</cv_fit_rules>

## Scoring Rules

- **Three-phase scoring**: rubric score (0-100) + resume overlay modifier (−15 to +15) = final `match_score` + cv_fit assessment. Cap final score at 0 minimum, 100 maximum.
- Be conservative. 80+ = "almost certainly great fit." 50-79 = "worth reviewing." <50 = "weak match, included for completeness."
- Full description available → `score_confidence: "high"`.
- Only title/snippet available → assign preliminary score, `score_confidence: "low"`. Resume overlay is less reliable without full description — note this in `resume_match_summary`.
- Check `data/exclusions.md` — skip vacancies matching any auto-skip signal.

## Examples

<scoring_examples>

### Example 1: Strong match — 90 points
**Position:** Frontend Engineer, Observability Platform
**Company:** Grafana Labs | **Location:** Remote, Canada EST

| Category | Points | Reason |
|----------|--------|--------|
| Tech Stack | 30 | React +15, TypeScript +10, GraphQL +5 |
| Product Domain | 15 | Observability +10, B2B +5 |
| Complexity | 10 | "Real-time dashboards" +5, "high-cardinality" +5 |
| Seniority | 12 | Senior-leaning language, candidate can attempt |
| Geography | 10 | "Remote, Canada EST" confirmed |
| Company | 8 | Confirmed Canada-hiring |
| **Rubric subtotal** | **80** | |
| **Resume Overlay** | **+10** | Direct: built monitoring dashboards with multiple data sources (+5). Direct: real-time status tracking across 300+ data products (+5). No gaps. |
| **Final score** | **90** | |

`resume_match_summary`: "Strong direct match — candidate built monitoring dashboards combining execution status, record volumes, and error rates at Aker Systems, which maps directly to Grafana's observability platform work. Real-time data product tracking experience is directly relevant. No significant gaps."
`cv_fit`: **"ready"** — CV already highlights monitoring dashboards and real-time data tracking prominently. No adaptation needed.

### Example 2: Medium match — 58 points
**Position:** Software Engineer II, Frontend
**Company:** Cresta (Series C) | **Location:** Remote US/Canada

| Category | Points | Reason |
|----------|--------|--------|
| Tech Stack | 25 | React +15, TypeScript +10, no GraphQL |
| Product Domain | 5 | B2B enterprise +5, domain is AI sales (generic) |
| Complexity | 3 | "Own features end-to-end" +3 |
| Seniority | 15 | SWE II, 3+ years |
| Geography | 5 | "Remote US/Canada" but no explicit Canada signals |
| Company | 5 | Series C +5 |
| **Rubric subtotal** | **58** | |
| **Resume Overlay** | **0** | Adjacent: B2B enterprise experience (+2). Gap: AI/ML-adjacent product, candidate has no ML domain experience (−2). Net zero. |
| **Final score** | **58** | |

`resume_match_summary`: "B2B enterprise experience is adjacent but the AI sales domain is far from candidate's data platform background. No direct experience overlap with the specific product area. No hard gaps either — neutral overlay."
`cv_fit`: **"adapt"** — Reorder CV to lead with B2B enterprise experience and end-to-end ownership. Add "customer-facing product" framing. Domain mismatch (AI sales) can't be fixed by CV tweaks alone but general frontend skills transfer.

### Example 3: Weak match — 22 points
**Position:** Frontend Developer
**Company:** Unknown seed-stage | **Location:** Remote

| Category | Points | Reason |
|----------|--------|--------|
| Tech Stack | 15 | React +15, no TypeScript |
| Product Domain | 0 | E-commerce storefront |
| Complexity | -10 | Basic CRUD |
| Seniority | 15 | "2-4 years" mid-level |
| Geography | 5 | "Remote" no signals |
| Company | 2 | Unknown/early-stage |
| **Rubric subtotal** | **27** | |
| **Resume Overlay** | **−5** | Gap: e-commerce storefront is far from candidate's data platform / internal tools domain (−3). Gap: no complexity signals means candidate's strengths (flow diagrams, schema-driven UI, monitoring) are wasted (−2). |
| **Final score** | **22** | |

`resume_match_summary`: "No experience overlap — e-commerce storefront with basic CRUD doesn't leverage candidate's data platform, monitoring, or flow diagram experience. Candidate would be overqualified in some areas and underutilized in others."
`cv_fit`: **"rewrite"** — Nothing in current CV maps to e-commerce/storefront. Combined with low score (22), not worth the effort.

### Example 4: AUTO-SKIP — Staff level
**Position:** Staff Frontend Engineer, Observability
**Company:** Datadog | **Location:** Montreal

**Result: AUTO-SKIP. Do not add to database.**

Why: Staff level → auto-skip regardless of company. This rule has no exceptions — Staff/Principal/Distinguished are always skipped.

### Example 5: Vue-only override — 55 points
**Position:** Senior Frontend Engineer
**Company:** GitLab (all-remote, hires in Canada) | **Location:** Remote, Canada

| Category | Points | Reason |
|----------|--------|--------|
| Tech Stack | 10 | Vue-only, but GitLab is confirmed Canada-hiring → override applies. Cap at +10 (TypeScript +10, no React/GraphQL bonus) |
| Product Domain | 13 | Developer tools +8, B2B +5 |
| Complexity | 9 | Design system +4, "own features end-to-end" +3, multi-tenant +2 |
| Seniority | 12 | Senior, candidate can attempt |
| Geography | 10 | "Remote, Canada" confirmed |
| Company | 8 | Confirmed Canada-hiring |
| **Rubric subtotal** | **62 → 52** | Conservative adjustment: Vue is outside candidate's core stack |
| **Resume Overlay** | **+3** | Adjacent: candidate built enterprise platform UIs for government clients, GitLab is similar enterprise scale (+2). Adjacent: candidate has end-to-end frontend ownership experience (+1). Gap offset: Vue is not in candidate's stack but is learnable (already accounted for in rubric adjustment). |
| **Final score** | **55** | |

`resume_match_summary`: "Enterprise platform experience at Aker Systems (government + private sector) is adjacent to GitLab's scale. End-to-end frontend ownership aligns. Vue gap is real but already penalized in rubric — candidate decides if Vue learning curve is acceptable."
`cv_fit`: **"adapt"** — Reframe React experience as transferable component architecture skills. Emphasize enterprise platform scale and end-to-end ownership. Vue override triggers minimum "adapt".

### Example 6: Borderline — 50 points
**Position:** Frontend Engineer
**Company:** Series B fintech startup | **Location:** Toronto (hybrid)

| Category | Points | Reason |
|----------|--------|--------|
| Tech Stack | 25 | React +15, TypeScript +10, no GraphQL |
| Product Domain | 7 | Fintech +7, but no B2B signal |
| Complexity | 0 | No complexity signals in description |
| Seniority | 15 | "3-5 years" mid-level |
| Geography | 8 | Toronto office |
| Company | 5 | Series B startup |
| **Rubric subtotal** | **60 → 50** | Conservative: no complexity signals, hybrid requires relocation |
| **Resume Overlay** | **0** | No direct matches (description too vague to identify specific overlaps). No clear gaps either. Insufficient info for meaningful overlay. |
| **Final score** | **50** | |

`resume_match_summary`: "Description lacks specifics — cannot determine if the fintech product involves dashboards, data-dense UI, or internal tools that would leverage candidate's strengths. Neutral overlay; score stays at borderline."
`cv_fit`: **"adapt"** — Low-confidence description, defaulting to "adapt". If more details emerge, may upgrade to "ready" (if fintech involves dashboards) or downgrade to "rewrite" (if it's pure payments UI).

</scoring_examples>
