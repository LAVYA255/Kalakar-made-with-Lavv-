# Building Blocks — Mixable UI/UX Patterns

A design-forward site is rarely "one big idea." It's a curated collection of small named patterns, each chosen on purpose. This file catalogs the patterns so you can mix them deliberately — one loader + one hero + one nav + one scroll signature + one cursor + one footer = a unique site, even though every individual piece has been seen before.

**How to use:** When briefing a build, pick ONE pattern from each category. Don't pick three heroes or two cursor styles — the goal is one strong choice per slot.

---

## Loaders & intros

| Pattern | Description | Library | Best for |
|---|---|---|---|
| **Percent counter** | "0% → 100%" with asset preload progress | hand-rolled + `Promise.all` on critical assets | Agency / studio showreel |
| **Brand mark draw-in** | SVG logo draws stroke-by-stroke | `vivus` or GSAP `DrawSVGPlugin` | Editorial, fashion, luxury |
| **Sliding panels** | Solid colored panels slide off to reveal site | GSAP timeline | Agency, brand campaign |
| **Mask reveal** | Letter / shape mask wipes off the page | CSS `clip-path` + GSAP | Designer portfolio |
| **Audio-on prompt** | "Best experienced with sound on" overlay | Custom + Howler | Studio showreel, film/music |
| **Typewriter intro** | Greeting types out character by character | `splitting` + GSAP stagger | Personal site, brutalist |
| **3D bootstrap** | Three.js scene loads in, camera dolly | R3F + `@react-three/drei` `useProgress` | Generative hero, agency |
| **None (instant)** | Site loads immediately; no intro | — | VC firm, docs, minimalist |
| **Skeleton-into-real** | Wireframe layout fades into the finished design | GSAP timeline | Editorial, case study |

**Rule:** if the loader is longer than the actual load time, kill it. Loaders that exist to be art make the site feel slow.

---

## Hero patterns

| Pattern | Description | Library | Domains |
|---|---|---|---|
| **Kinetic typography** | Oversized animated word(s); the brand IS the hero | GSAP + `split-type` | Studio, designer, music artist |
| **WebGL mesh gradient** | Animated gradient mesh background, sharp type overlay | `@paper-design/shaders-react` or custom GLSL | SaaS, AI startup, fintech |
| **Image distortion field** | Hero image bends/ripples on cursor | `curtainsjs` or R3F plane + GLSL | Fashion, agency, photographer |
| **Video loop + overlay** | Full-bleed muted looping video, type overlay | Mux + `<video>` | Lookbook, hospitality, hotel |
| **3D object centerpiece** | One glTF model rotating, parallax on scroll | R3F + drei + `gltf-transform`-optimized model | Product launch, agency |
| **Split-screen** | 50/50 — text on one side, media on the other | CSS Grid + GSAP | Restaurant, real estate, F&B |
| **Marquee strip** | Endless horizontal scrolling text band as hero | `react-fast-marquee` or GSAP | Streetwear, music, agency |
| **Full-bleed photo with kinetic caption** | Editorial photo, caption animates per scroll | GSAP ScrollTrigger | Photographer, fashion, travel |
| **Asymmetric collage** | Multiple images at offset positions, parallax | GSAP scroll layers | Designer portfolio, agency |
| **Particle field** | Generative particles with subtle interaction | R3F + `simplex-noise` + `maath` | AI / web3 / data startup |
| **Audio-reactive viz** | Visualization driven by ambient music | `tone` + R3F | Music artist, podcast, DJ |
| **Type-only minimalist** | Just words. Big. Confident. | Pure CSS + variable font | Author, consultant, law firm |
| **Hand-rolled WebGL painting** | Damien Mortini school — generative painterly composition | Raw WebGL + `ogl` + GLSL | Brand microsite, art-led commerce |

---

## Navigation patterns

| Pattern | Description | Best for |
|---|---|---|
| **Sticky transparent → solid** | Bar fades to solid on scroll | SaaS, most archetypes |
| **Fullscreen hamburger** | Click → overlay with massive type links | Studio, designer, fashion |
| **Persistent side-tab** | Vertical nav strip on the left/right edge | Editorial, magazine, gallery |
| **Floating dock** | Tab-bar-style floating in viewport | Designer portfolio, app marketing |
| **Cmd+K command palette** | `cmdk` library, power-user navigation | Docs, SaaS, internal tool look |
| **Dot navigation** | Vertical dots for in-page sections | Long-scroll case study |
| **Marquee nav** | Links scroll horizontally in the header | Brand campaign, experimental |
| **No nav (single page)** | Everything is one scroll | Microsite, campaign, art piece |
| **Floating "menu" hint** | Small CTA opens overlay; rest is clean | Luxury, fashion, hospitality |

---

## Page transition patterns

| Pattern | Description | Library |
|---|---|---|
| **View Transitions API** | Native browser crossfade with shared elements | Built-in (Astro, Next 15+) |
| **Curtain wipe** | Solid color sweeps across, hides swap, sweeps out | GSAP timeline |
| **Mask reveal** | Circular / shaped clip-path reveals new page | `clip-path` + GSAP |
| **Persistent WebGL canvas** | Canvas never unmounts; content swaps beneath | Barba.js + Three/OGL — see `agency-wiring.md` |
| **Slide-up / slide-over** | New page slides over old, like iOS | Framer Motion `AnimatePresence` |
| **Letterboxed fade** | Black bars in/out + crossfade | GSAP |
| **None** | Instant. Snappy. | — |

---

## Cursor patterns

| Pattern | Description | Library |
|---|---|---|
| **Magnetic** | Cursor pulled toward interactive elements | GSAP `quickTo` + hand-roll |
| **Sticky text** | Cursor morphs into label ("View Project") on hover | `mouse-follower` (Cuberto) |
| **Image preview** | Cursor becomes thumbnail of hovered link | GSAP + image swap |
| **Blend-mode dot** | Inverted-color cursor (`mix-blend-mode: difference`) | Pure CSS |
| **Dot + ring** | Small dot, outer ring lags behind | GSAP `quickTo` |
| **Glow / blob** | Soft blob with radial gradient | `blobity` |
| **Crosshair** | Long thin lines extending from cursor | Custom |
| **Native** | OS cursor; respect for accessibility | — |

**Rule:** if you hide the native cursor (`cursor: none`), the custom cursor MUST be visible at all times. Otherwise you've broken the site for keyboard users.

---

## Scroll signatures

| Pattern | Description | Library |
|---|---|---|
| **Lenis-smooth** | Buttery momentum-eased scroll | `lenis` |
| **Native fast** | OS-native scroll; for sites that should feel snappy | — |
| **Horizontal pinned section** | Vertical scroll drives horizontal pan | GSAP ScrollTrigger pin + tween |
| **Scrub video** | Scroll position controls video timeline | GSAP ScrollTrigger + `<video>` |
| **Stacked cards** | Cards stack like a deck as you scroll | GSAP + `position: sticky` |
| **Parallax layers** | Multiple z-depths move at different speeds | GSAP yPercent stagger |
| **Color shift per section** | Background color tween per IntersectionObserver | Custom + GSAP |
| **Marquee-on-scroll-velocity** | Marquee speeds up / reverses with scroll direction | `react-fast-marquee` + scroll velocity |
| **Pinned scrub-reveal** | Text reveals word-by-word as you scroll its section | `split-type` + ScrollTrigger |
| **Snap sections** | CSS scroll-snap, one viewport per section | CSS `scroll-snap-type` |

---

## Footer patterns

| Pattern | Description | Best for |
|---|---|---|
| **Oversized type signature** | Brand name / slogan in 30vw type, minimal else | Studio, agency |
| **Fullscreen newsletter** | Footer IS a signup form, hero-sized | SaaS, newsletter business |
| **Contact-as-art** | Email / address typeset like an editorial closing | VC firm, law firm, luxury |
| **Sticky reveal** | Footer hides until last section "lifts off" to reveal it | Studio, designer |
| **Map embed** | Custom-styled map (Mapbox / native) for physical business | Restaurant, hotel, real estate |
| **Awards / press logos** | Logo strip of accolades, marquee or grid | Agency, hospitality |
| **Now playing / status** | "Currently reading / building / listening" widget | Designer portfolio, indie hacker |
| **Sitemap + manifesto** | Full site map + a manifesto paragraph | Studio, philosophy-driven brand |

---

## Audio UI patterns

| Pattern | When | How |
|---|---|---|
| **Persistent mute toggle** | Site has any audio | Top-right SFX icon, state in localStorage |
| **Scene-based ambient** | Long-form narrative | Preload per section, crossfade on entry — Howler |
| **Sound-reactive viz** | Music artist, podcast | `tone` analyzer + R3F mesh deformation |
| **UI sound effects** | Studio showreel | Subtle hover/click sounds (Howler, sub-200ms files) |
| **Audio-on intro overlay** | First-visit ambient experience | Modal: "Continue with sound / continue silent" |

**Rule:** never autoplay with sound. Period.

---

## Form patterns

| Pattern | Description | Library |
|---|---|---|
| **Conversational multi-step** | One field per screen, animated transitions | `react-hook-form` + Framer Motion |
| **Floating labels** | Label shrinks above input on focus | Tailwind + CSS |
| **Inline validation art** | Success/error states as illustrations | Lottie / Rive |
| **Single-field giant input** | "Tell us your idea" — one big textarea | Custom |
| **Calendly-style booking** | Embed `cal.com` or custom slot picker | `cal.com/embed` |

---

## Image presentation patterns

| Pattern | Description | Library |
|---|---|---|
| **LQIP blur-up** | Tiny base64 preview → swap to full image | `plaiceholder` / `thumbhash` |
| **Dithered duotone** | Brand-color two-tone with retro dither | Custom GLSL or `@paper-design/shaders` |
| **Hover distortion** | Image ripples on cursor enter | `curtainsjs` or `hover-effect` |
| **Before/after slider** | Comparison reveal | `react-compare-slider` |
| **Marquee gallery** | Endless horizontal image strip | GSAP marquee |
| **Tilt on hover** | 3D-style perspective tilt | Custom transforms |
| **Stagger reveal grid** | Cells fade/slide in stagger on scroll | GSAP + IntersectionObserver |
| **Mason / packed** | Pinterest-style packed grid | `masonry-layout` / `muuri` |
| **Lightbox** | Click to expand fullscreen | `photoswipe` |

---

## Typography patterns

| Pattern | Description | Tools |
|---|---|---|
| **Variable font slider** | User scrubs a slider, font weight/width morphs | Variable font + range input |
| **Kinetic display** | Headline letters animate in stagger on scroll | `split-type` + GSAP |
| **Marquee text band** | Looping horizontal text | `react-fast-marquee` |
| **Type-on-path** | Text follows a curve / circle | GSAP `MotionPathPlugin` or SVG textPath |
| **Glyph hover swap** | Letter changes glyph variant on hover (ligatures) | OpenType features + CSS |
| **Wrap-balanced headline** | No orphans, ever | `react-wrap-balancer` |
| **3D text in scene** | Type lives inside WebGL | `troika-three-text` |
| **Marquee on scroll velocity** | Reverses with scroll direction | Custom |

---

## Theme patterns

| Pattern | Description | Library |
|---|---|---|
| **System tri-state** | Dark / Light / System | `next-themes` / Astro custom |
| **OKLCH animated transition** | Color tokens crossfade between modes | CSS `view-transition` + OKLCH vars |
| **Per-section theme** | Page tints shift section-by-section | IntersectionObserver + CSS vars |
| **Brand-locked (no toggle)** | One mode, on purpose | — |

---

## 404 / Empty / Error patterns

Every design-forward site should have a designed 404 — it's a free aesthetic moment that 95% of sites waste.

- **Generative noise / glitch** — animated WebGL fill
- **ASCII art** — `figlet`-style massive text saying "lost"
- **Playable mini-game** — Three.js or Canvas2D (Bruno Simon school)
- **Editorial joke** — full-bleed image with witty caption
- **Search bar with suggestions** — recovery-first

---

## Easter eggs (optional but loved)

- **Konami code** unlocks debug mode (leva panel)
- **`/secret` route** with a hidden experiment
- **Console.log art** with ASCII brand mark + hiring CTA
- **`?theme=hyper`** flag enabling extreme variant
- **Click logo 5 times** triggers a moment

These are unboxing-moments. Add one per site. Don't add five.

---

## How to compose

A site is roughly:

```
1 × loader  +  1 × hero  +  1 × nav  +  1 × scroll-signature
+ 1 × cursor  +  1 × transition  +  1 × footer
+ N × image / type / audio / form patterns (as content demands)
+ N × small content sections (each its own micro-composition)
```

Pick one strong choice per slot. Resist the urge to add more. Constraint is the design.
