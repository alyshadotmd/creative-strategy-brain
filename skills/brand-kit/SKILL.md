---
name: brand-kit
description: Builds a structured brand & asset kit document (logo, color, type, voice, imagery, photography, usage rules, asset inventory) for any brand — from a client's existing brand page, a folder of uploaded assets, a website scrape, or a short interview. Use this whenever the user says "build a brand kit", "document their brand", "pull their brand guidelines", "turn this brand page into a kit", "what are their colors/fonts", or uploads logos, fonts, or a brand book and wants it organized. Also trigger when a static ad, landing page, or design brief needs visual identity rules and no brand kit exists yet for that brand. This is the visual + verbal identity layer. It complements brand-overview and the research folder (strategy layer) — run both before design or copy execution. Minimum input is a website URL; a brand PDF, logo pack, font files, or product shots given at the same time make it better. Output is always two things: the kit saved at `brand/brand-kit.md`, and every brand asset that meets the quality bar (fonts, logos, product images, lifestyle images, illustrations) downloaded into the brain's `assets/` folders so `app-generation` and every design task can use them without asking.
---

# Brand Kit Builder

Turns scattered brand material into one clean, opinionated reference doc: what the brand looks like, sounds like, and what you're allowed to do with it.

**What it is not:** it is not brand strategy (audience, competitors, differentiation — that's `brand-overview` in `1. research/skills/`) and it is not a product profile (`product-info`, same folder). It's the identity rulebook a designer, editor, or copywriter opens before touching a single pixel or sentence.

**The bar:** every rule in the finished kit should be specific enough that someone who has never seen the brand could make an on-brand asset — and catch an off-brand one — without asking a follow-up question.

---

## PHASE 1: FIND THE SOURCE

Brand kits come from four kinds of source. Identify which you have before doing anything else. Ask only if it isn't obvious from what the user gave you.

| Source type | What it looks like | How to work it |
|---|---|---|
| **A. Existing brand page or book** | A brand-kit URL, a PDF brand book, a Notion/Figma guidelines page | Best case. Fetch or read it in full. Your job is to extract, structure, and tighten — not reinvent. Preserve the brand's own wording for rules and examples. |
| **B. Uploaded assets, no guidelines** | Logo PNGs, font files, product shots, a Canva export | Inventory the files, pull colors and type from what's there, then infer the rules and label every inferred rule as such. Uploaded originals beat anything scraped from the site — save them into `assets/` first (Phase 3), then fill gaps from the site. |
| **C. Website only** | Just a URL | Scrape the live site: fetch the homepage, a product page, and the about page. Pull hex codes and font names from CSS where you can (`web_fetch` the page, look for `font-family`, `--color-*` variables, `background`, `color` declarations). Screenshot-level observations count but flag them as observed, not stated. The site is also the primary place to **harvest asset files** (Phase 3) — logos, product and lifestyle images, illustrations, and self-hosted font files. |
| **D. Nothing yet** | Brand is pre-launch or the user just has ideas | Run the interview below, then build a **proposed** kit clearly labeled as a draft for the brand to approve. |

Sources stack. A brand page (A) plus uploaded fonts (B) plus the live site (C) is common — merge them, and when they conflict, the most recent explicitly-stated source wins. Note the conflict in Research Notes.

### Interview (only when needed)

Ask all at once, in one message. Skip any question already answered by the source material.

**Basics**
1. Brand name and website URL
2. Where do brand assets live right now? (link, folder, upload, "nowhere")
3. Is there an existing brand book, style guide, or brand page — even an outdated one?

**Identity**
4. Primary colors — hex codes if you have them, or "whatever's on the site"
5. Fonts — names, and do you have the files?
6. Is there a mascot, icon system, or illustration style?

**Rules and rights**
7. Anything the brand is strict about? (logo treatment, words they never use, colors that clash)
8. Who owns the photography and creator content, and are there usage restrictions?
9. Who's the point of contact for approvals and for high-res / vector originals?

Confirm before building:

> "Got it — I'll pull everything into one kit and flag anything I had to infer rather than confirm. Give me a moment."

---

## PHASE 2: EXTRACT

Work through the seven sections below. For each, capture what the source says, then check it against the live product where possible (the site, a recent ad, packaging). A brand book that says "no serifs" while the homepage is set in a serif is a finding, not a contradiction to smooth over — the live brand is the truth, and the kit should say so.

### Provenance tags — use them on every rule

- **[stated]** — written explicitly in a brand page, book, or by the user
- **[observed]** — you saw it on the live site, in ads, or in the assets, but nobody wrote the rule down
- **[inferred]** — your recommendation, based on the pattern; the brand hasn't confirmed it

A kit built from source type A should be mostly [stated]. A kit built from C or D will be mostly [observed] and [inferred] — that's fine, as long as it's honest about it. Never upgrade an inference to a stated rule.

### 01 — Logo
- Every mark variant (primary, reversed, mascot, monogram/avatar) and the surface each one lives on
- Clear-space rule (usually expressed relative to a letterform — "the height of the W")
- Which mark to use at small / avatar sizes
- Explicit don'ts: recolor, rotate, stretch, effects, rebuilding the wordmark, busy backgrounds
- **Look for the trap:** the surface combination where a mark disappears (a lavender mascot on deep purple, a white logo on cream). Every brand has one. Name it.

### 02 — Color
- Full palette grouped by **job**, not by hue: Ink (type, lines, CTAs), Signal (the one attention color), Surfaces (backgrounds, cards), Support (secondary fills, mascot, tints), Accents (used sparingly)
- Every swatch gets a hex code and a one-line job description. A hex code with no job is a decoration, not a system.
- The **priority rule** — most good systems have one loud color and a rule about how often it may appear (e.g. one signal moment per screen)
- Density rule — how many colors per card/section before it reads chaotic
- Body copy color — is it pure black or a brand dark? (Almost never pure black in warm systems.)
- Common mistakes — the two or three misuses you'd see from a new designer. If the source doesn't list them, write them from the palette logic and tag [inferred].

### 03 — Type
- Each typeface: name, weight(s), and **its voice** — what it's for emotionally, not just structurally
- Casing rules per face (all caps vs sentence case) and which content types each one owns (headlines / eyebrows / buttons / body / emotional one-liners)
- Scale relationships worth stating ("pricing numerals run 2–3× the labels around them", "kicker at 12px, wide tracking, 62% opacity")
- Signature treatments — marker highlights, hand-drawn underlines, tilts — and the **frequency rule** for each (usually one per screen)
- **Licensing.** Always check. Font files on a brand page are almost always licensed to the brand only. Read the page source or font files for license strings. Write the license scope into the kit verbatim and tell the reader who to ask before using the fonts anywhere else.

### 04 — Voice
- One-line character description ("like a friend who read the studies")
- Register rules: person (second person? first person plural?), what you call the customer, what you never call them
- **Sounds like us** — 5–8 real lines from the brand's own copy. Pull them from the site, packaging, emails. Don't write new ones for a type-A kit; do write proposed ones for type D and label them.
- **Never say** — the banned list, and *why* each word is banned (wrong category, over-commodified, legally risky). The "why" is what lets a writer generalize to words not on the list.
- The compliance swap — the specific word substitutions that matter legally or categorically ("clinically studied," not "clinically proven"). Flag these as high-priority.
- Specificity rule — does the brand use real numbers? Real review counts?
- Emoji and iconography stance — allowed, banned, or one exception

### 05 — Imagery & Illustration
- Illustration vs photography: which does the brand lead with, and where does the other one appear
- Temperature and contrast: warm/cool, high/low contrast, backdrop rules
- Mascot or character system: fixed attributes (body color, outline color), expression states, default expression, forbidden surfaces
- Decorative elements (sparkles, shapes, textures) and their color variants per surface
- Any sequential system (how-it-works steps, ritual illustrations)
- File specs of what exists: format, transparency, max long edge, and what that resolution is *right for* (web/social/decks vs print)

### 06 — Photography
- Where the photos came from (in-house shoot, studio like Soona, creators) — this determines rights
- Rights statement in plain language: who owns it, where it may be used
- Shot categories as the brand organizes them (product / ritual / lifestyle / moments), with a one-line list of what exists in each
- What's missing that a strategist would want (e.g. no photos of the target customer, no before/after, no UGC) — tag [observed]
- File specs and how to get originals

### 07 — Using These
- What the reader may do freely (work for the brand, pitches, mockups, sharing internally)
- What needs a check first (own portfolio, altering marks, fonts, print/vector)
- What the kit **doesn't** cover — creator/UGC content nearly always lives outside the kit with per-creator agreements. Say so explicitly. This is the most common way a team gets burned.
- Point of contact

---

## PHASE 3: HARVEST AND SAVE THE ASSETS

The kit describes; the folders deliver. This phase fills the brain's `assets/` folders from whatever the user gave you plus the live site, so nobody downstream has to go hunting. It runs **every time**, even when the only input is a URL.

### Where things go

The brain holds one brand. `assets/` is flat — never create a brand subfolder.

| Category | Folder | What belongs here |
|---|---|---|
| Fonts | `assets/fonts/` | Every typeface + weight the brand actually uses, as font files |
| Logos | `assets/logos/` | Wordmark, mark/monogram, mascot, reversed/one-color variants |
| Product images | `assets/images/product/` | Packshots and PDP gallery images — the product is the subject |
| Lifestyle images | `assets/images/lifestyle/` | Photography of the brand's world — people, rituals, product in use, environments |
| Illustrations | `assets/images/illustrations/` | Mascot states, decorative elements, icon system, how-it-works graphics |
| The kit | `brand/brand-kit.md` | The document from Phase 4 |

### Order of operations

1. **Uploads first.** Anything the user handed you (logo pack, font files, brand PDF, product shots) is the original — sort it into the folders above before touching the site. If a PDF brand book is provided, extract the embedded images (logos, illustrations, photography) and save the ones that meet the bar. Do **not** save fonts embedded in a PDF — they are subsetted and unusable; record the font names instead and source the files properly.
2. **Then the site.** Fetch the homepage, at least one product page per product (or the top 3–5 if there are many), the about page, and any of `/brand`, `/press`, `/media`, `/media-kit`, `/brand-assets` that exist — press pages often have a real logo pack. Collect candidates from `<img src>` and `srcset` (always take the **largest** candidate), `og:image`, CSS `background-image`, inline `<svg>` logos, and every `@font-face { src: url(...) }` in the site's stylesheets. On Shopify-style CDNs, strip size suffixes (`_800x`, `_1200x1200`, `?width=`) to reach the original.
3. **Sort each candidate** into exactly one category, or discard it. Logo = wordmark/mark/mascot used as identity. Product = the product is the subject on a clean or simple backdrop. Lifestyle = photography with a person, setting, or the product in use. Illustration = drawn or vector art that is part of the brand system. Discard: UI chrome (arrows, hamburger, cart, social icons), payment badges, third-party logos (press mentions, "as seen in"), stock hero banners with baked-in headlines, and anything from another brand.
4. **Apply the quality bar** below. Save what passes. Log what fails with its URL so a human can chase the original.
5. **Dedupe.** Same image at several sizes → keep the largest only. Same logo as SVG and PNG → keep both (SVG is the master; PNG is convenience). Identical files by content → keep one.
6. **Name files** `[brand]-[category]-[descriptor].[ext]`, lowercase, hyphens — so a logo becomes `<brand>-logo-<variant>-<colorway>.svg`, a product shot `<brand>-product-<item>-<angle>.jpg`, a lifestyle shot `<brand>-lifestyle-<scene>.jpg`, a font file `<brand>-font-<family>-<weight>.woff2`. The descriptor should let someone pick the right file from the filename alone.

### Quality bar — the minimum to save a file

Files below the bar are **not saved**. They are listed in the kit under "Found but below the bar" with the source URL, so a designer knows the asset exists and where to ask for the original. This keeps `assets/` trustworthy: if a file is in there, it is safe to build with.

**Fonts** (`assets/fonts/`)
- Real font files only: `.woff2`, `.woff`, `.ttf`, or `.otf`. Never save a CSS file, a Google Fonts link, or a PDF-embedded subset as a "font".
- Save every face **and weight** the site actually uses for headlines, body, and UI. A brand with a display face and a body face at two weights each = four files minimum. Missing a weight that the site uses is a gap — list it.
- Self-hosted webfonts pulled from the site are licensed to the brand. Save them, and write the licensing note into the kit (03 — Type): brand work only, ask before any other use.
- Open-license fonts (Google Fonts / SIL OFL): download the static `.ttf` files from the official source rather than scraping the site. Note the license as open in the kit.
- If the font cannot be sourced (proprietary, not self-hosted, served from a third-party font service like Adobe Fonts or Typekit): save nothing, record the exact font name, weights, and where it is served from under "Not here — ask the brand contact". Do not substitute a look-alike.

**Logos** (`assets/logos/`)
- Vector (`.svg`) is the target. If only raster exists: `.png` with a **transparent background**, **≥ 1000 px** on the long edge.
- Minimum set to call the category complete: the primary mark, plus at least one of (reversed/one-color variant, standalone mark or monogram). A brand with a mascot needs the mascot mark too.
- Below the bar: favicons, `.ico`, `apple-touch-icon`, any logo under 400 px, logos on a baked-in non-transparent background, logos cropped out of screenshots. Record them; do not save them.

**Product images** (`assets/images/product/`)
- **≥ 1200 px** on the long edge, `.jpg`, `.png`, or `.webp`.
- The product is unmistakably the subject, on a clean or brand-consistent backdrop. No baked-in text overlays, price tags, sale badges, or "NEW" stickers.
- Minimum set: at least one clean front-facing packshot **per product/SKU**, ideally three angles (front, angle, detail). Fewer than one per product is a gap.
- Below the bar: anything under 800 px, thumbnails, collage/comparison graphics, images with UI elements from the PDP.

**Lifestyle images** (`assets/images/lifestyle/`)
- **≥ 1200 px** on the long edge.
- Shows the brand's world — a person, a setting, a ritual, the product in use. Should look like the brand's own photography, not a stock hero (if it looks like stock, save it but tag `[likely stock — check rights]` in the kit).
- Target set: **5 or more** distinct scenes. Under 5 is a gap worth flagging — a strategist will run out of imagery fast.
- Below the bar: anything under 800 px, banners with headlines baked in, heavily filtered social crops, screenshots.

**Illustrations** (`assets/images/illustrations/`)
- `.svg` preferred; otherwise `.png` with transparency, **≥ 800 px** on the long edge.
- Part of the brand's visual system: mascot and its expression states, decorative elements (sparkles, shapes, textures), how-it-works or ritual graphics, a custom icon set.
- No minimum count — some brands have none. If none exist, say so in the kit and move on. But if the site clearly uses a mascot or illustration style and you could not capture usable files, that is a gap to flag.

**Everything**
- Only the brand's own assets. Never save third-party logos, press marks, creator faces from UGC (rights live outside the kit), or another brand's product.
- Do not save a category placeholder or an empty file. Empty folder = honest signal that the asset is missing.
- When in doubt between two categories, pick the one a designer would look in first, and never save the same file in two folders.

### Inventory (goes into the kit)

After saving, count and list per folder: file count, filenames a reader would reference by name (every logo variant, every font file), resolution range and format. Then two lists:

- **Found but below the bar** — what exists on the site but didn't pass, with URL and the reason (e.g. "logo only available as 180 px PNG on the footer — ask for SVG")
- **Not here — ask the brand contact** — what the kit references that you could not source at all (a font weight, vector originals, print resolution, photography of the target customer)

---

## PHASE 4: BUILD THE DOCUMENT

### Output format

```markdown
# [Brand] — Brand & Asset Kit

Source: [URL(s), file names, or "interview with [user], [date]"]
Saved: [YYYY-MM-DD]
Kit status: [Extracted from official brand page | Assembled from assets + site | Proposed draft — needs brand approval]
Page note: [any freshness/contact note from the source, verbatim]

## Overview

**What it is:** [Product in one sentence, in the brand's own words if possible.]

**Who it's for:** [Primary customer, specific enough to picture. Secondary if there is one.]

**Why it looks like this:** [The category convention this brand is reacting to, and how. One or two sentences.]

**Brand feel:** [Three to five words. The line a designer keeps in their head.]

## 01 — Logo

The marks: [Which mark on which surface.]

Marks: [List of variants]. Files: `assets/logos/` — [filenames per variant].

**Please do**
- [Clear-space rule]
- [Surface rules]
- [Small-size rule]

**Please don't**
- [Alteration rules]
- [The disappearing-mark trap]
- [Wordmark and background rules]

## 02 — Color

[One-sentence summary of the palette logic: which color does which job.]

**[Ink group name] (type, lines, CTAs, outlines)**
- [Name] — [job]: `#HEX`

**[Signal group name] (the priority signal)**
- [Name] — [job]: `#HEX`

**[Surface group name] (the surfaces)**
- [Name] — [job]: `#HEX`

**[Support group name] ([job])**
- [Name] — [job]: `#HEX`

**Accents (used sparingly)**
- [Name] — [job]: `#HEX`

**The rules**
- [Priority-color frequency rule]
- [Colors-per-section density rule]
- [Body copy color rule]

**Common mistakes**
- [Misuse 1]
- [Misuse 2]
- [Misuse 3]

## 03 — Type

[One sentence on how the typefaces relate — co-equal? hierarchy? Note any reversal from an earlier brand book.]

**[Typeface 1] [Weight]** — [role], [casing], [tracking]
- Example headlines: [2–3 real ones]
- Used for: [content types]
- [Scale rules]

**[Typeface 2] [Weight]** — [role], [casing]
- Used for: [content types]

**Signature treatments**
- [Treatment 1]
- [Treatment 2]
- [Frequency rule]

**Casing**
- [Rule per face]

**Fonts:** [Names.] Files: `assets/fonts/` — [one filename per face/weight, or "not sourced — see Not here"].

> Licensing note: [Verbatim license scope from the source. Who may use these, where, and who to ask otherwise.]

## 04 — Voice

[Character line.] [Register rules — person, what to call the customer.]

**Sounds like us**
- "[Real line]"
- "[Real line]"
- "[Real line]"
- "[Real line]"
- "[Real line]"

**Never say**
- "[Word/phrase]" — [why]
- "[Word/phrase]" — say "[substitute]" instead. [Priority note if compliance-related.]
- "[Word/phrase]" — [why]

**Be specific:** [Numbers rule with real examples from the brand.]

**[Emoji / iconography stance.]**

## 05 — Imagery

[Illustration vs photo lead. Temperature. Contrast. Backdrop rules.]

**Product illustrations:** [List.] Files: `assets/images/illustrations/` — [filenames].

**The mascot / character:** [Fixed attributes, expression states, default, forbidden surfaces.]

**[Decorative elements]:** [Variants per surface.]

**[Sequential system, if any]:** [Steps.]

[File specs: format, transparency, max size, what it's right for, how to get more.]

## 06 — Photography

[Source of the photography and rights statement in plain language.]

**Product:** [Shots that exist.]
**[Category 2]:** [Shots that exist.]
**[Category 3]:** [Shots that exist.]

Files: `assets/images/product/` ([n]) and `assets/images/lifestyle/` ([n]) — resolution range, what it's right for, how to get originals.

## 07 — Using these

**You're welcome to:**
- [Free uses]

**Please check with [Brand] first:**
- [Gated uses]

**Things this kit doesn't cover:**
- Creator and UGC content — [per-agreement note]
- [Print/vector originals note]

Contact: [Name/role/channel, or "your [Brand] contact"]

---

## Assets saved in `assets/`

[Dedup note if applicable.]

- `fonts/` ([n] files) — [filenames per face/weight]. [License scope reminder.]
- `logos/` ([n] files) — [filenames]
- `images/product/` ([n] files) — [filenames, grouped by product]
- `images/lifestyle/` ([n] files) — [one-line summary of scenes]
- `images/illustrations/` ([n] files) — [summary]

**Category status:** Fonts [complete / gaps] · Logos [complete / gaps] · Product [complete / gaps] · Lifestyle [complete / gaps] · Illustrations [complete / gaps / none exist]

**Found but below the bar** (exists, not saved — ask for the original):
- [what] — [URL] — [why it failed]

**Not here — ask the brand contact:**
- [what, and where it is likely to come from]

---

## Kit notes

*Provenance: [n] rules stated / [n] observed / [n] inferred. Inferred rules are marked inline.*
*Conflicts found: [e.g. brand book says X, live site does Y — kit follows the live site]*
*Gaps: [anything a designer or writer will hit that this kit can't answer]*
```

### Writing rules for the kit itself

- **Write rules as instructions, not descriptions.** "Put the purple mark on cream" beats "the purple mark is often shown on cream."
- **Keep the brand's voice in the kit.** A kit for a warm, witty brand should read warm and witty. "Please do / Please don't" over "Permitted / Prohibited" when that's the brand. Match the register of the source.
- **One example beats three adjectives.** Wherever a rule can be shown with a real headline, hex code, or filename, show it.
- **Name the trap in every section.** Logo that disappears, color that gets overused, font that gets used for the wrong job, word that creates legal exposure, photo set that can't be used in ads. Kits exist to prevent the predictable mistake.
- **Hex codes in backticks, filenames in backticks, real copy in quotes.** Consistency makes the kit scannable.
- **No filler sections.** If the brand has no mascot, delete the mascot lines. If there's no photography, say "No photography exists — illustration only" and move on. An empty template heading is worse than a missing one.
- **Tag inferences inline.** `[inferred]` at the end of any rule the brand didn't state. A reader should be able to see at a glance what's law and what's your recommendation.

---

## PHASE 5: DELIVER

1. **Save** the kit as `brand/brand-kit.md`. The asset files are already in their `assets/` folders from Phase 3 — confirm every file the kit names actually exists at that path.
2. **Present** the kit and the asset inventory to the person
3. **Lead with status** — one line on where the kit came from and how much is confirmed vs inferred
4. **Flag the three things that matter most** — usually a licensing constraint, a compliance word swap, and the UGC-rights gap. These are the ones that cost money if missed.
5. **State the asset gaps in one line** — which of the five categories are complete and which need a human to chase originals. If fonts or logos are incomplete, say so plainly: `app-generation` cannot run on-brand without them.
6. **Ask one closing question:**

> "Anything here that doesn't match how the brand actually shows up? Once you confirm, this is the identity reference for every design and copy task on [Brand]."

---

## Downstream handoff

Once confirmed, the kit is the visual and verbal source of truth. Reference it explicitly:

- **`app-generation`** — reads `brand/brand-kit.md` and pulls fonts, logos, and imagery straight from the `assets/` folders. It stops if the kit or the fonts are missing.
- **Static ad design / landing pages / decks** — palette, type, logo rules, priority-color rule, imagery temperature
- **Copywriting skills** (hook writing, scripts, captions — and any copy-standards skill present in the environment) — the Sounds Like Us / Never Say lists and register rules layer on top of them; where they conflict, the brand's compliance swaps win, the human-sounding rules win everywhere else
- **Ad QA** — the Common Mistakes and Please Don't lists are the QA checklist
- **Creator briefs** — the voice section plus the UGC-rights note, so creators know the register and the team knows what they can reuse

Pair with `brand-overview` and the research folder for strategy. Kit answers "how do we look and sound"; research answers "who are we talking to and why should they care." Neither replaces the other.
