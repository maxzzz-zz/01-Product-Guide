# Site Baseline

Inventory of the files in the current `01-Product Guide` project. This records what is present in the repository; it does not independently verify product facts, legal requirements, image rights, production hosting, or the live website.

## 1. Site Identity

- **Current project name:** `01-Product Guide` (project folder name).
- **Product name:** Yu Sleep.
- **Brand name explicitly present:** “Yu Sleep” is used in the title and product content. “Sleep Formula Guide” is used as the header/footer guide identity on the main page. The legal-page terms template also contains the unresolved text “BRAND NAME.”
- **Current domain:** UNKNOWN. No production domain is established in the project files.
- **Domain placeholders:** `YOUR-DOMAIN.com` appears in legal page canonical URLs, `robots.txt`, and `sitemap.xml`.
- **Site type:** Static product information/affiliate landing page for a liquid sleep-support supplement, with a redirect endpoint and contact/legal pages.
- **Deployment assumptions:** The project is plain static HTML/CSS with local assets and can be served from a web root. Root-relative CTA routes such as `/order` assume deployment at the domain root. No Hostinger account, document root, production domain, HTTPS setup, deployment process, or routing configuration is recorded in these files. These are assumptions from the file layout, not confirmed deployment facts.

## 2. Affiliate Configuration

- **Current local affiliate/order path:** `/order` is linked from the main page. The endpoint file is `order/index.html`; whether the exact path resolves as intended depends on host directory-index behavior.
- **Exact affiliate destination:** NOT CONFIGURED.
- **Destination currently present:** `YOUR-CLICKBANK-AFFILIATE-LINK`, repeated in the order page's HTML meta refresh, JavaScript redirect, and manual fallback anchor. This is a placeholder string, not a real configured URL.
- **Order-page indexing:** `order/index.html` has `noindex, nofollow`.
- **Known CTA/order routes:**
  - Main page header CTA: `/order`.
  - Main page mobile-nav CTA: `/order`.
  - Three package-card CTAs: `/order`.
  - Bonuses availability CTA: `/order`.
  - Guarantee CTA: `/order`.
  - Verdict/current-offer CTA: `/order`.
  - Final CTA: `/order`.
  - Hero buttons go to internal sections `#overview` and `#packages`, not the affiliate destination.
- **Unresolved configuration:** Real affiliate destination, affiliate program/account, tracking parameters, whether the redirect path is supported by the eventual host, and the final production domain. No affiliate URL should be inferred or added without an explicit source.

## 3. Product Information

The items below are transcribed or summarized from the project content only. **All product facts, offer terms, product performance/safety statements, ingredient amounts, prices, and guarantee terms require verification against current authoritative product/merchant information before production.** Their presence in HTML is not proof that they are accurate or current.

### Product and category

- Product: Yu Sleep.
- The FAQ describes it as a “liquid dietary supplement.”
- The main page describes a liquid sleep-support formula and says the serving is 2 mL nightly/two full droppers. Verify the product label and current directions.

### Benefits/features and claims present

The page claims or promotes:

- Fall asleep faster, stay asleep longer, wake refreshed/energized, and get deep/restful or uninterrupted sleep.
- Liquid format, “fast-acting,” rapid absorption, and easier use than pills.
- Natural ingredients/formula; “100% Natural”; “safe”; “non-habit forming”; no harsh chemicals; and no groggy after-effects.
- Calm the mind, relax muscles, support natural melatonin production, reduce nighttime stress, soothe anxiety, boost serotonin, and affect brain waves.
- A “TOP-RATED SLEEP SUPPLEMENT” label with five star symbols.
- “The Science Behind…”/“proven natural extracts” and “well-researched formula” language.
- Multi-bottle savings, “Save Up to 50%,” “lowest possible price,” and “100% risk-free”/risk-free trial wording.
- A one-time payment with no hidden fees or subscriptions.

These are claims in the site's copy, not verified findings. In particular, health, safety, efficacy, ranking/rating, savings, and offer claims need substantiation and current review.

### Ingredients listed in the main page

The ingredients section names nine items:

1. Vitamin B2 and Vitamin B6 (also shown as 0.5 mg + 0.5 mg).
2. Melatonin (shown as 0.9 mg).
3. Red tart cherry (described as juice concentrate).
4. Magnesium glycinate.
5. Apigenin.
6. Lemon balm extract.
7. 5-HTP.
8. L-Theanine.
9. GABA.

The page includes benefit descriptions alongside several ingredients. Verify ingredient identity, amount, spelling/form, and descriptions against the current supplement facts/label. The FAQ itself says to review current supplement facts for full details.

### Package options and displayed prices

The main page displays the following per-bottle prices and supply durations:

| Package | Supply shown | Price shown |
|---|---:|---:|
| 2 bottles | 60-day supply | $69 per bottle |
| 3 bottles | 90-day supply | $59 per bottle |
| 6 bottles | 180-day supply | $49 per bottle |

The page labels six bottles “Best Value” and advertises savings “up to 50%.” Currency, current availability, total order prices, shipping, taxes, and price validity are NOT CONFIRMED in the project files. Verify all offer details before publishing.

### Bonuses shown

Three bonus cards are present:

1. “The Wind Down Routine” — bedtime stories/calming techniques.
2. “Younger and Happier While You Sleep” — nighttime routine and natural approaches to sleep.
3. “Popular Bedtime Snacks That Trigger 3 AM Walkeups & Racing Thoughts” — the title contains the spelling “Walkeups” in the source.

The page says bonus availability may vary and directs visitors to the current offer/order page. Verify names, contents, inclusion conditions, and availability. The repeated footer/legal disclosure does not establish that bonuses are currently offered.

### Guarantee shown

The page advertises a 60-day money-back guarantee, including “full refund,” “no questions asked,” and “zero hassle” wording. Verify the current merchant's exact terms, eligibility, return process, and applicability to each package. Do not treat page copy or the guarantee image as proof of current terms.

## 4. Content Sources

- **`index.html`:** Main product/affiliate landing page. Contains product overview, product claims, ingredient descriptions and some amounts, packages/prices/supply durations, bonus descriptions, guarantee wording, FAQs, CTA links, affiliate/medical footer disclosures, page title and meta description, and inline JavaScript.
- **`order/index.html`:** Redirect endpoint. Contains the unconfigured affiliate destination placeholder in three redirect mechanisms and a noindex directive.
- **`contact.html`:** Contact page, including generic instructions for website questions and separate guidance about product/order questions. Canonical uses a placeholder domain.
- **`privacy-policy.html`:** Privacy policy. Canonical uses a placeholder domain. Its text describes possible collection/analytics/cookies in general terms; the actual services/data collection in use are not established here.
- **`terms.html`:** Terms page with unresolved “BRAND NAME” text in title, body, and footer, plus a placeholder canonical domain.
- **`disclaimer.html`:** Disclaimer page covering general/product/affiliate-related topics; canonical uses a placeholder domain.
- **`style.css`:** Shared presentation, responsive rules, and visual styles; no product fact source of truth is defined here.
- **`robots.txt`:** Allows all crawlers and names a placeholder sitemap URL.
- **`sitemap.xml`:** Sitemap entries use the placeholder domain; lists homepage and legal/contact pages.
- **`assets/images/`:** Product, ingredient, package, bonus, guarantee, favicon, and lifestyle image files. Asset origin and rights are not recorded.
- **Other source of product truth:** UNKNOWN. No product fact sheet, merchant source, claim substantiation record, or review date is included.

## 5. SEO Baseline

### Main page

- **Title:** `Yu Sleep | Liquid Sleep Support Formula`.
- **Meta description:** “Discover Yu Sleep, a convenient liquid sleep support formula with carefully selected ingredients designed to complement your nighttime routine and support relaxation and restful sleep. Learn more today.”
- **H1:** “Yu Sleep; Fall Asleep Faster. Wake Up Refreshed” (Yu Sleep is in a span; the source also has a semicolon after it).
- **Major H2 sections:**
  - “Why Liquid is Better for Your Sleep?”
  - “The Science Behind Your Best Night’s Sleep”
  - “Your Journey to Better Sleep Starts Here”
  - “Choose Your Package & Save Up to 50% Today!”
  - “Exclusive Bonuses Just For You”
  - “Your Purchase is 100% Protected”
  - “Why Yu Sleep is Worth Your Investment Today”
  - “Questions About Yu Sleep”
  - “Claim Your Exclusive Yu Sleep Discount Today”
- **Canonical:** Missing from `index.html`.
- **Open Graph/social metadata:** No Open Graph or Twitter card tags found.
- **Structured data:** No JSON-LD or other structured data found.
- **Image alt text:** Main-page images have alt attributes. Most are descriptive; all three bonus images share the generic text “Yu Sleep bonus resource.” Decorative images/alt choices have not been accessibility-reviewed.
- **Robots meta:** No homepage robots meta tag found.

### Site-wide crawl files and other pages

- **`robots.txt`:** `User-agent: *` and `Allow: /`; sitemap location is `https://YOUR-DOMAIN.com/sitemap.xml` (placeholder).
- **`sitemap.xml`:** Contains the placeholder domain for the home, privacy policy, disclaimer, terms, and contact URLs. It does not list the order redirect.
- **Legal-page canonicals:** Present but use `https://YOUR-DOMAIN.com/` placeholder URLs.
- **Terms title/description:** Include “BRAND NAME” placeholder text.
- **Order page:** `noindex, nofollow`; no canonical. The destination is a placeholder.
- **Unresolved SEO items:** Production domain, canonical strategy, final sitemap URLs and contents, robots production policy, social preview image/metadata, and whether any structured data is appropriate.

## 6. Legal Baseline

- **Contact page:** `contact.html`. It distinguishes questions about the website from questions about products/orders. No verified operator identity, physical/mailing address, or working email/phone was established from the inspected page content.
- **Privacy policy:** `privacy-policy.html`. It describes privacy, cookies, analytics, affiliate links, third-party sites, and related topics. Whether each described practice reflects actual site behavior is UNKNOWN.
- **Terms:** `terms.html`. Contains multiple “BRAND NAME” placeholders, including the title, body references, and footer.
- **Disclaimer:** `disclaimer.html`. Includes general information, product information, affiliate disclosure, third-party websites, purchases, and no-professional-advice sections.
- **Operator/brand details explicitly present:** “Yu Sleep” and “Sleep Formula Guide” appear as product/site branding. A legal operator/publisher identity is not confirmed.
- **Placeholders:** `YOUR-DOMAIN.com` in canonical tags; `BRAND NAME` throughout terms; contact details/operator identity not confirmed.
- **Site-specific review required:** Confirm operator identity/contact, domain, actual data collection/analytics/cookie practices, affiliate relationship and disclosure language, product-specific disclaimers, and all policy statements. This inventory is not legal advice and does not assess legal sufficiency.

## 7. Assets Baseline

All listed assets are under `assets/images/`. Classification is based on filenames and current page references, not verified ownership or licensing.

| Asset(s) | Classification | Current use/status |
|---|---|---|
| `favicon.png` | Favicon/brand | Referenced by `index.html`; branding/rights unverified |
| `yu-sleep-liquid-sleep-support-hero.webp` | Product | Main-page hero image |
| `vitamin-b2-b6.jpg`, `melatonin.jpg`, `red-tart-cherry.jpg`, `magnesium.jpg`, `apigenin.jpg`, `lemon-balm.jpg`, `5-htp.jpg`, `l-theanine.jpg`, `gaba.jpg` | Ingredient | Referenced in ingredient cards |
| `package-2-bottles.webp`, `package-3-bottles.webp`, `package-6-bottles.webp` | Package/product | Referenced in package cards |
| `bonus-1.png`, `bonus-2.png`, `bonus-3.png` | Bonuses | Referenced in bonus cards |
| `60-day-money-back-guarantee.png` | Guarantee | Referenced in guarantee section |
| `sleep-lifestyle.webp` | Lifestyle | Present in assets folder; no reference found in inspected HTML, so apparently unused |
| Social-share image | Social | No dedicated social/Open Graph image identified |

Rights, source, permissions, and attribution requirements for all product/brand/ingredient/bonus images are UNKNOWN and require confirmation. Do not assume that files present in the repository are licensed for use.

Some PNG assets are relatively large by file size: guarantee image ~747 KB, bonus 3 ~688 KB, bonus 1 ~224 KB, bonus 2 ~156 KB. This is a file-size observation only; dimensions, visual quality, and transfer performance have not been measured. Most non-hero images do not declare lazy loading or intrinsic width/height in the inspected main page.

## 8. Technical Baseline

- **Architecture:** Static HTML pages; one shared `style.css`; local image files; no framework or package/build configuration identified.
- **JavaScript:** Inline script in `index.html` controls the mobile menu and FAQ accordion. Inline script in `order/index.html` attempts the affiliate redirect. No separate JS file identified.
- **Responsive behavior:** CSS includes responsive breakpoints at 1000px, 800px, and 560px, plus ingredient-specific rules at 991px and 575px. The source includes layout changes for mobile/tablet; actual browser/device rendering has not been tested for this baseline.
- **External libraries/services:** None identified in the inspected HTML/CSS. No analytics/pixel integration identified. The actual hosting or affiliate service is unknown.
- **Fonts:** System stacks: Arial/Helvetica/sans-serif for body, Georgia/Times New Roman/serif for selected headings. No external font service identified.
- **Accessibility observations:** Images generally have alt attributes. The menu button has an `aria-label` and `aria-expanded`; script updates expanded state. Its label remains “Open navigation menu” even when open. FAQ controls are buttons, but no `aria-expanded`/answer association was found in the inspected markup. Keyboard, contrast, screen reader, and focus behavior have not been tested.
- **Image optimization observations:** WebP is used for some product/lifestyle images, while ingredient and bonus assets include JPEG/PNG. Several PNGs are relatively large by byte size. The hero image specifies eager loading; other main-page images generally lack explicit loading behavior and dimensions.
- **Known technical risks:** Placeholder redirect target; root-relative `/order` path assumes domain-root deployment; main canonical absent; placeholder sitemap/canonicals; terms brand placeholder; inconsistent/older legal-page navigation anchors/classes identified in earlier project inspection; source includes visibly garbled characters in some punctuation/arrows/copyright text, suggesting a potential encoding issue. No browser, validator, accessibility, link, or performance tests were run for this document.

## 9. Known Problems

- [ ] Affiliate destination is `YOUR-CLICKBANK-AFFILIATE-LINK`, not a configured URL.
- [ ] Production domain is not specified; `YOUR-DOMAIN.com` remains in canonical tags, `robots.txt`, and `sitemap.xml`.
- [ ] Main page has no canonical URL.
- [ ] `terms.html` contains “BRAND NAME” placeholders in metadata and page content.
- [ ] Affiliate order route depends on root path and directory index behavior that have not been confirmed.
- [ ] Displayed product claims, amounts, pricing, package supply durations, bonuses, guarantee, and “top-rated” language have not been verified.
- [ ] Legal operator/contact identity and the actual practices described by privacy text are unconfirmed.
- [ ] Image provenance, ownership, licensing, and attribution are undocumented.
- [ ] `sleep-lifestyle.webp` appears unused by inspected HTML.
- [ ] Bonus image alt text is generic and repeated.
- [ ] No Open Graph metadata, social image metadata, or structured data was found.
- [ ] Some text appears to have encoding/mojibake artifacts.
- [ ] Legal-page navigation/layout consistency and section links have known concerns from project inspection.
- [ ] No deployment configuration, live-domain confirmation, or production verification is recorded.

## 10. Verification Checklist

Confirm each item before production:

- [ ] Production domain and ownership.
- [ ] HTTPS certificate and canonical host/redirect behavior.
- [ ] Exact affiliate URL from the authorized affiliate account/source.
- [ ] Correct local CTA and order route behavior on the intended host.
- [ ] Product identity, category, ingredients, amounts, and serving instructions against current product sources.
- [ ] Product claims and evidence/approval for health, efficacy, safety, rating, and comparative statements.
- [ ] Current package options, prices, currency, supply durations, shipping/fees, and availability.
- [ ] Current bonus names, content, inclusion conditions, and availability.
- [ ] Exact guarantee terms and refund process.
- [ ] Legal operator identity and working contact details.
- [ ] Privacy/legal statements against actual site services and data practices.
- [ ] Image source, ownership/license, permissions, and attribution.
- [ ] Per-page SEO title and description.
- [ ] Correct canonical URLs on all pages.
- [ ] Sitemap URLs and page inclusion against the production domain.
- [ ] Robots policy and sitemap reference against production/staging needs.
- [ ] Open Graph/social image and metadata if required.
- [ ] CTA/order destination and redirect behavior, including manual fallback.
- [ ] Desktop, tablet, and mobile layout on real browser widths.
- [ ] Keyboard navigation, focus states, menu, FAQ, and image alternatives.
- [ ] Text encoding and special characters in browser rendering.
- [ ] Live-site verification after deployment, including legal pages and all CTA paths.

## 11. Do Not Guess

The following are unresolved unless confirmed from a reliable, authorized source:

- Production domain: **UNKNOWN**.
- Affiliate destination: **NOT CONFIGURED**; only a placeholder is present.
- Hostinger account, document root, and deployment procedure: **UNKNOWN**.
- Legal operator/publisher name and contact details: **UNKNOWN/UNCONFIRMED**.
- Whether “Sleep Formula Guide” is the legal/business brand or only page branding: **UNKNOWN**.
- Current accuracy and approval of product claims: **REQUIRES VERIFICATION**.
- Current formula/ingredient amounts and complete supplement facts: **REQUIRES VERIFICATION**.
- Current pricing, total package charges, currency context, and availability: **REQUIRES VERIFICATION**.
- Current bonus offer and guarantee terms: **REQUIRES VERIFICATION**.
- Image ownership, licenses, permissions, and attribution: **UNKNOWN**.
- Actual analytics, cookies, tracking, and personal-data practices: **UNKNOWN**.
- Whether current live website matches repository content: **UNKNOWN**.
- Social image, Open Graph, and structured data requirements: **NOT CONFIGURED/UNKNOWN**.

No facts or URLs should be supplied to fill these gaps without verification.

## 12. Baseline Rules

This file is a reference and inventory of the current project state. It is not permission to change the website, affiliate destination, product claims, pricing, guarantee, legal pages, assets, SEO files, or deployment. Any future changes require their own explicit scope and must use verified information. Unknowns in this baseline must remain marked as unknown until confirmed.

## A. Current baseline summary

The project is a static Yu Sleep product/affiliate landing site with a main product page, a local order redirect page, four legal/contact pages, a stylesheet, and product-related image assets. Product copy and offer details live primarily in `index.html`. The affiliate destination and production domain are still placeholders in the repository.

## B. Critical unresolved items

1. Production domain and deployment setup.
2. Exact affiliate destination and working order route.
3. Verification of product claims, ingredients/doses, prices, packages, bonuses, and guarantee.
4. Legal operator/contact details and site-specific legal/privacy accuracy.
5. Domain-specific canonicals, sitemap, and robots configuration.
6. Image rights and source records.
7. Encoding/rendering and responsive/live-site verification.

## C. Recommended next action

Confirm the production domain/deployment owner and obtain the exact authorized affiliate destination and current product/offer source materials. Keep all other unknowns unresolved until verified; this baseline itself does not authorize website changes.

