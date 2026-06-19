# Aesthetic Directions

This file is read by the `claude-design` skill during Stage 2 (Aesthetic Commitment). It contains 22 bold, distinctive aesthetic blueprints. Each is opinionated and complete — the skill picks ONE and commits.

**Meta-rules** (always apply):
1. Never repeat the same direction across two consecutive generations in the same conversation.
2. When inventing a new direction not listed here, justify each axis (typography, color, motion, layout) explicitly.
3. Never water down a direction toward "safe" — boldness > tepidness.
4. Match the direction to brief context (audience, industry, tone). Don't pick brutalist for a luxury jeweler.

---

## 1. Brutalist Editorial

**Vibe**: Stripped-back magazine aesthetic. Raw HTML feel intentionally exposed. Massive typography as the hero. Reads like a published manifesto.

**Typography**:
- Display: PP Editorial New, Söhne, GT Sectra, or Tiempos Headline. Massive sizes (10-20vw on hero). Negative letter-spacing on display.
- Body: Söhne Mono, JetBrains Mono, or Inter (when paired with mono context, Inter feels brutal not generic). Justified or hard-left.

**Color palette**:
- `#FFFFFF` (paper white) or `#F4EFE6` (cream)
- `#000000` (ink)
- `#FF3B30` (electric red) — single accent
- Rules: No gradients. No drop shadows. Borders are 1-2px solid black. Or no borders.

**Texture/effects**: Grain overlay (subtle, 2% opacity). Hard edges. Maybe a single noise texture on hero. No glow.

**Animation tone**: Snappy, mechanical. Cuts and reveals (not fades). Hover causes letter underlines, color inversion, or hard movement. No spring physics — `cubic-bezier(0.7, 0, 0.3, 1)` for everything.

**Best fit for**: Editorial publications, design studios, contrarian SaaS, intellectual products, minimalist agencies.

**Don't use for**: Family-friendly e-commerce, kids products, healthcare patient-facing.

---

## 2. Glassmorphism Cinematic

**Vibe**: Apple-keynote-meets-luxury-watch. Floating frosted panels over a moody backdrop. Color grading like a film still.

**Typography**:
- Display: Sora, Outfit, or PP Neue Montreal. Medium weight, generous line height, +2-4% letter-spacing on small caps.
- Body: Inter Variable, Outfit, or Inter Tight. Light to regular.

**Color palette**:
- Background: deep gradient mesh — e.g., `#0A0A1B` → `#1B0A2E` → `#0B1F2E`. Never flat black.
- Glass surfaces: `rgba(255,255,255,0.06)` with `backdrop-filter: blur(24px)` and a 1px white border at 10% opacity.
- Accent 1: A vivid mid-tone — e.g., `#7C3AED`, `#22D3EE`, or `#F0ABFC`.
- Accent 2: A warm complement — `#FB923C`, `#F59E0B`.

**Texture/effects**: Radial gradient glow behind hero text. Noise grain. Subtle vignette on hero. Slight chromatic aberration on logo.

**Animation tone**: Fluid, slow-motion. Spring physics with high damping. Scroll-linked parallax on glass cards. Soft glow pulses.

**Best fit for**: SaaS premium, finance/fintech serious, high-ticket coaching/courses, AI products.

**Don't use for**: Brutalist publications, kids/playful brands, e-commerce mass market.

---

## 3. Neo-Minimal Swiss

**Vibe**: Helvetica-tradition, but updated. Heavy whitespace. Mathematical grid. Restrained color. Looks like Spotify-meets-MUJI.

**Typography**:
- Display: ABC Diatype, Söhne, NB International, or Helvetica Neue Display. Tight letter-spacing.
- Body: Söhne, Söhne Breit, or Inter Tight.

**Color palette**:
- Background: `#FAFAFA` or pure `#FFFFFF`
- Text: `#0F0F0F`
- Single accent: a saturated mid-tone — `#FF5722` or `#005CFF` or `#00B86B`.
- Rule of thirds: 80% neutral, 15% secondary neutral, 5% accent.

**Texture/effects**: NONE. The texture IS the typography and grid.

**Animation tone**: Restrained. Fade-up reveals (200ms, ease-out). Hover underlines. No bouncy springs.

**Best fit for**: Design tools, B2B serious, minimalist e-commerce (luxury), portfolios.

**Don't use for**: Maximalist brands, kids, festivals.

---

## 4. Retro Y2K Web

**Vibe**: 2002 Geocities + Apple iLife UI. Glossy buttons. Chrome gradients. Beveled cards. Self-aware nostalgia.

**Typography**:
- Display: Druk, ITC Avant Garde, or Eurostile. Extreme weight contrasts.
- Body: Geist Mono, Söhne Mono.

**Color palette**:
- Pastels: `#FFE5F1`, `#C7E9FF`, `#D4FFE5`
- Sharp accent: hot pink `#FF1A8C` or electric blue `#0080FF`
- Dark: navy `#000033`

**Texture/effects**: Chrome gradients on buttons. Beveled 3D shadows (90s skeumorphism). Sparkle PNGs. Bubble cursor.

**Animation tone**: Playful, snappy. Scaling on hover. Confetti on CTA click.

**Best fit for**: Creators, lifestyle brands targeting Gen Z, indie products with personality.

**Don't use for**: Banks, healthcare, B2B serious.

---

## 5. Organic Botanical

**Vibe**: Hand-drawn elements, organic shapes, paper textures. Natural color palette. Reads like a high-end skincare brand.

**Typography**:
- Display: Recoleta, Playfair Display Italic, or Reckless. Slow, considered.
- Body: Söhne, GT Walsheim, or Inter Tight.

**Color palette**:
- Cream `#F8F4ED`, sage `#A8B5A0`, terracotta `#D4866B`, deep forest `#3F4E3D`, ink `#1C1B1A`.

**Texture/effects**: Paper noise overlay (5% opacity). Hand-drawn squiggles as dividers. SVG botanical illustrations sparingly. Subtle gradient washes.

**Animation tone**: Slow, breathing. Imagery fades in. Subtle parallax on illustrations. No sharp movements.

**Best fit for**: Wellness, skincare, food/beverage premium, holistic services, sustainable brands.

**Don't use for**: Tech B2B, fast-paced startups, fintech.

---

## 6. Cyberpunk Neon

**Vibe**: Blade Runner alleyway. Heavy neon outlines. Glitch effects. Dark base with hyper-saturated highlights.

**Typography**:
- Display: Druk Wide, Monument Extended, or PP Pangaia (italic).
- Body: JetBrains Mono, IBM Plex Mono.

**Color palette**:
- Base: `#0A0014` (deep purple-black)
- Neons: `#FF006E` (magenta), `#00F0FF` (cyan), `#FFD60A` (electric yellow)
- One muted: `#1A1B3A` (mid-tone purple) for surfaces.

**Texture/effects**: Glow on neon text. Scanlines optional. Glitch on hover (translate + RGB split). Grid background with perspective.

**Animation tone**: Sharp, glitchy. Text scrambles. Color cycling. Fast cuts.

**Best fit for**: Gaming, web3 (carefully), creator economy edgy, music/festivals, indie SaaS for devs.

**Don't use for**: Anything serious, finance, family.

---

## 7. Editorial Photography

**Vibe**: Vogue meets Apollo Magazine. Massive photography hero. Sparse, refined typography. Long-form magazine layout.

**Typography**:
- Display: GT Sectra, Tiempos Headline, or Garaje Old. Large italic display.
- Body: Söhne or Inter Tight. Generous line height (1.7+).

**Color palette**:
- Photographic: derived from hero image (extract dominant + accent)
- Default: `#FFFFFF` paper, `#0A0A0A` ink, single accent from photo.

**Texture/effects**: Heavy reliance on imagery. Grain on photos. Subtle sepia or color-grade.

**Animation tone**: Slow Ken Burns on hero photo. Text fades in like film credits. Scroll-linked photo reveals.

**Best fit for**: Magazines, agencies, photography-led brands, fashion, travel, narrative-driven sites.

**Don't use for**: Sites with no photography budget. Functional B2B.

---

## 8. Bold Maximalist

**Vibe**: Everything turned up. Massive type, vibrant colors, layered elements. Reads like a poster festival or Stripe Press cover.

**Typography**:
- Display: Druk, Migra, or Migra Italic. Sized at 12-25vw on hero.
- Body: Inter Tight or Söhne. Compact.

**Color palette**:
- Bright primary `#FF4E1A`
- Secondary: `#0066FF`
- Background: Off-white `#FAF6F0`
- Accent: yellow `#FFE600`
- Pop: `#FF1F8F`

**Texture/effects**: Overlapping shapes. Diagonal text. Bold borders. Photo collages with cutouts.

**Animation tone**: Energetic, snappy. Diagonal slides. Text rotates on hover. Color flashes.

**Best fit for**: Festivals, agencies, conferences, podcasts, creative SaaS.

**Don't use for**: Healthcare, finance, B2B conservative.

---

## 9. Luxury Minimal (Refined)

**Vibe**: Hermès web. Restraint. Massive whitespace. Subtle gold/cream tones. The opposite of trying-too-hard.

**Typography**:
- Display: Saol Display, GT America Mono Light Italic, or Reckless Neue (light weight).
- Body: GT America, Söhne, or Inter Tight. Light weights.

**Color palette**:
- Cream `#F5F1EA`
- Ink `#0F0F0F`
- Whisper accent: `#A98B5C` (champagne) or `#7B6651` (taupe)

**Texture/effects**: Almost none. Subtle paper noise. Hairline borders.

**Animation tone**: Glacial. 800ms fade-ups. Subtle hover state changes. No springs.

**Best fit for**: Luxury goods, high-ticket consulting, private banking, art galleries.

**Don't use for**: Anything mass-market or playful.

---

## 10. Playful Toy

**Vibe**: Dribbble illustration vibes. Rounded everything. Pastel colors. Bouncy interactions. Reads like Notion's marketing site or Linear's old aesthetic.

**Typography**:
- Display: General Sans, Cabinet Grotesk, or Recoleta Bold (rounded).
- Body: General Sans Variable, Inter Variable.

**Color palette**:
- Pastels with one saturated: `#FFB5D8`, `#B5D8FF`, `#FFE6B5`, `#C5FFB5`
- Text: `#1A1A2E`
- Accent: vibrant mid-tone `#7C3AED` or `#10B981`

**Texture/effects**: Rounded corners (24-48px radius). Soft shadows. Doodle-style illustrations. Floating shapes.

**Animation tone**: Bouncy spring (damping 12, stiffness 200). Wiggle on hover. Bounce-in on scroll.

**Best fit for**: SaaS friendly, productivity, creator tools, family/kids products, education.

**Don't use for**: Banks, healthcare serious, luxury.

---

## 11. Dark Tech Terminal

**Vibe**: Vercel docs meets a hacker's dotfiles. Mono everywhere. Pure black + neon-but-restrained. Reads like docs site for serious tools.

**Typography**:
- Display: Geist Mono, JetBrains Mono Bold, or IBM Plex Mono.
- Body: Geist Sans, Inter, or Söhne.

**Color palette**:
- Pitch black `#000000` or `#0A0A0A`
- Foreground: `#EDEDED` or `#FAFAFA`
- Accent green: `#00DC82` (Vercel green) or `#3FCF8E` (Supabase green)
- Muted gray scale: `#52525B`, `#27272A`

**Texture/effects**: Subtle CRT scanlines optional. Code blocks with proper syntax highlighting. Cursor blinks.

**Animation tone**: Snappy, terminal-feeling. Type-on effect for headlines. No bouncy springs.

**Best fit for**: Developer tools, technical SaaS, infrastructure products, AI tools for devs.

**Don't use for**: Non-technical audiences, lifestyle brands.

---

## 12. Retro-Futurist 80s

**Vibe**: Stranger Things title card meets Synthwave. Outrun aesthetics. Chrome typography. Sunset gradients.

**Typography**:
- Display: Monument Extended, Druk Wide, or Anton (chrome 3D effect).
- Body: Söhne or Geist.

**Color palette**:
- Magenta-purple gradient `#FF006E` → `#8338EC`
- Cyan accent `#00F5FF`
- Yellow highlight `#FFE600`
- Deep navy base `#03002E`

**Texture/effects**: Chrome gradients on type. Grid floor with perspective. Sun setting behind. Stars/scanlines.

**Animation tone**: Smooth, gliding. Type slides in. Grid moves toward viewer.

**Best fit for**: Gaming, music, creator economy, nostalgic brands, podcasts.

**Don't use for**: B2B, finance, healthcare.

---

## 13. Industrial Utilitarian

**Vibe**: Construction site signage meets Notion docs. All-caps. Hard angles. Functional aesthetic. No frills.

**Typography**:
- Display: Druk Condensed, Knockout, or PP Mori (extra bold).
- Body: GT America Mono, IBM Plex Mono.

**Color palette**:
- Industrial yellow `#FFCC00` + black `#0A0A0A`
- Concrete gray `#7C7C7C`
- Off-white `#EFEDE5`

**Texture/effects**: Chevron/diagonal stripes. Border crops. Stamp/stencil treatment on labels.

**Animation tone**: Mechanical. Slide-from-side reveals. No bouncing.

**Best fit for**: B2B industrial, construction, manufacturing, logistics, security.

**Don't use for**: Wellness, family, luxury.

---

## 14. Soft Pastel Aspirational

**Vibe**: Glossier meets Notion. Soft pinks, dusty blues, creamy whites. Reads like a wellness DTC brand or a feminine SaaS.

**Typography**:
- Display: Saol Display Italic, Recoleta, or Tiempos Italic.
- Body: Söhne or Inter.

**Color palette**:
- Blush `#FFE0E5`
- Dusty blue `#B8C5D9`
- Cream `#FBF7F2`
- Deep navy text `#1A1A2E`
- Single warm accent: `#D4866B` or `#C9A875`

**Texture/effects**: Soft gradients, NOT pastel rainbows. Subtle glow. Curved dividers.

**Animation tone**: Gentle, slow fade-ups. Soft hover state lightening.

**Best fit for**: Wellness, skincare, women-led brands, lifestyle, gentle SaaS.

**Don't use for**: Brutalist or maximalist. Avoid for masculine-coded brands.

---

## 15. Architectural Concrete

**Vibe**: Tadao Ando meets Apple Park. Slate concrete textures. Slow scroll. Spatial. Reads like an architecture firm.

**Typography**:
- Display: Söhne Breit, GT America Extended, or NB International Pro Mono.
- Body: Söhne or Söhne Breit.

**Color palette**:
- Concrete `#A09F95`
- Off-black `#1B1B1B`
- Cream `#F2EEE6`
- Deep moss `#2E3F2C`

**Texture/effects**: Concrete photo backgrounds. Grain. Heavy shadows on cards. Geometric framing.

**Animation tone**: Architectural reveals — sections slide in like building blocks. Sky-blue parallax on hero.

**Best fit for**: Architecture, real estate premium, design studios, art galleries.

**Don't use for**: Tech consumer, kids, e-commerce mass.

---

## 16. Pop Editorial

**Vibe**: Saturated. Loud. Pop-art-meets-magazine. Reads like Fast Company magazine cover.

**Typography**:
- Display: Druk, Founders Grotesk Bold, or Migra. Massive scale.
- Body: GT America or Söhne.

**Color palette**:
- Hot orange `#FF4400`
- Electric blue `#0066FF`
- Sunshine yellow `#FFD400`
- Off-white `#F8F4EE`
- Off-black `#0A0A0A`

**Texture/effects**: Halftone patterns. Diagonal text. Photo cutouts. Marker-like highlights on key words.

**Animation tone**: Punchy. Scale-up on hover. Text rotates. Color flashes.

**Best fit for**: Media, agencies, creators, conferences, events.

**Don't use for**: B2B serious, healthcare.

---

## 17. Monochrome Mood

**Vibe**: All black-and-white-and-gray. No color anywhere. Photography drives mood. Looks like a Polaroid photo essay.

**Typography**:
- Display: Reckless Neue, Tiempos Headline, or PP Editorial New.
- Body: Söhne or Inter Tight.

**Color palette**:
- ONLY: `#000`, `#1A1A1A`, `#3A3A3A`, `#7A7A7A`, `#C8C8C8`, `#FAFAFA`
- That's it. No accent.

**Texture/effects**: Heavy use of B&W photography. Grain. Sometimes a single tinted color-graded photo as exception.

**Animation tone**: Slow, emotional. Photo fades.

**Best fit for**: Photography, art, narrative brands, niche editorial, gallery sites.

**Don't use for**: SaaS, e-commerce, anything functional.

---

## 18. Soft Gradient Aurora

**Vibe**: Linear's earlier aesthetic. Lush gradient orbs. Soft glow. Looks like AI futuristic but in a tasteful way.

**Typography**:
- Display: Inter Display, Geist, or Söhne.
- Body: Inter, Geist, or Söhne.

**Color palette**:
- Background gradient: `#0A0E27` → `#1A0E2E` → `#0E1A2E`
- Orbs: `#7C3AED`, `#06B6D4`, `#EC4899` (with high blur)
- Foreground: `#F8FAFC`

**Texture/effects**: Massive blurred gradient orbs in hero. Subtle noise. Glass cards.

**Animation tone**: Floaty. Orbs drift slowly. Cards lift on hover. Smooth.

**Best fit for**: AI products, modern SaaS, developer tools, fintech with vibe.

**Don't use for**: Tradition-heavy brands, formal industries.

---

## 19. Warm Earth Tone

**Vibe**: Patagonia website meets a craft coffee brand. Burnt sienna, deep browns, mustard yellows. Cozy, grounded, premium.

**Typography**:
- Display: Reckless Neue, Tiempos, or Recoleta Italic.
- Body: Söhne or Inter Tight.

**Color palette**:
- Sand `#E8DCC4`
- Burnt sienna `#C5612C`
- Deep brown `#3A2A1F`
- Mustard `#D4A574`
- Forest `#5C6B43`

**Texture/effects**: Paper-like backgrounds. Hand-drawn flourishes. Photography of nature/products warmly graded.

**Animation tone**: Warm, grounded. Slow reveals. Subtle hover breathing.

**Best fit for**: Coffee, food premium, outdoor brands, craft products, sustainable goods.

**Don't use for**: Tech, SaaS, finance.

---

## 20. High-Contrast Brutalism

**Vibe**: Pushed Brutalist. Full-bleed black sections. Type so big it bleeds off-page. Grid-as-content.

**Typography**:
- Display: Druk Wide Heavy, Monument Extended, or PP Mori (heaviest).
- Body: PP Neue Montreal, Söhne Breit.

**Color palette**:
- Pure `#000` and pure `#FFF`
- Single neon: `#00FF00` or `#FF0000`. ONE.

**Texture/effects**: Hard edges, no shadows, no rounded corners. Grid lines visible. Heavy borders.

**Animation tone**: Brutal cuts. Inverted hover (black ↔ white instantly).

**Best fit for**: Edgy agencies, contrarian SaaS, music/festival edgy, design provocateurs.

**Don't use for**: 95% of brands. Use sparingly.

---

## 21. Apple-Keynote Premium

**Vibe**: Apple product page. Massive product hero, scroll-revealed features, every section feels chosen. Cinematic but restrained.

**Typography**:
- Display: SF Pro Display (when allowed) or Inter Display Variable.
- Body: SF Pro Text or Inter Variable.

**Color palette**:
- Pristine white `#FFFFFF`
- Apple-grays: `#F5F5F7`, `#86868B`, `#1D1D1F`
- Single product accent: from product photography (e.g., titanium silver `#A8A8AC`).

**Texture/effects**: Massive product photography. Subtle gradient glow behind product. Heavy use of negative space.

**Animation tone**: Cinematic scroll-linked reveals. Product rotates. Text fades in segments. ScrollSmoother feel.

**Best fit for**: Premium hardware/software products, design tools, anything with a "product hero" image.

**Don't use for**: Service businesses, content sites, multipage docs.

---

## 22. Print-Inspired Mid-Century

**Vibe**: 1960s Swiss design meets a Brooklyn agency. Bauhaus shapes. Mid-century color. Reads like a record album cover.

**Typography**:
- Display: GT Sectra Display, ITC Avant Garde Gothic, or Reckless.
- Body: GT America or Söhne.

**Color palette**:
- Cream `#F5EFE0`
- Mustard `#D4A574`
- Burnt orange `#D45D2E`
- Deep navy `#1F2937`
- Cherry red `#DC2626`

**Texture/effects**: Geometric shapes (circles, triangles) as decoration. Risograph-style print noise. Off-register printing effect.

**Animation tone**: Restrained. Print-flip reveals. Geometric morphing.

**Best fit for**: Design studios, vintage brands, music labels, podcasts.

**Don't use for**: Tech B2B serious, healthcare.

---

## How to pick a direction

Read the brief. Identify:

1. **Industry**: tech, wellness, finance, creator, retail, etc.
2. **Audience**: B2C consumer, B2B professional, technical user, etc.
3. **Tone signals from brief**: words like "professional", "fun", "luxury", "edgy"
4. **Existing brand**: if user provided brand guide, defer to it but interpret boldly

Then:

- Eliminate directions that conflict with industry/audience
- From remaining, pick 1 that matches tone strongest
- If 2 are equally good, pick the more distinctive one
- Justify your pick to the user in 2-3 sentences before proceeding

**Never**:
- Default to glassmorphism or aurora because they're "safe" — they're overused.
- Pick a direction the user didn't ask for and that contradicts their brand entirely (unless they explicitly asked for "rebrand my vibe").
- Combine 2 directions into "fusion" — pick ONE and execute it precisely.

---

## Inventing a new direction (when none of the 22 fit)

Sometimes the brief truly demands something new. To invent a direction, define EACH axis:

```
Direction name: [punchy, specific]
Vibe: [2 sentences, evocative]
Typography:
  - Display: [specific font name + treatment]
  - Body: [specific font name]
Color palette:
  - 4-7 hex values with usage notes
Texture/effects:
  - [3-5 specific elements]
Animation tone:
  - [snappy/fluid/restrained/exuberant + concrete examples]
Best fit for: [specific industries/audiences]
Don't use for: [anti-fit examples]
```

Don't ship without all 7 axes defined. Vagueness here = generic AI output.
