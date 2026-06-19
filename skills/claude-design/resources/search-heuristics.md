# Search Heuristics

This file is read by the `claude-design` skill during Stage 3 (Library Discovery) and Stage 4 (Component Hunt). It contains stable knowledge about how to find component libraries via web search — the kind of knowledge that does not go stale.

---

## Search query templates

Run multiple of these per generation, varying by aesthetic direction and component category. The `{X}` placeholders are filled by Claude based on the brief and aesthetic.

### For library discovery (Stage 3)

```
"best react component libraries {YEAR}"
"best tailwind ui component libraries {YEAR}"
"shadcn ui alternatives {YEAR}"
"open source react ui kits {AESTHETIC} {YEAR}"
"github trending react ui components {YEAR}"
"awesome react components"
"react animation libraries {YEAR}"
"motion-primitives alternatives {YEAR}"
"tailwind landing page templates github {YEAR}"
"astro component libraries {YEAR}"
```

Replace `{YEAR}` with the current year. Replace `{AESTHETIC}` with the chosen direction (e.g., "brutalist", "minimal", "glassmorphism").

### For category-specific component hunt (Stage 4)

```
"{CATEGORY} component {AESTHETIC} tailwind react github"
"{CATEGORY} animated tailwind {YEAR}"
"{CATEGORY} {AESTHETIC} ui design github"
"hero section {AESTHETIC} react motion github"
"pricing table {AESTHETIC} tailwind copy paste"
"testimonial carousel {AESTHETIC} react"
"footer design {AESTHETIC} accessible"
"navbar {AESTHETIC} react motion sticky"
"cta button {AESTHETIC} animated"
"feature grid {AESTHETIC} bento"
```

### For animation-specific work

```
"gsap scrolltrigger examples github {YEAR}"
"framer motion animations github {YEAR}"
"motion library examples react"
"css only animations {AESTHETIC}"
"awwwards site clone github" (cuidado: muchos resultados son spam)
"codrops experiments {YEAR}"
```

### For design inspiration (when stuck on aesthetic)

```
"awwwards sites {YEAR} {INDUSTRY}"
"siteinspire {INDUSTRY} {YEAR}"
"httpster {INDUSTRY} {YEAR}"
"lapa ninja landing pages {INDUSTRY}"
```

---

## Quality filters

Apply these to every library or component candidate. Reject anything that fails 3+ filters.

### Hard filters (reject if any fails)

| Filter | How to check |
|---|---|
| **Has live demo or screenshots** | Look for `/components`, `/showcase`, `demo` in URL or README |
| **License is permissive** | MIT, ISC, Apache 2.0, BSD. Avoid GPL or "free for non-commercial" |
| **Compatible with React + Tailwind** | Check README/docs for "Tailwind" mention; React is usually obvious |
| **Not abandoned** | Last commit < 12 months ago |

### Soft filters (prefer higher score)

| Filter | Threshold | Weight |
|---|---|---|
| GitHub stars | > 1,000 = good, > 5,000 = great, > 20,000 = exceptional | High |
| Last commit | < 3 months = green, < 6 = yellow, < 12 = orange | High |
| Has TypeScript types | Bonus | Medium |
| Has accessible primitives (Radix-based) | Bonus | Medium |
| Has documentation site | Bonus | Medium |
| Author has reputation (Vercel, shadcn, etc.) | Bonus | Low |

### Anti-patterns (auto-reject)

These are signals of low quality or generic AI-style work:

- README is mostly emojis and buzzwords with little substance
- No screenshots/demos and no code examples
- "Powered by AI" or "GPT" in description (not always bad, but suspicious for design libs)
- Single-author project with no contributors and no recent activity
- Components that are obviously copies of shadcn with no value-add
- Promotes paid course/discord prominently in README (often skill-flipping)

---

## Known stable aggregator URLs

These URLs change rarely; they're useful starting points when WebSearch returns garbage.

### GitHub aggregators

```
https://github.com/brillout/awesome-react-components
https://github.com/topics/react-components
https://github.com/topics/tailwind-components
https://github.com/topics/ui-library
https://github.com/trending/typescript?since=monthly
https://github.com/trending/javascript?since=monthly
```

### Curated lists (websites)

```
https://bestofjs.org/projects?tags=ui&sort=downloads
https://react.libhunt.com/categories/2418-ui-components
https://www.componentdriven.org/
https://uikits.io/
```

### Specific libraries known to be high quality (as of 2026)

These are starting points; do NOT bake them in as the catalog. Always re-validate freshness before using:

- shadcn/ui — base, accessible, copy-paste pattern
- Magic UI — marketing animations
- Aceternity UI — flashy heroes, 3D effects
- Motion-Primitives — Emil Kowalski's primitives
- kokonut UI — minimalist refined
- HextaUI — backgrounds and gradients
- Tailark — full marketing blocks
- Hyper UI — Tailwind blocks
- Park UI — Panda CSS alternative

If your search returns these, fine. If your search reveals something newer/better, prefer that.

---

## Library type taxonomy

Classify each candidate library by what it offers. Different taxonomies serve different needs.

| Type | Description | Use for |
|---|---|---|
| **Base / Headless** | Unstyled accessible primitives | Foundation for custom styling (Radix UI, Headless UI, Ariakit) |
| **Styled base** | Themed, accessible, styled | Default starting point (shadcn, Park UI) |
| **Motion-focused** | Animation-heavy, marketing | Heroes, features, eye-candy (Magic UI, Aceternity, Motion-Primitives) |
| **Marketing blocks** | Full sections, ready to drop | Pricing, testimonials, FAQ (Tailark, Hyper UI) |
| **Animation library** | Just primitives, BYO components | Custom motion (GSAP, Motion, anime.js) |
| **Background/effect** | Decorative atmospheres | Hero backdrops (HextaUI, magicpattern) |
| **Aggregator/gallery** | Index of components from many sources | Discovery (21st.dev, ui-libs) |

A complete page typically uses 2-4 types: 1 styled base + 1-2 motion-focused + maybe an effect lib.

---

## Search-then-filter algorithm

Pseudocode for how Claude executes Stage 3 (library discovery):

```
1. Determine aesthetic direction (from Stage 2) and required categories (from Stage 1).

2. For each search query template, run WebSearch:
   - Read titles + snippets of top 10 results
   - Identify candidate libraries mentioned
   - Note any "best of" articles for further reading

3. For each unique candidate library:
   a. WebFetch the library's GitHub repo (or main site)
   b. Extract: stars, last commit, license, components offered, screenshots
   c. Apply hard filters (reject if any fail)
   d. Apply soft filters (compute score)

4. Rank candidates by score within each library type.

5. Build session catalog:
   - 1-2 styled base libraries
   - 2-3 motion-focused libraries (matched to aesthetic)
   - 0-1 marketing blocks library (if multipage or lots of standard sections)
   - 1-2 animation libraries (Motion almost always; GSAP if scroll-heavy)
   - 0-1 effect/background library

Total: 5-9 libraries. More than that wastes Stage 4 time.

6. Output session catalog with brief justification per choice.
```

---

## Anti-patterns to filter out (frontend-design wisdom)

When evaluating a library or component, REJECT if you see:

### Typography anti-patterns
- Inter as primary heading font (overused in AI demos)
- Roboto or system fonts on a "premium" library
- Space Grotesk used 3+ years in a row everywhere
- Default Tailwind `font-sans` with no overrides
- All headings in the same weight (no hierarchy)

### Color anti-patterns
- Purple gradient on white background (the AI cliché)
- Pastel rainbow logos and section dividers
- Pure-black text on pure-white (no warmth, no consideration)
- "Modern" palette = generic blue/purple/pink + grays
- Indigo-500 to Purple-500 gradient (Tailwind default vibes)

### Layout anti-patterns
- Centered everything, all sections look the same
- Predictable: hero → 3-col features → testimonials → pricing → CTA → footer (in that exact order)
- No section overlap, asymmetry, or visual surprise
- Equal-weight grids with no focal point

### Animation anti-patterns
- Bouncy spring on EVERY element (overuse of `damping: 10`)
- Fade-in on scroll for everything (lazy)
- Particle systems with no purpose
- Infinite loops without `prefers-reduced-motion` fallback
- Animations longer than 600ms on UI interactions

When you see ANY of these, downgrade the candidate. When you build, AVOID THEM ENTIRELY.

---

## Caching within session

Within a single skill invocation, maintain a mental cache:

- `sessionLibraries[name] = { score, components, fetched_at }`
- `sessionComponents[category] = [winner, runner_up, runner_up2]`

If user iterates ("cambia el hero"), reuse `sessionComponents["hero"]` runner-ups. Do NOT re-search.

If user starts a new generation in the same conversation, reuse `sessionLibraries` if aesthetic direction is similar; re-search if drastically different.

---

## When all search fails (last-resort fallback)

If 3 search attempts return no usable results AND fetched aggregators are also empty:

Use this minimal embedded list of libraries known to exist as of skill version 1.0.0:

- `https://github.com/shadcn-ui/ui` (base styled)
- `https://github.com/magicuidesign/magicui` (motion)
- `https://github.com/aceternity/ui` (flashy)

Fetch these directly. Generate a deliberately-restrained design (because we have less to work with). Tell the user: "Search results were limited; output uses fallback libraries. Quality may be below standard."

This fallback should fire < 1% of the time. If it fires often, the search heuristics need updating.
