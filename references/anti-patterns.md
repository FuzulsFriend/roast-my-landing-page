# Anti-Patterns — Always-Wrong Patterns to Flag Immediately

These patterns are never acceptable on a landing page. Flag them on sight regardless of business type, industry, or context. Each one directly hurts visitors, conversion, or both.

---

## 1. `outline: none` Without Replacement

**What it is:** CSS that removes the focus indicator (the ring or border that shows which element is selected when tabbing with a keyboard) without adding a custom replacement.

**Why it's bad:** Keyboard users (including screen reader users, people with motor disabilities, and power users) can't see where they are on the page. It's like removing the mouse cursor. This is also a WCAG AA violation.

**The fix:** Either keep the default outline or replace it with a custom `:focus-visible` style that's at least 2px and has 3:1 contrast. Never remove focus styles globally.

---

## 2. `transition: all`

**What it is:** CSS that animates every property change on an element, instead of specifying which properties should animate.

**Why it's bad:** Causes unexpected animations, janky performance (especially on mobile), and layout shifts. When properties like `height`, `width`, or `margin` animate unintentionally, it looks broken. Also forces the browser to watch every property for changes, hurting performance.

**The fix:** Always specify which properties to transition: `transition: opacity 200ms ease, transform 200ms ease`. Never use `transition: all`.

---

## 3. Images Without Width and Height

**What it is:** `<img>` tags without explicit `width` and `height` attributes (or CSS equivalents), causing layout shift when images load.

**Why it's bad:** The page jumps around as images load. Visitors try to click a button, the layout shifts, and they click the wrong thing. This is the single most common cause of poor Cumulative Layout Shift (CLS) scores, which also hurts SEO.

**The fix:** Add `width` and `height` attributes to every `<img>` tag that match the image's aspect ratio. The browser reserves space before the image loads. Alternatively, use CSS `aspect-ratio`.

---

## 4. Icon Buttons Without Labels

**What it is:** Buttons or links that show only an icon (hamburger menu, close X, search magnifying glass) with no text label and no `aria-label`.

**Why it's bad:** Screen reader users hear "button" with no context. Even sighted users can misinterpret icons — a heart could mean "like", "favorite", "health", or "donate" depending on context.

**The fix:** Add `aria-label="Menu"`, `aria-label="Close"`, etc. to icon-only buttons. Better yet, add a visible text label next to the icon when space allows.

---

## 5. Auto-Playing Video With Sound

**What it is:** A video that starts playing with audio as soon as the page loads, without the visitor clicking play.

**Why it's bad:** Startles visitors, especially in quiet environments (offices, libraries, public transport). Many visitors will immediately close the tab. Also violates WCAG success criterion 1.4.2 (Audio Control). Browser autoplay policies may block it anyway, causing broken behavior.

**The fix:** Videos can autoplay muted (with visible controls). Sound should only play after the visitor explicitly clicks play. Always show pause/mute controls.

---

## 6. Popup or Modal on Page Load

**What it is:** A popup, overlay, or modal that appears within the first 5 seconds of landing on the page, before the visitor has read anything.

**Why it's bad:** The visitor hasn't even decided if the page is relevant yet. Interrupting them with "Subscribe to our newsletter!" before they've read a single word is hostile. Google also penalizes intrusive interstitials on mobile for SEO.

**The fix:** If you must use a popup, trigger it on exit-intent (cursor moving toward the browser close button) or after meaningful engagement (scrolled 50%+ or spent 30+ seconds). One popup maximum per visit.

---

## 7. "Click Here" Link Text

**What it is:** Links where the clickable text says "click here", "here", "this link", or "read more" instead of describing the destination.

**Why it's bad:** Screen reader users navigate by listing all links on a page. A list of "click here", "click here", "click here" tells them nothing. It's also bad for SEO (search engines use link text to understand linked content) and bad for scannability (sighted users can't tell what the link goes to without reading the surrounding text).

**The fix:** Make the link text describe the destination: "Read our pricing guide" instead of "Click here to read our pricing guide." The link text should make sense out of context.

---

## 8. Carousel or Slider as Main Content

**What it is:** An auto-rotating carousel/slider as the hero section, cycling through multiple messages or images.

**Why it's bad:** Studies consistently show that users ignore carousels. Less than 1% of visitors click past the first slide. Auto-rotation means visitors can't read at their own pace. It also creates accessibility problems (moving content is hard to read, pause controls are often missing).

**The fix:** Pick the single strongest message and display it statically. If multiple messages are needed, stack them vertically so visitors can scroll at their own pace.

---

## 9. Horizontal Scroll on Mobile

**What it is:** Content that extends beyond the viewport width on mobile, forcing visitors to scroll sideways to see everything.

**Why it's bad:** Horizontal scroll breaks the fundamental expectation of mobile browsing (vertical scroll only). Visitors may not even realize there's more content to the right. It makes the page feel broken and unprofessional.

**The fix:** Set `max-width: 100%` on all content elements. Use responsive images. Test at 375px viewport width. Check for fixed-width elements, tables, or code blocks that don't wrap.

---

## 10. Text as Image

**What it is:** Important text (headlines, feature descriptions, pricing) rendered as an image instead of actual text.

**Why it's bad:** Can't be selected, copied, translated, resized, or read by screen readers. Looks blurry on high-DPI screens if not exported at 2x. Increases page load time. Impossible for search engines to index. Can't be updated without a designer.

**The fix:** Use HTML text with CSS styling. The only acceptable exception is logos.

---

## 11. Infinite Scroll Without Purpose

**What it is:** A landing page that loads more content endlessly as the visitor scrolls, with no clear ending.

**Why it's bad:** Visitors never reach the footer (where contact info, legal links, and secondary navigation live). There's no sense of completion or progress. The page feels exhausting rather than informative.

**The fix:** Landing pages should have a clear beginning, middle, and end. Use pagination or "load more" buttons for content lists, but the main landing page should have a definite structure.

---

## 12. Sticky Elements That Cover Content

**What it is:** Fixed/sticky banners, cookie notices, chat widgets, or navigation bars that permanently cover a significant portion of the viewport, especially on mobile.

**Why it's bad:** On a 667px mobile viewport, a 60px sticky header + 80px cookie banner + 60px chat widget = 200px of screen space taken up by non-content. Visitors see less than half the page. Touch targets may overlap.

**The fix:** Cookie banners should be dismissible. Sticky headers should be compact (under 50px). Chat widgets should minimize. Never stack more than one sticky element. Test on mobile — if more than 15% of the viewport is fixed elements, it's a problem.

---

## 13. No HTTPS

**What it is:** The page loads over HTTP instead of HTTPS, or loads over HTTPS but includes HTTP resources (mixed content).

**Why it's bad:** Browsers show "Not Secure" warnings. Visitors (especially those entering payment or personal info) will leave. It's also an SEO ranking factor — Google penalizes HTTP pages. Mixed content can cause images or scripts to fail loading.

**The fix:** Install an SSL certificate (free from Let's Encrypt). Redirect all HTTP traffic to HTTPS. Fix any mixed content by updating resource URLs to HTTPS.

---

## 14. Misleading CTA or Dark Patterns

**What it is:** CTA buttons that don't do what they say, trick the visitor into unintended actions, or use manipulative design to force a choice.

**Examples:**
- "Download Free" button that actually starts a paid checkout
- "No thanks, I don't want to grow my business" as the dismiss option (shaming)
- Pre-checked checkboxes for newsletter signup or terms agreement
- Close button that's actually a confirmation button
- "Free trial" that requires a credit card with no clear disclosure

**Why it's bad:** Destroys trust immediately. May violate consumer protection laws in many jurisdictions. Visitors who feel tricked never come back and often leave negative reviews.

**The fix:** Every CTA must honestly describe what happens next. Dismiss options should be neutral ("No thanks" or "Maybe later"). Checkboxes should never be pre-checked. Free means free — no hidden catches.

---

## 15. Background Music or Sound Effects

**What it is:** Any audio that plays as part of the page experience (background music, hover sound effects, scroll-triggered audio).

**Why it's bad:** Visitors don't expect audio from a webpage. It's disruptive in shared spaces, startling for some users, and creates accessibility issues. It adds to page load time. Most visitors will immediately look for a way to stop it — and if they can't, they'll close the tab.

**The fix:** No audio should play without explicit user interaction (clicking a play button). This is a simpler version of the auto-playing video rule — but it applies to any audio element.

---

## 16. Fixed Background Images (Parallax) on Mobile

**What it is:** `background-attachment: fixed` used for parallax scrolling effects on mobile devices.

**Why it's bad:** iOS Safari and many Android browsers don't support `background-attachment: fixed` properly. The effect either doesn't work (image just sits static), causes jarring visual glitches, or destroys scroll performance. It also makes the background image uncacheable in some implementations.

**The fix:** Disable parallax on mobile viewports entirely (use `background-attachment: scroll` in mobile media queries). If parallax is critical to the design, use JavaScript-based parallax that degrades gracefully.

---

## 17. Aggressive Cookie/Consent Banners

**What it is:** Cookie consent banners that cover a large portion of the screen, have a brightly colored "Accept All" button but a tiny, hard-to-find "Manage Preferences" link, or reappear after being dismissed.

**Why it's bad:** While cookie consent is legally required in many regions, aggressive implementation creates a hostile first impression. Visitors associate the page with annoyance before they've read a word of content. Dark patterns in consent banners (making "reject" hard to find) also violate GDPR enforcement guidance.

**The fix:** Make "Accept" and "Reject" or "Manage" equally visible and easy to click. Keep the banner compact. Remember the visitor's choice so it doesn't reappear. Never block the entire page behind a consent wall.

---

## Using Anti-Patterns in the Audit

When any of these patterns is found:

1. **Flag it immediately** in the findings with severity "Critical" or "Warning"
2. **Apply the penalty** listed in `scoring-rubric.md` (Anti-Pattern Penalties section)
3. **Explain in plain English** — the report should describe the impact on real visitors, not reference the anti-pattern by number
4. **Include the fix** — every anti-pattern has a clear solution

### Severity Classification

| Severity | Anti-Patterns |
|----------|--------------|
| **Critical** (always mention in Top 3 Roasts) | #5 Auto-playing video, #6 Popup on load, #13 No HTTPS, #14 Dark patterns |
| **Warning** (mention if in top issues) | #1 outline:none, #2 transition:all, #3 No image dimensions, #8 Carousel hero, #9 Horizontal scroll, #12 Sticky elements covering content, #17 Aggressive cookie banner |
| **Flag** (always note, may not be top 3) | #4 Icon buttons without labels, #7 "Click here" links, #10 Text as image, #11 Infinite scroll, #15 Background audio, #16 Parallax on mobile |
