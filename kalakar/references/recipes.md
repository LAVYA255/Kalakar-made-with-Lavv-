# Combo Recipes

Eleven proven stacks behind award-winning work. Use as starting points; swap parts as the brief demands.

---

## 1. The Classic Awwwards Stack

The 80% recipe. If you don't know what to build, build this.

```
lenis  +  gsap + ScrollTrigger  +  split-type (or splitting)  +  mouse-follower
  +  @barba/core (MPA) | astro view transitions | next-view-transitions (SPA / RSC)
```

- Smooth scroll → scroll-driven timelines → per-character text reveals → magnetic cursor → seamless page transitions.
- 80% of Awwwards SOTDs from 2022–2025 ship some variant of this.
- Drop in `@fontsource-variable/*` + `react-wrap-balancer` for typography polish.
- Add `fontaine` if you have CLS from font swap.

---

## 2. The React Spatial Stack

For interactive 3D hero scenes (Vercel Conf, Linear product, Resend launch).

```
@react-three/fiber  +  @react-three/drei  +  @react-three/postprocessing
  +  leva  +  maath  +  react-use-measure  +  detect-gpu  +  @theatre/core
```

- `leva` for live-tweaking uniforms.
- `detect-gpu` to downgrade quality on mobile.
- `@theatre/core` to keyframe cinematics visually instead of writing tweens.
- Add `troika-three-text` if any text lives inside the scene.
- Add `simplex-noise` + `alea` for generative motion.

---

## 3. The darkroom.engineering Stack (was Studio Freight)

Across darkroom.engineering client work (Resend, Mux, Vercel pages, GTA VI Rockstar teaser).

```
Next.js  +  lenis  +  @darkroom.engineering/tempus  +  hamo
  +  gsap  +  next/font  +  Sanity  +  Vercel  +  Hygraph
  +  one persistent WebGL canvas at the layout level
```

- `@darkroom.engineering/tempus` centralizes RAF — prevents jank between Lenis, GSAP, and any R3F.
- `hamo` provides React hooks for visibility / raf / media without boilerplate.
- Clone **Satūs** (or **Novus**) for the canonical wiring as a starting point.
- The WebGL canvas lives in the root layout; page transitions swap content beneath it, canvas keeps rendering. See `agency-wiring.md`.

---

## 4. The Floema Stack (Luis Henrique Bizarro / Burocratik era)

The "Endless School of Motion" pattern — bespoke shaders on every image, gallery-style portfolio.

```
Express server (or Nuxt 3)  +  Prismic | Sanity  +  Pug | Vue SFC
  +  @barba/core  +  gsap  +  ogl (instead of three)
  +  custom shaders via glslify (+ lygia for shader fns)
  +  splitting  +  locomotive-scroll (now lenis)
  +  howler for per-scene ambient audio
```

- `ogl` is intentional — Floema-tier sites prefer it over `three` for shader-first hero meshes.
- Audio is preloaded per scene with `<link rel="prefetch" as="audio">`.

---

## 5. The Codrops Demo Stack

Drop-in demo pattern, no framework — for tutorials, single-screen experiments.

```
Vanilla JS  +  Vite  +  gsap  +  splitting  +  lenis
  +  curtainsjs | ogl  +  lygia shaders  +  hover-effect
```

---

## 6. The Editorial Astro Stack

Long-form type-driven sites (Vercel ship blog, Linear changelog, Tailwind docs energy).

```
Astro  +  View Transitions  +  Sanity | @keystatic/core
  +  @fontsource-variable/*  +  @capsizecss/core  +  fontaine
  +  react-wrap-balancer  +  expressive-code | shiki
  +  Pagefind (search)
```

- Skip Lenis. Editorial wants fast and clean, not smooth and laggy.
- View Transitions API handles all transitions.

---

## 7. The Generative Hero Stack

Cobalt blobs, glass distortions, soft-shadowed product hero.

```
@react-three/fiber  +  @react-three/drei (MeshTransmissionMaterial, Float, ScrollControls)
  +  @react-three/postprocessing (Bloom, ChromaticAberration, DepthOfField)
  +  simplex-noise  +  maath  +  leva
```

---

## 8. The Linear / Vercel Marketing Stack

For B2B SaaS that needs to look serious and ship motion.

```
Next.js (App Router)  +  Tailwind  +  motion (framer-motion)
  +  Radix + shadcn/ui  +  cmdk  +  sonner  +  vaul
  +  react-wrap-balancer  +  Sanity | Contentful  +  Vercel OG
  +  @react-three/fiber for hero only
```

---

## 9. The Custom Scroll-Driven Site

When you need bespoke scroll behavior (horizontal galleries, gesture-driven sections).

```
lenis  +  normalize-wheel  +  virtual-scroll  +  lethargy
  +  gsap ScrollTrigger  +  splitting
  +  IntersectionObserver  +  scroll-out (CSS vars)
```

---

## 10. The Image-Distortion Hero

The "image breathes / ripples on cursor" hero everyone's seen.

```
curtainsjs (DOM-anchored) | ogl plane mesh (scene-anchored)
  +  custom GLSL displacement shader (curl noise / RGB shift on mouse velocity)
  +  splitting for the headline overlay
  +  mouse-follower for magnetic cursor
```

---

## 11. The Cuberto Showcase Stack

The "Awwwards Site of the Day" specifically Cuberto-flavored.

```
mouse-follower  +  gsap  +  lenis | locomotive-scroll  +  @barba/core
  +  custom WebGL canvas backgrounds (ogl or three)
  +  bespoke loader animation
```

---

## 12. The Generative Art Portfolio

For canvas-sketch / Mattdesl / Bruno Simon-flavored work.

```
canvas-sketch  +  canvas-sketch-util  +  simplex-noise  +  chroma-js
  +  p5 | two.js  +  tone for sonification
```

---

## 13. The Paper Shaders / SaaS Hero Stack

The new easy tier — Stripe/Linear-grade gradient heroes without writing GLSL.

```
Next.js  +  @paper-design/shaders-react  +  motion (Framer)  +  Tailwind
  +  shadcn + Radix + cmdk + sonner  +  react-wrap-balancer
  +  Sanity | Contentful  +  Vercel OG
```

- Drop `<MeshGradient />` / `<DotOrbit />` / `<Warp />` as hero background.
- Pair with subtle `motion` component animations.
- 30 minutes from npm install to shipping hero.
- For non-shader teams: swap Paper Shaders for **Unicorn Studio** embed (29kb).

---

## 14. The European Nuxt Agency Stack

What Bürocratik, Obys, Fiddle.Digital, REF actually ship.

```
Nuxt 3 (+ Nitro)  +  @tresjs/core  +  @tresjs/cientos
  +  lenis  +  gsap  +  ogl (for shader-heavy hero)
  +  Sanity | DatoCMS  +  @nuxtjs/i18n
  +  @rive-app/canvas  +  howler (per-scene audio)
  +  @barba/core OR Nuxt page transitions
```

- The European craft equivalent to recipe #8 (Linear/Vercel marketing).
- Persistent canvas across page transitions is the signature.
- See `agency-wiring.md` for how to wire the persistent canvas in Nuxt.

---

## Mix & match logic

- **Always add** `prefers-reduced-motion` gating + `detect-gpu` if there's WebGL.
- **Audio gets a mute toggle** at all times — and starts muted unless the user has interacted.
- **Page transitions** default to View Transitions API. Use `@barba/core` only on MPAs without VT support, or when you specifically want the persistent-canvas trick.
- When Lenis + GSAP + R3F coexist, **always route RAF through `@darkroom.engineering/tempus`** to prevent triple-RAF jank.
- When you have variable fonts, **always pair with `fontaine`** to override fallback metrics (kills CLS).
- For text inside WebGL, **always use `troika-three-text`** — never `<Text>` in `<Html>`.
- For glTF models, **always run `gltf-transform optimize`** before shipping. 80%+ savings is normal.
- For dev tuning, **always wire `leva`** behind `NODE_ENV === 'development'`. Don't ship Leva to prod.
- For Vue/Nuxt 3D, use `@tresjs/core` + `@tresjs/cientos` (the R3F + drei equivalents).
