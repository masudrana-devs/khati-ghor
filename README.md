# খাঁটি ঘর (KHATI GHOR)

A single-page, bilingual (Bangla / English) e-commerce landing page for an organic and pure food brand in Bangladesh. The whole site is one self-contained `index.html` file. There is no build step and no backend.

## Features

**Storefront**
- 8 products, each with a weight selector that updates the price, a family usage hint, a freshness batch badge, a health/safety tag and a Quick View modal
- Family Combo Pack banner (৳১,৫৩০, includes free delivery)
- Sourcing story, comparison table, interactive home purity-test tabs, customer reviews and FAQ accordion
- Call back request banner

**Cart and checkout**
- Slide-over cart with quantity controls and a free-delivery progress bar (free over ৳১,৫০০ or with the Combo Pack)
- Coupon `KHATI10` for 10% off
- Delivery area selector with a live estimated delivery date
- Cash on Delivery, bKash and Nagad (TrxID field appears for bKash and Nagad)
- Gift option with a hide-price toggle and a gift message
- Order confirmation modal and a 1-click WhatsApp receipt

**Experience**
- Language switcher (Bangla / English) that translates the whole page
- Light and dark mode
- Cart, language and theme are remembered between visits
- Order tracking modal
- Mobile slide-in menu and a sticky bottom bar (Call, WhatsApp, Cart)

## Tech stack

- HTML, vanilla JavaScript
- [Tailwind CSS](https://tailwindcss.com/) via CDN
- Google Fonts: Hind Siliguri, Playfair Display, Plus Jakarta Sans

An internet connection is needed for the Tailwind CDN and the fonts.

## Run locally

Open `index.html` in any modern browser. No install is required.

## Deploy to GitHub Pages

1. Create a GitHub repository and upload `index.html` and `README.md` to the root.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select `main` and `/ (root)`, then save.
4. After a minute your site is live at `https://<your-username>.github.io/<repo-name>/`.

## Customise

Everything lives in the `<script>` block at the bottom of `index.html`.

| What | Where to change |
|---|---|
| Product prices and weights | `PD` array (`v: [[weightIndex, price], ...]`) |
| Product names, source, tags, benefits, storage notes | `T.bn.P` and `T.en.P` |
| Weight labels | `T.bn.W` and `T.en.W` |
| Usage hints | `T.bn.U` and `T.en.U` |
| Product illustrations | `ART` array (inline SVG) |
| Combo price | `COMBO` and `COMBO_OLD` constants |
| Coupon code and discount | The `KHATI10` check in the `#applyCp` handler |
| Free delivery threshold | `calc()` function (`1500`) and the progress bar |
| Delivery charges | `<option value="70">` and `<option value="130">` in the `#zone` select |
| WhatsApp number | `8801711000000` (receipt link and bottom bar) |
| Call number | `tel:+8801711000000` in the bottom bar |
| bKash / Nagad merchant number | `01711-000000` in the `#payBox` block |
| Footer contact details | `fPh`, `fAd`, `fHr` in both languages |
| Colours | CSS variables in `:root` and `.dark` |

When you add a product, add one entry to each of `PD`, `ART`, `T.bn.P`, `T.en.P` and `T.bn.U` / `T.en.U`, and extend the `sel` array.

## Data stored in the browser

| Key | Purpose |
|---|---|
| `kg_lang` | Selected language |
| `kg_theme` | Light or dark mode |
| `kg_cart` | Cart items and coupon |
| `kg_orders` | Orders placed on this device (used by order tracking) |
| `kg_cb` | Call back requests entered on this device |

## Important limitations

This is a static site, so some features are front-end only:

- **Orders** are sent to you only through the WhatsApp receipt button. Nothing is stored on a server.
- **Call back requests** are saved only in the visitor's own browser. Connect them to a form service (for example Formspree or Google Forms) or your own backend before relying on them.
- **Order tracking** works only for orders placed on the same device. Real orders show "Order received" and never advance, and `#KG-5924` is a demo ID. A real tracker needs a backend that you update.
- **Sample content:** product details, prices, sources, reviews and the purity-test steps are placeholders. Replace them with your real information.
- **Claims:** the "BSTI and lab-tested" badge and "lab tested" wording should be shown only if you hold real certificates.
- **Honey safety:** honey must not be given to infants under 1 year. Keep that note on the honey products.

## License

Add the licence of your choice (for example MIT) before publishing.
