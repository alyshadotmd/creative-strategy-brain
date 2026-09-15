---
name: brain-setup
description: Onboards a new brand into the brain, with the LLM doing the work. Use this the first time a brand is set up in a brain, or when a person says "set up the brain", "onboard this brand", "get the brain ready for [brand]", or the research folders are still empty. Runs the setup sequence in order — verify the folder structure, build the brand kit and assets, confirm app-generation is unblocked, document the brand's own products, collect every customer review, then identify at least three competitors and build a brand overview, product profiles, and review exports for each — and ends with a status report of what is filled and what is still missing. Minimum input is a website URL; everything else it asks for or finds.
---

# Brain Setup

One brain holds one brand. This skill takes an empty brain and a website URL and fills the folders that every downstream skill depends on. The person should have to do very little: answer a few questions, drop in files they already have, approve a list of competitors. Everything else is fetched, extracted, and saved by you.

**Finish the whole sequence.** Work the steps in order, but run independent fetches in parallel where you can, and never wait on a person for something you can find yourself. Every deliverable in the steps below is required, not optional. Record a gap only when the data genuinely cannot be obtained — it is not public, it sits behind a login, or the person has to supply it. The amount of work already done in a session is never a reason to stop early.

**Standing rules for the whole run**
- Never invent data. A review, a price, an ingredient, a competitor claim — if you did not read it from a source, it does not go in a file. Gaps are recorded as gaps.
- Only collect what is publicly visible or what the person gives you. Do not bypass logins, paywalls, or rate limits.
- Everything is brand-agnostic. This skill and the skills it calls contain no brand-specific content; every specific comes from the brand in front of you.
- Save as you go. A file in the brain is progress; a plan in the chat is not.

---

## What you need from the person

Ask for all of this in one message at the start, then proceed with whatever comes back. Skip anything already answered.

1. **Website URL** (required — the only thing you cannot work without)
2. **Brand assets they already have** — brand book PDF, logo pack, font files, product shots (optional; improves the brand kit)
3. **Where their reviews live** — a review platform name (and access if they can give it), a CSV export, or "just pull them from the site"
4. **Who they consider their competitors** — names or URLs, or "not sure" (you'll research candidates)
5. **Which products matter most** — if the catalog is large, which ones to prioritize for review collection

While you wait for the answers, start Step 0 and Step 1 — they need only the URL.

---

## Step 0: Verify the folder structure

Confirm the brain matches the map below. Create anything missing. Do not create extra top-level folders.

```
1. research/
  brand/                      brand-overview.md for the brand itself
  product/                    one <product-name>.md per product
  customer/
    reviews/                  one <product-name>-reviews.csv per product (+ raw export)
    ad comments/              exported ad comments, if any
  competitors/
    <competitor-slug>/        one folder per competitor (rename the competitor-1/2/3 placeholders)
      brand/                  brand-overview.md
      product/                one <product-name>.md per product you pulled reviews for
      customer/               one <product-name>-reviews.csv per product (+ raw export)
  creators/ · skills/
2. ideate/  ·  3. create/  ·  4. analyze/
assets/
  fonts/ · logos/ · images/product/ · images/lifestyle/ · images/illustrations/
  brand-kit-<brand>.md
skills/ · integrations/ · strategy/ · team/
```

Read `README.md` at the brain root if anything is unclear about where something belongs.

## Step 1: Build the brand kit and harvest assets

Run the `brand-kit` skill (`skills/brand-kit/SKILL.md`) with the URL and any assets the person provided. It writes `assets/brand-kit-<brand>.md` and fills the `assets/` folders with every font, logo, product image, lifestyle image, and illustration that meets its quality bar.

Do not move on until the kit file exists. Note which asset categories it reported as complete and which have gaps — that feeds Step 2 and the final report.

## Step 2: Confirm app-generation is unblocked

`app-generation` (`skills/app-generation/SKILL.md`) needs three things before it can build anything on-brand: the kit file, at least the display and body font files in `assets/fonts/`, and at least a primary logo in `assets/logos/`. Check all three exist. If they do, mark app-generation **ready** in the status report. If not, mark it **blocked** and name exactly which file is missing and where it would come from — do not build an app during setup, and do not substitute fonts or logos to force it through.

## Step 3: Document the brand's own products and brand

**Brand overview → `1. research/brand/brand-overview.md`**
Run the `brand-overview` skill (`1. research/skills/brand-overview/SKILL.md`) in its own-brand mode. It pulls from the site, the brand kit, and anything the person said.

**Product profiles → `1. research/product/<product-name>.md`, one per product**
Run the `product-info` skill (`1. research/skills/product-info/SKILL.md`) for each product. It decides which dimensions to document from the product type and writes facts only — what the product is, contains, is made of, comes in, costs, and how it's used, as the brand states it. If the catalog is large, do the products the person prioritized first and list the rest as not yet profiled.

File names are the product's name, lowercased, hyphenated. If the brand has one product, there is one file.

## Step 4: Collect the brand's customer reviews

**Goal:** every review the brand has, in `1. research/customer/reviews/`, one normalized CSV per product.

**If the brand has no reviews yet** (pre-launch, or the person says so), skip straight to Step 5 — the competitors' customers are the voice of customer until the brand has its own.

Otherwise work the intake paths in this order, stopping at the first that yields the full review set:

1. **Platform integration.** If a review platform tool is connected in this environment (Judge.me, Okendo, Yotpo, Junip, Stamped, Loox, Shopify's native reviews, or another), use it to export all reviews for every product.
2. **A file the person provides.** A CSV or spreadsheet export dropped into the chat. Read the whole file before doing anything with it. Save the raw file alongside the normalized one.
3. **Pull from the site.** Identify the review widget on a product page (the platform is usually visible in the page source or network requests). Most platforms expose a public, paginated endpoint that the widget itself calls — find it, page through it to the end, and collect every review for every product. If there is no endpoint, parse the rendered review section page by page. Record the platform and endpoint pattern in the brand overview so nobody has to rediscover it.

**Normalize every source into the standard schema** — one CSV per product, named `<product-name>-reviews.csv`:

| Column | Content |
|---|---|
| `date` | ISO date the review was posted |
| `rating` | Integer 1–5 |
| `title` | Review title, empty if none |
| `body` | Full review text, verbatim, untrimmed |
| `reviewer` | Display name as shown, or empty |
| `product` | Product name as the brand names it |
| `variant` | Size / flavor / option if provided, else empty |
| `verified` | `true` / `false` / empty if the platform doesn't say |
| `incentivized` | `true` if flagged as rewarded/incentivized, else empty |
| `source` | Platform or method (`judge.me`, `okendo`, `csv-upload`, `site-scrape`, …) |
| `source_url` | The product or review page the review came from |

Keep the raw export next to it as `<product-name>-reviews-raw.<ext>`. Never edit, filter, or "clean" review text — downstream skills need the customer's exact words, including the negative reviews.

**Completeness check:** compare your row count to the review count the site displays for each product. If they don't match, page again or note the shortfall in the status report. A partial pull labeled as complete is worse than a gap.

**Ad comments** (optional): if the person can export comments from their ads, save them to `1. research/customer/ad comments/` in the same schema where it fits (`body`, `date`, `source`, `source_url`; leave the rest empty).

## Step 5: Identify and document competitors

**Minimum: three competitors.** More is fine if the person names them.

**Identify.** If the person named competitors, use those. If not, research candidates: brands selling a comparable product to a comparable customer at a comparable price point, found through the brand's own category terms, marketplace "customers also bought" patterns, and search. Put a shortlist of five to seven in front of the person with one line each on why they qualify, and ask them to confirm, remove, or add. Do not proceed past three unconfirmed guesses — a wrong competitor poisons the research folder.

**For each confirmed competitor**, rename a placeholder folder (`competitor-1`, `-2`, `-3`) to the brand's slug — lowercase, hyphenated — and create more if there are more than three. Then fill it:

1. **`brand/brand-overview.md`** — run the `brand-overview` skill in competitor mode. Who they are, full product range, the product(s) that compete directly with ours, their reviews platform and review base, paid-social posture if the tools to see it are connected, and where they sit relative to our brand.
2. **`product/<product-name>.md`** — run the `product-info` skill for each product you are pulling reviews for. Same standard as Step 3. Profile the products that compete with ours, not the competitor's entire catalog; list the rest of their range in the brand overview.
3. **`customer/<product-name>-reviews.csv`** — same intake paths and same schema as Step 4, pulled from the competitor's site. Same completeness check. Same raw file alongside.

Run competitors in parallel where you can — three sites' worth of fetching is the largest step.

## Step 6: Status report

End the run with one report, saved to the brain root as `SETUP-STATUS.md` and summarized in the chat. For each item: **filled**, **partial** (with what's missing and the count), or **missing** (with where it would come from). Cover:

- Brand kit: exists / asset categories complete vs gaps
- App-generation: ready / blocked on [file]
- Brand overview and product profiles: which products are profiled, which aren't
- Customer reviews: per product, rows collected vs count shown on site; source used
- Competitors: confirmed list; per competitor, overview / products / reviews status
- Anything you could not do and why (no public review endpoint, platform requires login, site blocked fetching, person still owes a file)

Close with the next step: run `review-audit` (`1. research/skills/review-audit/SKILL.md`) on the brand's reviews — or on the competitors' if the brand has none — to produce the voice-of-customer the `persona-messaging-matrix` app and the `creative-engine` need.

---

## Completeness

There is no step budget and no session budget. The setup is done when every deliverable in Steps 0–6 exists in the brain, or is recorded as a gap with the reason it could not be obtained from the source. A large step is not a reason to sample it: many products, many competitors, or high review volume means the step takes longer, not that it gets trimmed. The status report names what is genuinely missing from the sources — never what was cut to reach an ending.
