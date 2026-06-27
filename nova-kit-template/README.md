<div align="center">

<!--
  ─────────────────────────────────────────────────────────────
  NOVA KIT — animated SVG banner
  Hand-coded with SMIL + CSS keyframes. No GIF, no PNG.
  Falls back to a static composition if animations are blocked.
  ─────────────────────────────────────────────────────────────
-->

<a href="https://your-demo-url.com">
<picture>
<img alt="NOVA KIT — a neobrutalist link-in-bio & creator drop template" width="880" src="./public/banner.svg" />
</picture>
</a>

# **NOVA KIT**

**A neobrutalist link-in-bio & creator drop template**

`mobile-first` · `zero-config rebrand` · `in-browser admin`

[![Template](https://img.shields.io/badge/template-v1.0-c6ff3a?style=flat-square&labelColor=0a0a0a)](#)
[![React 19](https://img.shields.io/badge/react-19-fafafa?style=flat-square&labelColor=0a0a0a)](https://react.dev)
[![TanStack Start](https://img.shields.io/badge/tanstack-start_v1-c6ff3a?style=flat-square&labelColor=0a0a0a)](https://tanstack.com/start)
[![Tailwind v4](https://img.shields.io/badge/tailwind-v4-fafafa?style=flat-square&labelColor=0a0a0a)](https://tailwindcss.com)
[![Mobile First](https://img.shields.io/badge/mobile-first-c6ff3a?style=flat-square&labelColor=0a0a0a)](#)
[![License](https://img.shields.io/badge/license-commercial-fafafa?style=flat-square&labelColor=0a0a0a)](#-license)

──────────────────────────────────────────

### ▌ LIVE DEMO

**▸ [ View live demo ](https://your-demo-url.com)** &nbsp;·&nbsp; **▸ [ Admin panel ](https://your-demo-url.com/admin)**

<sub>Replace the URLs above with your deployment, e.g. <code>https://nova-kit.vercel.app</code></sub>

──────────────────────────────────────────

</div>

## ▌ WHAT IS THIS

A fast, opinionated front-end template for creators, indie makers, and solo
brands who want a **link-sharing + content monetization page** that doesn't
look like every other Linktree clone.

Built around a **single config file** and a **live admin UI**, so a
non-developer can rebrand it end-to-end without touching React.

──────────────────────────────────────────

## ▌ FEATURES

```
[ ✓ ]  Mobile-first neobrutalist layout
[ ✓ ]  Marquee ticker, profile card, stat row, featured drop
[ ✓ ]  Category filter chips + live search
[ ✓ ]  Individual link detail pages with prominent CTA
[ ✓ ]  Skeleton loading + crossfade transitions
[ ✓ ]  /admin in-browser editor (Save / Reset / Import / Export JSON)
[ ✓ ]  Light + dark theme tokens (any CSS color)
[ ✓ ]  Per-route SEO, OG & Twitter meta
[ ✓ ]  404 + not-found boundaries on every route
[ ✓ ]  Type-safe routes via TanStack Router
```

──────────────────────────────────────────

## ▌ DESIGN SYSTEM

Carried straight from the storefront — the README, the banner, and the badges
all use the same tokens as the live site.

| Token            | Hex       | Role                       |
| ---------------- | --------- | -------------------------- |
| `--background`   | `#0a0a0a` | Pitch-black surface        |
| `--foreground`   | `#fafafa` | Primary ink                |
| `--lime`         | `#c6ff3a` | CTA / highlight            |
| `--accent`       | `#f1ecd8` | Warm accent surface        |
| `--muted-fg`     | `#a3a3a3` | Secondary text             |

**Type:** `Space Grotesk` (display, -0.02em tracking) + `JetBrains Mono` (data/labels).
**Motif:** hard 4px shadow, 2px borders, scoreboard-style pills, terminal dividers.

──────────────────────────────────────────

## ▌ STACK

| Layer        | Tech                                    |
| ------------ | --------------------------------------- |
| Framework    | **TanStack Start v1** (React 19, SSR)   |
| Build        | **Vite 7**                              |
| Styling      | **Tailwind CSS v4** (CSS-first tokens)  |
| Router       | **TanStack Router** (file-based)        |
| Typography   | **Space Grotesk** + **JetBrains Mono**  |
| Icons        | **lucide-react**                        |

──────────────────────────────────────────

## ▌ QUICK START

```bash
# 1. install
bun install

# 2. dev (http://localhost:8080)
bun dev

# 3. production build
bun run build
```

──────────────────────────────────────────

## ▌ ROUTES

```
/                    →  Home — marquee, profile, featured, link list
/links/$linkId       →  Link detail page with "Open Link" CTA
/admin               →  Live editor (localStorage + Import/Export JSON)
*                    →  404
```

──────────────────────────────────────────

## ▌ REBRAND IN 60 SECONDS

Two equally valid paths — pick the one that fits the buyer.

### ░ Option A — edit one file

Open `src/site.config.ts` and change:

```ts
brand: {
  name:         "YOUR BRAND",
  handle:       "@you",
  tagline:      "What you do, in one line.",
  avatarLetter: "Y",
  avatarUrl:    "",                 // optional image URL
  stats: { followers: "10K", links: "12", clicks: "120K" },
  footer:       "© 2026 Your Brand",
},
seo:        { title: "...", description: "...", ogImage: "..." },
theme:      { light: { ... }, dark: { ... } },   // any CSS color
marquee:    ["NEW DROP →", "FREE SHIPPING →"],
categories: ["All", "Tools", "Drops", "Press"],
links:      [ { id, title, description, url, category, cta, badge?, price? } ],
```

Save. The site reflects the change instantly.

### ░ Option B — visit `/admin`

A full in-browser editor with color pickers, live preview, and:

```
[ SAVE ]   →  persists to localStorage
[ RESET ]  →  back to defaults
[ EXPORT ] →  download site.config.json
[ IMPORT ] →  upload site.config.json
```

Hand `/admin` to a non-technical client. They never see code.

──────────────────────────────────────────

## ▌ BROWSING & FILTERING

The home grid is driven by two pieces of state — a category chip and a
free-text search. Both feed a single derived list that the grid renders
with a 180ms crossfade so item swaps never jump.

```
[ All ] [ Featured ] [ Resources ] [ Shop ] [ Social ]
                ↓
   ┌────────────────────────────┐
   │  search ─ "icon"           │
   └────────────────────────────┘
                ↓
        derived  →  crossfade  →  grid
```

──────────────────────────────────────────

## ▌ LINK FLOW

```
Home grid
   │  tap card
   ▼
/links/$linkId      ← skeleton → fade-slide-in
   │  "Open Link"
   ▼
Outbound URL  (target="_blank", rel="noopener")
```

──────────────────────────────────────────

## ▌ RESPONSIVE BREAKPOINTS

| Range              | Layout                                  |
| ------------------ | --------------------------------------- |
| `< 480px`          | Single column, full-width CTAs          |
| `480 – 768px`      | Single column, looser padding           |
| `768 – 1024px`     | 2-up link grid                          |
| `> 1024px`         | 2-up grid, centered 720px column        |

Tested portrait + landscape; tap targets ≥ 44px throughout.

──────────────────────────────────────────

## ▌ PROJECT STRUCTURE

```
src/
├─ routes/
│   ├─ __root.tsx           ←  shell, SEO defaults, providers
│   ├─ index.tsx            ←  home page
│   ├─ links.$linkId.tsx    ←  link detail
│   └─ admin.tsx            ←  in-browser editor
├─ components/
│   ├─ LinkCard.tsx
│   ├─ Skeletons.tsx
│   └─ ThemeStyle.tsx       ←  SSR theme token injector
├─ hooks/
│   └─ useSiteConfig.tsx    ←  live config provider
├─ lib/
│   └─ site-config-store.ts ←  localStorage overrides + merge
├─ site.config.ts           ←  ★ EDIT ME
└─ styles.css               ←  Tailwind v4 tokens, animations
```

──────────────────────────────────────────

## ▌ DESIGN TOKENS

Defined in `src/styles.css`, overridable from `site.config.ts`:

```
--background        --foreground        --card
--accent            --lime              --lime-foreground
--muted-foreground
```

Utilities: `.shadow-brutal`, `.shadow-brutal-lg`, `.press`, `.grain`,
`.fade-slide-in`, `.stagger`, `.crossfade`.

──────────────────────────────────────────

## ▌ DEPLOY

Works on any host that runs a TanStack Start build.
Recommended: **Cloudflare Pages / Workers**, **Vercel**, **Netlify**.

```bash
bun run build
# output: .output/  →  deploy as a Node/Edge app
```

──────────────────────────────────────────

## ▌ KNOWN LIMITATIONS

Being honest matters more than overselling — here's what this template
does **not** ship with:

```
[ ! ]  No built-in checkout. Price tags link out; bring your own Stripe/Gumroad.
[ ! ]  No CMS. Content lives in site.config.ts (or /admin → localStorage).
[ ! ]  /admin overrides are per-browser. Export JSON to share with teammates.
[ ! ]  No analytics out of the box. Drop in Plausible/Umami/GA yourself.
[ ! ]  No i18n layer. Strings are config-driven but single-locale.
[ ! ]  No auth on /admin. Add a route guard before shipping a live editor publicly.
```

──────────────────────────────────────────

## ▌ LICENSE

Sold as a commercial template. One license per end product.
See `LICENSE` for full terms.

<div align="center">

──────────────────────────────────────────

**Made for creators who ship.**

`v1.0` · `2026`

</div>

