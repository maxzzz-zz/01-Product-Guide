# Scalable Affiliate Website Architecture Plan

## Purpose and guiding decisions

The goal is to support many product-focused affiliate websites, each with its own domain and Hostinger deployment, while reducing repeated design and maintenance work. Product facts, claims, branding, images, legal identity, SEO metadata, and affiliate destinations must remain isolated per site.

Recommended approach:

- Keep the current Yu Sleep website working as it is while planning and preparing the next steps.
- Start with plain HTML, CSS, and JavaScript. Do not add a framework just to organize two sites.
- Treat each website as an independently deployable site with its own final HTML, CSS, assets, domain configuration, policies, and affiliate link configuration.
- Reuse visual patterns and implementation through a documented starter/template first. Introduce automated shared components only when repeated manual work justifies a build process.
- Store per-site configuration and content separately from reusable layout. A future static generator can consume these inputs and produce standalone static output, but that is a later decision.
- Make changes additive and reviewable. Do not move or replace the current website as part of the initial architecture work.

## 1. Current project: preserve and classify

### What remains unchanged initially

The existing `01-Product Guide` website is the Yu Sleep site. Its current files remain in place and its current deployment remains independent while the architecture is prepared. In particular, this plan does not call for changing or moving `index.html`, `style.css`, the legal pages, assets, order redirect, `robots.txt`, or `sitemap.xml` as an architecture exercise.

Before any future implementation, inspect the live repository status and deployment arrangement. Keep the current site available until a separately reviewed replacement is ready and can be compared against it.

### What can become reusable

These are reusable patterns, not automatically reusable copy or assets:

- Page shell, semantic section structure, container widths, and responsive grid patterns.
- Header and navigation layout, mobile menu behavior, footer layout, and back-to-top behavior.
- CTA button styles and CTA placement patterns.
- FAQ accordion behavior and accessible disclosure pattern.
- Reusable visual patterns for ingredient/feature cards, package cards, bonus cards, guarantee panels, trust points, and final offer sections.
- Shared design tokens and neutral utility classes.
- Repeatable technical checklists for metadata, internal links, performance, accessibility, and deployment.

Extract or reproduce a pattern only after understanding its current behavior and testing it in the destination site. Avoid turning all sections into generic components if sites do not actually share them.

### What is Yu Sleep-specific

Keep these values and content owned by the Yu Sleep site:

- Product name, product category, brand identity, colors, product logo, and domain.
- Ingredient names, descriptions, health-related statements, product claims, and any evidence supporting those statements.
- Package names, serving/supply details, prices, bonuses, offer copy, and guarantee terms.
- Affiliate destination, tracking parameters, order route, and disclosure wording as applicable.
- Product photos, package artwork, ingredient graphics, guarantee badge, favicon, and any other brand assets.
- Page titles, descriptions, canonical URLs, Open Graph values, structured data, sitemap, and robots policy.
- Contact details, operator identity, jurisdiction-specific notices, and legal policies.

These facts must not be copied to another product site without verification and explicit site-specific review.

## 2. Reusable architecture

### Shared layout patterns

Define a small set of page-level patterns that can be used where appropriate:

1. **Site shell:** document metadata, header, main content landmark, footer, and shared stylesheet.
2. **Header:** site-specific logo/name and navigation to that site's own sections/pages.
3. **Hero:** site-specific headline, summary, product image, and primary CTA.
4. **Information sections:** overview, benefits, ingredients/features, how it works, and evidence or caveats when appropriate.
5. **Offer sections:** package comparison, bonuses, guarantee, terms/availability note, and CTA.
6. **FAQ:** product-specific questions with a reusable accessible interaction pattern.
7. **Disclosure/footer:** per-site affiliate notice, medical or other relevant disclaimer, legal links, and contact information.
8. **Utility patterns:** cards, buttons, section headings, responsive containers, and image wrappers.

Not every product needs every section. The page should reflect the product and available verified information rather than forcing all sites into the same sales-page outline.

### Shared CSS strategy

- Keep a small, documented set of neutral tokens for spacing, container widths, typography scale, breakpoints, border radii, and interaction states.
- Allow brand colors and optional typography to be set per site. Do not encode Yu Sleep's palette as the shared default.
- Prefix or scope site styles where needed to prevent one site's CSS from changing another site's page.
- Share only stable styles. Site-specific visual variations should be expressed through that site's configuration or stylesheet overrides.
- Avoid global selectors that unexpectedly change unrelated components. Preserve visible focus states and responsive layouts.
- During the plain-static stage, a starter stylesheet may be copied into a new site and then customized. Document that copies can diverge; do not pretend copied files are automatically synchronized.

### Components/sections to make reusable over time

| Pattern | Reusable behavior/structure | Must remain site-specific |
|---|---|---|
| Header/navigation | Responsive layout, accessible menu interactions | Logo, brand name, links, CTA label and destination |
| CTA button | Styling, focus/hover states, link conventions | Text, affiliate route, disclosure context |
| FAQ | Button/answer semantics, keyboard behavior, expanded state | Questions and answers |
| Feature/ingredient card | Image/title/body layout | Facts, claims, image, alt text |
| Package card | Price/feature hierarchy and responsive comparison | Package details, prices, availability, labels |
| Bonus card | Image/content layout | Bonus, image, inclusion terms |
| Guarantee panel | Layout and icon/image position | Exact guarantee, limitations, artwork |
| Offer section | Layout for offer and action | Offer details, date/availability, affiliate URL |
| Footer | Shared layout, legal-link placement | Legal entity, disclosure, contacts, policies, links |

In a future component-based setup these patterns may be components. In plain HTML they can initially be copied from a reviewed starter page. The copy process should be explicit and should never pull another product's text, values, images, or links along with it.

## 3. Product/site configuration

Maintain one reviewed configuration record per site. YAML or JSON is appropriate as a source format once a build tool reads it. At the plain-static stage it can serve as a documented source-of-truth checklist, but static HTML will not consume it automatically. Until there is a generator, changes to rendered HTML remain manual and should be checked against the record.

Illustrative schema (values below are placeholders, not product facts):

```yaml
siteId: "02-example"
siteName: "Example Product Guide"
domain: "https://example-domain.invalid"
brand:
  name: "Example Brand"
  logo: "assets/brand/logo.svg"
  colors:
    primary: "#123456"
    accent: "#abcdef"
product:
  name: "Example Product"
  category: "Example category"
  benefits: []
  featuresOrIngredients: []
  packages: []
  bonuses: []
  guarantee:
    summary: ""
    termsUrl: ""
affiliate:
  destination: ""
  orderPath: "/order/"
  disclosure: ""
seo:
  title: ""
  description: ""
  canonical: ""
  openGraphImage: "assets/social/share.jpg"
  sitemap:
    enabled: true
    includePaths: ["/", "/privacy-policy/", "/terms/"]
  robots:
    indexSite: true
    disallowPaths: []
legal:
  operatorName: ""
  contact: ""
  privacyPolicyPath: "/privacy-policy/"
  termsPath: "/terms/"
  disclaimerPath: "/disclaimer/"
```

The schema should evolve only when actual sites need new fields. Recommended field rules:

- **Product facts and claims:** record source/verification date in editorial notes or a separate review record; do not publish unsupported values automatically.
- **Pricing and packages:** support multiple package entries with exact labels, currency, price, shipping/availability notes, and last-reviewed date where needed.
- **Benefits/features/ingredients:** store distinct items with product-specific title, approved copy, image path, and alt text; avoid a generic unverified `benefits` list shared across sites.
- **Guarantee and bonuses:** store exact reviewed wording and conditions rather than a generic promise.
- **Affiliate URL:** store only the explicitly supplied affiliate destination. Do not infer it from a brand URL or fabricate tracking parameters.
- **Domain/SEO:** derive canonical and sitemap locations from a verified production domain in a future build, or validate manually in the plain-static stage. Never publish `.invalid`, `YOUR-DOMAIN`, or other placeholders.
- **Robots:** keep staging/noindex decisions separate from production indexing and verify the published files for each domain.

Secrets such as hosting passwords, API tokens, and account credentials do not belong in site configuration or Git. Affiliate URLs are not normally credentials, but should still be reviewed carefully because they control revenue attribution and destination.

## 4. Content separation

Keep four kinds of material distinct:

1. **Reusable presentation:** layout, interaction behavior, CSS patterns, and neutral components.
2. **Site identity:** domain, logo, color palette, navigation labels, contact identity, and legal operator details.
3. **Product content:** product facts, prices, ingredients/features, claims, offers, images, FAQs, and affiliate destination.
4. **Deployment output:** the exact standalone files uploaded to one domain/account.

Do not put product facts in shared components or shared defaults. Shared components should receive site data or contain neutral presentation only. During the plain HTML stage, separation is a file organization and review discipline rather than a runtime guarantee. A later build process should make site selection explicit and should fail if required domain, canonical, or affiliate destination values are missing.

## 5. Multi-site strategy

Use stable site IDs, not product names alone, to identify sites. Each site owns its source content and assets and produces its own deployment bundle. A change to Website 02 should not rewrite Website 01's files or build output.

At the beginning, keep the existing Yu Sleep site in the current project root. Add the next site in a separate directory or repository only after deciding where the portfolio source of truth should live. Do not move the existing site as a prerequisite. When the portfolio grows, place sites beneath `sites/` and shared source beneath `shared/`; generate each site's deployable output separately.

Use an explicit site selection such as `build --site 02-example` in a future build workflow. Never build all sites by accidentally combining their content into one page or by relying on whichever config was edited last. Each site's output should contain only that site's pages, styles, assets, robots file, sitemap, and redirects.

## 6. Git/GitHub strategy

For one person, keep the workflow simple:

- **`main` (or the repository's current protected/default branch):** reviewed, deployable state. Avoid creating a second long-lived production branch if it adds overhead.
- **`development`:** optional integration branch when several site changes are in progress. For a solo operator with one small change at a time, short-lived feature branches from `main` are usually simpler than maintaining both `development` and `main` indefinitely.
- **Feature branches:** use focused names such as `site/02-example`, `template/accessible-faq`, or `seo/yu-canonical`. One branch should represent one reviewable change.
- **Individual websites:** isolate changes by site directory/config. Keep deployments tied to a site-specific folder or build command.
- **Reusable template changes:** make a dedicated branch, verify the change against at least two representative sites, then merge. Do not update each site indiscriminately without reviewing its brand-specific overrides.
- **History:** do not rewrite shared history. Inspect `git status` before work and review the diff before committing.
- **Commits:** use small commits with clear intent. Keep credentials and local deployment secrets out of the repository.

If all websites are in one monorepo, a shared template update and the corresponding affected site updates can be reviewed together. If sites are managed in separate repositories, distribute reusable changes through a versioned starter/template or deliberate cherry-picks rather than silently coupling deployment repositories.

## 7. Safe Codex workflow

For each task, use this sequence:

1. **Analyze:** inspect applicable `AGENTS.md`, Git status, relevant files, links, and asset ownership. Confirm the target site and the requested scope.
2. **Plan:** state intended files and changes. Identify product facts, affiliate URLs, domains, and legal material that must not be guessed.
3. **Implement:** make only the authorized changes, confined to the selected site's files or explicitly shared template. Preserve unrelated sites.
4. **Review:** inspect the diff for accidental cross-site edits, invented facts, wrong links, placeholders, and unintentional removals.
5. **Test:** perform appropriate local checks when authorized: HTML/link checks, responsive browser review, accessibility checks, and a production-like preview. Report precisely what was and was not tested.
6. **Commit:** stage only intended files and use a focused commit. Do not change Git configuration or rewrite history unless explicitly authorized.
7. **Publish:** deploy only the selected site's reviewed output to its matching Hostinger domain/account. Confirm the target before uploading and check the live domain afterward.

Analysis and planning can be read-only. Treat legal edits, new claims, pricing/offer changes, and affiliate destination changes as requiring explicit instruction and verified source material. Ask for missing values rather than inventing them.

## 8. Hostinger deployment

Each site must be deployable as a self-contained static directory. Its deployment bundle should include the site's HTML pages, local CSS/JS, owned assets, legal pages, `robots.txt`, `sitemap.xml`, favicon, and any host-specific redirect configuration that is actually required.

- Configure and verify the domain and HTTPS for each Hostinger account separately.
- Upload only the selected site's output to its document root, typically `public_html`, after a preview and file-list review.
- Keep the source repository separate from the deployed web root when possible. Never upload `.git`, credentials, drafts, or other sites' assets.
- Ensure internal links work from the domain root and that no output points at another site's domain.
- Verify the live homepage, legal pages, order route, CTA destination, canonical, robots, sitemap, and mobile layout after publishing.
- Keep a rollback copy/tag or previous deploy artifact for each site.
- Do not assume a shared repository means shared hosting: each output and domain remains independently deployable.

In the plain-static phase, the folder uploaded to Hostinger should be the complete site. If shared source assets are outside that folder, copy them into the site's deployment bundle rather than making the live site depend on a sibling path.

## 9. Per-site SEO

Every site owns and validates its own SEO settings:

- **Title:** unique, accurate, readable, and specific to that page/site.
- **Description:** distinct, truthful summary; avoid unsubstantiated guarantees and repetitive boilerplate.
- **Canonical:** absolute production URL on that site's domain for each indexable page. Avoid cross-domain canonical links unless intentionally managing duplicate content.
- **Sitemap:** absolute URLs for that domain only, limited to intended canonical/indexable pages. Keep last-modified values accurate if included.
- **robots.txt:** production sitemap URL must match the site's domain. Do not use a disallow rule as a substitute for noindex. Keep staging protected from indexing using the hosting/environment controls available.
- **Open Graph:** site-specific title, description, canonical page URL, image, and image alt/type/dimensions as practical. Social image must belong to that product/brand.
- **Structured data:** add only when page content genuinely matches a supported schema. Product/Offer values must match current visible content and verified offer facts. Do not add ratings, reviews, prices, stock status, or organization details that are not substantiated. Validate structured data before publishing.
- **Internal links and image text:** preserve crawlable HTML links, descriptive alt text for meaningful images, and empty alt text for decorative images.
- **Redirect endpoint:** decide its indexing policy and canonical behavior deliberately. Keep it out of the sitemap when it is only a redirect.

For the current Yu Sleep site, the prior review found placeholder domain values in sitemap/legal canonicals, no homepage canonical, and a placeholder affiliate destination. These should be considered known migration tasks, but not silently changed as part of architecture setup.

## 10. Legal and disclosure

A shared legal-page structure can provide consistent headings, footer navigation, and a review checklist. Boilerplate can be templated only where it is truly generic and appropriate for the applicable business and jurisdiction.

Each site must separately verify and supply:

- Legal operator or publisher name and contact details.
- Jurisdiction, governing law, and any required consumer/privacy notices.
- Data collection, cookies, analytics, advertising pixels, and retention practices actually used by that site.
- Affiliate relationships and disclosure placement/language for the products and programs used.
- Medical, financial, or other regulated-category disclaimers relevant to that product and claims.
- Merchant responsibility for checkout, shipping, refunds, subscriptions, and customer service.
- Product/brand permissions, terms, and any required trademarks notices.

Do not copy Yu Sleep's legal pages wholesale to another site or treat a generic template as legal advice. Have site-specific legal content reviewed as appropriate. Keep disclosures visible near affiliate CTAs and in a page/footer location, and make them accurate for the actual relationship.

## 11. Asset organization

Use a per-site asset root and stable, descriptive filenames. For example:

```text
sites/
  01-yu-sleep/
    assets/
      brand/
      product/
      ingredients/
      packages/
      bonuses/
      social/
      favicon/
  02-example/
    assets/
      brand/
      product/
      features/
      packages/
      social/
      favicon/
```

Do not put product-specific images in a general shared-assets directory. Shared assets should be limited to genuinely generic UI assets (for example, a neutral arrow icon) and should be licensed/owned for reuse. Use site-relative paths, descriptive alt text, and appropriate image formats/sizes. Record image source, usage rights, and any required attribution in site-owned notes or metadata. Review image references after copying a template to ensure none still point to another product's assets.

## 12. Affiliate link management

- Store the affiliate destination once per site in that site's configuration/source-of-truth record.
- In the plain HTML stage, use one clearly identified local order endpoint such as `/order/` and make that endpoint the single place containing the configured destination. Keep every CTA pointed at the local endpoint so the destination is easier to update and audit.
- Use a descriptive, branded link label. Do not disguise the destination in a way that misleads visitors.
- Do not invent ClickBank or other tracking values. Preserve only the exact URL explicitly supplied and verify it with the affiliate account owner before publishing.
- Add `rel="sponsored"` to direct paid/affiliate links where appropriate, along with safe target behavior if opening a new tab. If a redirect endpoint is used, ensure the disclosure remains clear on the pages that link to it.
- Confirm the endpoint responds as intended, uses the correct site's affiliate URL, does not loop, and has an appropriate indexing policy. Include a manual fallback where useful.
- Before every release, search the selected site's output for placeholder strings such as `YOUR-`, `example.com`, or empty destinations.

A future generator should validate that each production site has exactly one configured affiliate destination and that all CTA components reference it rather than embedding ad hoc URLs.

## 13. Migration path without breaking Yu Sleep

This is a proposed sequence, not authorization to perform these edits. Keep the current root site intact unless a future task explicitly authorizes a particular file change.

### Phase 0 — Baseline and inventory

- Preserve the existing root project as the current Yu Sleep implementation.
- Record which domain/account currently serves it, its upload procedure, affiliate program, and source of truth for product facts.
- Capture a file inventory and screenshots or a browser review of desktop and mobile behavior for comparison.
- Record known placeholders and issues without changing the site.

### Phase 1 — Establish site identity and content records

- Create a site-specific content/config record for Yu Sleep in a future authorized change.
- Populate only from verified current material. Mark unknown values as unresolved instead of guessing.
- Define the per-site checklist for domain, affiliate destination, legal owner/contact, image rights, and SEO values.
- Keep this record separate from current HTML until the data is reviewed.

### Phase 2 — Create a neutral starter using a new site

- Do not refactor the live/current Yu Sleep pages first.
- When a second product is ready, create a separate site directory or separate repository from a neutralized copy/starter, after removing every Yu Sleep fact, asset, URL, claim, color, and legal identity from that starter.
- Populate the second site only with its verified content and assets.
- Deploy and validate Website 02 independently while Website 01 remains untouched.

### Phase 3 — Compare and extract stable patterns

- Compare the two sites and identify patterns truly shared by both.
- Document component boundaries and site-specific overrides.
- If continued copying creates frequent fixes or inconsistencies, implement shared source/templates in an isolated branch and build output for both sites.
- Test shared changes against both sites before adopting them. Keep each site's rendered output independent.

### Phase 4 — Introduce a build pipeline only when justified

- Choose a static generator only when manual synchronization, configuration errors, or page count make static copying expensive.
- Migrate one representative non-production site first. Keep its generated output separate from its source.
- Compare generated pages against the current rendered site and verify links, metadata, responsive behavior, and assets.
- Migrate Yu Sleep only in a separately reviewed, reversible change, after output parity is demonstrated and deployment rollback is ready.

### Phase 5 — Independent production releases

- Deploy each site's output to its matching Hostinger domain/account.
- Confirm domain-specific canonical, sitemap, robots, affiliate redirect, legal links, and analytics policy.
- Retain the previous working deployment until the new release is confirmed.

## 14. Scaling milestones

### At 2 websites

- Keep the existing Yu Sleep site unchanged while establishing a clearly separate Website 02.
- Use a written site checklist/config for both, even if the current site's actual HTML remains the source of its rendered content.
- Copy only neutral layout patterns into Website 02; replace every product-specific value and asset.
- Compare the two to identify which pieces really repeat. Avoid building an abstraction for a single coincidence.
- Maintain site-specific deploy bundles and release checklists.

### At 5 websites

- Move toward a monorepo layout with `sites/` and `shared/`, or intentionally keep separate repos if access/ownership demands it.
- Standardize site IDs, config schema, asset conventions, metadata fields, link conventions, and legal review checklist.
- Adopt shared template source and a repeatable build command if manual drift has become a real maintenance cost.
- Add automated checks for required config, broken local links, placeholder values, asset path ownership, sitemap/domain mismatch, and HTML validity.
- Version shared template changes and test them against a representative site set before release.

### At 10+ websites

- Use a static-site generator or equivalent build system with explicit per-site builds and strict site-data boundaries.
- Add continuous integration to build and validate each changed site independently.
- Consider shared components as a versioned internal package only if multiple repositories require them; otherwise, a monorepo can remain simpler.
- Track owners/review dates for product claims, pricing, affiliate destinations, disclosures, and legal pages.
- Automate previews and deployment only after target-site mapping is explicit and protected against deploying one site's output to another domain.
- Review whether content editing needs a structured CMS. Add one only if nontechnical editing volume warrants it.

## 15. Future framework option

Astro or another static-site generator becomes worthwhile when one or more of these conditions are true:

- The same layout or section has to be corrected manually in several sites.
- Site configuration must reliably generate titles, canonical links, Open Graph tags, robots files, and sitemaps.
- There are many pages or content records and hand-maintained HTML is causing drift.
- Repeated link/placeholder checks should be enforced before deployment.
- Multiple contributors need clear boundaries between content and presentation.

A framework is not required merely because there are multiple domains. A build system adds dependency updates, configuration, build failures, and a learning/maintenance burden. Start with plain static files and a reviewed starter for the first additional site. If a generator is adopted, prefer static output with no required runtime server, and migrate incrementally with a rollback path. Astro is a reasonable candidate for content-focused sites, but choose it only after testing one site and confirming the deployment output works on the intended Hostinger plan.

## 16. Main risks and controls

| Risk | Control |
|---|---|
| Product A claims, assets, or prices appear on Product B | Per-site content/assets folders; site ownership review; automated path/content checks later |
| Wrong affiliate URL or lost attribution | One site-owned destination; centralized local order endpoint; pre-publish click verification |
| Placeholder domain/canonical/sitemap reaches production | Required-field checks and production search for placeholders |
| Shared CSS/template change breaks a site's identity or layout | Scoped styles, site-specific overrides, multi-site preview, focused releases |
| Legal pages are copied inappropriately | Site-specific legal review and facts; never assume boilerplate applies universally |
| Current Yu Sleep site is broken during restructuring | Keep it in place; build a second site first; use preview, parity checks, and rollback |
| Wrong output uploaded to a Hostinger account | Explicit site-to-domain mapping, named release bundles, pre-upload checklist |
| Plain HTML copies drift | Accept and document this at small scale; adopt shared source/build only when drift costs more than the build system |
| Stale price, bonus, guarantee, or health claim | Maintain source/review dates and re-verify before publication; never invent updates |
| Heavy/incorrect assets or rights issues | Site-owned asset directories, optimization review, source/license tracking |
| SEO duplication or cross-site canonical mistakes | Generate/validate absolute URLs per site and inspect each live domain |
| Secrets enter Git | Keep credentials out of site config/repository; use hosting/provider secret storage |
| Framework/build complexity exceeds value | Adopt incrementally with one-site pilot and static-output verification |

## A. Recommended architecture diagram

```text
Affiliate portfolio source repository
│
├── shared/                         Neutral presentation and build tooling (later)
│   ├── layouts/                    Site shell, header/footer patterns
│   ├── components/                 CTA, FAQ, cards, offer patterns
│   ├── styles/                     Tokens and shared responsive styles
│   └── scripts/                    Validation/build scripts (later)
│
├── sites/
│   ├── 01-yu-sleep/                Site-owned config, content, legal, assets
│   │   ├── site.config.yaml
│   │   ├── content/
│   │   ├── legal/
│   │   └── assets/
│   ├── 02-product-name/
│   │   ├── site.config.yaml
│   │   ├── content/
│   │   ├── legal/
│   │   └── assets/
│   └── 03-product-name/ ...
│
└── dist/                           Generated, standalone outputs (later)
    ├── 01-yu-sleep/                Upload only to Website 01 domain/account
    ├── 02-product-name/            Upload only to Website 02 domain/account
    └── 03-product-name/             Upload only to Website 03 domain/account
```

During the transition, the current Yu Sleep site remains at the project root and is deployed as it is today. The diagram represents the eventual organized source model; it is not an instruction to move the existing files now. Each `dist/<site-id>/` directory is self-contained and deployable without access to another site's files.

## B. Recommended folder structure

Eventual monorepo source structure:

```text
affiliate-websites/
├── AGENTS.md
├── README.md
├── shared/
│   ├── styles/
│   │   ├── tokens.css
│   │   └── components.css
│   ├── components/                 (when a generator is adopted)
│   ├── layouts/                    (when a generator is adopted)
│   └── validation/                 (future scripts/checklists)
├── sites/
│   ├── 01-yu-sleep/
│   │   ├── site.config.yaml
│   │   ├── content/
│   │   │   ├── home.yaml
│   │   │   └── faq.yaml
│   │   ├── legal/                  Site-specific reviewed source content
│   │   ├── assets/
│   │   │   ├── brand/
│   │   │   ├── product/
│   │   │   ├── ingredients/
│   │   │   ├── packages/
│   │   │   ├── bonuses/
│   │   │   ├── social/
│   │   │   └── favicon/
│   │   └── static/                 Site-specific static files/config
│   ├── 02-product-name/
│   │   ├── site.config.yaml
│   │   ├── content/
│   │   ├── legal/
│   │   ├── assets/
│   │   └── static/
│   └── 03-product-name/
├── dist/                            Build output; do not hand-edit
│   ├── 01-yu-sleep/
│   └── 02-product-name/
└── .gitignore                       (future, if generated output needs exclusion)
```

The current root files stay where they are during early phases. The structure above is the target after a separately approved migration. Do not add a `dist/` pipeline or move current files until that work is specifically planned and authorized.

## C. Recommended migration phases

1. **Baseline:** keep current Yu Sleep files and deployment intact; inventory domain, deployment, facts, assets, and placeholders.
2. **Site records:** define and review per-site configuration/content fields; do not guess missing product or legal data.
3. **Second-site pilot:** create Website 02 separately from a neutral starter, with only its own verified claims, brand, assets, URLs, and legal information.
4. **Pattern review:** compare sites and identify proven shared layouts/styles; avoid premature abstractions.
5. **Shared source:** introduce a shared starter/template in an isolated branch when drift causes real maintenance work; verify against multiple sites.
6. **Build-system pilot:** when warranted, generate one site's static output first and compare it with expected pages.
7. **Yu Sleep migration (optional):** only after parity, testing, and rollback are demonstrated; perform as a separate reviewed change.
8. **Independent release:** deploy each site's self-contained output only to its mapped domain/account and verify SEO, links, and rendering live.

## D. What we should do FIRST

Before changing the site, document the current Yu Sleep production domain/account, exact affiliate destination source, content/fact sources, asset rights, legal operator/contact details, and the existing upload/rollback procedure. Then define a per-site content/config checklist and use it to plan Website 02. Keep all unknown values explicitly unresolved. This establishes reliable boundaries without risking the current website.

## E. What we should NOT do yet

- Do not move or rewrite the current Yu Sleep files to fit the proposed folders.
- Do not replace the current static site with Astro or another framework now.
- Do not build a generic CMS, complex design system, shared package, or automated multi-account deployment before there is a demonstrated need.
- Do not share product claims, prices, guarantees, ingredients, legal text, affiliate URLs, branding, or images between sites.
- Do not invent missing affiliate URLs, domain values, pricing, legal identity, or product facts.
- Do not deploy a shared-template change to all sites without reviewing each site's output.
- Do not publish sitemap/canonical/robots settings containing placeholders.
- Do not treat generated output as the editable source of truth once a build process exists.
- Do not combine multiple websites into one Hostinger deployment merely because they share a repository.

