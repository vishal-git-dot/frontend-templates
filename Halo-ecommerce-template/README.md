<div align="center">

# Halo

**A modern ecommerce frontend template with a Glow Threads WebGL background.**

Landing, sign in / sign up, product explore and product pages in a single, dependency-free file.

[![Live Demo](https://img.shields.io/badge/Live_Demo-View_Site-8b6cff?style=for-the-badge&logo=githubpages&logoColor=white)](https://vishal-git-dot.github.io/frontend-templates/Halo-ecommerce-template/index.html)

![License: MIT](https://img.shields.io/badge/license-MIT-38d5ff?style=flat-square)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![WebGL](https://img.shields.io/badge/WebGL-990000?style=flat-square&logo=webgl&logoColor=white)
![No build step](https://img.shields.io/badge/build-none-2fe0b5?style=flat-square)
![PRs welcome](https://img.shields.io/badge/PRs-welcome-9a7cff?style=flat-square)

</div>

---

<!-- Add a screenshot or GIF of the site here:
![Halo preview](./preview.png)
-->

## Features

- **Glow Threads background.** Bundles of luminous threads rendered in a WebGL fragment shader. The effect runs at full strength on the landing page and dims on content pages so text stays readable.
- **Four connected pages.** Landing, sign in / create account, explore and product, linked through the nav, cards and buttons.
- **Explore with filters.** Category chips and a price sort.
- **Product page.** Colour swatches that recolour the product, quantity stepper, add to cart and related items.
- **Cart drawer.** Line items, remove buttons and a running total.
- **Zero dependencies.** One HTML file. No framework, no bundler, no `npm install`.
- **Accessible by default.** Visible focus states, labelled controls, ARIA tab roles and `prefers-reduced-motion` support.
- **Responsive.** Fluid type and layouts from phone to desktop.
- **Graceful fallback.** If WebGL is unavailable, the page still works on a plain dark background.

## Pages

| Page | Route | What it has |
| --- | --- | --- |
| Landing | `#/` | Hero, new arrivals, value points, sign-up banner |
| Sign in / Sign up | `#/login` | Tabbed form with validation |
| Explore | `#/explore` | Category filters, sorting, product grid |
| Product | `#/product/:id` | Gallery tile, options, add to cart, related items |

Routing is hash-based, so the template works on any static host without server configuration.

## Quick start

1. Download or clone this repository.
2. Rename `halo-store.html` to `index.html` (skip if it already is).
3. Open it in a browser, or serve the folder locally:

```bash
npx serve .
# or
python3 -m http.server 8000
```

## Deploy to GitHub Pages

1. Push `index.html` to the root of your repository.
2. Go to **Settings → Pages**.
3. Set the source to **Deploy from a branch**, then choose `main` and `/ (root)`.
4. Save. Your site will be live at `https://YOUR-USERNAME.github.io/YOUR-REPO/` within a couple of minutes.

Then update the **Live Demo** badge at the top of this file with your real URL.

## Customization

Everything lives in `index.html`.

**Brand colours.** Edit the CSS variables at the top of the stylesheet:

```css
:root {
  --bg: #070611;     /* page background */
  --fg: #f1eeff;     /* main text */
  --muted: #a8a2c6;  /* secondary text */
  --line: rgba(255,255,255,.14);
}
```

**Thread colours.** In the fragment shader, change the two `vec3` values `A` and `B` (RGB from 0 to 1). The threads blend between them.

**Thread intensity per page.** Each view sets `calmT` (0 is full strength, 1 is calmest). Raise it on any page where text needs more contrast.

**Products.** Edit the `P` array near the top of the script:

```js
{ id: 1, n: "Arc desk lamp", c: "Lamps", p: 128, h: 268, d: "Description…" }
```

| Key | Meaning |
| --- | --- |
| `id` | Unique number, used in the product URL |
| `n` | Product name |
| `c` | Category (add new ones to the filter list in `V.explore`) |
| `p` | Price |
| `h` | Hue (0 to 360) used for the product tile colour |
| `d` | Description |

**Product images.** Tiles are CSS gradients. To use photos, replace the `.tile` background with an `<img>` or `background-image`.

## Notes

- This is a **frontend template only**. Sign in, cart and checkout are demo interactions and nothing is sent to a server. Connect your own auth and payments to make it production-ready.
- The Bricolage Grotesque font loads from Google Fonts, with a system font fallback.
- Requires a browser with WebGL support. All current versions of Chrome, Edge, Firefox and Safari work.

## Roadmap ideas

- [ ] Real product images and a gallery
- [ ] Persistent cart (localStorage)
- [ ] Search
- [ ] Checkout page
- [ ] Light theme

## Contributing

Issues and pull requests are welcome. For larger changes, please open an issue first to discuss what you would like to change.

## License

Released under the [MIT License](./LICENSE).
