# Nielsen's 10 Usability Heuristics — Adapted for Landing Pages

Jakob Nielsen's 10 general principles for interaction design, reframed specifically for evaluating landing pages.

---

## 1. Visibility of System Status

**Principle:** The page should always keep visitors informed about what's going on through appropriate feedback within a reasonable time.

**What to check on a landing page:**
- [ ] Loading indicators for any async content (images, dynamic sections)
- [ ] Form submissions show clear feedback (success message, error message, loading spinner)
- [ ] Progress indicators on multi-step forms or signups
- [ ] CTA buttons show a loading state after being clicked
- [ ] If content loads lazily, there's a placeholder (not a blank space that suddenly fills in)

**Common violations:**
- Clicking a CTA and nothing visibly happens (no loading state, page just sits there)
- Form submitted but no confirmation — visitor doesn't know if it worked
- Images loading slowly with no placeholder, causing layout shift
- "We'll get back to you" with no estimated timeframe

**Severity:** Warning — Visitors who click and see nothing will assume it's broken and leave.

---

## 2. Match Between System and the Real World

**Principle:** The page should speak the visitor's language, using words, phrases, and concepts familiar to the target audience rather than internal jargon.

**What to check on a landing page:**
- [ ] Headlines use the language customers actually use (not internal product names or technical terms)
- [ ] Features are described in terms of outcomes, not implementation
- [ ] Navigation labels are intuitive ("Pricing" not "Plans and Packages")
- [ ] Icons are universally understood or paired with text labels
- [ ] The page describes the problem the way the customer would describe it

**Common violations:**
- Using internal feature names ("SmartFlow Engine") that mean nothing to visitors
- Writing copy from the company's perspective instead of the customer's
- Icons without labels (what does that abstract geometric shape mean?)
- Describing the solution before establishing the problem

**Severity:** Critical — If visitors don't understand what you do, nothing else matters.

---

## 3. User Control and Freedom

**Principle:** Visitors need a clear "way out" when they take a wrong action. Support undo and redo.

**What to check on a landing page:**
- [ ] Popups and modals have obvious close buttons (X in the corner, clickable backdrop)
- [ ] Forms can be dismissed or reset
- [ ] Navigation back to the homepage is always available (logo click)
- [ ] Email signup forms have an unsubscribe note
- [ ] No forced funnels where the visitor can't go back

**Common violations:**
- Modal with no close button (or close button that's nearly invisible)
- Popup that covers the whole page with no way to dismiss
- Sticky banner that can't be closed and covers content
- Chat widget that opens automatically and can't be minimized

**Severity:** Warning — Trapped visitors don't convert; they close the tab.

---

## 4. Consistency and Standards

**Principle:** Visitors shouldn't have to wonder whether different words, actions, or icons mean the same thing. Follow platform conventions.

**What to check on a landing page:**
- [ ] Button styles are consistent (same shape, padding, and style for all CTAs)
- [ ] Colors have consistent meaning (e.g., primary color for CTAs, not also used for non-interactive elements)
- [ ] Typography follows a consistent scale (2-3 font sizes, not 7 different sizes)
- [ ] Link styles are consistent (all underlined, or all colored, not mixed)
- [ ] Common patterns work as expected (logo goes to homepage, underlined text is clickable)

**Common violations:**
- Some buttons are rounded, others are square, with no visual logic
- Primary CTA color also used for decorative elements (training visitors to ignore it)
- Links that look like buttons and buttons that look like links
- Inconsistent spacing between sections

**Severity:** Suggestion — Inconsistency erodes trust subconsciously. Visitors may not articulate it, but the page feels "off."

---

## 5. Error Prevention

**Principle:** Design to prevent problems from occurring in the first place. Eliminate error-prone conditions.

**What to check on a landing page:**
- [ ] Form fields have clear labels and placeholder examples
- [ ] Email fields validate format in real-time (not just after submission)
- [ ] Required fields are clearly marked
- [ ] Inline validation helps visitors fix errors before submitting
- [ ] Date/phone fields use appropriate input types (date picker, tel input)

**Common violations:**
- Form with 10 fields and no validation until you hit "Submit"
- Required fields not marked — visitor fills half the form and gets an error
- No input format hints (is the phone number with country code or without?)
- Free-text fields where a dropdown would prevent errors

**Severity:** Warning — Every form error is a chance for the visitor to give up.

---

## 6. Recognition Rather Than Recall

**Principle:** Minimize the visitor's memory load. Make information visible rather than requiring visitors to remember it.

**What to check on a landing page:**
- [ ] Pricing page shows feature comparisons side-by-side (not "see plan details" links)
- [ ] CTA reminds the visitor what they're getting ("Start my free trial" not just "Submit")
- [ ] Key value props are repeated near CTAs lower on the page
- [ ] If there's a multi-step process, all steps are visible (progress bar)
- [ ] Contact info, pricing, or key details don't require visitors to scroll back up

**Common violations:**
- Headline says "Try it free" but the CTA says "Get started" (free part lost)
- Pricing page requires clicking into each plan separately to compare features
- Long page with CTA only at the top — visitor must scroll all the way back
- Key benefits mentioned once at the top but not reinforced near the conversion point

**Severity:** Suggestion — Visitors scan; they don't memorize. Repeat what matters.

---

## 7. Flexibility and Efficiency of Use

**Principle:** Provide shortcuts for experienced visitors while remaining accessible to new ones.

**What to check on a landing page:**
- [ ] Quick-access links to key sections (Pricing, Features, FAQ) in the nav
- [ ] "Skip to content" link for keyboard users
- [ ] Multiple conversion paths (direct signup AND "book a demo" for different buyer types)
- [ ] Anchor links or table of contents on long pages
- [ ] Return visitors can quickly find the CTA without reading everything again

**Common violations:**
- No navigation at all — single-page scroll with no way to jump to sections
- Only one conversion path (e.g., "Book a demo" but no self-serve option)
- No way to quickly get to pricing (buried at the bottom of a 10-section page)

**Severity:** Suggestion — Power users (comparison shoppers, returning visitors) need efficient paths.

---

## 8. Aesthetic and Minimalist Design

**Principle:** Pages should not contain information that is irrelevant or rarely needed. Every element should serve the conversion goal.

**What to check on a landing page:**
- [ ] No unnecessary elements competing with the primary CTA
- [ ] Content is focused — every section moves toward the conversion goal
- [ ] Adequate whitespace (not cramming too much into the viewport)
- [ ] Images and graphics support the message (not just decorative)
- [ ] Social media links don't distract from the primary conversion goal

**Common violations:**
- Social media icons in the header (sending visitors AWAY from the conversion page)
- Decorative animations that distract from the value proposition
- "About the founder" section that's longer than the product description
- Stock photos that add no information (smiling businesspeople, abstract gradients)
- Sidebar with unrelated content competing for attention

**Severity:** Warning — Every irrelevant element dilutes the conversion message. Less is more.

---

## 9. Help Users Recognize, Diagnose, and Recover from Errors

**Principle:** Error messages should be in plain language, indicate the problem, and suggest a solution.

**What to check on a landing page:**
- [ ] Form error messages appear next to the field with the problem (not just a red banner at the top)
- [ ] Error messages say what went wrong AND how to fix it
- [ ] Error styling is visible (red border, icon) but not alarming
- [ ] Page-level errors (like "something went wrong") include a recovery action
- [ ] 404 pages have navigation back to the main site

**Common violations:**
- "Invalid input" with no indication of which field or what's wrong
- Error message only at the top of a long form — visitor can't find the offending field
- Red text on dark background (invisible error message)
- Form clears all fields after an error (visitor has to start over)

**Severity:** Warning — Bad error handling during signup or checkout is a direct conversion killer.

---

## 10. Help and Documentation

**Principle:** Even though it's better if the page works without explanation, visitors may need help. This should be easy to find and focused on the visitor's task.

**What to check on a landing page:**
- [ ] FAQ section addresses the top 5-7 concerns visitors would have
- [ ] "How it works" section explains the process in 3-4 simple steps
- [ ] Contact information or chat support is available but not intrusive
- [ ] Tooltip or explanatory text for complex features or pricing
- [ ] Pricing page explains what each feature means (not just feature names)

**Common violations:**
- No FAQ section at all
- FAQ with generic questions that don't address real objections
- "Contact us" is the only help, buried in the footer
- Complex pricing tiers with no explanation of what's included
- Technical feature names with no description of what they mean for the customer

**Severity:** Suggestion — FAQs and "how it works" sections directly impact conversion by reducing uncertainty.

---

## Using This in the Audit

When scoring the **First Impression** and **Copy and Messaging** dimensions, cross-reference against these heuristics:

- **Heuristics 2, 6, 8** map most directly to First Impression
- **Heuristics 2, 4, 8** map most directly to Copy and Messaging
- **Heuristics 1, 5, 9** map most directly to CTA (form interaction)
- **Heuristics 3, 10** map most directly to Trust and Social Proof
- **Heuristic 7** maps to Mobile and Accessibility

When a violation is found, note the heuristic number in the finding for reference, but explain the issue in plain English in the report.
