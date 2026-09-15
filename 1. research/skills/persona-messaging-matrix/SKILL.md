---
name: persona-messaging-matrix
description: Turns the reviews in the brain into a custom-branded web app that maps who the brand's customers are and how to talk to them — an entry-point lens the reviews choose, two levels of who-and-why, an awareness breakdown, a messaging matrix, and personas. Uses the brand's own reviews when it has enough of them and competitor reviews when it doesn't. Decides from the reviews whether a multi-product brand needs one app, one app with product tabs, or separate apps. Use when someone says "build the persona app", "make the messaging matrix", "map our customers from the reviews", or after brain-setup and review-audit have run. Also writes the personas back to the brain so the creative strategy engine can use them.
---

# Persona & Messaging Matrix

Builds one kind of deliverable: a custom-branded, openable web app that shows who a brand's customers are and how to talk to them, built entirely from the reviews already in the brain. It also writes the analysis behind the app back into `1. research/` so the rest of the system can use it without opening the app.

Two rules sit above everything else:

1. **The reviews decide the lens and the words; the arc stays fixed.** The app always follows the same progression (Step 5). What the reviews decide is which top-level lens opens it, how the brand's products are grouped into apps and tabs, and every customer-facing line.
2. **Everything that is not a customer quote is written in very plain language.** Short, literal, no jargon, no cleverness. A section description says what the section is in one plain line, not what is clever about it.

This skill contains no brand-specific content. Every label, segment, and line comes from the reviews in front of you.

---

## Step 0: Resolve the inputs

| Input | Where it lives | If missing |
|---|---|---|
| Brand name and products | `1. research/brand/brand-overview.md`, `1. research/product/` | Run `brand-overview` / `product-info` |
| The brand's own reviews | `1. research/customer/reviews/` | Fall back to competitors (Step 1) |
| Competitor reviews | `1. research/competitors/<slug>/customer/` | Run `brain-setup` Step 5 |
| Review audits, if any | `1. research/customer/` and competitor folders — output of `review-audit` | Mine the reviews yourself (Step 3) |
| Brand look and feel | `assets/brand-kit-<brand>.md` and the `assets/` folders | Run `brand-kit` — do not invent a palette |
| Claims guardrails | Brand kit (04 — Voice, compliance swaps) and any claims doc | Ask; default to flagging every outcome claim |
| App build method | `skills/app-generation/SKILL.md` | Required — this skill does not define its own design |

If a required input is missing, say which and stop rather than inventing it.

## Step 1: Choose the review source

**The brand's own reviews come first.** They are the only reviews that can speak for the brand. Use them as the primary source whenever they clear the gate in Step 2.

**Competitor reviews are the fallback and the category voice.** When the brand is new, has too few reviews, or its reviews are almost all incentivized, build the app from the competitors' reviews. When both exist, the brand's own reviews carry the proof layer and the competitors' add depth to the category read.

Non-negotiable source rules:
- A competitor quote is never presented as this brand's claim, testimonial, or result. It teaches the language; it does not speak for the brand. Every competitor-sourced line is labeled as category voice.
- The brand's own reviews are usable as proof, but flag any that are not arm's-length: creator or affiliate seeds, employee or founder reviews, gifted units. Keep those out of the proof layer or label them.
- Outcome, health, performance, and numeric claims found in reviews are flagged for brand clearance before appearing anywhere. Shippable copy sticks to behavior a customer describes, not results a customer asserts.

## Step 2: Decide the scope — how many apps, how many tabs

Do not decide this from the catalog. Decide it from the reviews.

**First, mine themes across every in-scope review** (Step 3), tagging each review with the product it's about. Then look at how the top themes distribute across products and apply the rule:

| Tier | What the reviews show | Build |
|---|---|---|
| **One product, or one product in many variations** | Same buyer, same job; variants differ in flavor, size, strength, color, formulation | **One app.** Variants appear inside it as a lens or filter if the reviews split on them, not as tabs. |
| **A product family** | Same buyer and same job across products, but individual products carry their own themes | **One app with a tab per product** — a product earns its own tab only if it clears the review gate on its own *and* its top themes diverge from the family's. Otherwise it folds into the family view. |
| **Distinct product lines** | Different buyer, or a different job, so a review of one tells you little about a buyer of another | **Separate apps**, one per line, each scoped to its own reviews and its own competitors. A thin brand-level "who buys from us" summary can sit above them if wanted. |

The test between tiers is one question: does knowing what customers say about product A help you write to a buyer of product B? Yes throughout → one app. Yes, but each product also has its own story → tabs. No → separate apps.

Competitor reviews scope the same way. A competitor for one product line is not a competitor for another; keep their reviews inside the app for the line they compete with.

**Review gate.** Each app needs **100+ organic in-scope reviews** before you name category-level segments, and each product needs **100+ organic reviews of its own** before it gets a tab or product-specific personas. Under the gate, stop and say the base is too thin; offer to pull more (the brand's platform, more competitors) instead of guessing. State the scope decision and the review counts behind it in the app's method note.

## Step 3: Get the data — from review-audit first

If `review-audit` has already run on the in-scope reviews, **its output is the data source.** Its buckets (pains, pain origins, desires, failed solutions, objections, transformations, standout language), its personas, and its trigger moments feed the arc directly. Do not re-mine what the audit already did; do check that its scope matches yours and extend it where it doesn't.

If no audit exists for the in-scope reviews, mine them yourself:
- Tag each review by the themes it raises, in the customers' words. Let themes emerge; do not force a preset list.
- **Down-weight incentivized and seeded reviews.** Base shares on organic reviews; report incentivized share separately. A source that is nearly all incentivized is near-zero signal — and that fact becomes an authenticity insight, not data.
- Rank themes by frequency in organic reviews. The top one to three are the spine of the app.
- Separate what customers say (observed, quotable) from why you think it happens (inference). Only the first goes in customer-facing copy.
- Note per source: products reviewed, count, star average, organic vs incentivized.

## Step 4: Choose the entry-point lens

Find the single highest-level way the reviews naturally sort. Exactly one lens leads the app. Candidates the data might support: the customer's life stage, the core pains they keep raising, the primary use case or job the product is hired for, who buys versus who it's for, the perspective they bring, the trigger moment that sent them looking. Choose the lens the reviews split on most cleanly **and** that most changes how you'd talk to each group. This is the decision to get right; everything else hangs off it.

## Step 5: The fixed arc

Keep the same six beats every time. Only the entry-point lens and the labels change, because the reviews choose them. Do not reorder or drop beats.

**Optional preface — First-party proof.** If the brand has its own reviews, open with them as a short validation layer before Beat 1: count, average, the themes they confirm, a few verbatim quotes. Keep its numbers out of the category shares.

1. **Entry-point lens (level 1).** The top-level buckets, each named in plain language from the reviews, with share and a one-line description.
2. **Who (level 2).** Inside each bucket, who these customers actually are — sub-segments, roles, contexts — named from the reviews.
3. **Why (level 3).** Why they really buy — jobs, trigger moments, what they compare against, what they'd tried before — named from the reviews. A segment-by-theme grid with filled / half / empty markers works well here.
4. **Awareness.** How customers arrive: how aware they are of the problem and the solution when they show up, and what moves them from one stage to the next. Same grid style where useful.
5. **Messaging matrix.** One plain-language angle per segment, written in customer voice, echoing real review phrasing.
6. **Personas.** Two to five data-supported customer types with rough share, each pulling the arc together into a person you can picture — with their trigger moments, so the creative strategy engine can pick them up.

When the app has product tabs (Tier 2), every tab runs the full arc for its product; a "family" tab runs it across all of them.

## Step 6: Write the copy

- Customer-facing lines echo real reviews. Quote verbatim, keep quotes short, and label competitor-sourced quotes as category voice.
- Everything structural is one literal line. A section description says what the section is, never what's clever about it, and never uses a term the app hasn't introduced yet.
- Section headers do not repeat: a number-only eyebrow with the title beneath, not the same words twice.
- Skimmable: short blocks, plain nouns, no filler.

## Step 7: Build it with app-generation

Build the app by running `skills/app-generation/SKILL.md`. That skill owns the design: brand kit as the only source of truth, brand fonts, real logo file, palette as tokens, no stock design system. Requirements this app adds on top:

- Sticky tab navigation across the top, one tab per section (and per product, when the scope is Tier 2), with the active tab highlighted as you scroll.
- Content lives in one data file the app renders — `data/matrix.json` — so copy edits never touch code. The app reads the tab and section list from the data; it does not hard-code them.
- Reusable render blocks: card list, segment-by-theme grid, persona cards, quote wall, first-party proof.
- If the app will be served under a subpath, fonts and images must not depend on root-absolute paths — embed fonts or reference files relatively, as app-generation directs.
- Thumb test: legible at phone width, tabs reachable, nothing clipped.

```
data/matrix.json
{
  "meta": { "brand", "scope", "products": [...], "totalReviews", "organicCount",
            "sources": [ { "name", "count", "organic", "incentivizedPct", "note" } ],
            "methodNote": "<plain-language scope + weighting + tier decision>" },
  "tabs":     [ { "id", "num", "label", "product": null | "<product>" } ],
  "sections": [ { "id", "num", "title", "plainDescription",
                  "type": "cards" | "grid" | "personas" | "quotes" | "proof",
                  "product": null | "<product>", "items": [ ... ] } ],
  "firstParty": { "count", "avg", "themesConfirmed": [...], "quotes": [...] }   // only when own reviews exist
}
```

Verify the build before delivering. If the hosting environment offers private vs public visibility, ask once and recommend private — the app shows customer and brand strategy.

## Step 8: Write it back to the brain

The app and the markdown are two views of one source. **`matrix.json` is the source of truth and it lives in the brain**, not in the app. The app copies or reads it at build time; the markdown is generated from it. Nobody hand-edits the markdown — when something changes, change the JSON, regenerate the markdown, rebuild the app.

Folder: `1. research/customer/persona-messaging-matrix/` (for Tier 3, one subfolder per product line, named for the line). It contains:

- `matrix.json` — the data the app renders (schema in Step 7)
- `overview.md` — scope and tier decision with the review counts behind it, sources with organic vs incentivized split, the chosen lens and why, claim flags, where the app is
- `segments.md` — beats 1–3: the entry-point buckets with shares, the who and why levels beneath each, grids rendered as markdown tables
- `awareness.md` — beat 4
- `messaging-matrix.md` — beat 5, one angle per segment in customer voice, with the quotes it echoes

Every generated file opens with one line: generated from `matrix.json` on [date] — edit the JSON, not this file.

**Personas are the exception.** They go to `1. research/customer/personas/`, one file per persona, because that is where `creative-engine` reads them. Each persona file must stand alone — who they are, rough share, their trigger moments, awareness-stage tendencies, the language they use, and the messaging angle that fits — so the engine never has to open the matrix folder to use one. They are still generated from `matrix.json`; the persona section of the JSON is the source.

When the app has product tabs, the markdown mirrors it: a section per product inside each file, plus the family view.

Finally, note the app's location and the matrix folder in `1. research/brand/brand-overview.md`.

---

## QA checklist

- [ ] Source chosen correctly: own reviews when they clear the gate, competitors otherwise; every competitor quote labeled category voice
- [ ] Scope decided from mined themes, not the catalog; tier and counts stated in the method note
- [ ] 100+ organic in-scope reviews per app; 100+ per product before it gets a tab or product personas
- [ ] review-audit output used as the data source where it exists
- [ ] Shares based on organic reviews; incentivized share reported separately; non-arm's-length own reviews flagged
- [ ] Exactly one entry-point lens; fixed six-beat arc followed (plus first-party preface when own reviews exist)
- [ ] Customer-facing copy echoes real reviews; everything else is one plain line; no repeated headers
- [ ] Outcome, health, performance, and numeric claims flagged for clearance
- [ ] Built via app-generation from the brand kit; tabs and sections read from `matrix.json`
- [ ] Build verified; visibility chosen if the environment offers it
- [ ] `matrix.json` saved to `1. research/customer/persona-messaging-matrix/` with markdown generated from it; personas written to `1. research/customer/personas/`
