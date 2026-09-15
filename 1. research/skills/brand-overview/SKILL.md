---
name: brand-overview
description: Builds a brand overview document for either the brand the brain belongs to or one of its competitors — who they are, their full product range, the products that matter for our work, their review platform and review base, their paid-social posture where tools allow, and (for competitors) where they sit relative to our brand. Use this when brain-setup documents the brand or a competitor, when someone says "document this brand", "who is [competitor]", "build the competitor package", or when a new competitor enters the research folder. Output is one markdown file: `brand/brand-overview.md` for the brand itself, or `brand/brand-overview.md` inside the competitor's folder under `1. research/competitors/`.
---

# Brand Overview

One brand, one file, the picture a strategist needs before reading a single review or ad. It sits above the product profiles and the review exports in the same folder and tells the reader what the brand is, what it sells, which of its products we care about and why, where its customer voice lives, and — for a competitor — what it has already proven and where it has left room.

**Two modes.** For the brand the brain belongs to, the overview is a reference: what we are and what we say about ourselves. For a competitor, the overview is intelligence: the same facts, plus a section on how they sit against us. The skill decides which mode from where the file is being saved.

---

## Step 1: Establish the facts at the top

Open the file with a block of short factual lines — the things someone checks in five seconds:

- Primary domain, and the e-commerce or site platform if it's identifiable from the page source
- Social handles that exist
- Category, in plain terms
- Review platform, and the export method or endpoint pattern used to pull reviews, so nobody has to rediscover it
- Any identifiers from connected competitive-intelligence or ad-library tools, if those tools are present in this environment — otherwise omit the lines entirely
- Date captured

## Step 2: Who they are

Two to five sentences. What the brand sells and to whom, founders or founding story if the brand states it, how it positions itself, and how it appears to grow — creator-led, paid social, retail, community, wholesale. Pull from the about page, the homepage, press pages, and the brand kit if one exists. Distinguish what the brand states from what you observed; mark observations as such.

## Step 3: The full product range

A table of every product on the live site at capture, grouped the way the brand groups them (collections, lines, categories). Note the hero or flagship line if the site makes it obvious — placement, badges, homepage real estate. Mark which products have a profile in `product/` and reviews in `customer/`, so the reader knows what's documented and what's only listed.

## Step 4: The focus products

For each product that has been profiled and had reviews pulled — the ones that compete with ours, or ours themselves — a short block linking to its `product/<product-name>.md` and `customer/<product-name>-reviews.csv`, then:

- A one-line factual summary of what it is and what's in it or what it's made of
- Price and purchase options, as stated
- How the brand positions it on its own page: the headline, the hero bullets, any comparison table, quoted rather than paraphrased
- The review base: count, average rating, platform, and any flags the platform exposes (incentivized, seeded, verified share). If a review audit exists for this product, link it and name the personas it surfaced in one line — do not restate the audit.

## Step 5: Paid social posture

Only when a competitive-intelligence or ad-library tool is connected. Cover active ad volume and format mix, the formats and hooks that dominate, which products carry the spend, discounting behavior, and any segmentation pattern visible in the ads. Cite the tool and the date of the data. When no such tool is available, write one line saying the section was not captured and why — do not guess from a handful of ads you happened to see.

## Step 6: Position

**For a competitor — "Where this sits vs. our brand":** what this brand has already proven with paying customers that we can lean on; where they are strongest; where they are absent, generic, or under-invested; the specific lanes our brand can separate on; and the pattern of theirs most worth studying. Every point grounds in something observable in this folder or on their site — a page, a review pattern, an ad — not in opinion. Write it as a strategist's read, not a verdict.

**For our own brand — "Stated positioning":** who the brand says it's for and what it says makes it different, in its own words, with the pages those words came from. No evaluation.

## Step 7: Notes for research

Bullets for the next person or session: platform quirks discovered while pulling reviews, where the customer language is richest, tracking or follow status in connected tools, what could not be captured, and anything to watch for.

---

## Standards

- Facts are stated or observed and marked as which. Inferences are labeled as yours.
- Product facts live in the product profiles; the overview summarizes and links, it does not duplicate ingredient lists or spec tables.
- No empty sections. If a section doesn't apply or couldn't be captured, one line saying so, or drop it.
- Save to `brand/brand-overview.md` for the brand itself, or `1. research/competitors/<slug>/brand/brand-overview.md` for a competitor. Refresh the captured date whenever it's rebuilt.
