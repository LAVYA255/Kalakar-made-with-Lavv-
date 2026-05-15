# Performance Playbook

Design-forward sites die on Core Web Vitals if you're sloppy. WebGL + smooth scroll + custom cursor + audio = LCP / INP nightmare unless you stage it right. This is the playbook.

---

## The non-negotiables

1. **`prefers-reduced-motion`** gates every animation, every smooth scroll, every WebGL hero. No exceptions.
2. **Audio starts muted.** No autoplay-with-sound. Persistent mute toggle in the UI.
3. **WebGL hero has a static poster.** Ship the poster as LCP; mount the canvas after first paint.
4. **Fonts** are subset + self-hosted + paired with fallback metric overrides (`fontaine` or `next/font`).
5. **`detect-gpu`** gates feature tier on any R3F-heavy archetype. Mobile users on mid-tier phones get degraded shaders, fewer particles, lower DPR.
6. **INP target: <200ms.** Anything heavier than 200ms during scroll = jank. GSAP ScrollTrigger callbacks should be cheap; do heavy work in `requestIdleCallback`.
7. **AVIF for raster, then WebP, then JPEG.** Always with `<picture>` + responsive `srcset`.
8. **Third-party scripts** (GTM, analytics, chat) → `partytown` to move them off main thread.

---

## LCP strategy for WebGL heroes

The hero canvas is almost never the LCP element. Make it intentionally not be.

**Pattern:**
1. Render a static gradient PNG / WebP as the LCP element. Position it absolutely behind the hero.
2. Lazy-mount the Three / R3F canvas with `loading="lazy"` semantics (after `requestIdleCallback` or `requestAnimationFrame`-deferred).
3. Cross-fade the canvas in once it's ready.
4. On reduced motion, never mount the canvas — keep the poster.

```jsx
// Sketch — adapt to your framework
const [mountCanvas, setMountCanvas] = useState(false);

useEffect(() => {
  if (matchMedia('(prefers-reduced-motion: reduce)').matches) return;
  const tier = await getGPUTier(); // detect-gpu
  if (tier.tier < 2) return; // bail on weak devices
  requestIdleCallback(() => setMountCanvas(true));
}, []);
```

LCP element is the poster. Real LCP <1.5s even with 5MB shader compilation work happening in the background.

---

## INP & scroll jank

ScrollTrigger fires callbacks at 60fps. Anything blocking >16ms inside a callback drops a frame.

- **Centralize RAF.** When `lenis`, `gsap`, and `@react-three/fiber` all run their own RAF, you get triple-tick jitter. Route everything through `tempus`:

```js
import { tempus } from 'tempus';
import gsap from 'gsap';

gsap.ticker.lagSmoothing(0);
gsap.ticker.remove(gsap.updateRoot);
tempus.add((time) => gsap.updateRoot(time / 1000), 0);
```

- **Read DOM once per frame.** Cache `getBoundingClientRect` / `offsetWidth` reads at frame start; don't interleave reads and writes (layout thrash).
- **Use `transform` and `opacity` only** in animation hot paths. No `top`, `left`, `width`, `height`.
- **`will-change: transform`** only on actively animating elements. Remove after.
- **Defer heavy work** with `requestIdleCallback`. Lottie scrubs, SVG path measurements, image decoding — all idle work.

---

## Font loading & CLS

Variable fonts are 200-500KB. Loaded naively, they cause CLS as fallbacks reflow.

- **Self-host via `@fontsource-variable/inter`** (or `next/font` if Next).
- **Add `fontaine`** to auto-generate `@font-face` metric overrides for the system fallback. CLS from font swap goes to ~0.
- **Preload critical weights only.** `<link rel="preload" as="font" type="font/woff2" crossorigin>`.
- **`font-display: optional`** for non-essential weights (display only if already cached). `swap` for hero text.
- **`unicode-range`** to subset latin / latin-ext separately.

---

## GPU tiering with detect-gpu

```js
import { getGPUTier } from 'detect-gpu';

const gpuTier = await getGPUTier();
// tier 0 = blocklisted, 1 = weak, 2 = mid, 3 = strong

const features = {
  postprocessing: gpuTier.tier >= 2,
  shadows: gpuTier.tier >= 2,
  particleCount: gpuTier.tier >= 3 ? 5000 : gpuTier.tier >= 2 ? 2000 : 500,
  dpr: Math.min(gpuTier.tier, window.devicePixelRatio),
};
```

Pass `dpr` into R3F `<Canvas dpr={dpr}>`. Pass `particleCount` into your shader uniforms. Disable bloom / DOF / chromatic-aberration on tier <2.

---

## Image strategy

- **AVIF first.** `next/image` and `astro:assets` ship AVIF by default. `<picture>` with `type="image/avif"` then `image/webp` then `image/jpeg`.
- **Responsive `srcset`** at 1x, 2x, 3x. Use `sizes="(max-width: 768px) 100vw, 50vw"` honestly.
- **`loading="lazy"`** on below-fold; **`fetchpriority="high"`** + `loading="eager"` on hero.
- **`plaiceholder` or `thumbhash`** for LQIP blur-up. Inline as base64.
- **`decoding="async"`** everywhere.

---

## Audio rules

Browsers block autoplay-with-sound. Don't fight this — design around it.

- Audio is muted by default.
- A visible, accessible mute / unmute toggle persists in the UI.
- First user interaction (`click`, `keydown`) is the trigger to unmute or start. Use `howler` `Howl({ html5: false })` for short loops, `html5: true` for long tracks.
- **Floema pattern:** preload per-scene audio with `<link rel="prefetch" as="audio" href="...">` so it's ready when the scroll-section enters.

---

## OG / share images

Every page should have a tailored OG image. Generate them at the edge.

- **Next:** `@vercel/og` in a route handler returning `ImageResponse`. Cache for a year.
- **Astro:** `satori` + `sharp` in a build-time integration, or runtime via Astro endpoint.
- For conference / event sites, generate per-speaker OG images. Drives shares.

---

## llms.txt + AI search

AI Overviews / Perplexity / ChatGPT now drive 5-15% of discovery for some categories. Optimize for them.

- `llms.txt` at the root with a structured index of canonical pages.
- `llms-full.txt` if the site is small (< 50 pages) — dump the entire content tree as markdown.
- Use `schema-dts` for typed JSON-LD: `Article` for writing, `Person` for team / partners, `Organization` for the entity, `SoftwareApplication` / `Product` for SaaS, `Event` for conferences.
- Crawlable, semantic HTML inside `<main>` — don't bury copy inside `<canvas>`.

---

## Bundle hygiene

- **Code-split aggressively.** Hero canvas in its own chunk. Page-specific shaders dynamic-imported. No GSAP on the docs page if it doesn't animate.
- **`size-limit`** in CI. Fail the build if bundles bloat.
- **`@next/bundle-analyzer`** / `rollup-plugin-visualizer` to find offenders.
- **Tree-shakeable imports.** `import { gsap } from 'gsap'` not `import gsap from 'gsap/all'`.
- **Replace `lodash` with `es-toolkit`.** ~70% smaller, modern API.
- **Use `dayjs` over `moment`.** Or native `Intl.DateTimeFormat` where possible.

---

## Hosting / edge

- **Vercel** for Next / Astro — best edge story.
- **Cloudflare Pages** + Workers for tight latency budgets (ref.digital uses CF Workers for forms).
- **Shopify Oxygen** for Hydrogen sites.
- **Always set:**
  - `Cache-Control: public, max-age=31536000, immutable` for hashed assets.
  - `Cache-Control: s-maxage=86400, stale-while-revalidate=604800` for HTML.
  - Brotli for text assets.
- **HTTP/3 + early hints** on assets where supported.

---

## Lighthouse targets (design-forward sites)

| Metric | Target | Hard ceiling |
|---|---|---|
| LCP | <1.5s | 2.5s |
| INP | <100ms | 200ms |
| CLS | <0.05 | 0.1 |
| FCP | <1s | 1.8s |
| TBT | <100ms | 200ms |
| Bundle (initial JS) | <150KB gzip | 250KB |

If you blow these, the design suffers — the site feels heavy regardless of how pretty the motion is.

---

## Accessibility floor (non-negotiable)

- Tab navigation works without the custom cursor.
- All animations skippable.
- All audio captioned / has transcript.
- Focus indicators visible (don't `outline: none` without a replacement).
- Color contrast AA minimum (AAA for body text).
- `aria-hidden` on decorative canvas, `role="img"` with `aria-label` on meaningful canvas.
- Skip-to-content link.
- Form labels properly associated.

Awwwards-tier sites that fail basic a11y get roasted on Twitter. Don't be that site.
