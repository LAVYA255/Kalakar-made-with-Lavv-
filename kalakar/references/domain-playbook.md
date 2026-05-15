# Domain Playbook — Aesthetic Upgrade Path for Any Business

The promise of this skill is that **every domain deserves design-forward treatment** — not just agencies and SaaS. A dentist site can be Awwwards-grade. A bakery site can win FWA. A law firm can have a kinetic hero. The trick is matching the *signature moment* to the *business reality*.

Each entry below covers: what the bad/generic version looks like, what the aesthetic-elevated version looks like, which archetype it maps to (see `archetypes.md`), the signature moment, and the library combo.

---

## Hospitality & Food

### Restaurant (fine dining)
- **Generic:** WordPress, hero photo of food, menu PDF, OpenTable button.
- **Elevated:** Cinematic full-bleed hero video, kinetic typography of chef's philosophy, scroll-driven menu reveal with food photography, ambient soundscape, custom cursor when over dishes showing wine pairing on hover.
- **Archetype:** Cinematic Lookbook + Case Study mash.
- **Signature moment:** Scrolling through the tasting menu feels like a film — pinned video plays in sync with course description.
- **Stack:** Next.js + `lenis` + `gsap` ScrollTrigger + Mux for video + Sanity for menu (real-time updates) + Howler for ambient + `cal.com` for reservations or OpenTable embed.

### Café / coffee shop / bakery
- **Generic:** Squarespace, gallery + hours + map.
- **Elevated:** Hand-illustrated brand assets (Rive for animated logo), typographic menu, day-of-week specials with subtle animation, Instagram feed embedded as marquee, Mapbox stylized to brand colors.
- **Archetype:** Brand Microsite.
- **Signature moment:** Daily-rotating typographic poster on hero — different per day of week.
- **Stack:** Astro + `@rive-app/canvas` + `mapbox-gl` styled + Instagram Basic Display API + native CSS smooth scroll.

### Brewery / winery / distillery
- **Generic:** Stock photos, flag-style menu, "since 1923" badge.
- **Elevated:** Tactile typography (varietal labels treated like editorial pieces), scroll-scrubbed bottling-process video, terroir map with hover-revealed soil composition, generative pattern derived from grape genome.
- **Archetype:** Case Study Microsite + Brand.
- **Signature moment:** Each varietal has its own page with a unique generative "fingerprint" pattern.
- **Stack:** Astro + `gsap` ScrollTrigger + Mux + `mapbox-gl` + `simplex-noise` for fingerprints + Sanity for varietal docs.

### Hotel / resort / boutique hospitality
- **Generic:** Booking widget hero, photo carousel, room grid.
- **Elevated:** Full-bleed video hero, scroll-driven room "walkthrough" (image sequence scrubbing), custom interactive map of property, ambient soundscape per region, mute-by-default audio toggle.
- **Archetype:** Cinematic Lookbook.
- **Signature moment:** Booking widget feels integrated, not bolted on — appears as a sticky "card" that animates with the page.
- **Stack:** Next.js + `lenis` + `gsap` ScrollTrigger + Mux scrubbable streams + Mapbox custom + Cloudbeds / Mews booking API + Howler.

---

## Lifestyle / Fashion / Beauty

### Fashion brand / streetwear
- **Generic:** Shopify default theme.
- **Elevated:** Hydrogen-on-Remix custom Shopify, scroll-driven lookbook with horizontal pan sections, marquee branded strip, image distortion on hover, persistent audio loop (drop announcement track).
- **Archetype:** Cinematic Lookbook + Editorial Launch.
- **Signature moment:** Drop-day landing converts the entire homepage into the drop campaign with countdown.
- **Stack:** Hydrogen + Tailwind + `gsap` + `lenis` + Mux + Howler + Sanity for editorial content + Shopify as commerce backend.

### Beauty / skincare / fragrance
- **Generic:** Stock-photo grids, "natural ingredients" copy.
- **Elevated:** Ingredient pages as illustrated micro-stories, scroll-revealing the formula like a recipe, ambient nature soundscape, custom cursor showing scent notes on hover, palette tied to product line.
- **Archetype:** Brand Microsite + Editorial.
- **Signature moment:** "Make your own routine" interactive quiz with animated product reveal.
- **Stack:** Next.js + `motion` + `lenis` + `@paper-design/shaders-react` for ambient gradients + Sanity + Shopify Buy SDK + Howler.

### Jewelry / luxury accessories
- **Generic:** Catalog grid.
- **Elevated:** 3D product viewer for each piece (rotate, zoom, light source), scroll-scrubbed atelier-process video, editorial typography, restrained motion (luxury = restraint).
- **Archetype:** Case Study Microsite + Lookbook.
- **Signature moment:** Each piece has its own 3D viewer with realistic gemstone rendering (postprocessing bloom + DOF).
- **Stack:** Next.js + R3F + drei (`useGLTF` + `MeshTransmissionMaterial` for gems) + `gltf-transform` for product models + Shopify + `gsap` for editorial reveals.

---

## Creative Professionals

### Photographer
- **Generic:** Squarespace or Format gallery.
- **Elevated:** Image-distortion hover effects, full-bleed slideshow per series, scroll-driven story pacing, exhibit-style typographic captions, custom cursor showing image metadata.
- **Archetype:** Designer Portfolio + Case Study.
- **Signature moment:** Each series is its own micro-site with bespoke type pairing and motion.
- **Stack:** Astro + `lenis` + `gsap` + `curtainsjs` (image distortion) + `plaiceholder` LQIP + Sanity or local images.

### Filmmaker / director / videographer
- **Generic:** Vimeo embed grid.
- **Elevated:** Hero reel scrubbing on scroll, custom Mux player with branded controls, project case studies that play like director's commentary, optional ambient track per project.
- **Archetype:** Studio Showreel.
- **Signature moment:** Hover a project → preview video plays inline; click → fullscreen with scroll-scrubbed timeline.
- **Stack:** Next.js + Mux Player (customized) + `gsap` + `lenis` + `motion` for transitions + Sanity for project docs.

### Illustrator / graphic designer
- **Generic:** Behance redirect or generic portfolio.
- **Elevated:** Asymmetric grid, hand-cursor pointer, generative noise textures matching the work, kinetic typography, "now reading / making" widget in footer.
- **Archetype:** Designer Portfolio.
- **Signature moment:** Drag-and-drop work-in-progress preview on the homepage.
- **Stack:** Vite + React + `gsap` + `lenis` + `framer-motion` + MDX for project case studies.

### Music artist / band / DJ
- **Generic:** Bandcamp + Linktree.
- **Elevated:** Audio-reactive hero visualization, scroll-driven discography with embedded players, tour-date map, merch via Shopify Buy Button, lyric pages with scroll-synced lyrics.
- **Archetype:** Studio Showreel + Brand Microsite.
- **Signature moment:** Audio-reactive WebGL hero responds to the latest single playing in the background.
- **Stack:** Next.js + R3F + `tone` (analyzer node) + Howler + Spotify embed API or custom player + Shopify Buy SDK + Mapbox for tour map.

### Podcast / radio show
- **Generic:** Anchor.fm default page.
- **Elevated:** Waveform-driven hero, episode cards as designed objects, transcripts with timestamp-clickable lines, guest profiles with rich illustrations.
- **Archetype:** Editorial / Designer Portfolio.
- **Signature moment:** Click any sentence in the transcript → audio jumps to that timestamp.
- **Stack:** Astro + `wavesurfer.js` + `howler` + MDX transcripts + RSS feed parsing.

---

## Professional Services

### Law firm (boutique / craft)
- **Generic:** Stock photo of handshake, partner headshots in suits, Bootstrap.
- **Elevated:** Editorial typography (think VC firm aesthetic), partner pages as long-form profiles, case-study writeups treated as journalism, restrained motion, single signature interaction (animated case-resolution timeline).
- **Archetype:** VC Firm.
- **Signature moment:** Practice-area pages each have a custom illustrated header (Rive).
- **Stack:** Astro + native scroll + `@motionone/dom` + `@rive-app/canvas` for header illustrations + MDX + Sanity for case studies.

### Accountant / financial advisor / wealth manager
- **Generic:** Generic finance imagery.
- **Elevated:** Same playbook as VC firm — editorial, restrained, "thesis"-style writing pieces, partner credentials prominent.
- **Archetype:** VC Firm.
- **Signature moment:** Interactive net-worth visualization or fee transparency calculator.
- **Stack:** Astro + `motion` + `chroma-js` for chart palettes + MDX.

### Consultancy / strategist
- **Generic:** McKinsey-imitator with stock photos.
- **Elevated:** Manifesto-as-hero, case-studies-as-essays, "How we work" interactive timeline, custom illustrated framework diagrams (Rive).
- **Archetype:** VC Firm + Editorial Astro.
- **Signature moment:** Interactive framework diagram you can step through.
- **Stack:** Astro + `motion` + `@rive-app/canvas` + MDX.

---

## Health & Wellness

### Dentist / private clinic
- **Generic:** Stock smiling-patient photos, blue-and-white palette, online booking widget.
- **Elevated:** Warm bespoke palette (no medical-blue), clinic photography by an actual photographer, scroll-driven "what to expect" walkthrough, custom illustrated procedure explainers, embedded online booking that feels native.
- **Archetype:** Brand Microsite + Case Study.
- **Signature moment:** Procedure pages have a Rive animation explaining the process step by step.
- **Stack:** Astro + `lenis` (light) + `motion` + `@rive-app/canvas` + Sanity + native booking widget (custom-styled) or Calendly embed.

### Therapist / coach / wellness practitioner
- **Generic:** Generic "calm" stock imagery.
- **Elevated:** Long-form approach as the hero (writing-first), ambient color gradients (Paper Shaders), one tasteful illustration per page, audio testimonials with waveform.
- **Archetype:** VC Firm aesthetic + Editorial.
- **Signature moment:** "First session walkthrough" with subtle motion + warm color palette.
- **Stack:** Astro + `@paper-design/shaders-react` (subtle background) + `wavesurfer.js` for testimonials + MDX.

### Gym / yoga / fitness studio
- **Generic:** Photos of fit people, class grid.
- **Elevated:** Bold typographic hero, kinetic motion echoing the workout style (sharp for HIIT, flowing for yoga), class-schedule grid as designed artifact, member testimonials as marquee, branded video reels.
- **Archetype:** Brand Microsite.
- **Signature moment:** Class type pages have unique motion personality (HIIT = jagged GSAP, yoga = slow lerp).
- **Stack:** Next.js + `lenis` + `gsap` + Mux + MindBody / Mariana Tek API + Howler for class-style ambient previews.

### Doctor / specialist clinic / medspa
- **Generic:** Same as dentist.
- **Elevated:** Same playbook — bespoke palette, custom photography, illustrated procedure explainers, transparent pricing (rare in this space), warm copy.
- **Archetype:** Brand Microsite.
- **Stack:** Same as dentist above.

---

## Real Estate & Property

### Luxury real estate / individual listing
- **Generic:** MLS photo grid.
- **Elevated:** Cinematic hero video, scroll-driven floor-plan walkthrough, drone-photography parallax, 3D matterport embed styled, neighborhood explorer with custom map.
- **Archetype:** Cinematic Lookbook + Case Study.
- **Signature moment:** Scroll triggers a 3D model fly-through of the property.
- **Stack:** Next.js + Mux + R3F (matterport or custom glTF) + Mapbox custom + `lenis` + `gsap` ScrollTrigger.

### Volume real estate / agency (multi-listing)
- **Generic:** Search-filters-on-the-left layout.
- **Elevated:** Map-first interface, listing cards as designed objects, custom filter UI, "neighborhood feel" pages with editorial photography.
- **Archetype:** WebGL Hero SaaS + Editorial.
- **Stack:** Next.js + Mapbox + `motion` + Sanity / Listings API.

### Architect / interior design firm
- **Generic:** Project grid + about page.
- **Elevated:** Each project is its own micro-site with custom photography, scroll-driven before/after, materials palette as artifact, axonometric drawings as interactive SVG.
- **Archetype:** Studio Showreel + Case Study.
- **Signature moment:** Per-project palette swatch animates in as you scroll the page.
- **Stack:** Astro + `lenis` + `gsap` + Sanity + `react-compare-slider`.

### Furniture / home goods
- **Generic:** Shopify default.
- **Elevated:** 3D product viewers per piece, room scenes with hotspot products, editorial collections, made-process video per item.
- **Archetype:** Lookbook + Editorial.
- **Stack:** Hydrogen + R3F + drei + Sanity + Mux.

---

## Education & Culture

### University / school / program
- **Generic:** CMS template with too many sections.
- **Elevated:** Editorial-magazine aesthetic, student work as the homepage hero, scroll-driven program pages, faculty pages as designed profiles.
- **Archetype:** Editorial Astro + VC Firm.
- **Signature moment:** Homepage rotates featured student work weekly.
- **Stack:** Astro + Sanity + `gsap` + `lenis` (light) + MDX.

### Museum / art gallery / cultural institution
- **Generic:** Booking widget + exhibition grid.
- **Elevated:** Each exhibition is its own micro-site, audio guide integration, scroll-driven storytelling, custom typography per exhibition, interactive 3D model of key works.
- **Archetype:** Case Study Microsite + Editorial Launch.
- **Signature moment:** "Walking tour" mode — scroll through the exhibition virtually with audio narration.
- **Stack:** Next.js + Howler (audio guide) + R3F (3D works) + `gsap` + Sanity.

### NGO / nonprofit
- **Generic:** Hero with photo of children + donate button.
- **Elevated:** Manifesto-as-hero, data visualization of impact, donor testimonials as designed quotes, transparent financials, scroll-driven story of a single beneficiary.
- **Archetype:** Editorial Astro + Brand Microsite.
- **Signature moment:** Interactive impact map showing every dollar's journey.
- **Stack:** Astro + `d3` for visualization + Mapbox + Stripe / GiveButter embed + MDX for stories.

### Author / writer / journalist personal site
- **Generic:** WordPress default.
- **Elevated:** Minimalist brutalist, type-first, RSS-friendly, archive treated as a designed system.
- **Archetype:** Minimalist Brutalist.
- **Stack:** Astro + MDX + `pagefind` for search + `fontaine` for fallback metrics.

---

## Tech & Startup

### B2B SaaS
- **See archetype:** WebGL Hero SaaS (in `archetypes.md`).
- **Stack:** Next.js + R3F + `motion` + Tailwind + shadcn + Sanity + Vercel OG.

### AI startup / ML platform
- **Generic:** Same as SaaS but with "GPT" in the copy.
- **Elevated:** Generative shader hero (particle field, mesh gradient with subtle data viz), interactive playground embed, transparent benchmarks page, model-architecture explainer as scroll-driven story.
- **Archetype:** WebGL Hero SaaS + Case Study.
- **Signature moment:** "Try it live" inline playground in the hero (or right below).
- **Stack:** Next.js + R3F + `@paper-design/shaders-react` + Vercel AI SDK + `cmdk` + shadcn.

### Crypto / web3 project
- **Generic:** Generic crypto-bro aesthetic.
- **Elevated:** Sober editorial typography (counter the noise), data viz of protocol, transparent docs, restrained motion, one signature interactive (e.g. supply curve viz).
- **Archetype:** WebGL Hero SaaS + Editorial.
- **Stack:** Next.js + `d3` + `motion` + shadcn + MDX docs.

### Developer tool / open source library
- **Generic:** README-on-a-page.
- **Elevated:** Design-Forward Docs archetype, interactive code examples in the hero, copy-paste install command with click-to-copy, contributor wall, benchmarks page.
- **Archetype:** Design-Forward Documentation.
- **Stack:** Astro Starlight or Fumadocs + `shiki` + `pagefind` + MDX.

### Indie hacker product
- **Generic:** Carrd page.
- **Elevated:** Same as SaaS but smaller surface area, "built by one person" transparency moment (now-page, build-log, MRR transparency).
- **Archetype:** WebGL Hero SaaS lite.
- **Stack:** Astro + `motion` + Tailwind + Lemon Squeezy / Stripe.

---

## Commerce (Misc)

### Single-product brand (one hero product)
- **Generic:** Shopify default theme.
- **Elevated:** Editorial product launch playbook, 3D product viewer, scroll-driven feature tour, unboxing video, testimonial wall as designed grid.
- **Archetype:** Editorial Product Launch + Lookbook.
- **Stack:** Hydrogen + R3F + Mux + `gsap` + Shopify backend.

### Marketplace (Etsy-style multi-seller)
- **Generic:** Algolia search + grid.
- **Elevated:** Curated editorial collections featured on homepage, seller profile pages as designed artifacts, custom search UX, "vibe filters" (mood-based discovery).
- **Archetype:** Editorial + Lookbook.
- **Stack:** Next.js + Algolia + Sanity for editorial + Stripe Connect.

### D2C niche product (candles, sneakers, ceramics, etc.)
- **Generic:** Shopify default.
- **Elevated:** Brand-microsite playbook, product pages as editorial features, founder-story scroll, ingredient/material transparency.
- **Archetype:** Brand Microsite + Lookbook.
- **Stack:** Hydrogen or Next + Shopify Buy SDK + `gsap` + Mux + Sanity.

---

## Special / Hybrid

### Personal portfolio (anyone, not just designer)
- **Generic:** LinkedIn or About.me.
- **Elevated:** Single page, opinionated typography, now-page, writing index, projects index, photo / contact, one signature interaction (could be a small generative art piece, a kinetic name treatment, a custom cursor).
- **Archetype:** Minimalist Brutalist OR Designer Portfolio depending on personality.
- **Stack:** Astro + MDX + `motion` for one moment.

### Wedding / event invitation site
- **Generic:** The Knot template.
- **Elevated:** Cinematic hero, scroll-driven story of the couple, RSVP form as designed artifact, ambient music, custom typography, photography-rich.
- **Archetype:** Brand Microsite + Cinematic Lookbook.
- **Stack:** Astro + `gsap` + Mux + `lenis` + `react-hook-form` + ConvertKit / custom RSVP endpoint.

### Conference / event (already covered in archetypes)
- **Archetype:** Conference Site.

### Travel agency / tour operator
- **Generic:** Booking-engine-driven generic templates.
- **Elevated:** Per-destination editorial pages, scroll-driven itinerary reveals, custom maps, photography-led, booking widget custom-styled.
- **Archetype:** Cinematic Lookbook + Case Study.
- **Stack:** Next.js + Mapbox + `lenis` + `gsap` + Sanity + WeTravel / FareHarbor / Bokun API.

### Newsletter / publication
- **Generic:** Substack default.
- **Elevated:** Editorial typography, archive treated as a magazine, paywall as a designed moment, ambient color tied to issue, audio version per post.
- **Archetype:** Editorial Astro + Design-Forward Docs.
- **Stack:** Astro + MDX + Beehiiv / Buttondown API + `pagefind`.

### Recruiting / hiring brand page
- **Generic:** "Careers" page on the main site.
- **Elevated:** Standalone site, team photos as designed grid, "day in the life" video, benefits as illustrated cards, application form that doesn't feel like a form.
- **Archetype:** Editorial + Brand Microsite.
- **Stack:** Astro + Mux + `motion` + Greenhouse / Lever API.

### Religious / spiritual community
- **Generic:** Generic church template.
- **Elevated:** Editorial-magazine, sermon archive with audio + transcript, calendar of events, photography-led, restrained palette.
- **Archetype:** Editorial Astro.
- **Stack:** Astro + `wavesurfer.js` + MDX + ChurchCenter / Planning Center API.

### Local service business (plumber, electrician, contractor)
- **Generic:** Yellow Pages template.
- **Elevated:** Same VC-firm restraint applied — strong typography, real photography of the team and work, transparent pricing, scheduled-booking widget, neighborhood-served map.
- **Archetype:** Brand Microsite + VC Firm aesthetic.
- **Signature moment:** "Real photos of our recent work" gallery treated like a case study.
- **Stack:** Astro + `motion` + Mapbox + Calendly / Housecall Pro embed.

---

## The universal rule

For EVERY domain, the aesthetic upgrade path is the same three moves:

1. **Pick a real archetype** from `archetypes.md`. Don't say "small business site" — say "Editorial Astro" or "Brand Microsite."
2. **Choose ONE signature moment** that's specific to the domain. Not a "WebGL hero" generically — but a *map of property* for real estate, a *3D gem viewer* for jewelry, a *scroll-synced lyrics page* for a band.
3. **Mix building blocks deliberately** from `building-blocks.md`. One loader, one hero pattern, one nav, one scroll signature, one cursor, one footer. Constraint is the design.

Domain doesn't determine taste — the *application of taste to the domain* is what makes the site Awwwards-grade. A dentist site with thoughtfully chosen photography, restrained motion, a Rive procedure animation, and `lenis` smooth scroll will outclass 95% of agency sites.

---

## Pattern: when the user gives you "build a site for {anything}"

1. Identify the **domain** (above).
2. Identify the **archetype** (`archetypes.md`).
3. Pick the **signature moment** — ask the user if it's not obvious from the brief.
4. Compose **building blocks** (`building-blocks.md`) — one per slot.
5. Choose the **library combo** (`recipes.md` for proven starters, `libraries.md` for substitutions).
6. Confirm the **base stack** (`stack-decisions.md`) — Astro / Next / Nuxt / Vite-React / Hydrogen / Webflow.
7. State the plan in one paragraph. Get the user's "yes." Then scaffold.

Never reach for "generic small business template." Every brief is a chance to make something memorable.
