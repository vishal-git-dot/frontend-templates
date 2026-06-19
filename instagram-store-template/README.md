# 🛍️ Aroma & Co. Storefront Template

A fast, mobile-first storefront template built for sellers who run their shop the way they run an Instagram page — clean grid, tap a product, message to order. No backend, no build tools, no framework. One HTML file, ready to host anywhere.

---

## Why this template

- **Loads instantly.** Zero external requests — no font CDNs, no icon libraries, no images until you add your own. Everything is inline HTML, CSS, and JavaScript in a single file.
- **Mobile-first, not mobile-only.** Designed thumb-up: bottom nav, swipe-friendly category rail, slide-up sheets. Scales gracefully to tablet and desktop as a centered "app card."
- **Built to convert, not browse.** Every product is one tap away from a pre-filled WhatsApp message — no cart abandonment, no checkout forms, no account creation.
- **Editable by anyone.** All store info, products, and colors live in one clearly labeled section near the top of the file. Change values, save, done.

---

## Quick start

1. Open `instagram-store-template.html` in any text editor (Notepad, TextEdit, VS Code — anything works).
2. Find the `STORE SETTINGS` section near the top of the `<script>` tag.
3. Replace the placeholder name, bio, and WhatsApp number with your own.
4. Save the file, then double-click it to preview in your browser.
5. Upload it to any web host (see [Hosting it](#hosting-it) below) when you're happy with it.

That's the whole workflow. No `npm install`, no terminal, no deploy pipeline required.

---

## What's on the page

| Section | What it does |
|---|---|
| **Header** | Store name + bag icon with a live item-count badge |
| **Profile hero** | Avatar, store name, bio, and stats (product count, rating, ship time) — a storefront "bio card" |
| **Shop Now / Message Us** | Primary CTA scrolls to the grid; secondary CTA opens WhatsApp with a greeting message |
| **Category rail** | Circular filter chips, horizontally scrollable, like a stories bar |
| **Product grid** | Tight 2-column grid, price overlay on each tile, one-tap "+" quick-add |
| **Quick order sheet** | Tap any product → set quantity → "Order via WhatsApp" sends a pre-filled message, or "Add to bag" for a multi-item order |
| **Bag sheet** | Review everything added, remove items, then checkout as one combined WhatsApp message |
| **Bottom nav** | Home / Shop / Bag / Contact — fixed, thumb-reachable on every screen size |

---

## Customizing your store

Everything below lives inside the `<script>` tag, clearly separated from the rest of the code. You never need to touch the HTML or CSS structure to update your shop.

### 1. Store details

```js
const STORE = {
  name: "Aroma & Co.",
  avatarLetter: "A",
  bio: "Small-batch soy candles & home scents, hand-poured weekly.",
  rating: "4.9★",
  shipTime: "24h",
  whatsappNumber: "15551234567",   // country code + number, digits only, no + or spaces
  currency: "$",
  greeting: "Hi! I'd love to know more about your products 🌿"
};
```

> ⚠️ **Don't forget to replace `whatsappNumber`.** It must start with your country code and contain digits only — e.g. a US number `+1 (555) 123-4567` becomes `"15551234567"`.

### 2. Products

Each product is one object. Copy a block to add an item, delete one to remove it:

```js
{ id:9, name:"Lavender Fields", price:25, category:"candles", swatch:"💜", badge:"New" }
```

| Field | Required | Notes |
|---|---|---|
| `id` | ✅ | Must be unique — just count up from the last one |
| `name` | ✅ | Shown on the card and in the WhatsApp message |
| `price` | ✅ | A number, no currency symbol (that comes from `STORE.currency`) |
| `category` | ✅ | Must match one of the `key` values in `CATEGORIES` below |
| `swatch` | optional | An emoji used as a placeholder photo |
| `img` | optional | A real image URL — if present, this replaces the emoji |
| `badge` | optional | Small tag like `"New"` or `"Sale"` shown on the corner of the tile |

To use real product photos instead of emoji, just add an `img` field:

```js
{ id:1, name:"Driftwood & Sea Salt", price:24, category:"candles", img:"https://yoursite.com/photos/driftwood.jpg" }
```

### 3. Categories

```js
const CATEGORIES = [
  { key:"all", label:"All", icon:"🛍️" },
  { key:"candles", label:"Candles", icon:"🕯️" }
];
```

The `key` here must exactly match the `category` value used in your products, or that product won't show up when the filter is tapped.

### 4. Colors

At the very top of the `<style>` block:

```css
--brand:     #FF5C72;   /* buttons, prices, highlights — your main brand color */
--brand-ink: #FFFFFF;   /* text color that sits ON the brand color */
--accent:    #FFC857;   /* "New" / "Sale" badge color */
--canvas:    #FAFAFA;   /* page background */
```

Change the hex codes and every button, price, and badge updates automatically — no need to hunt through the rest of the file.

---

## Hosting it

This is a static file, so any of these work without extra setup:

- **GitHub Pages** — push the file to a repo, enable Pages, done.
- **Netlify / Vercel** — drag and drop the file into their dashboard.
- **Your existing host** — upload via FTP/cPanel like any other webpage.
- **Linked from your Instagram bio** — once hosted, drop the URL straight into your "link in bio" field.

No server, database, or environment variables needed — it's one self-contained file.

---

## How orders work (and what it doesn't do)

This template intentionally has **no real shopping cart, payment processing, or order database** — orders are handed off to WhatsApp as a pre-filled message, the same way most Instagram-store sellers already take orders today. That keeps the page fast and removes the cost/complexity of a backend.

The in-page "bag" only holds items in memory while the page is open — it resets if the page is refreshed. That's by design: it's a quick way to bundle several products into one message, not a persistent account-based cart.

If you outgrow this flow later, the product data structure (`PRODUCTS`) is simple enough to connect to a real backend, inventory system, or payment gateway without changing the visual design.

---

## Browser & device support

- Works in all modern mobile and desktop browsers (Safari, Chrome, Firefox, Edge, Samsung Internet).
- Respects `prefers-reduced-motion` for visitors who've disabled animations.
- Honors iPhone "safe area" insets so the bottom nav never sits under the home indicator.
- No JavaScript framework dependency — works even with browser extensions that block third-party scripts, since everything is first-party and inline.

---

## File structure

```
instagram-store-template.html   ← everything: markup, styles, and logic in one file
README.md                       ← this guide
```

There's nothing else to install. If you ever want to split it into separate `.css`/`.js` files for a larger project, the code is organized in clear, commented sections to make that easy later.

---

## Quick troubleshooting

| Problem | Likely cause |
|---|---|
| WhatsApp button doesn't open a chat | `whatsappNumber` has a `+`, spaces, or is missing a country code |
| A product never shows up | Its `category` doesn't match any `key` in `CATEGORIES` |
| Colors didn't change | Make sure you edited the hex values inside `:root { }`, not somewhere else in the CSS |
| Page looks the same after editing | Hard-refresh the browser (`Ctrl/Cmd + Shift + R`) — it may be using a cached copy |

---

## Copyright & License

This template was custom-built for you and is yours to use freely — edit it, rebrand it, sell products through it, and use it for any commercial purpose, with no attribution required and no usage restrictions.

**Independence from Instagram and WhatsApp**
The design borrows familiar *mobile shopping patterns* — a profile-style header, a story-style filter rail, a tap-to-message order flow — but everything here (markup, styles, colors, copy, code) is original work:
- No Instagram logo, wordmark, color gradient, font, icon, or other trademarked/copyrighted asset is used anywhere in this template.
- This template is **not affiliated with, endorsed by, or sponsored by** Instagram, Meta Platforms, Inc., or WhatsApp.
- "Instagram" and "WhatsApp" are trademarks of Meta Platforms, Inc., mentioned here only to describe the design inspiration and the chat-based ordering integration — not to claim any partnership.

**Content you add**
Your store name, logo, bio, and especially product photos and descriptions are your responsibility. Make sure you own the rights to anything you upload before publishing — the template itself doesn't check or guarantee the originality of content you add to it.

**No warranty**
The template is provided as-is, with no warranty of any kind. Test it yourself before relying on it for live sales.

*This section is a plain-language summary, not legal advice — if you need certainty for your specific business or region, it's worth a quick check with a lawyer.*

---

Happy selling! 🌿
