# FORUS public website · greenfield build

Built from `FORUS_Public_Website_Master_Brief_v1.1.md` (12 September 2026). This folder is a complete static site. Open `index.html` in a browser to review it locally; every page links to the others with relative paths, so it works from disk, from any static host, or dropped into a framework's `public` folder.

## Review build

Hosted for review at https://claytonmott-websites.github.io/forus-website-review/ (GitHub Pages, repository `claytonmott-websites/forus-website-review`). Push to `main` to update it.

## Pages

| File | Route in the brief | Notes |
|---|---|---|
| `index.html` | `/` | Home. All nine sections from the brief, in order. |
| `how-forus-works.html` | `/how-forus-works` | Journey, ecosystem, kinds of cooperatives, reference link, CTA. |
| `about.html` | `/about` | Institutional profile, rebuilt 12 September 2026: split cover hero with fact strip, What FORUS is with a journey spine, Why FORUS exists with the two supplied graphics (`assets/img/about-graphic-1` and `-2`, the usual picture versus with FORUS), Built by a cooperative (full-bleed ownership statement), the five-node cooperative ecosystem chain, A wider network (overlapping panel), the registration plate, the vision statement, CTA. All styles are scoped under `.ab-` classes. |
| `stories.html` | `/stories` | Hero, featured story, feed, launch state. |
| `story-template.html` | `/stories/[slug]` | The story detail template, populated with the DotCooperation announcement. |
| `story-world-agriculture-forum.html` | `/stories/[slug]` | Second story on the same template, the World Agriculture Forum announcement. |
| `register.html` | `/register` | Conversion page and handoff shell. |
| `privacy.html`, `terms.html` | footer routes | Branded shells, clearly marked "content pending". |
| `ecosystem.html` | `/ecosystem` | The existing detailed Features / Ecosystem page. Content unchanged; its header and footer menus were aligned to the new site's navigation for the review build, and its sections reordered to Twelve products, Your journey, Find your fit, Explore the products, Ways to join. Linked from How FORUS Works and the footer, not from primary navigation. |

Shared: `assets/css/site.css` (all styles, tokens at the top), `assets/js/site.js` (header state, mobile menu, scroll reveal; no dependencies), `assets/brand/` (logos, mark, pattern tile, .coop mark), `assets/img/` (photography at 720, 1200 and 1672px widths), `favicon.svg`.

## Mapping routes

Every internal link is a relative `.html` path. When the site moves onto real routes, replace `index.html` with `/`, `how-forus-works.html` with `/how-forus-works`, and so on. A single search-and-replace per page name covers it; there are no other route assumptions in the CSS or JS.

## Content rules that the build follows

- A positioning pass on 12 September 2026 tightened the copy around "FORUS is the digital infrastructure for the cooperative economy", weaving in "Built by a cooperative. Built for cooperatives.", "One platform. Many capabilities." and "Shared infrastructure for shared ownership." Structure, imagery and layout were not changed. The footer line now reads "Digital infrastructure for the cooperative economy."

- All copy is taken from the brief verbatim, with only presentational edits such as line breaks. No new claims, statistics, testimonials or case studies were written.
- The two stories are the two approved, distributed press releases of 10 September 2026 (DotCooperation partnership; World Agriculture Forum collaboration). Their text is reproduced as published. No other stories were invented. The story feed uses a two-column grid because there are exactly two stories; switch `.story-grid.two` to `.story-grid` when a third arrives.
- The public pages carry no readiness, pilot, roadmap or status language and no product counts. The Transparency section was removed on request (12 September 2026). All of that detail lives in the ecosystem reference page. The only remaining "pilot" wording is inside the reproduced DotCooperation press release, where it is a factual statement about a named programme.
- Identity language uses "cooperative identity", "shared foundation" and "secure sign-in". The phrase "verified identity" appears only inside the reproduced press releases.
- The About page partnership section names DotCooperation and the World Agriculture Forum using wording lifted from the press releases, and shows the .coop mark that is already approved for the footer. No other partner names or logos are shown.

## Items still needing a FORUS decision

| Item | Where | Current treatment |
|---|---|---|
| Registration handoff URL | `register.html`, both "Start your application" buttons (`data-handoff="registration"`) | Points to `https://forus.coop/register`. Replace with the live application URL. |
| Privacy Policy and Terms of Use | `privacy.html`, `terms.html` | Branded shells with a visible "content pending" note. Drop the approved legal text into the `.body-copy` block. |
| Social channels | Footer | Omitted because no production URLs were confirmed. A `.footer-social` row can be added next to the partner logos once URLs exist. |
| Partner logos | `about.html` partnership section | World Agriculture Forum is shown as a name, not a logo, pending permission for web use. Swap `.partner-name` for an `<img>` when confirmed. |
| Partner link in the footer | Footer | The .coop mark links to `identity.coop`. Confirm before launch. The International Cooperative Alliance logo was removed on request (12 September 2026). |
| Media contact on story pages | Story pages, "Media enquiries" box | Uses the FORUS media contact from the press releases. Remove the box if stories should not carry a contact. |
| FORUS Digital Cooperative and FORUS Digital Group relationship | Not explained anywhere, per the brief. | |

## Design system in brief

- **Palette.** Night Blue is the anchor, with Deep Blue, Medium Blue and Light Blue for structure, Orange for the primary action, Green for "available" states, and the full eight-colour spectrum only as the thin rule under each hero and the octagon mark. Two neutral tints, a warm sand and a cool mist, pace the page between white and Night Blue sections.
- **Type.** Montserrat throughout (Google Fonts, with a system fallback). Headlines are 800 weight with tight tracking and fluid sizes. Eyebrows are 700, uppercase, tracked, with a short rule.
- **Photography.** Full-bleed heroes with a Night Blue scrim from the bottom-left so text sits on the quiet part of the frame. Each `<img>` carries a `--focus` custom property that sets `object-position`, so crops hold the subject at every breakpoint. Change the focus by editing that one value.
- **Motion.** A short entrance on the hero, a scroll reveal on sections, hover lifts on cards. All of it is disabled under `prefers-reduced-motion`.
- **Layout.** One 1200px container on an 8px rhythm. Sections alternate composition: split editorial, dark statement, numbered steps, image mosaic, full-bleed statement, card grid, proof with an overlapping card, and a centred closing CTA. Breakpoints at 1100, 900 and 600px.

## Accessibility and performance

Semantic landmarks (`header`, `nav`, `main`, `footer`, `section` with `aria-labelledby`), one `h1` per page and a descending heading order, a skip link, visible focus rings, an accessible mobile menu (`aria-expanded`, `aria-controls`, Escape closes, focus returns to the button), descriptive alt text on every photograph and decorative SVGs hidden from assistive technology. Images use `srcset` and `sizes`, lazy-load below the fold, and the hero image is marked high priority. No JavaScript framework; the new pages, stylesheet, script and brand assets total under 200KB before photography. The copied `ecosystem.html` is self-contained (fonts embedded) and weighs 2.7MB on its own.

## Checked before handover

At 1280px and 390px on every page: no horizontal overflow, no dead links, no missing image files, zero console errors, mobile menu opens and closes. Screenshots of each page at both widths are in `../Mockups/`.
