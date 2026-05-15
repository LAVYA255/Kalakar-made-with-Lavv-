# Site Archetypes

Twelve recipes. Pick one. Each entry tells you the stack, the library combo, the signature moves, and the SEO/perf concerns specific to that kind of site.

---

## 1. Editorial Product Launch / Seasonal Showcase

**Reference sites:** Shopify Editions Winter 2026, Apple product pages, Linear "Method", Vercel Ship pages, Arc Browser launches.

**Defining characteristics**
- Long-form scrolly narrative — one product/announcement broken into discrete "chapters."
- Pinned section scrubs (GSAP ScrollTrigger pin + scrub) tying motion to scroll position.
- Hero is often a video-loop or WebGL / Rive title card with kinetic typography.
- Sticky in-page nav with section progress indicator; section IDs map to chapter URLs.
- Viewport-aware reveals (mask-clip, line-by-line text reveal).
- Distinct color palette per chapter (CSS custom properties swapped via IntersectionObserver).

**Page types:** Single long landing + per-feature deep-link anchors + changelog/blog + signup/CTA.

**Tech baseline:** **Next.js (App Router)** — needs ISR for chapter drops, OG-image generation per section, edge middleware for variant testing.

**Library combo**
- Animation: `gsap` + `ScrollTrigger` (commercial license)
- Scroll: `lenis`
- Component motion: `motion` (Framer Motion)
- 3D (selective, hero only): `@react-three/fiber` + `@react-three/drei`
- Vector motion: `@rive-app/react-canvas` for stateful title-card animations (Shopify Editions uses Rive)
- Type: variable fonts via `@fontsource-variable/*` + `split-type` for line reveals
- Image: `next/image` + `plaiceholder` placeholders; Sanity Image CDN or Mux for video
- CMS: Sanity or Contentful (structured chapters)
- Audio (optional ambient): `howler`

**Performance/SEO**
- Chapter-level OG images via `@vercel/og`.
- LCP risk from hero video — use AVIF poster + `preload="metadata"`.
- Section anchors must be crawlable HTML, not JS-rendered.
- Schema: `Product`, `Event`, or `Article` per chapter.
- INP target: <200ms — defer GSAP init off main thread.

---

## 2. VC / Investment Firm Site

**Reference sites:** Hashgraph VC, Sequoia, Lowercase, Founders Fund, Thrive Capital, Index Ventures.

**Defining characteristics**
- Restrained, "serious money" aesthetic — heavy editorial typography, generous whitespace.
- Portfolio grid as the centerpiece — logos in a quasi-Bauhaus grid.
- Thesis/writing section treated like a literary journal.
- Subtle motion only — text fade-ups, logo hover lifts, no gratuitous WebGL.
- Often ONE distinctive interaction (Hashgraph's depth-mapped portraits) as the signature moment.
- Custom serif display face paired with neutral grotesk.

**Page types:** Home, Thesis/About, Portfolio, Writing index + detail, Team, Contact.

**Tech baseline:** **Astro** — content-heavy, mostly static, partial hydration for the one signature interaction. (Hashgraph itself uses Nuxt 3 — equally valid for Vue teams.)

**Library combo**
- Animation: `@motionone/dom` for ambient motion; `gsap` only for the signature moment
- Scroll: native `scroll-behavior: smooth` — skip Lenis. Serious firms shouldn't feel "buttery."
- Transitions: Astro View Transitions API
- 3D: `ogl` (smaller than three) for shader portraits, or `p5` for generative network viz
- Cursor: subtle custom cursor on portfolio hover only
- Audio (if any): `howler` for a single ambient loop with persistent mute
- CMS: MDX in repo for thesis pieces, or Sanity if non-technical team writes
- Type: Editorial New, GT Sectra, Söhne Mono for data labels

**Performance/SEO**
- `Article` schema with `Person` author markup — drives AI Overview citations.
- LCP <1.5s expected.
- llms.txt mandatory — VCs increasingly evaluated by ChatGPT / Perplexity.
- Partner bios with credentials + prior investments — E-E-A-T critical.

---

## 3. Designer / Solo Creative Portfolio

**Reference sites:** Simon Holm Studio, Rauno Freiberg, Emil Kowalski, Mariana Castilho, Robin Noguier, Olivier Larose.

**Defining characteristics**
- Personality-forward — opinionated typography, signature interaction the designer is "known for."
- Home is often a single dense "résumé as art" page or a hyper-curated project list.
- Magnetic cursor, hover-driven previews, mouse-following image trails.
- Page transitions that feel designed (curtain wipes, mask transitions, view-transition swaps).
- Cmd+K spotlight nav increasingly common.
- Often a hidden Easter egg / playful detail.

**Page types:** Home, Work (filterable), Case studies, About, Now/Reading, Contact.

**Tech baseline:** **Vite + React** (or **Next.js** if SEO-leaning). Webflow is a totally valid escape hatch — Simon Holm uses Webflow + GSAP CDN + Lenis + Barba.

**Library combo**
- Animation: `gsap` (with Observer + CustomEase plugins) + `motion` for React state
- Scroll: `lenis` + `lenis/react`
- Transitions: `framer-motion` AnimatePresence with shared layout, OR `next-view-transitions`, OR `@barba/core` if MPA
- 3D: `@react-three/fiber` for hero shader / image displacement
- Cursor: build it. Don't use a library. The cursor IS the brand.
- Type: one unusual display face (Migra, PP Editorial Old, Surt, Pangram Pangram) + system mono
- Image effects: WebGL displacement on hover via R3F + custom GLSL (or `curtains.js` for DOM-anchored planes)
- CMS: MDX or Sanity lite
- Slider (when needed): `embla-carousel-react`

**Performance/SEO**
- WebGL on mobile drains battery — gate via `prefers-reduced-motion` + viewport check + `detect-gpu`.
- Image-heavy — AVIF + responsive `srcset`.
- Schema: `Person` + `CreativeWork` per project.

---

## 4. Studio / Agency Showreel

**Reference sites:** Obsidian Assembly, ref.digital, Resn, Active Theory, Locomotive, Immersive Garden, Unseen Studio, Hello Monday, Cuberto.

**Defining characteristics**
- "Look at what we can do" — the site IS the portfolio piece.
- Bold WebGL hero (often with audio reactivity or interactive shader).
- Asymmetric, broken-grid layouts.
- Marquee text strips, oversized type, intentional clipping.
- Project case studies are themselves micro-sites with bespoke design per case.
- Custom loader/intro animation is a signature feature.
- Often bilingual (EN/FR or EN/JA) — ref.digital is EN/FR via Nuxt i18n.

**Page types:** Home (showreel), Work index, Case studies (bespoke), Studio/About, Careers, Journal, Contact.

**Tech baseline:** **Next.js** for shell + case-study scaffolding; **Nuxt 3** if Vue (ref.digital, Obsidian Assembly); **SvelteKit** for cutting-edge feel.

**Library combo**
- Animation: full `gsap` Club (ScrollTrigger + SplitText + MorphSVG + Observer + CustomEase + DrawSVG + Flip)
- Scroll: `lenis` (always) + `tempus` for shared RAF when GSAP + R3F coexist
- Transitions: custom WebGL curtain reveal OR `@barba/core` for MPA OR view-transitions
- 3D: `@react-three/fiber` + `@react-three/drei` + `@react-three/postprocessing` (bloom, chromatic aberration, RGB shift)
- Shaders: raw GLSL via R3F or `ogl` for non-React, with `lygia` shader functions
- Cursor: custom + cursor-blending modes OR `mouse-follower` (Cuberto)
- Type: PP Neue Machina, Migra, PP Editorial Old, Söhne, custom commissioned
- Image effects: WebGL hover distortion (curl noise, RGB shift) — `curtains.js` for DOM-bound, R3F for scene-bound
- Audio: often included — `tone` or `howler` with subtle ambient + UI sounds + persistent mute control
- CMS: Sanity, Prismic (slice machine), or Storyblok (ref.digital uses Storyblok)
- Vector: `@rive-app/canvas` for stateful logos / loaders

**Performance/SEO**
- Hardest archetype to optimize — WebGL hero often kills LCP.
- Strategy: progressive enhancement. Ship HTML-first hero, mount WebGL after FCP.
- Schema: `Organization` + `Service` + per-case `CreativeWork`.
- SEO often deprioritized — agency leads come from referrals + awards listings.
- Submit aggressively: Awwwards, FWA, CSSDA, SiteSee, Godly, GoDaddy.

---

## 5. Case-Study Deep Dive (Single-Project Microsite)

**Reference sites:** Floema (Locomotive's case study), Stripe Press book pages, Apple "Designed by Apple" cases, Frank Body brand cases.

**Defining characteristics**
- One project, treated like a documentary.
- Long-scroll narrative with phase transitions (Discover → Design → Build → Ship).
- Heavy use of full-bleed imagery, video, before/after sliders.
- "Numbers that matter" — animated counters, growth charts.
- Pull-quotes from team/client.
- Frequently uses horizontal scroll sections for process timelines.
- Sometimes ambient multi-track audio per scene (Floema's bike narrative).

**Page types:** Single page with deep anchors. Sometimes a small index of cases.

**Tech baseline:** **Astro** if static + content-driven; **Next.js / Nuxt** if part of larger agency site. Floema itself is Nuxt 3 + Sanity by Burocratik.

**Library combo**
- Animation: `gsap` + `ScrollTrigger` (pin, scrub, horizontal scroll)
- Scroll: `lenis` + `tempus`
- 3D: rarely — maybe one product render
- Type: editorial pairing (serif headline + grotesk body)
- Image: Mux for video, Cloudinary or Sanity Image for stills, `plyr` or `vidstack` for inline video controls
- Counters: GSAP tween or `countup.js`
- Audio: `howler` for ambient per-scene tracks (Floema pattern — preload as `<link rel="prefetch" as="audio">`)
- CMS: MDX + frontmatter; or Sanity for non-dev edits
- For shader-heavy hero: `ogl` (Floema-style, lighter than three)

**Performance/SEO**
- Each case study gets its own indexable URL with full `Article` schema.
- Author + organization markup critical for B2B citation in AI search.
- LCP: lazy-load below-fold video, preload above-fold hero only.

---

## 6. Brand Microsite / Campaign

**Reference sites:** Nike campaign drops, Off-White launches, Aesop seasonal, A24 film sites, Carhartt WIP seasonal.

**Defining characteristics**
- Time-limited — exists for a season/campaign, then archived.
- Maximum design risk; brand-system-breaking allowed.
- Genre-experimental — Y2K, brutalist, vaporwave, terminal/CLI, anti-design.
- Sound design often included (campaign music, FX).
- Cursor and loader treated as brand assets.
- Sometimes deliberately confusing UX as creative statement.

**Page types:** Home + 2-4 supporting pages max. Often a single deep-scroll.

**Tech baseline:** **Vite + React** or **SvelteKit** — speed of build matters more than SEO maturity.

**Library combo**
- Animation: `gsap` (clutch for bespoke moments)
- Scroll: `lenis` + scroll snap
- Transitions: custom WebGL reveal
- 3D: `@react-three/fiber` with bespoke shader OR **Spline** embed for non-coders on the team
- Cursor: bespoke, always
- Type: most experimental face the brand tolerates (Pangram Pangram, Velvetyne foundry, Future Fonts)
- Image effects: WebGL displacement, dithering shaders, halftone — try `@vfx-js/core` / `react-vfx`
- Audio: `tone` for generative ambient; `howler` for triggered FX
- CMS: usually none — hardcoded MDX

**Performance/SEO**
- SEO secondary — campaign sites don't rank, they convert from paid + social.
- Track UTMs, optimize for share-image (OG/Twitter card is the real "hero").
- Schema: `Event` or `PromotionalEvent`.

---

## 7. Conference / Event Site

**Reference sites:** Config (Figma), Vercel Ship, Cloudflare Connect, Web Directions, Awwwards Conference, OFFF.

**Defining characteristics**
- Date-anchored — countdown, "happening now" states, post-event archive transition.
- Speaker grid is the heart of the site.
- Schedule view (often filterable by track/tag).
- Sponsor tiers with logo wall.
- Bold "ticket CTA" persistent in nav until sold out.
- After event: pivots to video archive / recap.

**Page types:** Home, Speakers + detail, Schedule, Venue, Sponsors, FAQ, Tickets, Code of Conduct, Post-event recap.

**Tech baseline:** **Next.js** — needs ISR for dynamic states (early-bird → general → sold out → archive), dynamic OG images per speaker.

**Library combo**
- Animation: `motion` (component-level, less GSAP needed)
- Scroll: `lenis` lite or native
- Transitions: `next-view-transitions`
- 3D (optional hero): Spline embed for the "wow"
- Type: bold display face + readable body
- Image: `next/image` + Mux for session recordings
- CMS: Sanity (speakers, sessions, sponsors as structured docs) or Notion via API
- Calendar: `add-to-calendar-button`
- UI: `cmdk` for search, `sonner` for toasts

**Performance/SEO**
- Critical: `Event` schema with `EventStatus` (scheduled / postponed / cancelled), `location`, `performer`.
- Per-speaker `Person` schema with `sameAs` links.
- Dynamic OG image per speaker (drives ticket sales on X / LinkedIn).
- llms.txt with key dates so AI assistants answer "when is X" correctly.

---

## 8. Fashion / Lookbook with Cinematic Scroll

**Reference sites:** Burberry seasonal, Jacquemus, Bottega Veneta digital journal, Loewe craft, SSENSE editorial.

**Defining characteristics**
- Image and video are the content — type is sparse, often only credits.
- Full-bleed cinematic frames stacked vertically with scroll-driven crossfade.
- Scroll-scrubbed video (sequence of frames or HLS scrubbing).
- Models, garments, locations as "named characters" with reveal cards.
- "Shop the look" product hotspots embedded in editorial frames.
- Mute-by-default ambient track.

**Page types:** Lookbook (long-scroll), Index of lookbooks, garment shop pages (often handed off to Shopify storefront), About/Craft.

**Tech baseline:** **Next.js** with **Shopify Hydrogen** integration if commerce-attached (Shopify Editions itself runs on Hydrogen/Remix/Oxygen); **Astro** if pure editorial.

**Library combo**
- Animation: `gsap` ScrollTrigger (scrub on video frame index)
- Scroll: `lenis`
- Video: Mux scrubbable streams OR pre-rendered image sequence + canvas playback (for buttery scrub)
- Type: editorial serif + ALL CAPS grotesk for credits
- Image: AVIF mandatory, art-direction with `<picture>`
- Audio: `howler` ambient loop
- CMS: Sanity with bespoke "Look" document type linking products
- Slider (when needed): `embla-carousel-react`

**Performance/SEO**
- Image sequences are bandwidth nightmares — use Mux scrubbable streams over frame arrays where possible.
- Schema: `Product` for shop-the-look items, `ImageGallery` for lookbook.
- Strong opportunity for Google Images SERP — alt text describing garment, color, season.

---

## 9. Experimental Net-Art / One-Pager Demo

**Reference sites:** Bruno Simon's portfolio, Hyper Island student showcases, Cyberia, B-Reel labs, Vasilis van Gemert, ertdfgcvb.

**Defining characteristics**
- Single-page or single-canvas; the site IS the artwork.
- Often non-standard nav — drag, gesture, keyboard, voice.
- Breaks conventional UX intentionally.
- Heavy WebGL or Canvas2D; sometimes WebGPU.
- Generative or interactive — different every visit.

**Page types:** One. Maybe a "credits" overlay.

**Tech baseline:** **Vite + Vanilla JS** or **Vite + React** — minimum framework overhead, maximum render-loop control.

**Library combo**
- Animation: hand-rolled `requestAnimationFrame` loop
- 3D: `three` raw (not R3F — finer control) or `ogl` for tiny bundle
- Physics: `cannon-es` or `@dimforge/rapier3d-compat`
- Shaders: raw GLSL — this is the whole point. Compose with `lygia`.
- Type: often rendered INTO the canvas, not DOM — `troika-three-text`
- Cursor: replaced entirely by canvas-rendered pointer
- Audio: Web Audio API directly, `tone` for generative
- Generative math: `simplex-noise`, `alea`, `eases`, `gl-matrix`
- Debug: `tweakpane`, `stats-gl`

**Performance/SEO**
- SEO near-zero — these are showcase pieces.
- Provide fallback HTML description for crawlers + accessibility tree.
- Submit to FWA, Awwwards, Codrops, CSSDA.
- Critical: `prefers-reduced-motion` fallback — otherwise accessibility nightmares.

---

## 10. Minimalist Brutalist / Text-Only Site

**Reference sites:** Karri Saarinen, Drew Wilson, Jack McDade, early "It's Nice That", Pentagram partners' personal pages, Frank Chimero.

**Defining characteristics**
- Type is everything. Often a single font, often system.
- Stark contrast, raw HTML feel, intentionally "undesigned."
- No animation, no scroll effects, no cursor tricks.
- Sometimes monospaced everywhere.
- Often weighted with strong opinions / writing.
- Loads in <500ms.

**Page types:** Home, Writing, Projects, About — all unfussy.

**Tech baseline:** **Astro** or plain HTML + build step. No SPA.

**Library combo**
- Animation: none, or `@motionone/dom` for one subtle reveal
- Scroll: native
- Transitions: Astro View Transitions
- 3D: never
- Cursor: native
- Type: iA Writer Mono, JetBrains Mono, IBM Plex, or pure system stack
- Image: rare; when present, dithered or duotone
- CMS: Markdown in repo
- Code blocks: `expressive-code` or `shiki`

**Performance/SEO**
- Best-in-class. LCP <800ms, INP <50ms trivially.
- Massive AI Overview / Perplexity citation potential — clean semantic HTML is what LLMs eat.
- llms.txt is a natural fit.
- Author schema critical — these are usually personal-brand SEO plays.

---

## 11. WebGL Hero with Headless CMS (SaaS / Web3 Marketing)

**Reference sites:** Linear, Vercel, Resend, Liveblocks, Cal.com, Modal, Replicate, Pinecone, Browserbase.

**Defining characteristics**
- WebGL or shader-driven hero (gradient mesh, particle system, animated aurora).
- Below the fold: traditional SaaS marketing — features, social proof, pricing.
- Hero motion is "ambient" not interactive — runs whether you engage or not.
- Often dark theme with neon/aurora accents.
- Heavy product imagery (UI screenshots) with subtle parallax.
- Docs site is a separate sibling deployment.

**Page types:** Home, Features (one per product surface), Customers, Pricing, Changelog, Blog, Careers, Docs (separate), Login.

**Tech baseline:** **Next.js** — needs SSR for SEO, MDX for marketing pages, edge for personalization, OG image generation.

**Library combo**
- Animation: `motion` (primary) + `gsap` for hero only
- Scroll: `lenis` (light touch — SaaS users skim, don't scroll-watch)
- Transitions: `next-view-transitions`
- 3D: `@react-three/fiber` for hero shader; `@react-three/drei` (`<MeshTransmissionMaterial>`, `<Float>`) + custom GLSL gradient mesh, OR Paper Design's shaders library
- Type: Inter, Geist, Söhne, GT America — neutral grotesks
- Image: `next/image` with AVIF
- CMS: Contentful, Sanity, or Builder.io (marketing wants page composition)
- Search: Algolia DocSearch if docs proximate, else Pagefind
- UI: shadcn + Radix + `vaul` + `sonner` + `cmdk`
- Headlines: `react-wrap-balancer`

**Performance/SEO**
- LCP is make-or-break. Hero shader must not block. Ship static gradient PNG as LCP, swap in WebGL canvas after first paint.
- Schema: `SoftwareApplication`, `Organization`, `FAQPage`.
- AI Overview: structured "what is X / how does X work" passages near top of feature pages.
- Critical: feature copy needs crawlable text — don't render inside Canvas.

---

## 12. Design-Forward Documentation Site

**Reference sites:** Stripe Docs, Tailwind CSS, Radix UI, shadcn/ui, React docs, Astro docs, Motion (Framer) docs.

**Defining characteristics**
- Treats docs as a designed product, not a wiki.
- Sticky sidebar TOC, in-page right-rail anchors, command-K search everywhere.
- Live interactive examples — components rendered in the doc with editable props.
- Dark/light parity (and often a "system" tri-state).
- Generous body typography; mono with smart syntax theming.
- Versioned content with version switcher in header.

**Page types:** Home/landing, Getting started, Concept docs, API reference, Examples gallery, Changelog, Migration guides.

**Tech baseline:** **Next.js** (with **Nextra** or **Fumadocs**) or **Astro Starlight** for the lightweight option.

**Library combo**
- Animation: `motion` for component examples; minimal page motion
- Scroll: native + `scroll-margin-top` for anchor offsets
- Transitions: View Transitions API
- 3D: only if the product is visual
- Type: Inter + Geist Mono / JetBrains Mono
- Search: Algolia DocSearch (cost) OR `pagefind` (free, static, private)
- Code: `shiki` (build-time, zero JS) or `expressive-code`
- CMS: MDX in repo, content as code
- UI: shadcn + Radix + `cmdk`

**Performance/SEO**
- Massive SEO opportunity — docs are the #1 source of LLM citations.
- Every section needs a stable anchor.
- Schema: `TechArticle`, `APIReference`, `HowTo` for tutorials.
- llms.txt + llms-full.txt mandatory — this is the canonical use case.
- Pagefind beats Algolia for cost + privacy at moderate traffic.

---

## Cross-cutting defaults (apply to all archetypes unless noted)

- **Reduced motion:** every animation gated by `prefers-reduced-motion`.
- **AVIF + WebP** with JPEG fallback for raster images.
- **Edge-rendered OG images** for shareability.
- **llms.txt** for AI search visibility (skip only for archetypes 6 and 9).
- **View Transitions API** as default page-transition primitive (with library fallback for older browsers).
- **Lenis is the default smooth-scroll** — but skip it for archetypes 2, 7, 10, 12 where "feel fast / serious" beats "feel smooth."
- **GSAP commercial license** assumed for archetypes 1, 3, 4, 5, 6, 8.
- **Spline** is the escape hatch for non-3D-coders on archetypes 6, 7, 11.
- **detect-gpu** for any 3D-heavy archetype (1, 3, 4, 6, 9, 11) to downgrade mobile.
