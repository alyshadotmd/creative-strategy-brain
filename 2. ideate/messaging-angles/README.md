# Messaging Angles

The library `creative-engine` reads at Step 5. An angle is the strategy an ad uses to make its case — one product truth, chosen because it answers what a trigger moment just made urgent. The strategy is reusable across brands; the angle is specific to this brand's product and customer.

## What goes here

One file per angle, named for the strategy it uses (lowercase, hyphenated). Each file records:

- **The strategy** — the reusable move, in one plain line
- **The product truth it leans on** — pulled from `brand/products/<product-name>.md`; if the truth isn't in a product profile, the angle can't use it
- **What it answers** — which pain, desire, failed solution, or objection from the review audit this angle speaks to, by theme name
- **Personas it fits** — by persona file name in `1. research/customer/personas/`
- **Trigger moments it pairs with** — which stage transitions this angle can carry without contortion
- **Expressions by stage** — how the same core truth is said at each awareness stage it honestly serves
- **Concepts that used it** — rows in `2. ideate/ad-concepts.md`
- **Results** — what `4. analyze` learned when it ran; expand the entry when it keeps winning

## Rules

- The core truth of an angle never changes; only its expression does. If you're rewriting the truth, that's a new angle.
- An angle with no product truth behind it is a slogan. An angle with no review theme behind it is a guess.
- Add an angle when a concept in `ad-concepts.md` uses a strategy that isn't here yet. A library that never grows means you stopped looking.
