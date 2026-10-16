---
name: review-audit
description: Analyzes positive, useful customer reviews to surface deep customer insights for ad ideation. Use this whenever someone provides customer reviews and wants to understand their customers better, extract VOC (voice of customer), find ad-ready language, or build messaging strategy from real customer language. Trigger for any request involving "analyze these reviews," "what are customers saying," "VOC analysis," or any variation of wanting to mine customer reviews for creative strategy inputs. Works on the brand's own reviews or a competitor's and produces one audit per product: eight buckets (two layers of pains, desires, failed solutions, objections, purchase triggers, transformations, where it fits in their day, standout language), every theme counted.
stage: 1-research
---

# Review Audit

This system mines customer reviews to extract the insights that make ad copy actually work: the real language, real pain, real moments, and real transformations that customers experienced. The output feeds directly into creative strategy and hook writing.

**The goal is to find the raw material for ads, not to summarize reviews.**

**This audit studies the customers the product worked for.** Everything it extracts describes their journey to the product: the life they had before it, what they tried instead, what made them hesitate, what made them buy, and what changed after. The reviewed product shows up in that story only as the solution. Complaints about the reviewed product belong to a separate negative review audit.

---

## What You Need Before Starting

**The reviews.** Use the reviews the person gives you (a CSV, an upload, or a paste) and say which source you used. When the reviews come as a CSV, a `product` column does the grouping in Step 2 and an `incentivized` column helps in Step 1.

**Whose reviews these are changes what they can do.** The brand's own reviews can speak for the brand. A competitor's reviews teach the category's language and its customers' moments; they are presented only as the competitor's customers, never as this brand's testimonials or results. Carry that label through every output.

---

## Step 1: Prepare the Reviews and Ask the One Question

**Remove duplicates.** When the same review appears twice (same reviewer and same text), keep one copy. When one copy was pulled from the review platform and the other came from an uploaded file, keep the platform copy.

**Count.** Count the reviews left (rows in a spreadsheet, discrete reviews in pasted text). Record the count and the number of duplicates removed for the output header.

**Incentivized reviews: the one question.** Check for incentivized reviews (the `incentivized` column, or language like "received this product for free" or "in exchange for an honest review"). When there are any, tell the person how many there are and what share of the set that is, then ask how to handle them:
1. **Leave them out:** only customers who chose to buy are analyzed.
2. **Use them, flagged:** they count toward patterns, and every count and quote that includes them is marked as incentivized.
3. **Use them like any other review:** no flag.

Wait for their answer, then follow it through every step. Record the choice and the incentivized share in the output header. This is the only question the audit asks; once it's answered (or when there are no incentivized reviews), the audit runs start to finish.

---

## Step 2: Split by Product

When the reviews cover more than one product, sort them by product (using the `product` column when there is one). Every step after this runs separately for each product, with its own counts and its own full output. When which product a review belongs to is unclear, ask before going on. When every review is for one product, go straight to Step 3.

---

## Step 3: Score Review Quality (1–5)

Score every review for quality.

| Score | What it looks like |
|---|---|
| **1** | Garbage — 3 words or fewer, gibberish, or zero signal ("great product", "love it", "👍"). Any review of 3 words or fewer is a 1, and so is any review that says nothing about the person, their problem, how they use it, or what changed ("So worth the money", "Great product, highly recommend"). |
| **2** | Low signal — very short, vague, no specific detail or emotion |
| **3** | Moderate — mentions the product, some specificity, but no vivid detail or emotional depth |
| **4** | High quality — specific detail about their life, how they use it, or how it made them feel |
| **5** | Gold — long, emotional, vivid, paragraph-level detail; the customer was so moved they wrote an essay about it |

**What the score decides.** Every analyzed review (score 2 to 5) counts once toward the theme counts, whatever its score, so the counts reflect how many customers said something. The score decides three other things:
- **Who gets in:** score 1 reviews are discarded.
- **Where the depth comes from:** 4s and 5s are read in full first and give the summaries their detail; score 5 reviews are primary sources.
- **Where quotes come from:** reviews scored 3 to 5, picked for how vivid and specific the line is. A strong line in a 3 is as usable as one in a 5.

---

## Step 4: Filter

The analysis set is reviews that are both useful (score 2 to 5) and positive.

**Sentiment.** Keep every review that tells a positive story: the product worked for them in some way (it fixed a problem, became part of their routine, changed how they feel). Judge this from what the review says, with the star rating as the first clue: a 3-star review that reads happy stays.

Set aside a review only when it has no positive story, when it is all about a bad experience with the reviewed product (it didn't work, side effects, taste, broke, arrived damaged, regret, refund). Count these for the output header.

**Mixed reviews keep their positive half.** When a review tells a positive story and also complains about the product ("Fixed my dizziness, but the taste is so bad I'm not sure I'll reorder"), it stays in the analysis set and only its positive story goes into the buckets. Small gripes work the same way ("wish the bottle were bigger"). Count mixed reviews separately in the output header.

**Minimum: 50 analyzed reviews per product.** Count each product's reviews left after both filters. A product runs only when it has at least 50; that's what it takes to surface reliable patterns. A product under 50 gets a short note in the output with its counts (received, discarded as low quality, set aside as negative, remaining) and no audit, while the products that reached 50 still run in full. When no product reaches 50, tell the person the counts, explain the 50-review minimum, and stop there.

---

## Step 5: Read Every Review and Note What It Carries

Read every review in the analysis set, all of them, however many there are; large sets get read in chunks. For each review, write a short note: its review ID (or row number), and what it says for each bucket in Step 6, in a few words each. Leave a bucket empty when the review doesn't speak to it; an empty note is a true note, and a guessed one breaks the counts.

Write the notes to a file. Every count in the audit is taken from these notes, one review at a time, and every quote points back to the review it came from.

---

## Step 6: Extract Insights by Bucket

Within each bucket, group similar insights from the review notes into themes.

**How big a theme is: the ad decides.** Two insights are one theme when an ad would say the same thing about both; they are two themes when they'd make different ads. "Headaches" and "migraines" are one theme when customers describe the same experience; "can't sleep" and "wake up at 3am" are two when one is about falling asleep and the other about staying asleep. Name each theme in the customers' own words where possible. A review counts once per theme, and it can count toward several themes in the same bucket. When a grouping is a close call, name the call you made in the summary.

**Every theme the notes show, most common first.** List every theme in each bucket, with no minimum size and no maximum count, ordered by how many reviews carry it. For each theme:
- Name the theme
- Count how many reviews carry it (from the Step 5 notes) and what share of the product's analyzed reviews that is
- Write a 2–3 sentence summary of the pattern across those reviews
- Flag the strongest quotes for the swipe file, each tagged with its review ID

**The buckets run in the order the customer actually makes the decision:** pain surfaces → desire forms → other solutions fail → hesitation about this product → the trigger that finally makes them buy → the transformation after → where it settles into their day → the language worth stealing from all of it. Keep this order in the output; it mirrors the journey the ads will have to walk.

Quotes are pulled exactly as written.

---

### Bucket 1: Pain Points
*What problem were they experiencing before they found this product?*

A pain point is the problem in the customer's life that sent them looking, the thing the product went on to solve. It lives in the "before": the sleepless nights, the bloating, the 3pm crash. Only problems from before the product count here; a bad experience with the reviewed product is outside this audit.

**Pains come in two layers. Report them as two lists:**
- **Pains from the problem** — what the problem itself does to them, the symptoms and struggles that come with it (dizziness, brain fog, headaches, cramps, hangovers).
- **Pains from how they were solving it** — what made their old way of handling the problem hard (can't drink enough water, other options taste bad or have too much sugar, fitting it into a demanding job or schedule). This layer is about the difficulty; the specific products and habits they tried go in Bucket 3.

Both layers make ad angles: the first speaks to the problem, the second to why other solutions failed.

Look for: what exactly the pain was, how they describe it word for word, how long they'd had it, what their lived experience of it was, and how it affected their life or their reality — in literal, physical, and emotional ways.

**Pain origin.** For each pain theme, note the pain origin wherever the reviews reveal it: how they found out they had this pain in the first place, what triggered it, the moment of realization. Reviews won't always carry this, but when they do it's disproportionately valuable: the realization moment is the raw material for unaware-stage ad concepts, where the ad has to recreate the discovery of the problem itself.

---

### Bucket 2: Desires
*What did they want — badly — that they felt they couldn't have or were trying to achieve?*

Look for: the specific outcome, feeling, identity, or experience they were chasing; what motivated that desire specifically; and how it showed up in their life in the moment — the "man, I wish I could just do this / have this / be this / experience this" moments.

Desire often stands on its own, beyond the mirror image of the pain. Capture it wherever the review expresses wanting and aspiration in its own right.

---

### Bucket 3: Failed Solutions
*What did they try before that didn't work?*

Failed solutions are the other products, habits, and approaches they tried before this one. The reviewed product is the solution that worked; this bucket holds only what came before it.

Look for: what they tried to solve the pain or achieve the desire, how it showed up in their life, what specifically about it failed for them, and how they felt about that experience afterward — the frustration, the wasted money, the "nothing works for me" resignation.

Failed solutions are often the *cause* of objections ("I've been burned before"). The attempt itself goes here; the resulting hesitation about this product goes in Bucket 4.

---

### Bucket 4: Objections Before Purchasing
*What almost stopped them from buying this?*

An objection is the hesitation, concern, or skepticism the customer had before they bought: "I was skeptical but...", "I almost didn't because of the price...". It is a doubt the product went on to overcome. Only doubts from before buying count here; disappointment after buying belongs to the negative review audit.

Look for: skepticism they mention having had about this exact product or service, what caused them to put off buying, the hesitations they had before purchase, the questions they needed answered before they'd commit, price hesitation, disbelief that this would actually work, fear of wasting money again.

In positive reviews, objections are almost always mentioned in past tense — "I was skeptical but..." or "I almost didn't try it because..." These are gold for objection-handling ad copy.

---

### Bucket 5: Purchase Triggers
*What finally made them buy?*

This bucket captures one specific kind of trigger moment: the one that moves a customer from considering this product to buying it.

Look for: the specific moment, event, or realization that pushed them over the edge — the thing that resolved their objection or finally made them take action. It could be a life event (wedding, diagnosis, vacation), a recommendation (friend, doctor, TikTok), hitting a breaking point, or running out of patience with other solutions.

---

### Bucket 6: Transformations
*What changed for them after using the product?*

Look for: the specific result they experienced; whether the product solved the pain and delivered the desire; how the outcome differed from the failed solutions ("nothing else worked — this did"); how the change showed up physically, emotionally, and in the rest of their life; and — most importantly — how they describe the transformation in their own words: what specifically changed. The more specific and visceral, the better.

---

### Bucket 7: Where It Fits in Their Day
*When do they reach for it now?*

These are the moments after buying when customers reach for the product: in the morning coffee, at their desk at 2pm, in the gym bag, before going out. Each one is an ad-ready micro moment, a scene the ad can open on.

Look for: the time of day, the place, the routine it's attached to, who's around, and what they're doing right before or after.

---

### Bucket 8: Standout Language & Ad-Ready Phrases
*Exact language worth stealing for ads.*

This bucket works differently from the others. Instead of themes, it is a curated collection of the most vivid, emotionally charged, specific, and scroll-stopping phrases pulled from across all buckets: the lines that made you stop while reading, that work as written, that a copywriter would highlight and build an ad around. Pull every line that earns its place, however many that is.

Pull these verbatim. Tag each quote with the product, the bucket it exemplifies, and its review ID as you pull it (plus an incentivized mark when the person chose to use incentivized reviews flagged). These tags let downstream skills pull standout language by product and bucket, and trace any line back to its review.

What to look for:
- Words, slang, speech patterns, and inside jokes native to how this customer talks
- Unusually specific, visceral descriptions of the pain, the before and after, or the transformation
- Emotion put in a way you couldn't have written yourself
- Lines that could run as a hook or in an ad exactly as written

---

## Output Format

Produce a separate full output for each product. Every count is shown with its share of that product's analyzed reviews. Structure:

```
─────────────────────────────────────
PRODUCT / SERVICE: [Name]
Source: [own brand | competitor: <name>]
Reviews received: [X] | Duplicates removed: [X] | Analyzed: [X] | Discarded (score 1): [X] | Set aside as negative: [X] | Mixed (positive half kept): [X] | Incentivized: [X]% ([left out | used, flagged | used, not flagged])
─────────────────────────────────────

AT A GLANCE
Top pains from the problem: [theme (N, X%), theme (N, X%), theme (N, X%)]
Top pains from how they were solving it: [top 3]
Top desires: [top 3]
Top failed solutions: [top 3]
Top objections: [top 3]
Top purchase triggers: [top 3]
Top transformations: [top 3]
Top moments in their day: [top 3]

---

BUCKET 1: PAIN POINTS

Pains from the problem
[Theme Name] — [N] reviews ([X]%)
Summary: [2–3 sentences on the pattern]
Origin: [how customers realized they had this pain — only where the reviews show it]

Pains from how they were solving it
[Theme Name] — [N] reviews ([X]%)
Summary: [2–3 sentences on the pattern]

---

BUCKET 2: DESIRES

[Theme Name] — [N] reviews ([X]%)
Summary: [2–3 sentences on the pattern]

---

BUCKET 3: FAILED SOLUTIONS

[Theme Name] — [N] reviews ([X]%)
Summary: [2–3 sentences on the pattern]

---

BUCKET 4: OBJECTIONS BEFORE PURCHASING

[Theme Name] — [N] reviews ([X]%)
Summary: [2–3 sentences on the pattern]

---

BUCKET 5: PURCHASE TRIGGERS

[Theme Name] — [N] reviews ([X]%)
Summary: [2–3 sentences on the pattern]

---

BUCKET 6: TRANSFORMATIONS

[Theme Name] — [N] reviews ([X]%)
Summary: [2–3 sentences on the pattern]

---

BUCKET 7: WHERE IT FITS IN THEIR DAY

[Moment] — [N] reviews ([X]%)
Summary: [2–3 sentences on the moment]

---

BUCKET 8: STANDOUT LANGUAGE & AD-READY PHRASES

"[Exact quote]" — [product · bucket · review ID]
"[Exact quote]" — [product · bucket · review ID]
"[Exact quote]" — [product · bucket · review ID]
[etc.]

─────────────────────────────────────
```

All word-for-word quotes live in Bucket 8. Buckets 1–7 hold clean summaries, and the swipe file is the dedicated place for raw language.

---

## Step 7: Save to the Brain

The audit is finished once it is in the brain. Save each file next to the reviews it came from:

- Own brand: `1. research/customer/review-audit-<product-name>.md` and `1. research/customer/review-notes-<product-name>.md`
- Competitor: `1. research/competitors/<slug>/customer/review-audit-<product-name>.md` and `1. research/competitors/<slug>/customer/review-notes-<product-name>.md`

The review notes let any count or quote be traced back to its review.

Add a short header to each file naming the product, the source (own brand or which competitor), the review counts behind it, and the date.

Personas come from `persona-finder` (`1. research/skills/persona-finder/SKILL.md`), which runs on the same reviews.

---

## How This Feeds the Rest of the Stack

- **Pain Points and Pain Origins → `creative-engine` Step 1** — pain themes are the anchor candidates; pain origins are the raw material for Unaware-stage trigger moments, where the ad recreates the discovery of the problem
- **Desires → `creative-engine` Step 1 and `2. ideate/hooks/`** — the desire side of the anchor, and the language for aspirational openers
- **Failed Solutions and Objections → `creative-engine` Step 5** — messaging angles that answer what a customer already tried and what they're afraid of; objection language for handling hesitation in copy
- **Purchase Triggers → `creative-engine` Step 4** — the buying moments the engine anchors concepts on
- **Transformations → `creative-engine` Step 6 and `2. ideate/hooks/`** — the outcome language the offer is written in, and social-proof openers
- **Where It Fits in Their Day → `creative-engine` Step 4 and `2. ideate/hooks/`** — ad-ready micro moments, scenes an ad can open on
- **Standout Language → `2. ideate/hooks/`** — native voice patterns pulled from real customers, tagged by product and bucket

---

## Notes on Quality

- Every count and quote traces back to a review ID in the review notes
- Every theme comes from what the reviews actually say; when a product's reviews carry only a few clear patterns, report those few and say the set is thin
