---
name: review-audit
description: Analyzes customer reviews to surface deep customer insights for ad ideation. Use this whenever a user provides customer reviews and wants to understand their customers better, extract VOC (voice of customer), find ad-ready language, or build messaging strategy from real customer language. Trigger for any request involving "analyze these reviews," "what are customers saying," "VOC analysis," or any variation of wanting to mine customer reviews for creative strategy inputs. Reads the review CSVs already in the brain (the brand's own or a competitor's), writes the audit back next to them, and writes one file per persona — each carrying its trigger moments — so persona-messaging-matrix and creative-engine can use them.
stage: 1-research
---

# Review Audit

This system mines customer reviews to extract the insights that make ad copy actually work: the real language, real pain, real moments, and real transformations that customers experienced. The output feeds directly into creative strategy and hook writing.

**The goal is not to summarize reviews. The goal is to find the raw material for ads.**

---

## What You Need Before Starting

**Where the reviews come from.** Read them from the brain, not from a paste, whenever they exist there:
- The brand's own reviews: `1. research/customer/reviews/<product-name>-reviews.csv`
- A competitor's reviews: `1. research/competitors/<slug>/customer/<product-name>-reviews.csv`

These CSVs use the standard schema written by `brain-setup` (`date, rating, title, body, reviewer, product, variant, verified, incentivized, source, source_url`). The `product` column does the grouping in Step 2; the `incentivized` column matters in Step 3. If the person pastes or uploads reviews instead, use those, but say which source you used.

**Whose reviews these are changes what they can do.** The brand's own reviews can speak for the brand. A competitor's reviews teach the category's language and its customers' moments; they can never be presented as this brand's testimonials or results. Carry that label through every output.

If multiple products are present in the review set, identify them before beginning. All output is separated by product. If product attribution is ambiguous, ask before proceeding.

---

## Step 1: Count the Reviews — Hard Gate

Count the total number of reviews provided (rows in a spreadsheet, discrete reviews in pasted text) before doing anything else.

**If the total is fewer than 100 reviews, do not run this audit.** Tell the user how many reviews were provided, explain that this analysis requires a minimum of 100 reviews to surface reliable patterns, and stop. Do not produce a partial audit.

If the total is 100 or more, record the count and proceed.

---

## Step 2: Group by Product

If the brand sells multiple products, sort all reviews by product first. Every subsequent step runs separately per product.

Record the review count per product — this determines whether that product qualifies for persona identification in Step 6 (100+ reviews required).

If all reviews are for a single product, skip grouping and proceed.

---

## Step 3: Score Review Quality (1–5)

Before analysis, score every review for quality. This determines what gets analyzed and what gets discarded.

| Score | What it looks like |
|---|---|
| **1** | Garbage — gibberish, swear words, 2–3 meaningless words, zero signal ("great product", "love it", "👍") |
| **2** | Low signal — very short, vague, no specific detail or emotion |
| **3** | Moderate — mentions the product, some specificity, but no vivid detail or emotional depth |
| **4** | High quality — specific, describes a real experience, references a before/after or a feeling |
| **5** | Gold — long, emotional, vivid, paragraph-level detail; the customer was so moved they wrote an essay about it |

**Score 5 reviews are the priority.** They contain the most usable language and the deepest insight.

**Incentivized reviews.** Where the `incentivized` column (or "received free product" language) flags a review, keep it for pattern confirmation but do not pull quotes from it and do not let it drive theme frequency. Report the incentivized share per product in the output header. A product whose reviews are nearly all incentivized has a thin signal — say so.

---

## Step 4: Filter

Discard all reviews scored **1**. Do not include them in analysis.

Analyze scores **2–5**, with emphasis on 4s and 5s. Low-scoring reviews (2–3) can contribute to pattern identification but should not be the source of pulled quotes.

---

## Step 5: Extract Insights by Bucket

Run this analysis separately for each product. Within each bucket, group similar insights together and write a brief summary of the pattern. Then pull the best word-for-word quotes that exemplify it.

**The buckets run in the order the customer actually makes the decision:** pain surfaces → desire forms → other solutions fail → hesitation about this product → the trigger that finally makes them buy → the transformation after → the language worth stealing from all of it. Keep this order in the output — it mirrors the journey the ads will have to walk.

Do not editorialize the quotes. Pull them exactly as written.

---

### Bucket 1: Pain Points
*What problem were they experiencing before they found this product?*

Look for: what exactly the pain was, how they describe it word for word, how long they'd had it, what their lived experience of it was, and how it affected their life or their reality — in literal, physical, and emotional ways.

**Also capture the pain origin wherever the reviews reveal it: how did they find out they had this pain point in the first place?** What triggered the pain? What was the moment of realization? Reviews won't always carry this, but when they do it's disproportionately valuable — the realization moment is the raw material for unaware-stage ad concepts, where the ad has to recreate the discovery of the problem itself.

For each pain theme identified:
- Name the theme
- Write a 2–3 sentence summary of the pattern across reviews
- Note the pain origin where the reviews reveal it
- Flag the strongest quotes for the swipe file

---

### Bucket 2: Desires
*What did they want — badly — that they felt they couldn't have or were trying to achieve?*

Look for: the specific outcome, feeling, identity, or experience they were chasing; what motivated that desire specifically; and how it showed up in their life in the moment — the "man, I wish I could just do this / have this / be this / experience this" moments.

Desire is not always the mirror image of the pain. Capture it where the review expresses wanting and aspiration in its own right, not just problem and relief.

For each desire theme identified:
- Name the theme
- Write a 2–3 sentence summary of the pattern
- Flag the strongest quotes for the swipe file

---

### Bucket 3: Failed Solutions
*What did they try before that didn't work?*

Look for: what they tried to solve the pain or achieve the desire, how it showed up in their life, what specifically about it failed for them, and how they felt about that experience afterward — the frustration, the wasted money, the "nothing works for me" resignation.

Note: failed solutions are often the *cause* of objections ("I've been burned before"). File the attempt itself here; file the resulting hesitation about this product in Bucket 4.

For each failed-solution theme identified:
- Name the theme
- Write a 2–3 sentence summary of the pattern
- Flag the strongest quotes for the swipe file

---

### Bucket 4: Objections Before Purchasing
*What almost stopped them from buying this?*

Look for: skepticism they mention having had about this exact product or service, what caused them to put off buying, the hesitations they had before purchase, the questions they needed answered before they'd commit, price hesitation, disbelief that this would actually work, fear of wasting money again.

Note: In positive reviews, objections are almost always mentioned in past tense — "I was skeptical but..." or "I almost didn't try it because..." These are gold for objection-handling ad copy.

For each objection theme identified:
- Name the theme
- Write a 2–3 sentence summary of the pattern
- Flag the strongest quotes for the swipe file

---

### Bucket 5: Purchase Triggers
*What finally made them buy?*

This bucket captures one specific kind of trigger moment: the one that moves a customer from considering this product to buying it. The wider set of trigger moments — the ones that move a person from not knowing they have a problem, to looking for a solution, to considering this product — is captured per persona in Step 6.

Look for: the specific moment, event, or realization that pushed them over the edge — the thing that resolved their objection or finally made them take action. It could be a life event (wedding, diagnosis, vacation), a recommendation (friend, doctor, TikTok), hitting a breaking point, or running out of patience with other solutions.

For each purchase-trigger theme identified:
- Name the theme
- Write a 2–3 sentence summary of the pattern
- Flag the strongest quotes for the swipe file

---

### Bucket 6: Transformations
*What changed for them after using the product?*

Look for: the specific result they experienced; whether the product solved the pain and delivered the desire; how the outcome differed from the failed solutions ("nothing else worked — this did"); how the change showed up physically, emotionally, and in the rest of their life; and — most importantly — how they describe the transformation in their own words: what specifically changed. The more specific and visceral, the better.

For each transformation theme identified:
- Name the theme
- Write a 2–3 sentence summary of the pattern
- Flag the strongest quotes for the swipe file

---

### Bucket 7: Standout Language & Ad-Ready Phrases
*Exact language worth stealing for ads.*

This bucket is different from the others. It is not organized by theme — it is a curated collection of the most vivid, emotionally charged, specific, and scroll-stopping phrases pulled from across all buckets. These are the lines that made you stop while reading. The ones that don't need to be rewritten. The ones a copywriter would highlight and build an ad around.

Pull these verbatim. Tag each quote with the product and the bucket it exemplifies as you pull it; once the Step 6 personas exist, add a persona tag wherever one clearly owns the quote. These tags are what let downstream skills pull standout language per persona.

What to look for:
- Terms, phrases, speech patterns, slang, and inside jokes native to how this customer talks
- Unusually specific descriptions of pain or transformation
- Phrases that capture an emotion in a way you couldn't have written yourself
- Before/after language that is visceral and concrete
- Lines that could work as a hook with zero editing
- Lines so unique, so highly emotional, or said so clearly or so differently that they could be taken directly from the review and used in an ad as-is
- Anything that made you feel something while reading it

---

## Step 6: Build Customer Personas

**Only for products with 100 or more reviews.** If a product falls below this threshold, skip this step for that product and note it in the output.

For each qualifying product, identify **3–5 distinct customer personas** that emerge from the reviews — so it's clear exactly which personas exist within each product. Personas are clusters of who is buying, why they bought, and what changed for them. They must be grounded in patterns actually present in the reviews. Do not invent personas the reviews don't support — if only 3 genuinely exist, present 3; never pad to 5.

For each persona, define:

- **Persona name** — a short, evocative label that names the person by their situation or stance, not by a demographic
- **Who they are** — 2–3 sentences on life context, situation, and identity signals visible in the reviews
- **Their pain** — the pain themes driving them, primary first (drawn from Bucket 1)
- **Their desire** — what they most wanted to have, be, or experience (theme(s) from Bucket 2, primary first)
- **Their failed solutions** — what they tried before that didn't work (theme(s) from Bucket 3)
- **Their objection** — what almost stopped them (theme(s) from Bucket 4, primary first)
- **Their purchase trigger** — what typically pushes them to buy (theme(s) from Bucket 5, primary first)
- **Their transformation** — the change they describe (theme(s) from Bucket 6, primary first)
- **How they talk** — distinctive vocabulary, tone, and phrases characteristic of this persona
- **Estimated share** — rough proportion of the product's reviews this persona represents

For every bucket-drawn field, use the theme names from Buckets 1–6 and list **every** theme that belongs to this persona, primary first — not just the primary. This persona↔theme mapping is what lets downstream skills compare personas against live ads and against each other.

### Then Go One Level Deeper: Trigger Moments

A persona describes the person. A trigger moment catches that person in the specific, concrete moment when the pain or desire stops being background and becomes something they act on — and moves them from one awareness stage to the next. It is an event, not a feeling: it has a where, a when, usually other people, and a consequence.

One persona usually carries several trigger moments, at different stages of awareness. The same person is a different buyer in a moment that names the problem for the first time than in a moment where a solution they tried has just failed them. Awareness lives at the trigger-moment level, not the persona level, and each moment is defined by the transition it drives:

- Unaware → Problem-Aware: the moment the problem gets named, noticed, or costs them something they can't ignore
- Problem-Aware → Solution-Aware: the moment they decide the problem is worth fixing and start looking
- Solution-Aware → Product-Aware: the moment a current approach fails them, or this product enters their view
- Product-Aware → Most-Aware: the moment the reason to act now appears (this is Bucket 5)

For each persona, extract **1–3 trigger moments** where the reviews carry enough situational detail. For each:

- **The moment** — named by circumstance, in one line, specific enough to shoot as a scene
- **Stage transition** — from which awareness stage to which
- **Life stage and role** — where they are in life, and who they're being in this moment
- **Circumstance** — the specific situation unfolding
- **Environment and context** — where they are, who's around, what else is happening
- **Emotional state** — what they're feeling, in their own words where possible
- **Needs vs. wants** — what they need functionally vs. what they want emotionally
- **Product intersection** — how the product enters, or could enter, this exact moment
- **Evidence** — the review lines that establish this moment

Trigger moments must come from the reviews. Stacking more attributes onto a persona does not make a trigger moment — the move is circumstance and event, not more qualifiers. The test: could you shoot it? If the review set doesn't carry this situational depth, say so plainly — that's a real finding. Never manufacture a moment.

---

## Output Format

Produce a separate full output for each product. Structure:

```
─────────────────────────────────────
PRODUCT / SERVICE: [Name]
Source: [own brand | competitor: <name>]
Reviews received: [X] | Analyzed: [X] | Discarded (score 1): [X] | Incentivized: [X]%
─────────────────────────────────────

BUCKET 1: PAIN POINTS

[Theme Name]
Summary: [2–3 sentences on the pattern]
Origin: [how customers realized they had this pain — only where the reviews show it]

[Theme Name]
Summary: [2–3 sentences on the pattern]

---

BUCKET 2: DESIRES

[Theme Name]
Summary: [2–3 sentences on the pattern]

---

BUCKET 3: FAILED SOLUTIONS

[Theme Name]
Summary: [2–3 sentences on the pattern]

---

BUCKET 4: OBJECTIONS BEFORE PURCHASING

[Theme Name]
Summary: [2–3 sentences on the pattern]

---

BUCKET 5: PURCHASE TRIGGERS

[Theme Name]
Summary: [2–3 sentences on the pattern]

---

BUCKET 6: TRANSFORMATIONS

[Theme Name]
Summary: [2–3 sentences on the pattern]

---

BUCKET 7: STANDOUT LANGUAGE & AD-READY PHRASES

"[Exact quote]" — [product · bucket · persona, where clear]
"[Exact quote]" — [product · bucket · persona, where clear]
"[Exact quote]" — [product · bucket · persona, where clear]
[etc.]

---

PERSONAS — [X] identified
(Only if this product/service has 100+ reviews. Otherwise: "Personas skipped — under 100 reviews.")

[Persona Name] — ~[X]% of reviews
Who: [2–3 sentences]
Pain: [Bucket 1 theme(s), primary first]
Desire: [Bucket 2 theme(s), primary first]
Failed solutions: [Bucket 3 theme(s)]
Objection: [Bucket 4 theme(s), primary first]
Purchase trigger: [Bucket 5 theme(s), primary first]
Transformation: [Bucket 6 theme(s), primary first]
Voice: [distinctive phrases and tone]

  Trigger moments:

  [The Moment — named by circumstance]
  Stage transition: [from → to]
  Life stage & role: [where they are in life / who they're being in this moment]
  Circumstance: [what's unfolding]
  Environment & context: [setting, who's around, what else is happening]
  Emotional state: [what they're feeling, in their words]
  Needs vs. wants: [functional need / emotional want]
  Product intersection: [how the product enters this exact moment]
  Evidence: "[review line that establishes this moment]"

  [Repeat for each trigger moment, 1–3 per persona — or: "Reviews don't carry enough situational depth for trigger moments."]

[Repeat for each persona, 3–5 total]

─────────────────────────────────────
```

All word-for-word quotes are collected in Bucket 7. Do not scatter quotes throughout buckets 1–6 — keep the summaries clean and let the swipe file be the dedicated place for raw language.

---

## Step 7: Save to the Brain

The audit is not finished until it is in the brain. Two kinds of file:

**The audit itself** — one file per product, saved next to the reviews it came from:
- Own brand: `1. research/customer/review-audit-<product-name>.md`
- Competitor: `1. research/competitors/<slug>/customer/review-audit-<product-name>.md`

**The personas** — one file per persona, in a `personas/` folder next to the audit:
- Own brand: `1. research/customer/personas/<persona-slug>.md`
- Competitor: `1. research/competitors/<slug>/customer/personas/<persona-slug>.md`

Each persona file stands alone: the persona block from the output (who, share, every bucket theme, voice) plus all of its trigger moments, plus a header naming the product, the source (own brand or which competitor), the review count behind it, and the date. `creative-engine` reads `1. research/customer/personas/` directly at its persona and trigger-moment steps, so a persona file must be usable without opening the audit.

`persona-messaging-matrix` consolidates personas across products and sources into the canonical set in `1. research/customer/personas/` when it runs; until then, the files this skill writes are the working set. When the brand has no reviews of its own, the competitor personas are the personas — say so in each file's header.

---

## How This Feeds the Rest of the Stack

- **Pain Points and Pain Origins → `creative-engine` Step 1** — pain themes are the anchor candidates; pain origins are the raw material for Unaware-stage trigger moments, where the ad recreates the discovery of the problem
- **Desires → `creative-engine` Step 1 and `2. ideate/hooks/`** — the desire side of the anchor, and the language for aspirational openers
- **Failed Solutions and Objections → `creative-engine` Step 5** — messaging angles that answer what a customer already tried and what they're afraid of; objection language for handling hesitation in copy
- **Purchase Triggers and per-persona Trigger Moments → `creative-engine` Step 4** — the moments the engine anchors concepts on, already tied to the stage transition they drive
- **Transformations → `creative-engine` Step 6 and `2. ideate/hooks/`** — the outcome language the offer is written in, and social-proof openers
- **Standout Language → `2. ideate/hooks/`** — native voice patterns pulled from real customers, tagged by product, bucket, and persona
- **Personas → `1. research/customer/personas/` → `creative-engine` Step 2 and `persona-messaging-matrix`** — grounded in real customers instead of assumptions
- **The whole audit → `persona-messaging-matrix`** — its data source when it exists, so the app is built on this rather than re-mining

---

## Notes on Quality

- Score 5 reviews should be read in full and treated as primary sources
- Score 2–3 reviews are useful for pattern confirmation but not quote sourcing
- If a single product's review set is small (under 20 reviews), note this — patterns may not be statistically meaningful but language is still usable
- If a product has too few quality reviews to surface meaningful patterns, flag it rather than manufacturing themes that aren't there
