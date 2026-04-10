# Exclusion Rules

Skip the vacancy entirely (do not add to database) if ANY of these match.

## Auto-skip by Tech

- Primary language: Go, Python, Java, PHP, Ruby (not React)
- WordPress / Webflow / Drupal
- Angular or Vue only (no mention of React) — **exception**: if company is confirmed Canada-hiring (see `data/companies-list.md`), do NOT skip. Pass to scoring instead — `flows/score.md` will apply a Tech Stack penalty.
- iOS / Android native (unless React Native)
- PHP / Laravel / Django templates as primary work
- Only HTML/CSS/jQuery, no modern framework

## Auto-skip by Level

- Junior / Intern / Entry-level
- Staff / Principal / Distinguished / Director / VP / 8+ years required

## Auto-skip by Eligibility

- "US citizens only" or "security clearance required"
- Agency / body-shop / outsourcing firm

## Auto-skip by Role Type

- Full-stack roles WITHOUT frontend-heavy markers. If the title contains "Full Stack" / "Fullstack" / "Full-Stack", look for at least one of these signals that the role is frontend-leaning:
  - Title or description explicitly says "frontend-heavy", "frontend-focused", "frontend-leaning", "React focus", "UI focus"
  - Tech stack lists React/Next.js/TypeScript as primary, backend mentioned as secondary
  - Description emphasizes UI work: "build user-facing features", "design system", "component library", "data visualization", "dashboard", "interactive UI"
  - Ratio of frontend-to-backend requirements is clearly frontend-dominant (e.g., 70%+ of listed requirements are frontend)
  - If none of these signals are present, or the role emphasizes backend (API design, database architecture, microservices, infrastructure, DevOps), AUTO-SKIP
  - When `score_confidence: "low"` (no full description available), include the role but add a note in `key_requirements`: "Full-stack — needs review for frontend weight"

## Auto-skip by Domain

- Simple marketing site / landing pages only

## Application Strategy Note

Target pace: 8-12 quality applications per week, not spray-and-pray.
Dual approach: Company-first (60%) + Keyword-first (40%).
For Wellfound: personalized "Note to Founder" messages → 6.4% callback vs LinkedIn 3.3%.
