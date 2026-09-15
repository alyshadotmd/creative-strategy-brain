---
name: product-info
description: Builds a facts-only profile of one product — everything the brand states about what it is, contains, is made of, comes in, costs, and how it's used — adapted to the product type, so a software plan, a consumable, a garment, and a piece of hardware each get the dimensions that matter for them. Use this whenever a product needs documenting before any strategy or messaging work, when brain-setup profiles the brand's own products or a competitor's, or when someone says "document this product", "pull the product info", "what's in it / what's it made of", or "build the product profile". Output is one markdown file per product. It never interprets, never frames benefits, and never fills a field the source doesn't state.
---

# Product Info

One product, one file, nothing but facts. This document is the factual input layer for every messaging skill downstream: if a claim isn't in here, an ad can't make it. The job is to capture every detail a strategist could need about the product — features, sizes, composition, materials, SKUs, customizations, pricing, positioning as stated — without deciding what any of it means.

**What it is not.** It is not a benefits document, a review summary, or a competitive take. It records what the brand says and what the label or spec sheet shows. A benefit the brand claims is recorded as a quoted claim, never rewritten as a fact.

---

## Step 1: Identify the product and its type

Before fetching anything, answer three questions from the product page:

1. **What is this product?** Its name as the brand writes it, and the category the brand puts it in.
2. **What type of thing is it?** This decides which dimensions you document. Broad types: something consumed (food, drink, supplement, personal care, cosmetics), something worn (apparel, footwear, accessories, textiles), a hard good (device, tool, furniture, equipment, packaged object), software or a service (plans, subscriptions, memberships, courses), or a hybrid (a device with a subscription, a kit with consumables). Many products are more than one type — document every type that applies.
3. **Is it one product or several?** One product page = one file, even when it has many variants. Separate product pages = separate files, even when the products are close siblings. Bundles get their own file that lists what's in them and links to each component's file. When the brand sells the same thing under one page with variants that differ in composition (not just size or color), note that in the variants section rather than splitting the file.

File name: the product's name, lowercased, hyphenated, saved to `brand/products/` for the brand itself, or the `product/` folder of whichever competitor it belongs to (`brand/products/` for the brand itself, `1. research/competitors/<slug>/product/` for a competitor).

## Step 2: Choose the dimensions

Every product gets the **universal** dimensions. Add the **type-specific** ones that apply. Drop anything the product genuinely has no version of — an empty heading is worse than a missing one.

**Universal — always**
- Identity: brand, product name, category as stated, form or format, product page URL
- Variants and SKUs: every option the buyer can choose — sizes, colors, flavors, strengths, counts, configurations, tiers — with the SKU or option name the brand uses, and any variant-specific price
- What's included: what arrives, how many, in what packaging; what's sold separately
- Pricing and purchase options: one-time price, subscription price and cadence, bundle pricing, tiered pricing, currency, date observed; discounts only if displayed on the page
- Channel: where it's sold (own site, marketplaces, retailers) as stated or observed
- Directions or usage as stated: how the brand says to use it, verbatim
- Guarantee, returns, shipping, warranty: as stated on the product page or a linked policy page
- Certifications, standards, and testing: only what is shown on the page or label
- Customizations: personalization, engraving, made-to-order options, configurable elements
- Stated positioning: the headline, the hero bullets, comparison tables, and the claims the brand leads with — quoted, so the strategist sees exactly how the brand frames it without you paraphrasing it into a fact
- Other stated facts: origin, manufacturing, sourcing, packaging, company facts stated on the product page
- Gaps and caveats: what the source does not disclose that a strategist would want
- Source: every URL and image you read, and the date

**Something consumed**
- Serving size and servings per container
- Active or functional components per serving, in label order, with amounts and units exactly as printed
- Full ingredient list, verbatim, in label order
- Allergen statements, dietary statements (as stated), storage instructions
- Nutrition or supplement panel values if present

**Something worn**
- Materials and fiber composition with percentages, per component if the label splits them (shell, lining, trim)
- Size range and the size chart itself (measurements, not just labels); fit description as stated; model measurements if given
- Colors and prints, by the brand's names
- Construction details the brand calls out: seams, closures, pockets, hardware, weight or thickness of fabric
- Care instructions, verbatim
- Country of manufacture, sourcing or production statements

**A hard good**
- Dimensions and weight, per variant if they differ
- Materials and finishes
- Capacity, output, power, battery, connectivity, compatibility — whichever apply
- What's in the box
- Setup or assembly requirements, replacement parts, consumables it needs
- Warranty terms
- Safety notices and regulatory marks shown

**Software or a service**
- Plans or tiers, and what each includes — feature by feature, as the pricing page lists them
- Pricing model: per seat, per usage, flat, annual vs monthly, free tier, trial terms
- Limits and quotas per tier
- Platforms and integrations listed
- Onboarding, support, and contract terms as stated
- Security, privacy, and compliance statements as stated

**Hybrids** get every applicable list. When a dimension appears in two lists, document it once.

## Step 3: Gather the sources

Read, in this order, stopping when the dimensions are filled:

1. The product page in full — including collapsed accordions, tabs, "details" and "specs" panels, size charts, FAQs, and comparison tables. These hide most of the facts.
2. Images on the product page that show the label, spec panel, care tag, or packaging. Read the text in them; the label is often more complete than the page copy.
3. Linked pages: ingredients or materials pages, size guides, shipping/returns/warranty policies, a pricing page for software.
4. Retailer listings that transcribe the label or spec sheet, when the brand's own page omits amounts or measurements. Record that the retailer was the source for those fields.
5. Anything the person handed you: a spec sheet, a label photo, a line sheet.

Transcribe in the order the source uses. Keep units. Do not total, convert, round, or reorder. If two sources disagree, record both and flag the conflict — the brand's own page wins for pricing and positioning; the label wins for composition.

## Step 4: Write the file

Structure the document top to bottom:

- **Title** — brand and product name, with a one-line italic stamp: facts-only profile, brand, date generated.
- **Standing note** — one blockquote stating that every field reflects what the brand or a label-transcribing retailer states, nothing is interpreted or reframed as a benefit, and it is the factual input layer for messaging work.
- **Identity** — a two-column table.
- **The dimensions you chose in Step 2**, each as its own heading, using tables for anything with amounts or specs and blockquotes for anything transcribed verbatim (ingredient lists, directions, care instructions, claims).
- **Stated positioning** — quoted, not paraphrased.
- **Gaps and caveats** — bulleted, specific: which amounts are undisclosed, which specs are missing, which claims have no stated basis on the page.
- **Source** — URLs, images read, retailer listings used, and the date.
- **Footer** — a one-line italic reminder to verify every figure against physical packaging or the brand's own documentation before using it in an advertising claim.

## Step 5: Check before saving

- Every number, amount, and measurement traces to a source you read. Nothing is estimated.
- No benefit language of your own anywhere. The brand's benefit claims appear only inside quotation marks under stated positioning or other stated facts.
- No empty sections and no placeholder text.
- Variants are complete — if the page shows a size or color selector, every option is listed.
- The gaps section names what's missing rather than leaving the reader to notice.
- The file name matches the product name and it is in `brand/products/` for our brand, or the right competitor's `product/` folder.

When the product has an unusually large variant set or a very long ingredient or feature list, completeness still wins over brevity — the strategist needs the whole thing once, here, rather than going back to the site.
