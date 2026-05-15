# Agency Wiring — The Canonical Pattern

How studios that win Awwwards actually assemble their stack. This isn't a recipe — it's a *pattern* that recurs across Bürocratik, darkroom.engineering, Obys, ToyFight, REF, Active Theory, Hello Monday, Resn, Immersive Garden.

---

## The canonical wiring (memorize this)

```
┌────────────────────────────────────────────────────────────────┐
│  Next.js (App Router)  OR  Nuxt 3                              │
│  + Tailwind + CSS vars for design tokens                       │
│                                                                │
│  ┌──────────────────────────────────────────────────────────┐  │
│  │  Persistent layout (never unmounts)                      │  │
│  │                                                          │  │
│  │  ┌────────────────────────────────────┐                  │  │
│  │  │  Single WebGL canvas              │  ← survives       │  │
│  │  │  (R3F or vanilla three / ogl)     │    page changes   │  │
│  │  └────────────────────────────────────┘                  │  │
│  │                                                          │  │
│  │  <PageContent />  ← swaps on route change                │  │
│  └──────────────────────────────────────────────────────────┘  │
│                                                                │
│  Page transitions: View Transitions API | Barba.js (vanilla)   │
│  Smooth scroll: lenis                                          │
│  Single RAF: @darkroom.engineering/tempus                      │
│  Animation: gsap (timelines) + motion (component state)        │
│  Content: Sanity | DatoCMS | Prismic + Zod schemas at boundary │
│  State: zustand (+ valtio for live tweaking)                   │
│  Debug: leva (gated by NODE_ENV)                               │
└────────────────────────────────────────────────────────────────┘
```

This is what's actually under the hood of the sites we're studying.

---

## The persistent-canvas trick (the big one)

The signature move of high-craft agency sites is **one WebGL canvas that survives across page transitions.** As you navigate Home → Work → About, the canvas keeps rendering — the image plane crossfades to a new texture, the shader keeps running, the camera pans. The DOM beneath swaps; the canvas does not.

**Why this matters:** it creates the "gallery experience" feel — like you're moving through one continuous world, not loading discrete pages. Floema, Locomotive's portfolio, ref.digital, Obsidian Assembly all do this.

**How to wire it (Next App Router):**
1. Put the canvas in the root layout (`app/layout.tsx`), not in any page.
2. Each page declares "what should be in the canvas right now" via a global store (`zustand` or `valtio`).
3. Page-change handlers tween the canvas state instead of unmounting/remounting.
4. Page transitions are content-only: the `<main>` fades out, new `<main>` fades in, canvas keeps going.

**How to wire it (vanilla / Nuxt + Barba):**
1. Mark the canvas container with `data-barba="wrapper"` parent + the page content with `data-barba="container"`.
2. Barba's hooks (`leave` / `enter`) animate the page content; the canvas lives outside the swap.
3. Barba's view-controllers per route tell the canvas which texture / scene to lerp toward.

**Common mistake:** spinning up a new R3F `<Canvas>` per page. You'll lose context, lose loaded textures, and the transition feels like a hard cut. One canvas, always.

---

## The single-RAF rule

When Lenis (scroll), GSAP (animation), and R3F (3D) each run their own `requestAnimationFrame` loop, you get **triple-tick jitter** — three competing ticks per frame, missed sync, layout thrash. Route them through one ticker.

```js
import { Tempus } from '@darkroom.engineering/tempus';
import gsap from 'gsap';
import Lenis from 'lenis';

const lenis = new Lenis();
gsap.ticker.lagSmoothing(0);
gsap.ticker.remove(gsap.updateRoot);

Tempus.add((time) => {
  lenis.raf(time);
  gsap.updateRoot(time / 1000);
}, 0);
```

For R3F, set `<Canvas frameloop="demand">` and call `invalidate()` from a Tempus subscription, OR use the default frameloop and live with one extra RAF — most sites do the latter and survive.

---

## Studios & creators worth studying

These are the people whose work powers half the Awwwards SOTD shelf. Read their public code, watch their conference talks, copy their patterns:

### Studios
- **darkroom.engineering** (was Studio Freight) — open-source `lenis`, `tempus`, `hamo`. Templates: `satus` (Next + their wiring), `novus` (newer iteration), `aniso` (ASCII art). Clients: Resend, Mux, Vercel marketing pages.
- **Bürocratik** (Portugal) — Built Floema, dozens of Awwwards SOTDs. Nuxt-heavy. Studio site itself is a benchmark.
- **Fiddle.Digital** (Russia/Belarus) — Built Obsidian Assembly. Nuxt + bespoke scroll/cursor patterns.
- **Obys Agency** (Ukraine) — Wildly typographic, Nuxt-based, heavy GSAP work.
- **ToyFight** (UK) — Playful, illustrative agency sites.
- **Locomotive** (Montreal) — Made `locomotive-scroll`, originated the modern "smooth scroll site" archetype.
- **Cuberto** — `mouse-follower`, distinctive magnetic-cursor look.
- **Active Theory** (LA) — Big-brand interactive (Nike, Beyoncé). Three.js + custom shaders.
- **Resn** (NZ) — Genre-experimental, often game-engine-grade WebGL.
- **Immersive Garden** (Paris) — Editorial / luxury / fashion-forward 3D sites.
- **Hello Monday** (NY/Aarhus) — Long-running, polished, lots of microsites.
- **Unseen Studio** — Modern brutalist / editorial.
- **lg2** (Montreal) — Built REF Digital.
- **Burocratik** (yes, two spellings exist) — Floema, lots of Sanity-driven Nuxt sites.

### People
- **Damien Mortini** — Creative technologist, hand-rolls minimal WebGL. Behind Shopify Editions Winter '26 visuals. Worth reading his GitHub.
- **Luis Henrique Bizarro** — "Endless School of Motion" course author; teaches the Express + Prismic + OGL + GSAP + Barba pattern. Where most agency devs learn this style.
- **Bruno Simon** — Three.js Journey course; his portfolio (a drivable car in 3D) is canonical.
- **Yuri Artyukh (akella)** — YouTube shader tutorials, lots of small experiments.
- **Paul Henschel** (drcmda) — Maintains R3F, drei, `maath`, `react-use-measure`, `react-spring`.
- **Poimandres** collective — `leva`, `zustand`, `valtio`, `jotai`, drei. Pretty much the modern React-3D scene.
- **Robin Delaporte** — `hover-effect` original.
- **Matt DesLauriers (mattdesl)** — `canvas-sketch`, generative art ecosystem.
- **Cassie Evans** — GSAP staff, accessible animation evangelist.

---

## Reverse-engineering the sites you admire (Spector.js)

Spector.js is a Chrome extension that captures every WebGL draw call on any page. When you see a hero effect and want to know how it's done:

1. Install Spector.js (extension).
2. Open the target site, click the Spector icon, capture a frame.
3. Inspect the program list — you'll see the actual vertex + fragment shaders the site is running.
4. Read the uniforms, attribute layout, render targets.

For non-WebGL detective work:
- **View source** — look for `_nuxt/`, `__NEXT_DATA__`, `astro-`, `data-wf-page` (Webflow), `cdn.shopify.com/oxygen-v2` (Hydrogen).
- **Look at script chunks** — search for `GSAP`, `ScrollTrigger`, `Lenis`, `barba`, `OGL`, `THREE`, `WebGLRenderer`.
- **Network tab** — image URLs reveal the CMS: `cdn.sanity.io`, `images.prismic.io`, `a.storyblok.com`, `cdn.datocms.com`.
- **Awwwards page** — every featured site lists tech stack + studio credits. The first place to look.
- **`window.__NUXT__.config`** — sometimes exposed; reveals CMS access tokens (read-only), build paths, hosting infra.

---

## The Damien Mortini / hand-rolled WebGL school

Shopify Editions Winter '26 is the current high-water mark. The visuals aren't built with R3F + drei conventions — they're hand-rolled around minimal WebGL primitives, generative compositions, painterly procedural textures. The site marries that with Rive for stateful vector animation and the Shopify Hydrogen/Remix/Oxygen backbone.

The pattern when you go this deep:
- Skip R3F. Use `ogl` or raw WebGL.
- Author models in Blender, export glTF, optimize with `gltf-transform` CLI (often 80%+ smaller).
- Compose shaders with `vite-plugin-glsl` for clean `.glsl` imports.
- Use `lygia` for noise / sdf / color math; don't reinvent.
- Tune uniforms live with `leva` or `tweakpane` in dev.
- Capture frame-perfect renders with `@theatre/core` or `motion-canvas`.

This is harder and slower than the R3F path, but it's where the "no other site looks like this" tier lives. Reach for it only when the brief demands it.

---

## Paper Shaders / Unicorn Studio — the new easy tier

Two recent tools that let you ship serious shader work without writing GLSL:

- **Paper Shaders** (`@paper-design/shaders`, `@paper-design/shaders-react`) — zero-dependency canvas shaders. Drop `<MeshGradient />`, `<DotOrbit />`, `<Warp />`, `<Halftone />`, `<Dithering />` as components. ~30 effects. Free, MIT. Pick for: SaaS hero gradients that look hand-crafted but aren't.
- **Unicorn Studio** — no-code WebGL editor. Designers author the effect in their UI, you embed a 29kb runtime. Pick for: design-led teams where the dev isn't writing shaders.

These have collapsed the cost of "Stripe-style mesh gradient hero" from 2 weeks of shader work to 30 minutes.

---

## The Nuxt-vs-Next split is geographic and cultural

Empirically: **US SaaS / Silicon Valley → Next**. **European craft agencies → Nuxt**. This isn't a tooling judgment, it's a community split.

- US ecosystem: Vercel, shadcn, Linear, Resend, Cal — all Next + Tailwind + Radix.
- European agencies: Bürocratik, Obys, REF, ToyFight, Fiddle — all Nuxt + Sanity/DatoCMS + GSAP + Lenis + Three/OGL.

For Vue/Nuxt 3D work, the equivalents are:
- **TresJS** (`@tresjs/core`) — Nuxt/Vue equivalent of R3F.
- **Cientos** (`@tresjs/cientos`) — Vue equivalent of drei.

If the brief reads "European agency aesthetic," consider Nuxt even if you usually reach for Next.

---

## The agency dev's daily debug stack

In `process.env.NODE_ENV === 'development'`:

- **`leva`** floating panel for every shader uniform, animation duration, camera position.
- **`r3f-perf`** HUD for FPS + draw calls + memory.
- **`stats-gl`** as a fallback for vanilla three.
- **Spector.js** Chrome extension for capturing GL draw calls.
- **`vite-plugin-glsl`** with HMR — edit shader, save, see result instantly.
- **`detect-gpu`** gating — toggle a `?lowend=1` URL flag to simulate a weak device locally.

Ship none of these to production except `detect-gpu`.
