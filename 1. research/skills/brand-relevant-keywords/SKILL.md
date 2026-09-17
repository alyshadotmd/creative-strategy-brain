---
name: brand-relevant-keywords
description: Builds the keyword bank used to find organic conversation about the problem a brand solves — the words customers use before they know the brand exists. Generates short-tail and long-tail queries grouped by intent (problem, desire, category, brand and competitor/failed solutions, trigger moments, persona probes), tests each one before it enters the bank, and records what each returns. Every query must be a type-able search; verbatim review sentences are grounding evidence, never queries. Use this before any social listening, community scrape, forum research, or search-data pull, and when someone says "find keywords for this brand", "what would my customer search", "give me queries for Reddit or TikTok", or "what are people typing before they find us". Output is one markdown file, `1. research/customer/keyword-bank.md`.
---

# Brand-Relevant Keywords

The query decides what you find. Run the wrong one and the research is wrong before anybody reads a word of it — not obviously wrong, which would be survivable, but plausibly wrong, full of real quotes from the wrong people.

This skill builds the bank of queries the brain uses to find organic conversation, and it builds them from the customer's language rather than the brand's.

## A query is something a person would type

The hard rule (added 2026-09-17 from Alysha's feedback on the Javvy build): **every entry in the query column must pass the "would a person actually type this into a search box" test** — Google, TikTok search, Reddit, Amazon. "chalky protein taste" is a keyword. "I've tried others but I didn't like the chalky, after taste they left in my mouth" is not a keyword — it is a review sentence, and it is gold, but it is *grounding*, not a query. Derive 1–2 realistic searches from the sentence, put the verbatim sentence in the grounding column with its reviewer and source file, and label the derived query constructed-from-review-language rather than presenting it as verbatim. Default surface priority for this org's research: **TikTok search first, Google second** — bias phrasing toward what someone types into TikTok unless the row's surface says otherwise.

## Who a query can reach

Every query has a reachable population, and it is usually narrower than it looks.

A query containing the brand name can only return people who already know the brand. Most of them bought. Many were incentivized to post. Their language is shaped by the brand's own marketing, which they have been reading for months — so it flatters, and it reads as validation.

A query describing the problem returns people who have never heard of the brand. They are describing a situation, not a product. This is where the language that makes ads work comes from, because it is the language the customer already has in their head when the ad finds them.

Both are useful. They are not interchangeable, and a bank that mixes them without marking which is which produces research that cannot be trusted, because nobody downstream can tell which quotes came from which population. **Every query in the bank is tagged with the population it reaches, and every pull records the query that produced it.**

---

## Inputs

| What | Where | If it isn't there |
|---|---|---|
| What the product actually is and does | `brand/products/` | Run `product-info` first. Without it the bank describes a product that doesn't exist. |
| How customers describe the problem in their own words | `1. research/customer/reviews/` and the review audit | The bank can still be built, but it will be your language rather than theirs. Mark it as unvalidated and rebuild after reviews land. |
| Personas and their trigger moments | `1. research/customer/personas/` | Build the bank anyway; map queries to personas when they exist. |
| Category framing and competitor names | `brand/brand-overview.md`, `1. research/competitors/` | Competitor terms can be skipped; the other three banks don't depend on them. |

Never start from the brand's own marketing copy. It is the one source guaranteed to contain nobody's language but the brand's.

---

## Step 1: Name the problem in plain words

Before writing a single query, write one line per problem the product solves, in language a person would use to a friend rather than to a search box. Not the category, not the benefit — the situation.

If the reviews are in the brain, this line comes from them verbatim wherever possible. If a review says it better than you can, use the review's words and note which file it came from.

A product that solves several unrelated problems gets a line each, and its queries separate. Collapsing them produces a bank that returns a blur.

## Step 2: Build the six banks

Alysha's framing, which this skill follows: product-related keywords (brand name, the category you actually sell, and adjacent terms like "high protein snack"), pain, desire, failed solutions, trigger moments, and a small set of persona probes. Pain and desire are two different angles and one usually dominates per brand — a customer may feel no pain about their coffee lacking protein while strongly desiring higher-protein everything. Read the review audit to decide which angle carries the weight for this brand, and say so in the bank's intro.

**Problem language.** What someone types when the problem is happening and no solution is in mind. Symptoms, complaints, frustrations, failed workarounds, the thing they are trying to stop. These reach people at the widest awareness gap and produce the most useful raw language.

**Desire language.** What someone types when they know the outcome they want but not how to get it. Aspirations, comparisons against a better state, questions about whether something is achievable. These reach people who are already looking, which makes them warmer and their language more solution-shaped.

**Category language.** What someone types once they know a category of solution exists but not which product. Category names, "best X for Y", comparisons between approaches, questions about how a category works. Include the names the customer uses even when the brand uses a different one — especially then.

**Brand and competitor terms (failed solutions).** The brand's name and its variants, competitor names, and product names. Competitor terms are the customer's failed or alternative solutions — source them from what reviewers say they tried, stack, or switched from, never from researcher-guessed brand lists. These reach existing customers and existing competitor customers. Useful for objections, switching language and post-purchase experience. Never used to establish what an unaware audience thinks.

**Trigger-moment queries.** The searches someone runs in the moment that starts the buying journey: the doctor's comment at a checkup, starting a medication, a life event, the day the daily-spend math stops making sense. Pull the actual triggers from the review audit and personas, then derive 1–2 type-able searches per trigger ("doctor said I need more protein", "starting GLP-1 what should I eat"). Bias these toward TikTok phrasing; this bank exists mostly to find the content people meet in that moment.

**Persona probes.** A handful (3–5) of experimental queries that name the persona itself ("GLP-1 mom") just to see what content comes up. Label the whole section explicitly as low-confidence discovery probes that may return nothing usable — that caveat is part of the section, not a footnote.

Within each bank, write both:

- **Short-tail** — two to four words, high volume, broad. Good for finding where conversation clusters. Poor for finding the exact moment.
- **Long-tail** — a longer natural search phrase describing a situation rather than naming a thing ("how to stop craving dessert at night"), still something a person would type, never a quoted review sentence. Low volume, high signal. This is where trigger moments surface.

A bank with only short-tail terms finds the category and misses the person. A bank with only long-tail terms finds a handful of people and misses where they gather. Both, every time.

## Step 3: Shape each query to its surface

The same intent takes a different form on every platform, and a query written for one returns nothing on another.

- A search engine gets a typed, compressed query — articles indexed against it
- A social platform gets a spoken-sounding phrase, plus the hashtags that phrase attracts
- A forum or community gets a question, because that is what people post there
- A review or Q&A surface gets the phrasing of a complaint or a comparison

Write each query in the form its target surface actually uses. Note which surface each is for. One intent can produce three or four queries this way, and they are not duplicates.

## Step 4: Test before it enters the bank

A query is a guess until it has been run. For each one, run it against its target surface, read the first stretch of results, and answer one question: **are these people in the state we care about?**

Three failures to watch for:

- **Wrong meaning.** A term with a second, more common sense returns a different population entirely, and the pull looks fine until someone reads it. Add the disambiguating word, or drop the query.
- **Wrong population.** The results are real but they are practitioners, resellers, or people discussing the category professionally rather than experiencing the problem. Common with category language.
- **No volume.** A long-tail query so specific that it returns almost nothing. Keep it only if what it does return is exceptional; otherwise loosen it one degree and re-test.

A query that fails is recorded with the reason, not silently deleted. The next person will think of it too.

## Step 5: Write the bank

One file, `1. research/customer/keyword-bank.md`, six sections matching the six banks. Each query is a row carrying:

- The query itself, exactly as it should be run — type-able, never a review sentence
- Short-tail or long-tail
- The surface it is written for
- The population it reaches — unaware, problem-aware, solution-aware, or existing customer
- The persona or trigger moment it targets, where one applies, plus the verbatim grounding quote with reviewer and source file when the query was derived from review language (labeled constructed-from-review-language)
- Tested / not yet tested, and what it returned

Order each section by how much signal the query produced once tested, so the next person starts with what works rather than at the top of a list.

---

## Standards

- Queries use the customer's words, reshaped into something type-able. Where a review said it, the verbatim quote lives in the grounding column with the file cited; the query column never holds a first-person review sentence.
- Every query is tagged with the population it reaches. An untagged bank is not finished.
- A query that has not been run is marked as untested. Never present an untested query as a finding.
- Failed queries stay in the file with the reason they failed.
- Never build the bank from the brand's marketing copy, its own category label, or its positioning statement unless customers demonstrably use those words too.
- Rebuild after any significant review import — new language changes what should be searched.
- The bank feeds every organic research pull the brain does: social listening, community and forum research, and search-data work. Each pull records the query that produced it so its population is traceable back to here.

**Done when** someone else could take the bank, run it without asking you anything, and come back with the same material you would have.
