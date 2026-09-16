---
name: brand-relevant-keywords
description: Builds the keyword bank used to find organic conversation about the problem a brand solves — the words customers use before they know the brand exists. Generates short-tail and long-tail queries grouped by intent (problem, desire, category, brand and competitor), tests each one before it enters the bank, and records what each returns. Use this before any social listening, community scrape, forum research, or search-data pull, and when someone says "find keywords for this brand", "what would my customer search", "give me queries for Reddit or TikTok", or "what are people typing before they find us". Output is one markdown file, `1. research/customer/keyword-bank.md`.
---

# Brand-Relevant Keywords

The query decides what you find. Run the wrong one and the research is wrong before anybody reads a word of it — not obviously wrong, which would be survivable, but plausibly wrong, full of real quotes from the wrong people.

This skill builds the bank of queries the brain uses to find organic conversation, and it builds them from the customer's language rather than the brand's.

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

## Step 2: Build the four banks

**Problem language.** What someone types when the problem is happening and no solution is in mind. Symptoms, complaints, frustrations, failed workarounds, the thing they are trying to stop. These reach people at the widest awareness gap and produce the most useful raw language.

**Desire language.** What someone types when they know the outcome they want but not how to get it. Aspirations, comparisons against a better state, questions about whether something is achievable. These reach people who are already looking, which makes them warmer and their language more solution-shaped.

**Category language.** What someone types once they know a category of solution exists but not which product. Category names, "best X for Y", comparisons between approaches, questions about how a category works. Include the names the customer uses even when the brand uses a different one — especially then.

**Brand and competitor terms.** The brand's name and its variants, competitor names, and product names. These reach existing customers and existing competitor customers. Useful for objections, switching language and post-purchase experience. Never used to establish what an unaware audience thinks.

Within each bank, write both:

- **Short-tail** — two to four words, high volume, broad. Good for finding where conversation clusters. Poor for finding the exact moment.
- **Long-tail** — the whole sentence someone types when they are describing a situation rather than naming a thing. Low volume, high signal. This is where trigger moments surface.

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

One file, `1. research/customer/keyword-bank.md`, four sections matching the four banks. Each query is a row carrying:

- The query itself, exactly as it should be run
- Short-tail or long-tail
- The surface it is written for
- The population it reaches — unaware, problem-aware, solution-aware, or existing customer
- The persona or trigger moment it targets, where one applies
- Tested / not yet tested, and what it returned

Order each section by how much signal the query produced once tested, so the next person starts with what works rather than at the top of a list.

---

## Standards

- Queries use the customer's words. Where a review said it, quote the review and cite the file.
- Every query is tagged with the population it reaches. An untagged bank is not finished.
- A query that has not been run is marked as untested. Never present an untested query as a finding.
- Failed queries stay in the file with the reason they failed.
- Never build the bank from the brand's marketing copy, its own category label, or its positioning statement unless customers demonstrably use those words too.
- Rebuild after any significant review import — new language changes what should be searched.
- The bank feeds every organic research pull the brain does: social listening, community and forum research, and search-data work. Each pull records the query that produced it so its population is traceable back to here.

**Done when** someone else could take the bank, run it without asking you anything, and come back with the same material you would have.
