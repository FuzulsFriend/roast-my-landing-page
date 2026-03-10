# Roast My Landing Page

> A Claude Code skill that audits any landing page across 6 dimensions and delivers a brutally honest score out of 100 — with specific fixes explained in plain English.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Skill-blue)](https://code.claude.com)
[![SKILL.md](https://img.shields.io/badge/SKILL.md-open%20standard-purple)](SKILL.md)

---

## What it does

Give it a URL. Get back a scored report card with specific fixes — not vague advice.

Uses established UX and conversion frameworks (Nielsen's 10 Heuristics, StoryBrand, CRO Pyramid, WCAG 2.2 AA) — not opinions.

**6 audit dimensions:**

| Dimension | Weight | What it checks |
|-----------|--------|---------------|
| First Impression | 20% | Can a visitor understand what you do in 3 seconds? |
| Copy & Messaging | 20% | Is the writing clear, jargon-free, and benefit-focused? |
| Call-to-Action | 15% | Is the CTA visible, compelling, and the only clear action? |
| Trust & Social Proof | 15% | Are there testimonials, logos, numbers, or guarantees? |
| Mobile & Accessibility | 15% | Does the page work on phones? Is it accessible? |
| Performance & Technical | 15% | Does it load fast? Are SEO basics covered? |

Every finding includes: what's wrong, why it matters, specific fix, and time estimate.

---

## Install

```bash
npx skills add FuzulsFriend/roast-my-landing-page
```

Or manually: copy `SKILL.md` into your `.claude/skills/` directory.

**Recommended for visual analysis:**
```bash
npx skills add lackeyjb/playwright-skill --skill playwright-skill
```

---

## Usage

Just ask Claude:

```
Roast my landing page: https://yoursite.com
```

```
Audit my website
```

```
What's wrong with my homepage?
```

---

## What you get

```
LANDING PAGE ROAST: yoursite.com
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Overall Score: 67/100 (D)
Business: SaaS | Goal: Free trial signup

BREAKDOWN:
  First Impression:  [████████░░]  78/100
  Copy and Messaging:[██████████]  82/100
  Call-to-Action:    [████████░░]  74/100
  Trust and Proof:   [████░░░░░░]  35/100  !!
  Mobile and Access: [████████░░]  76/100
  Performance:       [████░░░░░░]  38/100  !!

TOP 3 ROASTS:
1. "No testimonials anywhere on the page..."
2. "Your page took 6 seconds to load..."
3. "The signup button says 'Get Started' but..."
```

Plus: a visual browser report with animated score gauge, collapsible findings per dimension, and a step-by-step improvement timeline.

---

## What's included

```
roast-my-landing-page/
├── SKILL.md                           # Main skill instructions
├── assets/
│   ├── report-template.md             # Text report template
│   └── report-ui.html                 # Visual browser report (fire theme)
└── references/
    ├── scoring-rubric.md              # Exact checkpoints per dimension
    ├── nielsen-heuristics.md          # 10 heuristics adapted for landing pages
    ├── storybrand-framework.md        # StoryBrand audit format
    ├── cro-checklist.md               # CRO Pyramid + CTA rules
    ├── copy-analysis-rules.md         # Headline, body copy, jargon detection
    ├── wcag-essentials.md             # 8 WCAG rules in plain English
    ├── anti-patterns.md               # 17 always-wrong patterns
    ├── industry-benchmarks.md         # Weight adjustments per business type
    └── examples/
        ├── score-90-plus.md           # What an A+ page looks like
        └── common-fails.md            # Top 10 most common issues
```

---

## Works with

- **Agent Teams mode** — all 6 dimensions analyzed in parallel
- **Playwright CLI** — screenshots at 3 viewports, E2E smoke test
- **Chrome DevTools MCP** — Lighthouse metrics, console errors

Enable Agent Teams:
```bash
export CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1
```

---

## Industry-aware scoring

Different business types have different success criteria. The skill adjusts its scoring for:
- **SaaS** — trust signals and trial friction weighted heavily
- **Ecommerce** — product imagery and checkout flow
- **Course/coaching** — authority signals and transformation framing
- **Agency** — portfolio and credibility markers
- **Newsletter** — value proposition and low-friction signup
- **Early-stage / pre-launch** — social proof substitutes (founder credentials, beta count)

---

## License

MIT — use it, fork it, improve it, share it.

---

*Built with the [SKILL.md open standard](https://github.com/FuzulsFriend/roast-my-landing-page/blob/main/SKILL.md) — works across Claude Code, Codex CLI, Gemini CLI, and 15+ other AI coding assistants.*
