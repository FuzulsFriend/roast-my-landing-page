---
name: roast-my-landing-page
description: >
  Audits any landing page across 6 dimensions (first impression, copy, CTA,
  trust, mobile, performance) and delivers a brutally honest score out of 100
  with specific fixes. Use when asked to "roast my landing page", "audit my
  website", "review my site", "check my homepage", "landing page feedback",
  "is my website good", "website audit", "UX review", "conversion review",
  or "what's wrong with my landing page". Takes a URL and returns a scored
  report card with actionable improvements in plain English.
license: MIT
metadata:
  author: tomer-ezri
  version: "1.0.0"
  category: marketing
  tags: [landing-page, ux, audit, conversion, marketing, website]
---

# Roast My Landing Page

Get a brutally honest audit of your landing page — scored out of 100 with specific fixes.

---

## Onboarding

### First-Time Detection

Ask: **"Have you used Roast My Landing Page before?"**

If new user, show:

```
Welcome to Roast My Landing Page!

I'll analyze your landing page across 6 dimensions and give you a score
out of 100 — plus specific fixes explained in plain English.

I use established UX and conversion frameworks (Nielsen Heuristics,
StoryBrand, CRO best practices, WCAG accessibility) — not just opinions.
```

### Install Dependencies

```
RECOMMENDED:
  read-website-fast MCP (reads full page content fast)
    Install: claude mcp add read-website-fast -s user -- npx -y @just-every/mcp-read-website-fast
    Repo:    https://github.com/just-every/mcp-read-website-fast

  Playwright CLI skill (takes screenshots + tests user interactions)
    Install: npx skills add lackeyjb/playwright-skill --skill playwright-skill
    Repo:    https://github.com/lackeyjb/playwright-skill

OPTIONAL:
  Chrome DevTools MCP (Lighthouse audit + console errors + performance)
    Install: claude mcp add chrome-devtools -- npx -y chrome-devtools-mcp@latest
    Repo:    https://github.com/ChromeDevTools/chrome-devtools-mcp

SPEED BOOST:
  Agent Teams mode lets me run all 6 analyses in parallel.
  Enable: export CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1
  Docs:   https://code.claude.com/docs/en/agent-teams
```

### Context Questions (BEFORE auditing)

Ask these before starting any analysis:

1. **What type of business is this?** (SaaS / ecommerce / course / agency / newsletter / other)
2. **Who is your target customer?** (1 sentence)
3. **What should visitors DO on this page?** (sign up / buy / book demo / download / other)
4. **Is this launched publicly, or still in early access / pre-launch?** (This affects how strictly social proof and traction metrics are scored — see `references/industry-benchmarks.md` for early-stage exceptions.)

These answers change how the audit is scored — a SaaS page and an ecommerce page have different success criteria. See `references/industry-benchmarks.md` for details.

---

## Tool Detection + Fallback Chain

At the start of **every run**, detect available tools:

### Page Fetching (pick first available)
1. **read-website-fast MCP** — Best. Full page content, fast.
2. **WebFetch** (built-in) — Adequate. Works for most public pages.
3. **Apify RAG Web Browser** — For JS-heavy or blocked pages.
4. **Ask user** — Last resort. "Paste your HTML or share a screenshot."

### Screenshots (pick first available)
1. **Playwright CLI** — Best. Captures 3 viewports (desktop 1440px, tablet 768px, mobile 375px).
2. **Chrome DevTools MCP** — Good. Screenshots + Lighthouse metrics.
3. **None available** — Text-only analysis. Announce: "I can't take screenshots. Install Playwright CLI for visual analysis."

### Announce to User

```
Tools available: [list what was found]
Analysis mode: [full visual / text-only]
```

---

## Blocked URL Handling

| Scenario | How to detect | What to say |
|----------|--------------|-------------|
| 403/401 (login required) | HTTP status code | "This page requires login. Try: (1) paste the HTML, (2) share a screenshot, (3) use a staging URL without auth." |
| Cloudflare/bot protection | Challenge page in response | Try Apify RAG Browser. If still blocked: "The page has bot protection. Share a screenshot or paste the HTML." |
| JavaScript SPA (empty HTML) | Minimal content in response | Use Playwright to render. If unavailable: "I can only see the loading screen. Install Playwright CLI for full analysis." |
| Timeout (over 15 seconds) | No response | Retry once. Then: "Your page is too slow to reach — and your visitors are having the same problem." |
| localhost / private IP | URL starts with localhost, 127., 192.168., 10. | "I can't access local URLs. Deploy to a staging URL, or paste the HTML directly." |
| 5xx server error | HTTP 500, 502, 503, 504 status | Retry once after 10 seconds. If still failing: score Performance at 20/100 max. Flag ALL other dimension scores as "provisional — page was returning server errors during analysis." Tell user: "Your page is returning a server error. Fix this first, then re-run for accurate scores." |

---

## Agent Teams Roles

When Agent Teams is enabled, run all 6 analyses in parallel:

| Role | Agent Name | Dimension |
|------|-----------|-----------|
| Orchestrator | main | Coordinates all agents, assembles final report, talks to user |
| First Impression Analyst | audit-impression | 3-second test, visual hierarchy, above-fold content |
| Copy Analyst | audit-copy | Headlines, jargon, benefits vs features, StoryBrand structure |
| CTA Analyst | audit-cta | Visibility, placement, button copy, contrast, competing CTAs |
| Trust Analyst | audit-trust | Social proof, credibility markers, risk reversal, objections |
| Mobile and Accessibility Analyst | audit-mobile | Responsive design, touch targets, WCAG 2.2 AA, font sizes |
| Technical Analyst | audit-technical | Core Web Vitals, SEO basics, broken links, console errors |

**When Agent Teams is NOT available:** Run all 6 analyses sequentially in the main session. Same depth, just slower.

---

## The 6 Audit Dimensions

| Dimension | Weight | What it checks |
|-----------|--------|---------------|
| First Impression | 20% | Can a visitor understand what you do in 3 seconds? |
| Copy and Messaging | 20% | Is the writing clear, jargon-free, and benefit-focused? |
| Call-to-Action | 15% | Is the CTA visible, compelling, and the only clear action? |
| Trust and Social Proof | 15% | Are there testimonials, logos, numbers, or guarantees? |
| Mobile and Accessibility | 15% | Does the page work on phones? Is it accessible? |
| Performance and Technical | 15% | Does it load fast? Are SEO basics covered? |

Scoring criteria: `references/scoring-rubric.md`

Frameworks used per dimension:
- First Impression + Copy: `references/nielsen-heuristics.md`, `references/storybrand-framework.md`, `references/copy-analysis-rules.md`
- CTA + Trust: `references/cro-checklist.md`
- Mobile + Accessibility: `references/wcag-essentials.md`
- Technical: Core Web Vitals (via Lighthouse if Chrome DevTools available)
- All dimensions: `references/anti-patterns.md` (always-wrong patterns to flag immediately)

Industry-specific scoring adjustments: `references/industry-benchmarks.md`

---

## Analysis Flow

### Phase 1: FETCH AND CAPTURE

1. Fetch page content using best available tool
2. Take screenshots at 3 viewports if Playwright available (desktop 1440px, tablet 768px, mobile 375px)
3. Handle blocked URLs per the fallback table above
4. If page fetched but screenshots unavailable, proceed with text-only analysis

### Phase 2: DIMENSION ANALYSIS

Run all 6 dimension analyses (parallel if Agent Teams, sequential otherwise).

Each dimension analysis must:
1. Score 0-100 based on checkpoints in `references/scoring-rubric.md`
2. Record specific findings in this format:

```
FINDING: [what's wrong — plain English, no jargon]
IMPACT: [why this matters for visitors/business]
FIX:    [specific action to take]
EFFORT: [quick fix (under 30 min) / few hours / redesign needed]
```

### Phase 3: E2E SMOKE TEST (if Playwright available)

1. Navigate to URL — screenshot above the fold
2. Scroll full page — screenshot key sections
3. Click primary CTA — does it work? Where does it go?
4. Test on mobile viewport (375px) — screenshot
5. Check console for JavaScript errors
6. Report: "As a visitor, here's what I experienced..."

### Phase 4: SCORING AND REPORT

1. Collect all 6 dimension scores
1b. If a 5xx error was encountered, mark all scores as provisional and add a disclaimer to the report header: 'NOTE: The page returned a server error during analysis. Scores are provisional and may change when the page is stable. Fix the server error and re-run for accurate results.'
2. Apply weights to calculate total score (0-100)
3. Assign letter grade using the scale below
4. Rank findings by severity: Critical, Warning, Suggestion
5. Generate "Top 3 Roasts" — the biggest issues, honest but helpful
6. Generate "Top 3 Wins" — what the page does well
7. Generate "Path to improvement" — specific steps to go up one letter grade
8. Output using the format in `assets/report-template.md`

### Phase 5: VISUAL REPORT (browser preview)

Generate a self-contained HTML report and open it in the user's browser.

1. Create a JSON object with all audit data (see schema below)
2. Read the HTML template from `assets/report-ui.html`
3. Replace `{{REPORT_DATA}}` with the JSON string
4. Save to `./landing-page-roast-[domain]-[date].html`
5. Open in browser: `open` (macOS), `xdg-open` (Linux), `start` (Windows)
6. Tell the user: "Visual report saved to [path] and opened in your browser."

JSON schema for the report:
```json
{
  "meta": {
    "url": "string",
    "businessType": "string",
    "conversionGoal": "string",
    "targetCustomer": "string",
    "launchStage": "launched|early-access|pre-launch",
    "date": "YYYY-MM-DD",
    "mode": "full visual|text-only",
    "toolsUsed": ["string"],
    "provisional": false
  },
  "overall": {
    "score": 0,
    "grade": "string",
    "verdict": "string"
  },
  "dimensions": [
    { "name": "First Impression", "score": 0, "weight": 0.20, "critical": false },
    { "name": "Copy & Messaging", "score": 0, "weight": 0.20, "critical": false },
    { "name": "Call-to-Action", "score": 0, "weight": 0.15, "critical": false },
    { "name": "Trust & Proof", "score": 0, "weight": 0.15, "critical": false },
    { "name": "Mobile & Access", "score": 0, "weight": 0.15, "critical": false },
    { "name": "Performance", "score": 0, "weight": 0.15, "critical": false }
  ],
  "roasts": [
    { "issue": "string", "why": "string", "fix": "string", "effort": "string" }
  ],
  "wins": [
    { "what": "string", "why": "string" }
  ],
  "findings": {
    "firstImpression": [{ "severity": "CRITICAL|WARNING|SUGGESTION|PASS", "description": "string" }],
    "copyMessaging": [{ "severity": "string", "description": "string" }],
    "callToAction": [{ "severity": "string", "description": "string" }],
    "trustProof": [{ "severity": "string", "description": "string" }],
    "mobileAccess": [{ "severity": "string", "description": "string" }],
    "performance": [{ "severity": "string", "description": "string" }]
  },
  "antiPatterns": [
    { "name": "string", "impact": "string", "severity": "Critical|Warning|Flag" }
  ],
  "improvement": {
    "currentGrade": "string",
    "nextGrade": "string",
    "steps": [
      { "action": "string", "dimension": "string", "currentScore": 0, "projectedScore": 0, "time": "string" }
    ],
    "estimatedTime": "string",
    "projectedScore": 0,
    "projectedGrade": "string"
  },
  "industry": {
    "businessType": "string",
    "benchmark": "string",
    "position": "above|at|below"
  }
}
```

---

## Grading Scale

| Grade | Score | What it means |
|-------|-------|--------------|
| A+ | 95-100 | Excellent. Minor tweaks only. |
| A | 90-94 | Very strong. A few small improvements possible. |
| B+ | 85-89 | Good page with clear room to improve. |
| B | 80-84 | Solid foundation, missing some key elements. |
| C+ | 75-79 | Average. Several important things need fixing. |
| C | 70-74 | Below average. Visitors are probably leaving confused. |
| D | 60-69 | Needs serious work. Major issues with clarity or trust. |
| F | Below 60 | Actively hurting your business. Fix urgently. |

---

## Output Format

```
LANDING PAGE ROAST: [url]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Overall Score: [X]/100 ([Grade])
Business: [type] | Goal: [conversion goal]

BREAKDOWN:
  First Impression:  [████████░░]  [score]/100
  Copy and Messaging:[██████░░░░]  [score]/100
  Call-to-Action:    [█████████░]  [score]/100
  Trust and Proof:   [█████░░░░░]  [score]/100
  Mobile and Access: [███████░░░]  [score]/100
  Performance:       [████████░░]  [score]/100

TOP 3 ROASTS:
1. "[issue in plain English]"
   Why it matters: [impact on visitors]
   Fix: [specific action]
   Effort: [time estimate]

2. ...
3. ...

TOP 3 WINS:
1. "[what's working well]"
2. ...
3. ...

YOUR PATH FROM [current grade] TO [next grade]:
1. [specific step] ([dimension]: [current] -> [projected])
2. ...
3. ...
Estimated time: [total hours]
Expected new score: [projected]/100 ([projected grade])
```

See `assets/report-template.md` for the full template with all fields.

---

## Report Language Rules

Write every finding in simple English. The user may not be a developer.

**DO:**
- "Your signup button blends into the background — visitors can't find it"
- "No testimonials anywhere on the page. Visitors have no reason to trust you yet."
- "On phones, the text is too small to read without zooming in"

**DON'T:**
- "CTA has insufficient contrast ratio against the background gradient"
- "No social proof elements above the fold impacting conversion rate optimization"
- "Font-size below 16px on mobile viewport causes accessibility violations"

Tone: Like a friend who happens to be a UX expert — honest and direct, but always helpful. Never mean-spirited.

---

## Troubleshooting

**"Skill can't fetch the page"**
Check the URL is correct and publicly accessible. Try the fallback chain: WebFetch, then Apify, then ask user to paste HTML.

**"No screenshots available"**
Install Playwright CLI skill for visual analysis. Without it, the audit is text-only (still useful, but misses visual hierarchy and mobile layout issues).

**"Score seems too low"**
Business type affects the benchmark. Make sure the correct business type is set. Security and trust issues are weighted heavily because they directly impact whether visitors convert.

**"Score seems too high"**
The audit checks what's ON the page, not what's missing from the business. A beautiful page with no product-market fit will still score well on UX.

**"Analysis is too technical"**
Report language rules enforce simple English. If a finding slips through with jargon, rephrase it before presenting.
