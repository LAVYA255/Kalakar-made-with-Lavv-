# Library Catalog

230+ libraries that power design-forward web. Tiers: **essential** (you'll use it constantly), **popular** (good defaults), **niche-gem** (studio secret weapons most AIs miss). NPM package names in backticks.

---

## 1. Animation Engines

### Essential
- `gsap` — Industry-standard timeline-based animation. ScrollTrigger, Flip, SplitText, MorphSVG, DrawSVG, MotionPath plugins. Now free since 3.13. **essential**
- `motion` (was `framer-motion`) — Declarative React animation with layout animations + spring physics. layoutId magic, scroll-linked. **essential**
- `@motionone/dom` / `motion` (one) — Same author's tiny vanilla version on WAAPI. 3.8kb, hardware-accelerated, framework-agnostic. **popular**

### Popular
- `animejs` v4 — Rebuilt with timelines, scope, scroll-observer, draggables, WAAPI. MIT, low learning curve. **popular**
- `@theatre/core` / `@theatre/studio` — Browser-based animation editor; visually keyframe R3F scenes, export JSON. **niche-gem**
- `@motion-canvas/core` (**Motion Canvas**) — Code-driven alternative to Theatre.js; great for explainer-style cinematics. **niche-gem**
- `hydra-synth` (**Hydra**) — Live-coded visuals, used in installations and VJ work. **niche-gem**
- `popmotion` — Low-level animation primitives (powers Motion). Raw springs / inertia / keyframes. **niche-gem**
- `@formkit/auto-animate` — One-line layout animation. Zero-config list/grid transitions. **popular**
- `@react-spring/web` — Physics-based hooks. Imperative `useSpring`, gesture-friendly. **popular**
- `@use-gesture/react` — Drag/pinch/wheel/hover. Pairs with react-spring. **essential**

### Niche gems
- `animate-css-grid` — Animates grid-template changes (FLIP for grids). **niche-gem**
- `@react-spring/parallax` — Parallax pages composed of springs. **niche-gem**
- `velocity-animate` — Legacy but still shipping classic studio sites. **niche-gem**
- `wobble` — Critically-damped spring solver (Twitter Lite). **niche-gem**

---

## 2. Scroll & Smooth Scroll

### Essential
- `lenis` (was `@studio-freight/lenis`) — Current king of smooth scroll. Native-feeling momentum, RAF sync with GSAP, respects `prefers-reduced-motion`. **essential**
- `gsap` ScrollTrigger — Scroll-driven timelines, pinning, scrub, snap. Unmatched precision. **essential**
- `lenis/react` — React wrapper with hooks. **essential**

### Popular / Niche
- `locomotive-scroll` v5 — Pre-Lenis era; horizontal sections, parallax data-attrs. **popular**
- `@darkroom.engineering/tempus` (was `tempus`, was `@studio-freight/tempus`) — Centralized RAF orchestrator. Use when Lenis + GSAP + R3F coexist to prevent jank. **niche-gem (essential when 3D + scroll coexist)**
- `hamo` — React hooks for raf / scroll / visibility / media. By darkroom.engineering. **niche-gem**
- **Satūs** / **Novus** — darkroom.engineering's public Next.js starters with Lenis + Tempus + Hamo pre-wired. Reference repos, not npm packages. **(boilerplate)**
- `@ashthornton/asscroll` — Pre-Lenis smooth scroll on countless Awwwards entries. **niche-gem**
- `virtual-scroll` (ayamflow) — Unified wheel/touch input. **niche-gem**
- `lethargy` — Detects "intentional" wheel events vs inertial scroll. **niche-gem**
- `smooth-scrollbar` — Custom scrollbar with plugins. **niche-gem**
- `react-scroll-parallax` — Easy parallax in React. **popular**

---

## 3. Scroll-Triggered Reveal

- `splitting` — Wraps chars/words/lines in spans + CSS vars (`--char-index`). Studio standard for staggers. **essential (niche)**
- `split-type` — Modern lighter free replacement for GSAP SplitText. **niche-gem**
- GSAP `SplitText` plugin — Best-in-class line splitting with proper measurement. Free since 3.13. **essential**
- `scroll-out` — Tiny IO-based reveal lib that adds CSS custom props for `--scroll-percent`. **niche-gem**
- `aos` — Beginner-friendly data-attribute reveal. **popular**
- `react-intersection-observer` — IO hook. **essential**
- `@vueuse/core` / `@reactuses/core` `useIntersectionObserver` — **popular**
- `waypoints` — Legacy, still in Webflow exports. **niche-gem**

---

## 4. Page Transitions

- Astro View Transitions API — Built into Astro 3+. **essential**
- `next-view-transitions` (Shu Ding) — View Transitions for Next App Router. **popular**
- `@barba/core` — Classic SPA-style transitions for MPAs. Powers many Floema-era sites. **essential (niche)**
- `@dogstudio/highway` — Lighter Barba alternative. **niche-gem**
- `@unseenco/taxi` — Modern Barba successor. **niche-gem**
- `swup` — Plugin-based page-transition lib with cache, scroll, fragments. **popular**
- Framer Motion `<AnimatePresence>` — Route transitions in React. **essential**

---

## 5. 3D / WebGL

### Essential
- `three` — The 3D web. **essential**
- `@react-three/fiber` (R3F) — React reconciler for Three. **essential**
- `@react-three/drei` — Helper kitchen sink (Environment, useGLTF, Float, MeshTransmissionMaterial, ScrollControls, etc.). **essential**
- `@react-three/drei-vanilla` — Same helpers for vanilla Three. **niche-gem**

### Popular
- `ogl` (Nathan Gordon) — Minimal WebGL lib (~50kb). Studio favorite (Floema, ref.digital). Pick for shader-first work. **niche-gem (studio favorite)**
- `postprocessing` (Vanruesc) — Better-than-Three's-built-in effect composer. **essential**
- `@react-three/postprocessing` — R3F wrapper. **essential**
- `@react-three/rapier` — Rapier physics for R3F. **popular**
- `@react-three/xr` — VR/AR for R3F. **popular**
- `@react-three/cannon` — Cannon-es bindings. **popular**
- `@react-three/flex` — Yoga-flex layouts in 3D. **niche-gem**
- `@react-three/csg` — Boolean CSG ops. **niche-gem**
- `@react-three/gpu-pathtracer` — Real path tracing. **niche-gem**

### Niche gems
- `troika-three-text` — SDF text in Three. Only way to crisp 3D text. **essential (niche)**
- `lygia` — Shader function library (noise, sdf, color, generative). **niche-gem**
- `glslify` — `#pragma glslify:` shader imports via npm. **niche-gem**
- `regl` — Functional WebGL. **niche-gem**
- `playcanvas` — Alt 3D engine. **niche-gem**
- `@babylonjs/core` — Heavier alt to Three with better OOTB tooling. **popular**
- `three-stdlib` — Maintained fork of Three's `examples/jsm`. **popular**
- `three-mesh-bvh` — Fast raycasting / spatial queries. **niche-gem**
- `three-mesh-line` / `meshline` — Thick lines in WebGL (Three's default can't do thickness in WebGL2). **niche-gem**
- `@monogrid/gainmap-js` — JPEG gain-map HDR. **niche-gem**
- `maath` (Paul Henschel) — Math utils for R3F (easing, random, buffers). **niche-gem**
- `three-custom-shader-material` — Inject GLSL into any standard material. **niche-gem**
- `three-projected-material` — Project textures like a slide projector. **niche-gem**
- `three-mesh-ui` — Layout-engine UI panels in 3D. **niche-gem**

### Vue / Nuxt 3D (the European agency stack)
- `@tresjs/core` (**TresJS**) — Vue/Nuxt equivalent of `@react-three/fiber`. **essential (niche, for Nuxt)**
- `@tresjs/cientos` (**Cientos**) — Vue equivalent of `@react-three/drei`. **essential (niche, for Nuxt)**
- `@tresjs/post-processing` — Postprocessing for TresJS. **niche-gem**

### 3D asset tooling
- `@gltf-transform/cli` (**gltf-transform**) — Optimize glTF models. Cut file size 80%+ with `gltf-transform optimize input.glb output.glb`. Essential for any 3D site shipping models. **niche-gem (must-have CLI)**
- `gltfpack` (Meshoptimizer) — Alternative mesh optimizer. **niche-gem**
- Blender + the **Khronos glTF Validator** for asset prep. **(external tooling)**

---

## 6. Shaders / Creative GL

- `curtainsjs` — DOM `<img>`/`<video>` → WebGL planes with shaders. Classic for image distortion on hover. **niche-gem**
- `@paper-design/shaders` / `@paper-design/shaders-react` — Zero-dep canvas shaders as components. MeshGradient, DotOrbit, Warp, Halftone, Dithering. The new "Stripe-style hero gradient without writing GLSL." ~30 effects. **niche-gem (must-know 2025)**
- **Unicorn Studio** — No-code WebGL editor; designer authors, you embed a 29kb runtime. Escape hatch for design-led teams. **niche-gem**
- `vite-plugin-glsl` — `import frag from './x.glsl'` with HMR. Essential for any custom-shader workflow. **niche-gem**
- TSL (Three Shading Language) — Node-based shaders (r150+). In `three/webgpu`. **niche-gem**
- `shader-park-core` — Compose shaders in JS. **niche-gem**
- `glsl-canvas-js` — Quick GLSL playground in DOM. **niche-gem**
- `twgl.js` — "Tiny WebGL helpers" by gman. **niche-gem**
- `picogl` — Minimal WebGL 2. **niche-gem**
- `hover-effect` (Robin Delaporte) — OG image distortion-on-hover lib. **niche-gem**
- `spectorjs` — WebGL debugger; Chrome extension version is how you reverse-engineer shaders on sites you admire. **niche-gem**

---

## 7. 2D Canvas / Creative Coding

- `p5` — Processing for the web. **essential**
- `paper` — Vector graphics on canvas. **popular**
- `two.js` — Renderer-agnostic 2D scene graph (canvas/svg/webgl). **niche-gem**
- `konva` / `react-konva` — Interactive canvas scene graph. **popular**
- `roughjs` — Hand-drawn / sketchy graphics. **niche-gem**
- `pixi.js` — Hardware-accelerated 2D. **popular**
- `@pixi/react` — Pixi reconciler. **popular**
- `q5` — Modern p5 fork (faster, smaller). **niche-gem**
- `canvas-sketch` / `canvas-sketch-util` (Matt DesLauriers) — Plotter-style framework. **niche-gem**
- `@thi.ng/*` — Karsten Schmidt's vast functional creative-coding ecosystem (100+ packages). **niche-gem (deep cut)**

---

## 8. SVG / Vector / Lottie / Rive

- `lottie-web` / `lottie-react` — Bodymovin from AE. **essential**
- `@lottiefiles/dotlottie-web` — Modern Wasm-based player, ~70% smaller. **popular**
- `@rive-app/canvas` / `@rive-app/react-canvas` — Interactive vector w/ state machines. Used by Shopify Editions and ref.digital. **essential**
- `@svgdotjs/svg.js` — jQuery-for-SVG. **niche-gem**
- `vivus` — Animated SVG line drawing. **niche-gem**
- `svgo` — Optimizer. **essential**
- `svg-path-commander` — Parse/morph SVG paths. **niche-gem**
- `flubber` — Smooth path-to-path morphing. **niche-gem**

---

## 9. Cursor Effects

- `mouse-follower` (Cuberto) — The Cuberto cursor (magnetic, sticky, text). **niche-gem (Awwwards staple)**
- `kursor` (Cuberto) — Older simpler variant. **niche-gem**
- `react-animated-cursor` — Drop-in custom cursor. **popular**
- `blobity` — Sticky/blob cursor. **niche-gem**

---

## 10. Typography / Text Effects

- `splitting` / `split-type` — see §3
- GSAP `SplitText` — see §3
- `fitty` — Snug fit text to container. **niche-gem**
- `textillate` — Text animation built on animate.css. **niche-gem**
- `charming` — Pre-Splitting char wrapping. **niche-gem**
- `react-wrap-balancer` (Shu Ding) — Balanced title wrapping. **essential (niche)**
- `@capsizecss/core` / `@capsizecss/metrics` — Pixel-perfect typography metrics. **niche-gem**
- `fontaine` — Auto fallback font-face metric overrides. Kills CLS. **niche-gem**
- `@vfx-js/core` / `react-vfx` (amagi) — GLSL effects bound to text/img/video DOM. **niche-gem (Awwwards bait)**
- `react-text-transition` — Number/text crossfade. **niche-gem**

---

## 11. Image Effects & Distortion

- `curtainsjs` — see §6
- `hover-effect` — see §6
- `ramjet` (Rich Harris) — Morph any DOM element into any other. **niche-gem**
- `@pixi/filter-*` — Pixi filters. **niche-gem**
- `glfx` — Image filters via WebGL. **niche-gem**
- `react-compare-slider` — Before/after slider. **popular**
- `medium-zoom` — Tasteful image zoom. **popular**
- `photoswipe` — Lightbox. **popular**
- `blurhash` / `thumbhash` — Image placeholders. **essential (niche)**
- `plaiceholder` — LQIP/blur/CSS placeholders. **niche-gem**

---

## 12. Layout / Grids

- `muuri` — Draggable, filterable, animated grid. **niche-gem**
- `isotope-layout` — Filter/sort grids. **popular**
- `packery` — Bin-packing layout. **niche-gem**
- `masonry-layout` — Cascading grid. **popular**
- `gridstack` — Dashboard grids. **popular**
- `react-grid-layout` — Dashboard-style. **popular**
- `react-resizable-panels` (Brian Vaughn) — VS-Code-style panels. **essential (niche)**
- `react-rnd` — Resize + drag. **popular**

---

## 13. Physics

- `matter-js` — 2D rigid-body. **essential (niche)**
- `p2` — 2D alt. **niche-gem**
- `cannon-es` — Maintained Cannon fork. **popular**
- `@dimforge/rapier3d-compat` — Rust-Wasm physics, fastest. **popular**
- `planck` — Box2D port. **niche-gem**

---

## 14. Audio / Sound Design

- `howler` — Cross-browser audio. **essential**
- `tone` — Generative / musical audio. **popular**
- `pizzicato` — FX layer over WebAudio. **niche-gem**
- `wavesurfer.js` — Waveform UI. **popular**
- `meyda` — Audio feature extraction (FFT, MFCC). **niche-gem**
- `standardized-audio-context` — Polyfill/normalizer. **niche-gem**
- `soundfont-player` — General MIDI. **niche-gem**

---

## 15. Color

- `chroma-js` — Color manipulation/scales. **essential**
- `culori` — Modern, p3 / oklch-aware. **niche-gem**
- `color2k` — 2kb perf-focused. **niche-gem**
- `tinycolor2` — Classic. **popular**
- `@adobe/leonardo-contrast-colors` — Accessible palette generator. **niche-gem**
- `colorjs.io` — CSS Color 4 reference impl. **niche-gem**
- `react-colorful` — Tiny color picker. **popular**

---

## 16. Forms & Validation

- `react-hook-form` — **essential**
- `@conform-to/react` (Edmund Hung) — Progressive enhancement form lib. **niche-gem**
- `zod` — **essential**
- `valibot` — 10x smaller than Zod. **popular**
- `arktype` — **niche-gem**
- `@tanstack/react-form` — **popular**
- `sonner` — Toasts. **essential**

---

## 17. State Management

- `zustand` — **essential**
- `jotai` — Atomic state. **essential**
- `valtio` — Proxy state (great for R3F). **popular**
- `nanostores` — Tiny, framework-agnostic; Astro's official choice. **essential (niche)**
- `xstate` — State machines. **popular**
- `@legendapp/state` — Performance-focused observable state. **niche-gem**

---

## 18. Data Fetching

- `@tanstack/react-query` — **essential**
- `swr` — **essential**
- `ofetch` (unjs) — Universal fetch w/ smart parse. **popular**
- `ky` — Tiny fetch wrapper. **popular**
- `undici` — Node Fetch impl (server). **niche-gem**
- `redaxios` — Tiny Axios-API on fetch. **niche-gem**

---

## 19. CMS / Content

- `@sanity/client` / `next-sanity` — Used by Hashgraph VC, Floema. The agency favorite for 2024+. **essential**
- **DatoCMS** (`@datocms/cda-client`) — Better media handling than most. Used by REF Digital. **popular**
- `@prismicio/client` — Prismic. Easy slices model; the Floema/Bizzaro course teaches this. **popular**
- Hygraph (GraphCMS) — **popular**
- Storyblok — Visual editor + blocks. **popular**
- `payload` — Self-hosted, code-first. **popular (rising)**
- Directus — **popular**
- Contentful — **popular**
- `outstatic` — Git-based, lives in your Next repo. **niche-gem**
- `@keystatic/core` (Thinkmill) — Local + GitHub markdown CMS. **niche-gem**
- `tinacms` — Visual editing layer. **niche-gem**
- `velite` — Type-safe content layer. **niche-gem**
- `contentlayer2` — **niche-gem**

---

## 20. Image Optimization

- `sharp` — **essential**
- `@squoosh/lib` — Archived but still used. **niche-gem**
- `@unpic/react` / `@unpic/astro` (Matt Kane) — Universal `<Image>` for any CDN. **niche-gem**
- `ipx` (unjs) — Image proxy server. **niche-gem**
- `next/image` — built-in. **essential**
- `astro:assets` — built-in. **essential**
- `vite-imagetools` — Build-time transforms via `?w=400&format=webp`. **niche-gem**
- `plaiceholder` — LQIP. **niche-gem**

---

## 21. UI Component Primitives

- shadcn/ui — Copy-paste on Radix. **essential**
- `@radix-ui/react-*` — **essential**
- `@ark-ui/react` — Framework-agnostic state machines. **popular**
- `@ariakit/react` — **popular**
- `react-aria-components` (Adobe) — **essential**
- `vaul` (Emil Kowalski) — iOS-quality drawer. **essential (niche)**
- `sonner` (Emil Kowalski) — Toasts. **essential (niche)**
- `cmdk` (pacocoursey) — Command menu. **essential (niche)**
- `react-hotkeys-hook` — **popular**
- `react-wrap-balancer` — see §10
- `input-otp` (Guilherme Rodz) — OTP input. **niche-gem**

---

## 22. Tailwind Ecosystem

- `tailwind-variants` — **essential**
- `class-variance-authority` (cva) — **essential**
- `clsx` — **essential**
- `tailwind-merge` — **essential**
- `twind` — TW-in-JS. **niche-gem**
- `@tailwindcss/typography`, `@tailwindcss/forms`, `@tailwindcss/container-queries` — **essential**
- `tailwindcss-animate` — Radix-friendly animations. **popular**
- `@vanilla-extract/css` — TS CSS-in-JS, build-time. **niche-gem**
- `@pandacss/dev` (Chakra team) — Build-time CSS-in-JS. **niche-gem**
- `unocss` — Atomic engine. **popular**

---

## 23. Fonts

- `@fontsource/*` / `@fontsource-variable/*` — npm-installable Google fonts (self-host). **essential**
- `next/font` — built-in subsetting. **essential**
- `unifont` (unjs) — Universal font fetcher. **niche-gem**
- `fontaine` — Metric overrides for fallbacks. **niche-gem**
- `@capsizecss/core` — see §10
- `fontkit` — Font parsing. **niche-gem**

---

## 24. Meta-Frameworks

- Next.js — **essential**
- Astro — **essential** (studio darling now)
- Remix / React Router v7 — **essential**
- SvelteKit — **popular**
- Nuxt 3 — **popular** (used by Hashgraph VC, ref.digital, Obsidian Assembly, Floema)
- `@tanstack/start` — **popular (rising)**
- Qwik / Qwik City — Resumability. **niche-gem**
- SolidStart — **niche-gem**
- Fresh (Deno) — **niche-gem**
- `@11ty/eleventy` — Static, JS-light. **popular**
- Shopify Hydrogen on Remix — Used by Shopify Editions. **popular (commerce)**

---

## 25. Bundlers / Dev Tools

- Vite — **essential**
- Bun — Runtime + bundler. **popular**
- Turbopack / Turborepo — **popular**
- `million` — Virtual DOM accelerator for React. **niche-gem**
- Million Lint — Perf linter. **niche-gem**
- `@rsbuild/core` — Webpack-compat in Rust. **niche-gem**
- `@farmfe/core` — Rust bundler. **niche-gem**
- `tsup` — TS lib bundler. **popular**
- `unbuild` (unjs) — **niche-gem**

---

## 26. Routing

- `@tanstack/react-router` — Type-safe React routing. **popular**
- `wouter` — 1.5kb router. **niche-gem**
- `next/navigation`, `astro:routing` — built-in.
- `vike` (was vite-plugin-ssr) — **niche-gem**

---

## 27. i18n

- `next-intl` — **essential**
- `@inlang/paraglide-js` — Tree-shakable messages. **niche-gem**
- `@lingui/core` / `@lingui/react` — **popular**
- `i18next` / `react-i18next` — **essential**
- `rosetta` (Luke Edwards) — Tiny. **niche-gem**
- `@formatjs/intl` — ICU. **popular**

---

## 28. Accessibility

- `axe-core` / `@axe-core/react` — **essential**
- `react-aria` — see §21
- `a11y-dialog` — Accessible dialog. **niche-gem**
- `focus-trap-react` — **essential**
- `react-focus-lock` — alt. **popular**

---

## 29. Carousels / Sliders

- `embla-carousel-react` — Studio favorite, low-level, plugin-rich. **essential (niche)**
- `keen-slider` — **popular**
- `@splidejs/splide` — **popular**
- `swiper` — Used by Simon Holm. **essential**
- `flickity` — Classic. **popular**

---

## 30. Video / Media

- `lite-youtube-embed` (Paul Irish) — **essential (niche)**
- `lite-vimeo-embed` — **niche-gem**
- `plyr` — Accessible HTML5 player. **popular**
- `@vidstack/react` — Modern, headless. **niche-gem (rising)**
- `@mux/mux-player-react` — **popular**
- `mediabunny` — Browser-native video processing. **niche-gem**
- HLS.js / dash.js — Adaptive streaming. **popular**
- `video.js` — **popular**
- shaka-player — Google's streaming player. **niche-gem**

---

## 31. Debug GUI / Dev Tooling

- `tweakpane` — Studio favorite. **niche-gem (must-know)**
- `leva` (Poimandres) — React GUI for R3F. **essential (niche)**
- `dat.gui` — Original. **popular**
- `lil-gui` — Modern fork. **niche-gem**
- `stats-gl` — FPS monitor. **niche-gem**
- `r3f-perf` — Perf HUD for R3F. **niche-gem**
- `spectorjs` — WebGL debugger. **niche-gem**

---

## 32. Performance / Perf-utility

- `web-vitals` — Real-user CWV. **essential**
- `@builder.io/partytown` — Third-party scripts off-main-thread. **niche-gem**
- `comlink` — Worker RPC. **niche-gem**
- `@vercel/speed-insights`, `@vercel/analytics` — **popular**
- `@welldone-software/why-did-you-render` — Re-render audit. **niche-gem**
- `size-limit` — **niche-gem**

---

## 33. Networking / Server

- `hono` — Edge framework. **essential (rising)**
- `@hattip/core` — Universal HTTP. **niche-gem**
- `@trpc/server` — **popular**
- `@better-fetch/fetch` — Type-safe fetch wrapper. **niche-gem**

---

## 34. Auth

- `next-auth` / `@auth/core` — **essential**
- `@clerk/nextjs` — **popular**
- `lucia` — Sunsetting but still in repos. **niche-gem**
- `better-auth` — Successor in spirit. **niche-gem (rising)**
- `@supabase/supabase-js` — **popular**

---

## 35. Misc Studio Gems

- `mitt` (Jason Miller) — Tiny event emitter. In every studio toolkit. **niche-gem**
- `nanoid` — **essential**
- `ulid` — **niche-gem**
- `uuid` — **essential**
- `es-toolkit` — Modern lighter lodash replacement. **popular (rising)**
- `dayjs`, `date-fns` — **essential**
- `@js-temporal/polyfill` — **niche-gem**
- `react-tweet` (Vercel) — Statically render embedded tweets. **niche-gem**
- `shiki`, `rehype-pretty-code` — Syntax highlighting. **essential**
- `expressive-code` — Astro-favored code blocks. **niche-gem**
- MDX / `@mdx-js/react` / `next-mdx-remote` — **essential**
- `remark-gfm`, `rehype-slug`, `rehype-autolink-headings` — **essential**
- `react-error-boundary` — **essential**
- `detect-gpu` (Tim van Scherpenzeel) — Throttle 3D quality by device. **niche-gem (R3F sites)**
- `ua-parser-js` — Device sniff. **popular**
- `mathjs` — **niche-gem**
- `simplex-noise` — Every R3F site uses it. **niche-gem**
- `alea` — Seeded PRNG. **niche-gem**
- `gl-matrix` — Math for GL. **niche-gem**
- `eases` (Mattdesl) — Easing functions. **niche-gem**
- `bezier-easing` — Cubic-bezier solver. **niche-gem**
- `normalize-wheel` — Cross-browser wheel deltas. Essential for custom scroll. **niche-gem**
- `react-use-measure` (Paul Henschel) — R3F staple. **niche-gem**
- `react-merge-refs` — **niche-gem**
- `scroll-into-view-if-needed` — **niche-gem**
- `react-helmet-async` — Head mgmt. **popular**
- `next-seo`, `astro-seo` — **popular**
- `schema-dts` — Typed JSON-LD. **niche-gem**

---

## 36. unjs Ecosystem (studio under-the-radar essentials)

unjs is a galaxy of small, universal utilities. Almost every modern studio repo pulls several:

- `ofetch` — Smart-parse fetch
- `destr` — Safe JSON parse
- `defu` — Deep merge defaults
- `hookable` — Lifecycle hooks
- `consola` — Pretty logging
- `citty` — CLI framework
- `unstorage` — Any KV
- `unbuild` — Library builder
- `unimport` — Auto-imports
- `unenv` — Environment polyfills
- `scule` — String case conversion
- `pathe` — Cross-OS paths
- `mlly`, `jiti` — Module loaders
- `h3` — Nitro HTTP
- `listhen` — Server

All **niche-gem**. Worth knowing because Nuxt / Nitro / Vinxi / TanStack Start are built on these.

---

## 37. AI Visual / Generative SDKs

- `ai` (Vercel AI SDK) — **essential**
- `openai`, `replicate` — **popular**
- AI Elements / Vercel chatbot kits — **popular**
- `kokomi.js` — Three helpers (mesh effects, post). **niche-gem**

---

## Average-AI-won't-suggest hit list

Memorize these — they're what separates an Awwwards site from a Bootstrap site:

`ogl` · `lygia` · `troika-three-text` · `tweakpane` · `leva` · `mouse-follower` · `curtainsjs` · `hover-effect` · `splitting` · `split-type` · `lenis` · `@darkroom.engineering/tempus` · `hamo` · `@ashthornton/asscroll` · `@barba/core` · `@unseenco/taxi` · `swup` · `maath` · `detect-gpu` · `react-use-measure` · `normalize-wheel` · `virtual-scroll` · `lethargy` · `vaul` · `sonner` · `cmdk` · `input-otp` · `react-wrap-balancer` · `@capsizecss/core` · `fontaine` · `expressive-code` · `@keystatic/core` · `velite` · `outstatic` · `mitt` · `defu` · `ofetch` · `destr` · `scule` · `simplex-noise` · `alea` · `eases` · `bezier-easing` · `gl-matrix` · `@theatre/core` · `@motion-canvas/core` · `hydra-synth` · `million` · `@builder.io/partytown` · `comlink` · `react-resizable-panels` · `react-rnd` · `@lottiefiles/dotlottie-web` · `@rive-app/react-canvas` · `@vfx-js/core` · `react-vfx` · `lite-youtube-embed` · `@vidstack/react` · `mediabunny` · `schema-dts` · `plaiceholder` · `thumbhash` · `blurhash` · `pagefind` · `@paper-design/shaders-react` · **Unicorn Studio** · `vite-plugin-glsl` · `@tresjs/core` · `@tresjs/cientos` · `@gltf-transform/cli` · `three-mesh-line` · `spectorjs`

## Boilerplates worth cloning

- **Satūs** (darkroom.engineering) — Next.js + Lenis + Tempus + Hamo wired up. The canonical agency starter.
- **Novus** (darkroom.engineering) — newer iteration of Satūs.
- **R3F starter** (Poimandres) — `pmndrs/react-three-next` for Next + R3F.
- **Vite + R3F minimal** — `pmndrs/r3f-vite-starter`.
- **Nuxt + TresJS starter** — TresJS team maintains one.
- **Astro Starlight** — for docs archetype.
