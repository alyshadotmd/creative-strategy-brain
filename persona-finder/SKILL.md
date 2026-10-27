---
name: persona-finder
description: Reads positive, useful customer reviews one customer at a time, finds every persona the reviews show (who the customer is), ordered by how often each appears, each with its roles, variations, overlaps, and trigger moments from its own members' reviews.
stage: 1-research
---

# Persona Finder

This skill reads customer reviews to find who the customers are: every persona the reviews show, biggest first, each with its roles, variations, overlaps and trigger moments. The personas feed `creative-engine` Step 2. (`review-audit` is its partner: it mines the same reviews for pains, desires and language.)

**The goal is not to summarize reviews. The goal is to find the people an ad can be made for.**

**This skill studies the customers the product worked for.** Everything it extracts describes their journey to the product: the life they had before it, what they tried instead, what made them hesitate, what made them buy, and what changed after. The reviewed product shows up in that story only as the solution. Complaints about the reviewed product belong to a separate negative review audit.

---

## What You Need Before Starting

**One brand, one product per run.** Each run covers one product from one brand. Similar products from different brands still draw different customers, so each brand's reviews get their own run. It works the same on any brand's reviews, yours or anyone else's. When the reviews cover several products, Step 2 splits them so each product gets its own run.

**Where the reviews come from.** Use the reviews the person gives you: a CSV, an upload, or a paste. Say which source you used. A CSV works best with these columns: `date, rating, title, body, reviewer, product, variant, verified, incentivized, source, source_url`. A `product` column does the grouping in Step 2, and an `incentivized` column flags reviews that were given in exchange for free product.

## Step 1: Count the Reviews

Count the reviews (rows in a spreadsheet, discrete reviews in pasted text) and record the number for the output header. Remove duplicates first: when the same review appears twice (same reviewer and same text), keep one copy. When one copy was pulled from the review platform and the other came from an uploaded file, keep the platform copy. Report how many duplicates were removed. Whether the audit runs is decided after filtering, in Step 4.

---

## Step 2: Group by Product

When the reviews cover more than one product, sort them by product (use the `product` column when there is one) and run every step that follows separately for each product, with its own counts and its own full output. When which product a review belongs to is unclear, ask before going on. When every review is for one product, go straight to Step 3.

---

## Step 3: Score Review Quality (1–5)

Before analysis, score every review for quality. This determines what gets analyzed and what gets discarded.

| Score | What it looks like |
|---|---|
| **1** | Garbage — 3 words or fewer, gibberish, or zero signal ("great product", "love it", "👍"). Any review of 3 words or fewer is a 1, and so is any review that says nothing about the person, their problem, how they use it, or what changed ("So worth the money", "Great product, highly recommend"). |
| **2** | Low signal — very short, vague, no specific detail or emotion |
| **3** | Moderate — mentions the product, some specificity, but no vivid detail or emotional depth |
| **4** | High quality — specific detail about their life, how they use it, or how it made them feel |
| **5** | Gold — long, emotional, vivid, paragraph-level detail; the customer was so moved they wrote an essay about it |

**Score 5 reviews are the priority.** They contain the most usable language and the deepest insight.

**Incentivized reviews: ask first.** Before scoring, check for incentivized reviews (the `incentivized` column, or language like "received this product for free" or "in exchange for an honest review"). When there are any, tell the person how many there are and what share of the set that is, then ask how to handle them:
1. **Leave them out:** only customers who chose to buy are analyzed.
2. **Use them, flagged:** they count toward patterns, and every count and quote that includes them is marked as incentivized.
3. **Use them like any other review:** no flag.

Wait for their answer, then follow it through every step. Record the choice and the incentivized share in the output header.

---

## Step 4: Filter

The analysis set is reviews that are both useful and positive.

**Quality.** Discard all reviews scored **1**. Analyze scores **2–5**, with emphasis on 4s and 5s. Every analyzed review counts toward patterns. Quotes come from reviews scored 3 to 5, picked for how vivid and specific the line is; a strong line in a 3 is as usable as one in a 5.

**Sentiment.** Keep every review that tells a positive story: the product worked for them in some way (it fixed a problem, became part of their routine, changed how they feel). Judge this from what the review says, with the star rating as the first clue: a 3-star review that reads happy stays.

Set aside a review only when it has no positive story, when it is all about a bad experience with the reviewed product (it didn't work, side effects, taste, broke, arrived damaged, regret, refund). Count these and report the number in the output header; they are the input for the negative review audit.

**Mixed reviews keep their positive half.** When a review tells a positive story and also complains about the product ("Fixed my dizziness, but the taste is so bad I'm not sure I'll reorder"), it stays in the analysis set and its customer record holds only the positive story. Small gripes work the same way ("wish the bottle were bigger"). Count mixed reviews separately in the output header, so the negative review audit can also pick up their complaint.

**Hard gate: 50 analyzed reviews.** Count the reviews left after both filters. The audit runs only when at least 50 remain. Under 50, tell the user the counts (received, discarded as low quality, set aside as negative, remaining), explain that the audit needs 50 positive, useful reviews to surface reliable patterns, and stop. Do not produce a partial audit.

---

## Step 5: Read Each Review as One Customer

Every analyzed review is one real person's story. Read every review in the analysis set, all of them, however many there are; large sets get read in chunks. Before grouping anything, write a short record for each customer, built only from what their own review says. This keeps every detail attached to the person who said it.

For each review, fill in what it carries:

- **Record ID** — the review's ID or row number, so every later claim can point back to it
- **Who they are** — life context, situation, and identity signals the review shows
- **What they call themselves** — any way they describe themselves in their own words, verbatim: a label ("POTsie", "spoonie", "nurse", "mom of three") or a self-description ("I am a...", "I have...", "I'm someone who...", "as a...", "as an avid triathlete", "I work in the heat"). This applies to every persona the same way. Empty when they never describe themselves.
- **Other identities** — any second identity the review shows (a POTS patient who also travels for work)
- **Use case** — the one main thing they use the product for: the reason in their life they reach for it (managing their POTS, training, nights out drinking)
- **Pains from the problem** — what the use case itself does to them, the symptoms and struggles that come with it (dizziness, brain fog, headaches, cramps, hangovers). They live in the "before."
- **Pains from how they were solving it** — what made their old way of handling the problem hard (can't drink enough water, other electrolytes taste bad or have too much sugar, fitting it into a demanding job or school schedule, keeping it up around workouts). They live in the "before." A bad experience with the reviewed product is never a pain point here.
- **What they wanted** — the outcome, feeling, or identity they were chasing
- **What they tried before** — other products, habits, or approaches they tried before this one. The reviewed product is the one that worked, so it never goes here.
- **Hesitation before buying** — the doubt, worry, or skepticism they had before they bought ("I was skeptical but..."). Disappointment after buying belongs to the negative review audit.
- **What made them buy** — the moment, event, recommendation, or breaking point that pushed them to buy
- **What changed** — the result in their own words
- **Where it fits in their day** — the moments after buying when they reach for it (in the morning coffee, at their desk at 2pm, in the gym bag, before going out)
- **Situational detail** — any where, when, who-was-around detail (raw material for trigger moments in Step 7)
- **Their words** — the most vivid lines, verbatim

Write the records to a file. Every number in the output (members, variations, roles, pains, overlaps, moments, shared pains) is counted from these records, one record at a time.

Leave a field empty when the review doesn't say it. An empty field is a true record; a guessed one breaks the pairing this version exists to protect. Score 2 reviews usually fill only one or two fields; that's fine.

---

## Step 6: Group Customers Into Personas

### What a persona is

**A persona is who someone is.** It's an identity they'd claim that holds true beyond any single use of the product: the chronic illness patient, the social drinker, the athlete, the keto dieter, the frequent traveler, the parent, the doctor, the wife buying for her husband.

Four things live inside a persona instead of being one:

- **Use case.** Each persona has one main use case, the thing it uses the product for (managing a chronic illness, training, nights out). It follows from who they are. Anything that makes that use case harder (a demanding schedule, workouts, travel) is a pain point.
- **Pain points, in two layers.** Pains from the problem are what the use case does to them (for someone with POTS: dizziness). Pains from how they were solving it are what made their old fix hard (for that same person: can't drink enough water). Both layers make ad angles: the first speaks to the problem, the second to why other solutions failed. The same pain can show up in several personas, which makes it an angle to test across them. List it in each persona that carries it.
- **Where it fits in their day.** Adding it to coffee, putting it out at a party, or keeping it in a gym bag are moments in someone's day after they bought. They go in the persona block as ad-ready micro moments.
- **Buying behaviors.** Switching from another product, subscribing, stocking up, or buying as a gift describe how someone bought. They go in the persona's tried-before or what-made-them-buy fields.

**What they do regularly counts as who they are.** A review that shows someone doing an activity as a normal part of their life ("after my run", "on my long shifts", "every time I fly") places them in that identity, the same as saying "I'm a runner." A customer needs a stated or regularly shown identity to join a persona.

A persona is always an identity. Pain points ("can't drink enough water"), habits (drinks a lot of coffee), and buying behaviors (reads labels, gifts it) describe something about a person, so they go inside that person's persona. When a review shows only those, the customer stays unassigned.

Name each persona by the identity underneath what the review shows. A customer who supplies the household or buys for their kids is a parent. One who recommends it to patients is a doctor or practitioner. One who drinks at the parties they host is a social drinker.

Someone buying for another person starts in one persona: the person buying for someone they care for, with each relationship and reason as a variation (wife for her husband, adult daughter for her aging mom, parent for a child with POTS). When one relationship stands out, with enough members telling their own story, it becomes its own persona: "wives buying for their snoring husbands." Buying something as a gift is a buying behavior; the person goes in the persona of who they are and who they're buying for.

### How fine to split: the story decides

**Two groups are separate personas when they'd get told different stories in an ad.** Someone with POTS and someone with migraines are both chronic illness patients, but their stories differ (fainting at the checkout versus a migraine that wipes out the day), so each is its own persona. The same goes for a CrossFitter and a runner, and for "moms": mom is too broad, so ask what kind of mom (the mom keeping a kid with POTS hydrated, the mom packing sports bags for three kids).

**Variations stay inside one persona when the story is the same** and only the details change: tailgaters and hosts are both social drinkers preventing hangovers; Hashimoto's and Sjögren's patients may share one autoimmune story. Each variation is listed inside the persona with its own count and what's specific to it. Every variation shares its persona's one use case; what changes is the detail, most of all where it fits in their day.

**Finer detail inside one person's story is a micro-persona**, not a new persona: the POTS patient caught at the exact moment she nearly faints in public is the POTS persona at a trigger moment.

How fine the split goes depends on the brand, the product and the customers, so the line between a persona and a variation is a judgment. Make it with the story test, name the call you made, and note any group that sits on the line.

When related personas share a family (POTS, migraine and autoimmune personas all sit in the chronic illness family), group them under that family name in the output so the bigger picture stays visible.

### Primary persona and secondary personas

Some products sell mainly to one core persona that breaks into variations (a hydration drop bought mostly by chronic illness patients; an electrolyte mix bought mostly by athletes). When the largest persona has at least twice the members of the next largest, it is the **Primary Persona**. Report it first, and give each of its variations its own sub-block (members, roles, use case, both layers of pain points, what made them buy, where it fits in their day, its trigger moments, 2 to 3 quotes) so each variation can be briefed on its own. Every other persona is a **Secondary Persona**. When no persona is twice the next, there is no primary persona; say so, and report all personas as equals.

### Every persona, in order

Report **every** persona the records show, ordered by number of members, largest first (the Primary Persona first when there is one). There is no minimum size and no maximum count: a persona with 3 members gets a full block, built from what those 3 reviews say. A customer whose review shows nothing about who they are (only a pain, a use case, a behavior, or "works great") stays unassigned; report how many.

### Overlaps

Assign each customer to the persona that matches their main identity, the one their story is built around. When a customer also carries another persona's identity (a chronic illness patient who travels for work), record it as an overlap on both personas, described as the combined person and how the two identities meet: "POTS patient who travels often (3 customers): keeps a bottle in her carry-on because flights set off her symptoms." Count overlaps from the records.

Write every persona field from its own members' records only. That way everything paired inside a persona (this pain, with this past attempt, with this trigger) is a pairing that really happened in the same customers' lives.

### The persona block

Make each block as complete as its members' reviews allow:

- **Persona name** — who the person is, named by the identity, not a demographic
- **Members** — how many customer records belong to it, and that number as a share of the product's analyzed reviews
- **Who they are** — 2–3 sentences on life context, situation, and identity
- **Roles** — how members describe themselves, verbatim, with counts: labels ("POTsie" ×2, "spoonie" ×1) and self-descriptions ("I have POTS" ×4, "I'm someone who sweats a lot" ×1). Each distinct self-description is its own role: "I have Hashimoto's" and "as an ostomate" are two roles, never one bucket like "named-condition self-descriptions." Group only the same wording (or the same words with small grammar changes, like "I have POTS" and "having POTS"). Applies to every persona the same way. "None stated" only when no member described themselves.
- **Variations** — each specific version inside the persona (each illness, job, sport, scene, or relationship-and-reason), with its member count, one line on what's specific to it, and where it fits in that variation's day
- **Overlaps with** — each combined person ("POTS patient who travels often"), its count, and one line on how the two identities meet
- **Use case** — the one main use case, with how many members share it
- **Pains from the problem** — what the use case does to them, most common first, with counts
- **Pains from how they were solving it** — what made their old fix hard, most common first, with counts
- **What they wanted**
- **What they tried before**
- **Hesitation before buying**
- **What made them buy** — the buying moment, the emotionally charged micro moment that tipped them
- **What changed**
- **Where it fits in their day** — the moments after buying when members reach for it (morning coffee, the 2pm slump, the gym bag, before a night out), with counts. These are micro moments for ads, alongside the buying moment.
- **How they talk** — vocabulary, tone, and verbatim phrases from its members
- **Evidence** — 3 to 5 verbatim quotes from different members (as many as exist when the persona is smaller), each tagged with its record ID

When a field is empty for most members, say so instead of filling it from other personas.

### Shared pains

After the personas, list every pain point that shows up in more than one persona: the pain in customer words, which layer it is (from the problem, or from how they were solving it), the personas that carry it, and how many members in each. These are the angles to test across personas.

---

## Step 7: Find Each Persona's Trigger Moments

A persona describes the person. A trigger moment catches that person in the specific, concrete moment when the pain or desire stops being background and becomes something they act on — and moves them from one awareness stage to the next. It is an event, not a feeling: it has a where, a when, usually other people, and a consequence.

One persona usually carries several trigger moments, at different stages of awareness. The same person is a different buyer in a moment that names the problem for the first time than in a moment where a solution they tried has just failed them. Awareness lives at the trigger-moment level, not the persona level, and each moment is defined by the transition it drives:

- Unaware → Problem-Aware: the moment the problem gets named, noticed, or costs them something they can't ignore
- Problem-Aware → Solution-Aware: the moment they decide the problem is worth fixing and start looking
- Solution-Aware → Product-Aware: the moment a current approach fails them, or this product enters their view
- Product-Aware → Most-Aware: the moment the reason to act now appears (this is "what made them buy")

For each persona, extract **every trigger moment** its members' reviews carry, with no limit, the same way pain points are all listed. When several members describe the same moment, it is one moment with a count and evidence from each. List them most common first. For the Primary Persona, each moment sits in the sub-block of the variation its members belong to (a POTS moment under POTS). For each moment:

- **The moment** — named by circumstance, in one line, specific enough to shoot as a scene
- **Members** — how many customer records show this moment
- **Stage transition** — from which awareness stage to which
- **Life stage and role** — where they are in life, and who they're being in this moment
- **Circumstance** — the specific situation unfolding
- **Environment and context** — where they are, who's around, what else is happening
- **Emotional state** — what they're feeling, in their own words where possible
- **Needs vs. wants** — what they need functionally vs. what they want emotionally
- **Product intersection** — how the product enters, or could enter, this exact moment
- **Evidence** — the review lines that establish this moment, with the customer record each came from

Trigger moments must come from the reviews of that persona's own members, so the moment and the person stay paired the way they really happened. Stacking more attributes onto a persona does not make a trigger moment — the move is circumstance and event, not more qualifiers. The test: could you shoot it? If the review set doesn't carry this situational depth, say so plainly — that's a real finding. Never manufacture a moment.

---

## Output Format

Produce a separate full output for each product. Structure:

```
─────────────────────────────────────
PRODUCT / SERVICE: [Name]
Brand: [brand name]
Reviews received: [X] | Duplicates removed: [X] | Analyzed: [X] | Discarded (score 1): [X] | Set aside as negative: [X] | Mixed (positive half kept): [X] | Incentivized: [X]% ([left out | used, flagged | used, not flagged])
Customers grouped into personas: [X] | Unassigned: [X]
─────────────────────────────────────

PERSONAS — [X] identified, largest first
Primary persona: [name | none, no persona is twice the next]

[If there is a primary persona, its block comes first, followed by one sub-block per variation:
  Variation: [name] — [N] members
  Roles / Use case / Pains from the problem / Pains from how they were solving it / What made them buy / Where it fits in their day / Trigger moments / 2–3 quotes]

[Persona Name] — [X] members, ~[X]% of analyzed reviews
Who: [2–3 sentences]
Roles: ["label" ×N, ... | none stated]
Variations:
  [variation] — [N] members: [what's specific] | Where it fits in their day: [moment, ...]
Overlaps with: [combined person (N): how they meet, ...]
Use case: [one main use case (N)]
Pains from the problem: [pain (N), ...]
Pains from how they were solving it: [pain (N), ...]
Wanted: [...]
Tried before: [...]
Hesitation before buying: [...]
What made them buy: [...]
What changed: [...]
Where it fits in their day: [moment (N), ...]
Voice: [distinctive phrases and tone]
Evidence:
  "[Exact quote]" — [record ID]
  "[Exact quote]" — [record ID]

  Trigger moments:

  [The Moment — named by circumstance] — [N] members
  Stage transition: [from → to]
  Life stage & role: [...]
  Circumstance: [...]
  Environment & context: [...]
  Emotional state: [...]
  Needs vs. wants: [...]
  Product intersection: [...]
  Evidence: "[review line]" — [record ID]

  [Repeat for every trigger moment, most common first — or: "Reviews don't carry enough situational depth for trigger moments."]

[Repeat for every persona, largest first]

SHARED PAINS
["pain in customer words"] ([from the problem | from how they were solving it]) — [Persona (N), Persona (N), ...]

─────────────────────────────────────
```

---

## Step 8: Save the Personas

The personas are finished once they are saved where the brand's research lives, next to the reviews they came from. For a competitor, keep its files apart from the brand's own (for example in a folder named after the competitor). Save:

- The persona overview: `personas-<product-name>.md` (the full output above)
- The personas: `personas/<persona-slug>.md`, one file per persona with all of its trigger moments, usable on its own. `creative-engine` reads these directly.
- The customer records: `customer-records-<product-name>.md`, so any persona claim can be traced back to the reviews

Add a short header to each file naming the brand, the product, the source (own brand or which competitor), the review counts behind it, and the date. When the brand has no reviews of its own, the competitor personas are the personas; say so in each file's header.

---

## Notes on Quality

- Score 5 reviews are read in full and treated as primary sources
- Every persona claim traces back to at least one record ID
- When the records group messily, report the messy split as it is; it's a real finding
- When a product has too few quality reviews for meaningful personas, flag that and report what the reviews do show
