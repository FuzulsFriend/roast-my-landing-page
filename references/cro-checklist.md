# CRO (Conversion Rate Optimization) Checklist

Rules for evaluating whether a landing page is optimized for converting visitors into customers. Based on the Eisenberg CRO Pyramid and industry best practices.

---

## The CRO Pyramid (Bottom to Top)

A page must work at each level before the next level matters:

1. **FUNCTIONAL** — Does the page work at all?
2. **ACCESSIBLE** — Can all visitors access the page?
3. **USABLE** — Can visitors complete the desired action?
4. **INTUITIVE** — Can visitors figure it out without thinking?
5. **PERSUASIVE** — Does the page motivate action?

If the page is broken (level 1), it doesn't matter how persuasive it is (level 5).

---

## Level 1: Functional

- [ ] All links work (no 404s, no javascript:void, no # placeholders)
- [ ] All images load
- [ ] Forms submit successfully
- [ ] Page loads within 3 seconds
- [ ] No JavaScript console errors
- [ ] HTTPS with valid certificate
- [ ] CTA button actually does something when clicked

**If any of these fail:** Flag as CRITICAL. Nothing else matters until the page works.

---

## Level 2: Accessible

- [ ] Works on mobile (responsive, no horizontal scroll)
- [ ] Text readable without zooming (16px+ body text on mobile)
- [ ] Touch targets 44x44px minimum
- [ ] Color contrast meets WCAG AA (4.5:1 for text)
- [ ] Alt text on meaningful images
- [ ] Works with keyboard navigation
- [ ] No auto-playing audio or video
- [ ] Works across major browsers (Chrome, Safari, Firefox)

**If these fail:** Flag as WARNING. You're excluding a significant portion of visitors.

---

## Level 3: Usable

- [ ] Visitor can complete the primary action in 3 clicks or fewer
- [ ] Form fields have clear labels and helpful placeholder text
- [ ] Error messages are helpful and specific
- [ ] Clear visual feedback after actions (button loading state, success message)
- [ ] Navigation is obvious
- [ ] Page loads progressively (content appears, not a blank screen then everything at once)
- [ ] No unnecessary steps between "I want this" and "I got this"

**If these fail:** Flag as WARNING. Visitors might want to convert but can't figure out how.

---

## Level 4: Intuitive

- [ ] Value proposition understandable in 3 seconds
- [ ] Visual hierarchy guides the eye to the right places
- [ ] CTA stands out immediately
- [ ] Page structure follows a logical flow (problem -> solution -> proof -> action)
- [ ] Pricing is clear and easy to understand
- [ ] "How it works" is explained in 3-4 simple steps
- [ ] No jargon or insider language

**If these fail:** Flag as SUGGESTION. Page works but visitors have to think too hard.

---

## Level 5: Persuasive

- [ ] Headline addresses a specific pain point or desire
- [ ] Benefits-first copy (not features-first)
- [ ] Social proof present (testimonials, logos, numbers)
- [ ] Risk reversal (free trial, money-back guarantee, "no credit card needed")
- [ ] Urgency or scarcity if authentic (not fake countdown timers)
- [ ] CTA copy is specific and value-oriented ("Get my free report" not "Submit")
- [ ] Objections addressed (FAQ, comparison, "how it works")
- [ ] One clear primary CTA (not 5 competing actions)

**If these fail:** Flag as SUGGESTION. Page is usable but not compelling.

---

## CTA-Specific Rules

### Button Copy
| Good | Bad | Why |
|------|-----|-----|
| "Start my free trial" | "Submit" | Reminds visitor what they get |
| "Get the checklist" | "Download" | Specific about the deliverable |
| "Book a 15-min demo" | "Contact us" | Sets expectations |
| "Join 12,000 teams" | "Sign up" | Adds social proof to the CTA |

### Button Placement
- At least one CTA above the fold
- CTA repeated after key content sections (benefits, testimonials, pricing)
- Final CTA at the bottom of the page
- Sticky CTA on mobile (if non-intrusive)

### Button Design
- High contrast against background (pass the squint test)
- Generous padding (not a cramped link pretending to be a button)
- Consistent style across all CTAs
- Primary CTA visually dominant over secondary actions

---

## Trust Signals Checklist

### Essential (at least 2 of these)
- [ ] Customer testimonials with names and photos
- [ ] Company/client logos ("trusted by")
- [ ] Specific numbers (user count, results achieved, years in business)
- [ ] Money-back guarantee or free trial
- [ ] Media mentions or awards

### Red Flags (ALWAYS flag these)
- Fake testimonials (generic names, stock photos, no specifics)
- Fake urgency ("Only 3 left!" on a digital product)
- Fake countdown timers that reset on page reload
- "As seen on" logos that link to nothing

---

## Form Optimization

- [ ] Minimum fields needed (email only for newsletter, name + email for trials)
- [ ] Inline validation (real-time, not just on submit)
- [ ] Privacy note near email field ("No spam. Unsubscribe anytime.")
- [ ] Mobile keyboard matches field type
- [ ] Autofill works (proper input types)

### Field Count Impact on Conversion
| Fields | Typical Impact |
|--------|---------------|
| 1 (email) | Highest conversion |
| 2-3 | Slight drop |
| 4-6 | Significant drop (30-50% fewer completions) |
| 7+ | Most visitors abandon |

---

## Using This in the Audit

Cross-reference CTA and Trust dimension scores against this checklist:
- **CTA dimension:** Focus on Levels 3-5 for the primary CTA
- **Trust dimension:** Focus on the Trust Signals Checklist
- **Copy dimension:** Check if copy is at Level 4+ 
- **First Impression:** Check if the above-fold area hits Level 4-5
