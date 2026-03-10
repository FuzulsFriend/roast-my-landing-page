# WCAG Essentials for Landing Pages

8 accessibility rules that matter most for landing pages, explained in plain English. Based on WCAG 2.2 AA.

---

## Rule 1: Text Contrast

**What it means:** The text on your page needs to be readable against its background. Light gray text on a white background is hard for many people to read — not just people with vision problems.

**The standard:**
- Regular text (under 18px bold or under 24px normal): 4.5:1 contrast ratio minimum
- Large text (18px bold or 24px+ normal): 3:1 contrast ratio minimum
- UI components and meaningful graphics: 3:1 minimum

**Why it matters:** About 8% of men and 0.5% of women have some form of color vision deficiency. Low contrast text is also hard to read in sunlight, on cheap monitors, and for anyone over 40 whose eyes are getting worse.

**How to check:**
- Use a contrast checker tool (WebAIM contrast checker, Chrome DevTools color picker)
- In text-only analysis: look for light gray body text (#999, #aaa, #bbb on white), white text on light-colored backgrounds, or placeholder text used as actual content
- Check buttons: text inside buttons must also meet contrast requirements

**Common violations:**
- Placeholder text (#999) used as form labels
- Light gray footer text ("it's not important" is not an excuse)
- White text on a gradient or image without a background overlay
- "Disabled" looking buttons that are actually clickable
- Decorative text that still conveys information

---

## Rule 2: Image Alt Text

**What it means:** Every meaningful image needs a text description. Screen readers can't see images — they read the alt text instead. If there's no alt text, the screen reader either skips the image or reads the filename ("IMG_4837.jpg"), which is useless.

**The standard:**
- Meaningful images (product screenshots, team photos, infographics): descriptive alt text
- Decorative images (background patterns, dividers): empty alt attribute (alt="")
- Images of text: alt text should contain the same text (but avoid images of text entirely)

**Why it matters:** Screen reader users (blind and low-vision visitors) rely entirely on alt text to understand images. Search engines also use alt text for image indexing.

**How to check:**
- Look at the HTML for img tags. Check if alt attributes exist and are descriptive.
- Flag: alt text that's just the filename ("hero-image.png")
- Flag: missing alt attributes entirely (not the same as alt="")
- Flag: all images have identical alt text ("image")

**Common violations:**
- No alt attributes on any images (the most common violation)
- Alt text that says "image" or "photo" with no description
- Logo images without alt text (should say the company name)
- Product screenshots with no description of what's shown
- Hero images with decorative alt when they actually convey meaning

---

## Rule 3: Keyboard Navigation

**What it means:** Everything on the page that can be clicked with a mouse must also be usable with a keyboard. Some visitors navigate entirely with the Tab key (people with motor disabilities, power users, screen reader users).

**The standard:**
- All interactive elements (links, buttons, form fields) reachable with Tab
- Focus order follows visual order (top to bottom, left to right)
- No "keyboard traps" where Tab gets stuck in a section
- Escape key closes modals and popups

**Why it matters:** About 4% of adults have a motor disability that makes mouse use difficult or impossible. Keyboard navigation is also essential for screen reader users.

**How to check:**
- If Playwright is available: use Tab key simulation to navigate the page
- In code: look for `tabindex="-1"` on interactive elements (removes from tab order)
- Look for click handlers on div/span elements without role="button" and tabindex="0"
- Check for `onKeyDown` handlers on custom interactive elements

**Common violations:**
- Custom dropdown menus that only work with mouse clicks
- Modal dialogs that can't be closed with Escape
- Hamburger menu that opens on click but can't be activated with Enter/Space
- Interactive cards where the entire card is wrapped in a div with onClick but no keyboard support
- Skip navigation link missing (first focusable element should be "Skip to content")

---

## Rule 4: Focus Indicators

**What it means:** When a visitor tabs through the page, they need to see which element is currently focused — like a cursor for the keyboard. Removing the default focus outline without adding a replacement makes the page unusable for keyboard navigators.

**The standard:**
- Every focusable element must have a visible focus indicator
- Focus indicator must have at least 3:1 contrast against its surroundings
- Focus indicator must be at least 2px thick

**Why it matters:** Without focus indicators, keyboard users can't see where they are on the page. It's like removing the mouse cursor.

**How to check:**
- Search CSS for `outline: none`, `outline: 0`, or `:focus { outline: none }` without a replacement style
- Check if `:focus-visible` styles are defined as replacements
- If screenshots are available: tab through and check if focus is visible

**Common violations:**
- `*:focus { outline: none }` in the global CSS (removes ALL focus indicators)
- `outline: none` on buttons and links for "cleaner design"
- Custom focus styles that are too subtle (1px light gray border)
- Focus indicator only works on some elements, not all
- Focus styles match hover styles exactly (visitor can't tell the difference)

---

## Rule 5: Form Labels

**What it means:** Every form field needs a proper label that tells the visitor what to type. Placeholder text that disappears when you start typing is NOT a label — once the visitor starts typing, they can't see what the field was for.

**The standard:**
- Every input, select, and textarea must have an associated label element
- Labels must be visible (not just for screen readers)
- Placeholder text is a hint, not a replacement for labels
- Required fields must be clearly indicated

**Why it matters:** Screen readers announce the label when a field receives focus. Without labels, screen reader users hear "edit text" with no context. Sighted users also benefit — they can verify which field they're filling in.

**How to check:**
- Look for `<label for="fieldId">` matching each `<input id="fieldId">`
- Flag: inputs with placeholder text but no visible label
- Flag: labels that say "Field 1", "Field 2" or other non-descriptive text
- Check that required fields are marked with more than just color (asterisk + label text)

**Common violations:**
- Using only placeholder text as the label (disappears on focus)
- No label element at all — just a heading above a group of fields
- Labels present in HTML but visually hidden (sr-only) while placeholder text serves as the visible label
- Generic labels ("Enter value", "Your input")
- Error messages not associated with the field they refer to

---

## Rule 6: Touch Targets

**What it means:** On mobile devices, buttons and links need to be big enough to tap accurately with a finger. Small targets cause mis-taps, frustration, and accidental navigation.

**The standard:**
- Minimum touch target size: 44x44 CSS pixels (WCAG) / 48x48 (Google recommendation)
- Minimum spacing between touch targets: 8px
- Exception: inline text links in paragraphs (context makes them identifiable)

**Why it matters:** About 75% of web traffic is mobile. Fingers are imprecise — the average fingertip covers about 44px. Smaller targets cause errors, especially for people with motor difficulties or large fingers.

**How to check:**
- Measure button/link dimensions in the mobile viewport
- Check padding on navigation links (often too tight on mobile)
- Look for icon-only buttons (typically too small without adequate padding)
- Check spacing between close-together links (footer link lists are common offenders)

**Common violations:**
- Icon buttons with no padding (the icon is 20px, but the tap target needs to be 44px)
- Navigation links with only 8px vertical padding (tap target under 30px)
- Social media icon links at 24x24px
- Close buttons (X) on modals that are 20x20px
- Footer links stacked with only 4px between them

---

## Rule 7: Heading Hierarchy

**What it means:** Headings (H1, H2, H3) create an invisible outline of the page. Screen reader users navigate by jumping between headings — if the heading structure is broken, they can't understand the page layout.

**The standard:**
- Exactly one H1 per page (the main page heading)
- Headings follow logical order: H1 then H2, H2 then H3 (no skipping levels)
- Headings are used for structure, not just for styling (don't use H3 because you want smaller bold text)
- Every section of the page should have a heading

**Why it matters:** Screen reader users often start by listing all headings to understand page structure. Broken heading hierarchy makes the page feel disorganized and hard to navigate. It also hurts SEO — search engines use headings to understand page structure.

**How to check:**
- List all heading elements in DOM order: H1, H2, H3, etc.
- Flag: multiple H1 tags
- Flag: skipped levels (H1 followed by H3, with no H2)
- Flag: heading tags used purely for visual styling
- Flag: important sections with no heading at all

**Common violations:**
- Multiple H1 tags (company name as H1 in the header AND main headline as H1)
- Skipping from H1 to H3 or H4 (usually because the developer wanted a smaller font)
- Using bold paragraphs instead of headings for section titles
- No headings at all on single-page landing pages (one long page with no structure)
- Logo text in an H1 tag in the navigation bar

---

## Rule 8: Color Not Sole Indicator

**What it means:** Information can't be communicated through color alone. If the only way to know something is an error is that the text is red, colorblind visitors will miss it.

**The standard:**
- Links must be distinguishable from surrounding text by more than just color (underline, bold, icon)
- Error states must use an icon, text label, or border in addition to color change
- Charts/graphs must use patterns, labels, or shapes in addition to colors
- Required fields must use more than just a red asterisk (add "required" text)

**Why it matters:** About 1 in 12 men have some form of color blindness. Red-green color blindness is most common — so red error messages and green success messages can be invisible to these visitors.

**How to check:**
- Look at links within body text — are they underlined or only a different color?
- Check form error states — is there an icon or text in addition to the red color?
- Look for status indicators (success/warning/error) — do they rely solely on green/yellow/red?
- Check if any interactive elements are only distinguished by color from non-interactive elements

**Common violations:**
- Links in body text that are only blue (no underline) — hard to spot for colorblind users
- "Required" indicated only by a red asterisk with no tooltip or label
- Success/error messages that only change the border color of the input
- Charts using red/green to indicate good/bad with no labels
- Navigation links where the "active" state is only a color change

---

## Scoring Integration

These 8 rules feed into the **Mobile and Accessibility** dimension of the scoring rubric. Each rule maps to a checkpoint:

| Rule | Rubric Checkpoint | Points |
|------|------------------|--------|
| 1. Text Contrast | Color contrast (WCAG AA) | 15 |
| 2. Image Alt Text | Image alt text | 10 |
| 3. Keyboard Navigation | Keyboard navigation | 10 |
| 4. Focus Indicators | Keyboard navigation (included) | (included in #3) |
| 5. Form Labels | (bonus check — not a separate checkpoint) | -- |
| 6. Touch Targets | Touch targets | 15 |
| 7. Heading Hierarchy | Heading hierarchy | 8 |
| 8. Color Not Sole Indicator | Color not sole indicator | 7 |

Rules 1 and 6 carry the most weight because they affect the most visitors (everyone on mobile, everyone with less-than-perfect vision).

---

## Quick Pass/Fail Test

If you can only check 3 things, check these:

1. **Contrast:** Is there any light gray text on the page? If yes, check its ratio.
2. **Alt text:** Do the main images have alt attributes? Open the HTML and search for `<img`.
3. **Touch targets:** On mobile, are all buttons at least 44px tall? Check the CTA button specifically.

If all 3 pass, the page probably covers the basics. If any fail, dig deeper into the other rules.
