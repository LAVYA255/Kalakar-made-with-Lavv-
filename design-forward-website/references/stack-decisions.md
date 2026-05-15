# Meta-Framework Decisions

When to pick which base. Most design-forward sites land on one of these four: **Astro**, **Next.js**, **Nuxt 3**, **Vite + React**. Honorable mention: Webflow.

---

## Astro

**Pick when:**
- The site is mostly content (blogs, docs, portfolios, VC firms, editorials, lookbooks).
- You want zero-JS-by-default with islands of interactivity.
- View Transitions API is core to the design.
- Build-time content from MDX / Sanity / Keystatic / Velite.
- LCP / INP must be ridiculous (sub-1s LCP is trivial in Astro).

**Skip when:**
- The site is a heavy interactive WebGL playground (Astro can host it but the islands model fights you).
- You need real-time data, auth-gated app surfaces, or rich client routing.

**Studio-forward stack:** Astro + `@fontsource-variable/*` + `@keystatic/core` (or Sanity) + `expressive-code` + `react-wrap-balancer` (in a React island) + native CSS scroll + View Transitions.

---

## Next.js (App Router)

**Pick when:**
- SaaS marketing site, conference site, editorial product launch, lookbook with commerce.
- You need ISR for dynamic content windows (early-bird → sold out → archive).
- You want OG image generation at the edge (`@vercel/og`).
- The client team wants Sanity / Builder.io for page composition.
- App surfaces (auth, dashboards) live in the same repo.

**Skip when:**
- The brief is a one-pager experiment — Vite-React or vanilla is faster to ship.
- The team is Vue.

**Studio-forward stack:** Next App Router + Tailwind + shadcn + `motion` + `gsap` + `lenis/react` + `next-view-transitions` + Sanity + Vercel OG.

---

## Nuxt 3

**Pick when:**
- The team is Vue.
- You want SSR with Nitro's edge-anywhere deployment story.
- You want the unjs ecosystem (`ofetch`, `unstorage`, `pathe`, `defu`) baked in.

Reference: **Hashgraph VC, ref.digital, Obsidian Assembly, Floema** are all Nuxt 3. Burocratik / Fiddle / lg2 ship Nuxt. The Vue creative-agency ecosystem is unusually strong.

**Studio-forward stack:** Nuxt 3 + Nuxt i18n + Sanity (or Storyblok) + `lenis` + `gsap` + `three`/`ogl` + `howler` + `@rive-app/canvas`.

---

## Vite + React (no meta-framework)

**Pick when:**
- It's a one-page experiment, campaign microsite, or net-art piece.
- The render loop is the product — Three.js + raw RAF + zero SSR overhead.
- SEO is secondary.
- You want absolute minimal toolchain.

**Skip when:**
- The site has more than ~5 routes.
- You need SSR or ISR.
- The client cares about SEO.

**Studio-forward stack:** Vite + React + Tailwind + `gsap` + `lenis` + `@react-three/fiber` + `leva` + `motion`.

---

## SvelteKit

**Pick when:**
- The team is Svelte-native or the brief mentions Svelte explicitly.
- You want cutting-edge feel without bundle bloat (Svelte 5 / runes era).

**Studio-forward stack:** SvelteKit + `lenis` + `gsap` + `three` directly + `@threlte/core` for Svelte R3F-equivalent.

---

## Shopify Hydrogen (on Remix)

**Pick when:**
- Commerce is the spine of the site.
- Shopify is the source of truth for products.

Reference: **Shopify Editions Winter 2026** runs on Hydrogen + Remix + Oxygen edge runtime.

**Studio-forward stack:** Hydrogen + Tailwind + `motion` + `@rive-app/react-canvas` (Shopify Editions uses Rive heavily) + Sanity for editorial content alongside Shopify products.

---

## Webflow (escape hatch)

**Pick when:**
- The designer is the dev. No engineering team.
- Time-to-launch matters more than code ownership.
- The brief is a portfolio or campaign site < 20 pages.

Reference: **Simon Holm Studio** runs on Webflow + GSAP from cdnjs + Lenis from unpkg + Barba.js + Lottie + Swiper. It's still Awwwards-grade.

**Studio-forward stack:** Webflow + GSAP CDN + Lenis CDN + Barba.js + Lottie + Swiper + custom JS in Webflow embeds. Add Finsweet Attributes for filtering / CMS power-ups.

---

## Eleventy (11ty)

**Pick when:**
- The site must ship < 50KB JS.
- It's a long-tail content site, personal blog, or text-driven brand site.

**Studio-forward stack:** 11ty + Nunjucks templates + `vite` for asset bundling + `gsap` + `lenis` for the one motion moment.

---

## Decision tree (when in doubt)

```
Is it commerce-anchored on Shopify?               → Hydrogen
Is it a one-page experiment / net-art?            → Vite + React (or vanilla)
Is it docs / blog / VC / editorial / lookbook?    → Astro
Is the team Vue?                                  → Nuxt 3
Is it SaaS marketing / conference / launch?       → Next.js App Router
Is the team Svelte?                               → SvelteKit
Is the designer the dev?                          → Webflow
Else                                              → Next.js (safe default)
```
