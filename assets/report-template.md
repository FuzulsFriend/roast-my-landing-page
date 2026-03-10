# Report Output Template

Use this exact format when presenting the final audit report to the user.

---

## Format

```
LANDING PAGE ROAST
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
URL:      [URL]
Business: [BUSINESS_TYPE]
Goal:     [CONVERSION_GOAL]
Audience: [TARGET_CUSTOMER]
Analyzed: [DATE] | Mode: [full visual / text-only]
Tools:    [LIST_OF_TOOLS_USED]

━━━ OVERALL SCORE ━━━

  [SCORE]/100  —  [GRADE]
  [ONE_SENTENCE_VERDICT]

━━━ DIMENSION BREAKDOWN ━━━

  First Impression   [BAR_10_BLOCKS]  [SCORE]/100
  Copy & Messaging   [BAR_10_BLOCKS]  [SCORE]/100
  Call-to-Action     [BAR_10_BLOCKS]  [SCORE]/100
  Trust & Proof      [BAR_10_BLOCKS]  [SCORE]/100
  Mobile & Access    [BAR_10_BLOCKS]  [SCORE]/100
  Performance        [BAR_10_BLOCKS]  [SCORE]/100

━━━ TOP 3 ROASTS ━━━

1. "[ISSUE_PLAIN_ENGLISH]"
   Why it matters: [IMPACT_ON_VISITORS — 1-2 sentences]
   Fix: [SPECIFIC_ACTION — what to do, not just what's wrong]
   Effort: [quick fix (under 30 min) / few hours / redesign needed]

2. "[ISSUE_PLAIN_ENGLISH]"
   Why it matters: [IMPACT_ON_VISITORS]
   Fix: [SPECIFIC_ACTION]
   Effort: [EFFORT_LEVEL]

3. "[ISSUE_PLAIN_ENGLISH]"
   Why it matters: [IMPACT_ON_VISITORS]
   Fix: [SPECIFIC_ACTION]
   Effort: [EFFORT_LEVEL]

━━━ TOP 3 WINS ━━━

1. "[WHAT_IS_WORKING_WELL]"
   Why it works: [EXPLANATION]

2. "[WHAT_IS_WORKING_WELL]"
   Why it works: [EXPLANATION]

3. "[WHAT_IS_WORKING_WELL]"
   Why it works: [EXPLANATION]

━━━ FULL FINDINGS ━━━

FIRST IMPRESSION ([SCORE]/100)
  [SEVERITY]: [DESCRIPTION]
  [SEVERITY]: [DESCRIPTION]
  ...

COPY AND MESSAGING ([SCORE]/100)
  [SEVERITY]: [DESCRIPTION]
  [SEVERITY]: [DESCRIPTION]
  ...

CALL-TO-ACTION ([SCORE]/100)
  [SEVERITY]: [DESCRIPTION]
  [SEVERITY]: [DESCRIPTION]
  ...

TRUST AND SOCIAL PROOF ([SCORE]/100)
  [SEVERITY]: [DESCRIPTION]
  [SEVERITY]: [DESCRIPTION]
  ...

MOBILE AND ACCESSIBILITY ([SCORE]/100)
  [SEVERITY]: [DESCRIPTION]
  [SEVERITY]: [DESCRIPTION]
  ...

PERFORMANCE AND TECHNICAL ([SCORE]/100)
  [SEVERITY]: [DESCRIPTION]
  [SEVERITY]: [DESCRIPTION]
  ...

━━━ ANTI-PATTERNS DETECTED ━━━

[List any anti-patterns from references/anti-patterns.md found on the page]
[If none found: "No critical anti-patterns detected."]

━━━ YOUR PATH FROM [CURRENT_GRADE] TO [NEXT_GRADE] ━━━

To go from [CURRENT_SCORE] ([CURRENT_GRADE]) to [TARGET_SCORE]+ ([NEXT_GRADE]):

1. [SPECIFIC_STEP] ([DIMENSION]: [CURRENT] -> [PROJECTED])
   Time: [ESTIMATE]

2. [SPECIFIC_STEP] ([DIMENSION]: [CURRENT] -> [PROJECTED])
   Time: [ESTIMATE]

3. [SPECIFIC_STEP] ([DIMENSION]: [CURRENT] -> [PROJECTED])
   Time: [ESTIMATE]

Estimated total time: [TOTAL_HOURS]
Expected new score:   [PROJECTED_SCORE]/100 ([PROJECTED_GRADE])

━━━ INDUSTRY CONTEXT ━━━

Business type: [BUSINESS_TYPE]
Benchmark for this type: [BENCHMARK_DESCRIPTION from industry-benchmarks.md]
Your position: [ABOVE/AT/BELOW average for this business type]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Audited by Roast My Landing Page
github.com/tomer-ezri/roast-my-landing-page
```

---

## Progress Bar Format

Use block characters to create visual progress bars. Each bar is 10 characters wide:

```
100/100  ██████████
 90/100  █████████░
 80/100  ████████░░
 70/100  ███████░░░
 60/100  ██████░░░░
 50/100  █████░░░░░
 40/100  ████░░░░░░
 30/100  ███░░░░░░░
 20/100  ██░░░░░░░░
 10/100  █░░░░░░░░░
  0/100  ░░░░░░░░░░
```

Round to the nearest 10 for the bar. Show exact score as the number.

Add `!!` after scores below 60 to flag critical dimensions:
```
  Trust & Proof      ██████░░░░  62/100
  Performance        █████░░░░░  54/100  !!
```

---

## Overall Score Calculation

```
Overall = (First Impression x 0.20)
        + (Copy & Messaging x 0.20)
        + (Call-to-Action x 0.15)
        + (Trust & Proof x 0.15)
        + (Mobile & Access x 0.15)
        + (Performance x 0.15)
```

Round to nearest whole number. Apply grade from the grading scale.

---

## Grade Scale

| Grade | Score | Display |
|-------|-------|---------|
| A+ | 95-100 | Excellent |
| A | 90-94 | Very Strong |
| B+ | 85-89 | Good |
| B | 80-84 | Solid |
| C+ | 75-79 | Average |
| C | 70-74 | Below Average |
| D | 60-69 | Needs Work |
| F | Below 60 | Urgent |

---

## Severity Labels

Use these labels consistently in the Full Findings section:

| Label | When to use |
|-------|-------------|
| CRITICAL | Security issues, broken functionality, page literally doesn't work |
| WARNING | Significant UX or conversion problems that need fixing |
| SUGGESTION | Nice-to-have improvements that would help but aren't urgent |
| PASS | Checkpoint passes — briefly note what's working |

---

## Rules for Filling the Template

### One-Sentence Verdict
Write a single sentence that captures the page's biggest strength AND biggest weakness. Examples:
- "Clean design and clear CTA, but zero social proof means visitors have no reason to trust you."
- "Strong testimonials and credibility, but the headline is so vague that visitors leave before they see the proof."
- "Solid across the board — your biggest win is [X] and the main thing holding you back is [Y]."

### Top 3 Roasts
1. **Must be the 3 highest-impact issues** — the changes that would improve conversion the most
2. **Plain English only** — no jargon, no acronyms, no technical terms unless explained
3. **Each roast must include a specific fix** — not just "improve this" but "do X specifically"
4. **Order by impact** — biggest conversion killer first
5. **Tone: honest but helpful** — like a friend who happens to be a UX expert. Never mean-spirited.

### Top 3 Wins
1. **Must be genuine** — don't invent compliments. If only 1-2 things are good, list 1-2.
2. **Explain WHY it's good** — not just "nice design" but "the visual hierarchy guides the eye directly to the CTA"
3. **Use this to balance the roasts** — the report should feel fair, not just a takedown

### Full Findings
For each dimension, list every checkpoint from `references/scoring-rubric.md` with its status. Sort by severity: CRITICAL first, then WARNING, then SUGGESTION, then PASS.

### Path to Improvement
1. **Always target the next letter grade** — don't jump from D to A. Small wins build momentum.
2. **Pick the 3 highest-ROI changes** — lowest effort, highest point gain
3. **Include projected scores** — show exactly how each change moves the needle
4. **Be realistic on time estimates** — quick fix = under 30 min, few hours = 2-4 hours, redesign = 1-2 days+
5. **Projected scores should be conservative** — better to under-promise and over-deliver

### Industry Context
Reference `references/industry-benchmarks.md` for the business type. Include:
- Whether the score is above, at, or below the benchmark for this type
- Any "acceptable" exceptions that apply (e.g., early-stage SaaS with no social proof yet)
- Any "NOT acceptable" violations that need priority attention

### Anti-Patterns Section
List any patterns found from `references/anti-patterns.md`. For each:
- Name the pattern in plain English
- Explain the user impact in one sentence
- Note the severity (Critical / Warning / Flag)

If no anti-patterns are found, say so explicitly — it's a positive signal.

---

## Conditional Sections

### If Playwright screenshots were taken:
Add a "VISUAL REVIEW" section after the breakdown:

```
━━━ VISUAL REVIEW ━━━

Desktop (1440px):
  [Key observations from desktop screenshot]

Tablet (768px):
  [Key observations from tablet screenshot]

Mobile (375px):
  [Key observations from mobile screenshot]

CTA test: [What happened when the primary CTA was clicked]
```

### If Chrome DevTools / Lighthouse was available:
Add performance metrics to the Performance dimension findings:

```
Lighthouse scores:
  Performance:    [SCORE]
  Accessibility:  [SCORE]
  Best Practices: [SCORE]
  SEO:            [SCORE]

Core Web Vitals:
  LCP: [VALUE] ([GOOD/NEEDS IMPROVEMENT/POOR])
  FID: [VALUE] ([GOOD/NEEDS IMPROVEMENT/POOR])
  CLS: [VALUE] ([GOOD/NEEDS IMPROVEMENT/POOR])
```

### If text-only analysis (no screenshots):
Add a disclaimer at the top of the report:

```
NOTE: This audit was performed without screenshots (text-only mode).
Visual hierarchy, mobile layout, and some accessibility checks could not
be fully verified. Install Playwright CLI for a more complete audit.
```

---

## Extended Report (Optional)

If the user asks for more detail, provide a per-dimension breakdown:

```
DETAILED BREAKDOWN: [DIMENSION_NAME] ([SCORE]/100)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Checkpoint 1: [NAME] — [POINTS]/[MAX]
  [What was found]
  [Pass/Fail reasoning]

Checkpoint 2: [NAME] — [POINTS]/[MAX]
  [What was found]
  [Pass/Fail reasoning]

...

Anti-pattern penalties applied: [LIST or "None"]
Industry adjustment: [ADJUSTMENT or "None"]
```

Only provide this level of detail if requested. The standard report should be concise and actionable.

---

## Language Rules (Final Check)

Before presenting the report, verify:

1. **No jargon** — Every finding is written so a non-technical business owner can understand it
2. **No passive voice in recommendations** — "Add a testimonial section" not "A testimonial section should be added"
3. **Specific over vague** — "Your signup button is gray on a gray background" not "CTA contrast is insufficient"
4. **Honest but kind** — The tone is a knowledgeable friend, not a critic. Every roast includes a fix.
5. **No filler** — Every sentence in the report earns its place. Cut anything that doesn't inform or help.
6. **Tools disclosed** — Always list what tools were used. If screenshots weren't available, say so — it affects reliability of visual dimension scores.
