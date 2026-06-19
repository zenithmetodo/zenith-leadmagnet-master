# Static Audit Checklist (single-HTML)

This file is read by the `claude-design` skill during Stage 6 (Audit). It defines the checks Claude runs against a generated `.html` file before declaring it done. Also used by the `/audit` slash command on existing pages.

**Audit type**: Static (no runtime execution). Reads the single HTML file, applies pattern checks. Correlates ~85% with real Lighthouse scores.

**Output contract reminder**: This skill produces ONE self-contained `.html` file. There is no Astro project, no `<Image>` component, no `npm run build`. All checks below apply to vanilla HTML.

---

## Hard checks (BLOCK delivery if any fail)

These must pass. If they fail, auto-fix the issue and re-audit. Do NOT deliver a project that fails any hard check.

### H1 — Viewport meta tag

**Check**: The `<head>` of the HTML file contains:
```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

**If missing**: Insert into `<head>`.

---

### H2 — All buttons and links have accessible names

**Check**: For every `<button>` and `<a>` element, verify ONE of:
- Has visible text content (e.g., `<button>Click me</button>`)
- Has `aria-label="..."`
- Has `aria-labelledby="some-id"`
- Wraps an `<img>` with `alt`

**Audit pattern** (mental grep):
```
Find: <button[^>]*>(\s*<svg[^>]*>[^<]*<\/svg>\s*|\s*)<\/button>
       <a[^>]*>(\s*<svg[^>]*>[^<]*<\/svg>\s*|\s*)<\/a>
```

If matches lack `aria-label`, that's a fail.

**If fail**: Add `aria-label` describing the action (e.g., `aria-label="Open menu"`, `aria-label="Close dialog"`).

---

### H3 — All images have alt text or role="presentation"

**Check**: Every `<img>` and Astro `<Image>` has:
- `alt="descriptive text"` for content images
- `alt=""` AND `role="presentation"` for decorative-only images

**If fail**:
- If image is decorative (background, divider): add `alt=""` and `role="presentation"`
- If image is content: ASK USER for alt text rather than guessing

---

### H4 — Color contrast meets WCAG AA

**Check**: For every text/background combination in design tokens:
- Body text on body background: contrast ratio ≥ 4.5:1
- Large text (≥ 18px or ≥ 14px bold): ≥ 3:1
- UI components (buttons, focus rings): ≥ 3:1

**How to compute mentally**:
Use the WCAG formula:
```
L_text = relative luminance of text color
L_bg = relative luminance of background
contrast = (max(L_text, L_bg) + 0.05) / (min(L_text, L_bg) + 0.05)
```

If you can't be confident in mental calculation, use online tools or err on the side of higher contrast (text always near pure white or pure black on opposite background).

**If fail**: Adjust the lighter tone darker, or the darker tone lighter, until contrast passes. Update CSS custom properties accordingly.

---

### H5 — `prefers-reduced-motion` is respected globally

**Check**: The `<style>` block in the HTML file contains a complete reduced-motion block:

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
  /* Specific overrides for visual-only effects */
  .marquee, .infinite-scroll, .auto-rotate {
    animation: none !important;
  }
  .parallax {
    transform: none !important;
  }
}
```

**If missing**: Insert canonical block above into the `<style>` block.

**Additionally**: For any JS-driven animation (cursor RAF loop, magnetic handlers, IntersectionObserver triggers), verify the JS short-circuits when `matchMedia('(prefers-reduced-motion: reduce)').matches` is true. The template's JS already does this — if you removed those guards, fail the check.

---

### H6 — (removed in v2)

The Astro `<Image>` check from v1 does not apply to single-HTML output. If the page uses raw `<img>` tags with external URLs or data URIs, they must still have `alt`/`aria-hidden` (covered by H3) and ideally explicit `width`/`height` attributes to avoid layout shift (S4).

---

### H7 — Touch targets ≥ 44×44 px

**Check**: For every interactive element (`button`, `a`, `[role=button]`, form inputs):
- Computed `min-height` or actual rendered height ≥ 44px
- Computed `min-width` or actual rendered width ≥ 44px

**Audit pattern**: In Tailwind, look for buttons with classes like `h-8`, `h-10` (= 32px, 40px) and flag them. Acceptable: `h-11` (44px), `h-12` (48px), `min-h-[44px]`.

**If fail**: Add `min-h-[44px] min-w-[44px]` or upgrade to `h-11`+ Tailwind classes. Especially on mobile breakpoints.

---

### H8 — Fonts use `font-display: swap`

**Check**: Google Fonts URLs include `&display=swap`:
```html
<link href="https://fonts.googleapis.com/css2?family=...&display=swap" rel="stylesheet">
```

OR self-hosted fonts have `font-display: swap` in `@font-face`.

**If fail**: Add `&display=swap` to Google Fonts URL, or add to `@font-face`.

---

### H9 — No horizontal overflow on body

**Check**: `body` (or `html`) has either:
- `overflow-x: hidden` or `overflow-x: clip`
- OR all child elements respect `max-width: 100vw`

**Audit pattern**: Look for elements with `width: 110vw`, `min-width: 1200px`, or unbounded `whitespace: nowrap` content (e.g., the footer watermark or marquee). These are common offenders.

**If fail**: Add `overflow-x: clip` to `body` in the `<style>` block. Identify offending elements and constrain them with `overflow: hidden` on the parent.

**Special case — wheel hijack**: If you find ANY code that calls `e.preventDefault()` on `wheel` events, that is a hard fail. Remove it. macOS/iOS inertial scroll fights with wheel hijacking. Native scroll only.

---

### H10 — Forms have associated labels

**Check**: Every `<input>`, `<textarea>`, `<select>` has:
- A `<label for="id">` pointing to it
- OR is wrapped inside a `<label>`
- OR has `aria-label` / `aria-labelledby`
- Placeholder alone is NOT sufficient

**If fail**: Wrap input in `<label>` or add `aria-label`. Visible labels are preferred over `aria-label` for sighted users.

---

### H11 — Semantic HTML structure

**Check**: Page uses semantic landmarks:
- `<header>` for site/section headers
- `<main>` (one per page, contains primary content)
- `<nav>` for navigation regions
- `<footer>` for site/section footers
- `<section>` for thematic groupings (with `aria-labelledby` or visible heading)
- `<article>` for self-contained content (blog posts, cards with content)

**If fail**: Replace generic `<div>` wrappers with semantic equivalents.

---

### H12 — Skip-to-main-content link

**Check**: Layout has a "skip to main content" link as first focusable element:

```html
<a href="#main" class="sr-only focus:not-sr-only">Skip to main content</a>
<!-- ... -->
<main id="main">...</main>
```

**If missing**: Insert into `Base.astro` layout.

---

## Soft checks (WARN but don't block)

Report these but proceed with delivery. User may choose to address.

### S1 — File size

**Estimate**: Total HTML file size (CSS + JS + markup all inline).

**Threshold**: < 100 KB target for a typical landing page. Warn at 100-200 KB. Strong warn at > 300 KB (likely indicates inlined assets that should be removed or referenced externally).

**Mitigation**:
- Remove unused CSS rules
- Remove decorative JS (custom cursor, etc.) if the brief doesn't justify them
- Don't inline base64 images larger than ~5 KB — reference them externally or simplify the design

---

### S2 — Hero image priority

**Check**: Hero section image has `loading="eager"` and `fetchpriority="high"`.

**If missing**: Suggest adding to user. Auto-fix if straightforward.

---

### S3 — Below-fold images lazy-loaded

**Check**: All `<Image>` or `<img>` below the fold have `loading="lazy"` (Astro `<Image>` does this by default; raw `<img>` doesn't).

---

### S4 — Cumulative Layout Shift mitigations

**Check**:
- All images have explicit `width` and `height` attributes (or Astro `<Image>` which auto-injects them)
- No content reflows after fonts load (use `font-display: swap` + size-adjust where possible)

---

### S5 — Long animations have escape hatch

**Check**: Animations longer than 1500ms or infinite have:
- `prefers-reduced-motion` fallback (already H5)
- Optional: a "skip animation" button if animation is mandatory before content shows

---

### S6 — Color usage is balanced

**Check**: One dominant color (60%), one secondary (30%), one accent (10%). NOT 5 colors evenly distributed.

If you see lots of `bg-purple-500 / bg-blue-500 / bg-pink-500 / bg-green-500` everywhere, warn: "Color palette feels scattered; suggest committing to one accent."

---

### S7 — Font loading optimization

**Check**: Fonts are preconnected:
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
```

If using self-hosted, fonts are preloaded:
```html
<link rel="preload" href="/fonts/main.woff2" as="font" type="font/woff2" crossorigin>
```

---

### S8 — (removed in v2)

Code splitting is not applicable to single-HTML output. If the user requests multiple pages, generate one `.html` per page and link between them with relative `href="other-page.html"`.

---

### S9 — Unused CSS

**Check**: Scan the `<style>` block for selectors that don't match any element in the body. Common offenders: copied utility classes from a different direction, leftover template helpers.

**If fail**: Remove the unused selectors to keep the file lean.

---

### S10 — Aesthetic consistency

**Check** (subjective but useful): Spot check:
- All buttons share the same shape/size pattern
- All cards share the same border radius
- All headings use the chosen display font
- Spacing follows a clear scale (e.g., 4/8/12/16/24/32/48/64)

If inconsistent: warn user with specific examples.

---

## Audit algorithm (how Claude executes)

When called from Stage 6 of `claude-design` workflow OR from `/audit` slash command:

```
1. Read all generated files:
   - SKILL.md project structure (src/**/*.astro, src/**/*.tsx, src/styles/*.css)
   - Layout files
   - Components
   - Stylesheet

2. For each Hard check (H1-H12):
   - Apply the check
   - If fail:
     - Apply auto-fix if known pattern
     - Re-check
     - If still fails after auto-fix: STOP and report to user
   - If pass: continue

3. For each Soft check (S1-S10):
   - Apply the check
   - If fail: log warning with specific file/line + suggestion
   - Continue regardless

4. Generate audit report:
   - Summary: X passed, Y warnings, Z failures (should be 0 failures by now)
   - List of warnings with mitigations
   - Suggestions for next iteration

5. If invoked from Stage 6 of generation: deliver project + report.
   If invoked from /audit: report only, ask if user wants to apply fixes.
```

---

## Auto-fix patterns

When a hard check fails and the fix is mechanical, apply it without asking:

| Failure | Auto-fix |
|---|---|
| Missing viewport meta | Insert canonical `<meta>` into `<head>` |
| Missing `prefers-reduced-motion` block | Insert canonical block from H5 above into `<style>` |
| Missing `aria-label` on icon-only button/link | Infer from context (e.g., arrow → wrap a meaningful link text or add `aria-label`); add |
| Touch target too small | Add `min-height: 44px; min-width: 44px` to the relevant CSS rule |
| Missing `font-display: swap` | Append `&display=swap` to Google Fonts URL |
| Missing `overflow-x: clip` on body when needed | Add to `body` in `<style>` |
| Missing skip link | Insert `<a class="skip" href="#main">Skip to main content</a>` as first body child |
| Wheel hijack present | Remove the entire wheel-event listener block |

When a hard check fails and the fix needs judgment (e.g., contrast), do NOT auto-fix without user confirmation. Report and pause.

---

## Lighthouse correlation note

This static audit predicts ~85% of Lighthouse mobile scores. The remaining 15% comes from:

- Hosting (CDN, server response time)
- Real network conditions
- Actual image dimensions/compression
- Third-party scripts (analytics, fonts loaded from external)
- JavaScript execution on real devices

Tell the user: "Static audit passed. Real Lighthouse score depends on hosting + network. Run `npm run build && npx lighthouse http://localhost:4321` after deploy for the actual score."

---

## When the audit fails repeatedly

If 3 auto-fix attempts can't pass H1-H12:

- Stop generation
- Report ALL failures with specific files/lines
- Ask user: "These need manual decisions: [list]. Want me to address one by one?"
- Do NOT deliver a project that fails hard checks.
