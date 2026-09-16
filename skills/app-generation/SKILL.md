---
name: app-generation
description: Builds and restyles apps (Astro pages, reports, dashboards, matrices, docs) so every one ships fully custom-branded to the brand whose kit lives in the brain's assets folder. Use this before any app build, app restyle, "make this look on-brand", "build me a dashboard/report/matrix/doc page", or when a page is showing the stock design system look. Reads the brand kit at assets/, translates it into a CSS token sheet, font-face declarations, a typography map, and component recipes, then runs a QA pass. Standing rule: never ship an app in a default design-system presentation — no stock base-layout theme, no stock scaffold styling, no stock component-library themes. This skill is how.
---

# App Generation

Every app is fully custom-branded. Not "themed" — the stock framework look must be gone entirely. The brand kit in `brand/` is the only source of truth for what the app looks like; this skill is the method for turning that kit into a working page.

**Standing rule (applies to every app, no matter who asks):** never ship an app in a default design-system presentation — a stock base-layout theme, stock scaffold styling, or a stock component-library theme. Read this skill before every build or restyle.

---

## STEP 0: LOAD THE BRAND KIT

Before writing a line of markup, read the kit and locate the assets.

**Canonical sources (brain paths):**

| What | Where | Notes |
|---|---|---|
| Brand kit — rules, hexes, voice | `brand/brand-kit.md` | The output of the `brand-kit` skill (saved as `brand/brand-kit.md`). If it isn't there, stop and run that skill first — do not invent a palette. |
| Fonts | `brand/fonts/` | Licensed to the brand for brand work only. Read the kit's licensing note before use. |
| Logos and mascot | `brand/logos/` | The kit's 01 — Logo section says which mark goes on which surface. |
| Illustrations | `brand/illustrations/` | Sparkles, shapes, mascot states, how-it-works steps — whatever the kit's 05 section lists. |
| Photography | `assets/images/product/`, `assets/images/lifestyle/` | Rights per the kit's 06 section. |
| Built examples | wherever this environment keeps apps built for this brand | If a prior on-brand app exists, copy its **structure, tokens and components**. Check its fonts against the kit — older apps may predate a font decision. |

**Read these kit sections in order and pull the values you need:**

1. **02 — Color** → every hex with its job → becomes the token sheet (Step 2)
2. **03 — Type** → typeface names, weights, casing rules, signature treatments, licensing → becomes @font-face + typography map (Steps 1, 3)
3. **01 — Logo** and **05 — Imagery** → which mark on which surface, the disappearing-mark trap, mascot rules → header mark and illustration placement (Step 5)
4. **04 — Voice** → person, banned words, compliance swaps, emoji stance → UI microcopy rules (Step 6)
5. **Kit notes** → anything flagged [inferred] is a recommendation, not law; if a design choice hinges on it, say so in the handoff

If the kit is missing a value you need (a muted label color, a border color, a hover tint), derive it from the palette logic — a lighter step of the ink, a tint of the support color — and list every derived value in the handoff so the brand can confirm.

---

## STEP 1: PAGE SETUP

- Build the page as a standalone `src/pages/index.astro` that owns its full `<head>` and styling. If a shared base layout is used instead, every component-library default must be fully overridden — remember some libraries ship a global stylesheet that injects styles onto native elements (see the dropdown recipe in Step 4).
- **Copy the font files** from `brand/fonts/` into the app's `src/fonts/` — NOT `public/`. Vite must resolve the URL under the app's route prefix.
- **Never load Google Fonts** or any external font for a branded app. If the kit's fonts aren't in `brand/fonts/`, stop and ask for them; do not substitute.
- Declare each face once. Pattern (fill in the kit's typefaces and the weights you actually have files for):

```css
/* One @font-face per file. Family names prefixed with the brand so nothing collides with system fonts. */
@font-face { font-family: "[Brand] [Display]"; src: url("../fonts/[Display-Heavy].otf") format("opentype"); font-weight: 700 900; font-display: swap; }
@font-face { font-family: "[Brand] [Display]"; src: url("../fonts/[Display-Medium].otf") format("opentype"); font-weight: 400 600; font-display: swap; }
@font-face { font-family: "[Brand] [Editorial]"; src: url("../fonts/[Editorial-Bold].otf") format("opentype"); font-weight: 600 800; font-display: swap; }
```

- Static images (mascot, logos, product shots) go in `src/assets/` and are imported in frontmatter, not referenced by raw path.
- If content is DOM-injected by a client `<script>`, style it with `:global(...)` selectors — Astro's scoped CSS won't reach injected markup.

---

## STEP 2: TOKEN SHEET

Map the kit's color groups onto these token roles at `:root`. Keep the role names stable across every app so components are portable; only the hex values change per brand.

| Token | Kit source (02 — Color) | Job |
|---|---|---|
| `--ground` | Surfaces group — page background | Page background. The stock theme's background must never show. |
| `--surface` | Surfaces group — cards | Card background |
| `--surface-2` | Surfaces group — secondary panel | Panels, sticky table headers |
| `--ink` | Ink group — primary | Body type, lines, CTAs, outlines. Body copy is this, never `#000`. |
| `--ink-2` | Ink group — secondary | Secondary text |
| `--ink-3` | Derive: lighter step of ink | Muted labels, kickers |
| `--rule` | Support group — lightest | Default borders |
| `--rule-2` | Support group — mid | Stronger borders, hover shadows |
| `--signal` | Signal group — primary | THE priority color. Governed by the frequency rule below. |
| `--signal-soft` | Signal group — soft tint | Hovers, tints |
| `--signal-deep` | Signal group — shadow/sticker | Stickers, shadows |
| `--support`, `--support-2` | Support group fills | Pill backgrounds, mascot fills |
| `--accent` | Accents group | Warnings, guesses, kid/secondary flags — sparing |
| `--deep` | Ink group — darkest | Night strips / inverted bands only. Never a default background unless the kit says so. |
| `--card-shadow` | Derive from kit's shadow color | Hard offset (`3px 3px 0 <rule>`), no blur — unless the kit specifies a soft shadow system |
| `--card-shadow-hover` | Derive | Same offset, `--rule-2` |

Optional: a `:root[data-theme="dark"]` block remapping the same tokens onto the kit's dark ramp, if the app warrants a toggle and the kit has a dark surface.

### Color rules — read them out of the kit's "The rules" and enforce them

Most kits have a version of each of these. Copy the brand's exact wording into a comment above the token sheet.

- **The priority rule.** One `--signal` moment per screen: one highlighted phrase, one featured number, one active tab. Never two competing signal blocks in a viewport.
- **Density rule.** Two to three colors per card or section.
- **Body copy color.** `--ink`, never pure black.
- **Deep is not a background** (unless the kit says otherwise). Type, lines, CTAs, the occasional inverted strip.
- **Surface sequencing.** The kit's "common mistakes" usually name a bad sandwich (e.g. pure white between cream and signal). Honor it.

<details>
<summary>Worked example — token sheet shape (placeholder values, stable role names)</summary>

Hexes below are placeholders. Every value comes from the brand kit; only the role names stay fixed.

```css
:root{
  --ground:#FAFAF8;   --surface:#FFFFFF;   --surface-2:#F4F3EF;
  --ink:#1F2933;      --ink-2:#3E4C59;     --ink-3:#7B8794;      /* ink-3 derived */
  --rule:#E4E7EB;     --rule-2:#CBD2D9;
  --signal:#D8A200;   --signal-soft:#F7ECC4;  --signal-deep:#A87B00;
  --support:#E4E7EB;  --support-2:#CBD2D9;    --accent:#E8D5CF;
  --paper-cool:#F7F8FA;  --deep:#14181C;
  --card-shadow:3px 3px 0 var(--rule);  --card-shadow-hover:3px 3px 0 var(--rule-2);
}
```
Fonts: the kit's display face (heavy + medium weights) plus its editorial face. Priority rule: one signal moment per screen. Honor any surface restriction the kit states for the brand mark or mascot.
</details>

---

## STEP 3: TYPOGRAPHY MAP

The kit's 03 — Type section assigns each face a **job** and a **casing**. Translate that into three roles:

| Role | What it owns | Typical kit pattern |
|---|---|---|
| **Structural** | Kickers/eyebrows, section numbers, tab nav, buttons, pills/chips, table headers, stat labels, pricing numerals | Display face, heavy weight, all caps, tracked ~.07–.12em. Kicker: ~11–12px, wide tracking, muted (`--ink-3` or ~62% opacity). |
| **Emotional** | Page h1, section headlines, card titles, pull-quote one-liners | Editorial face, sentence case, non-italic by default |
| **Body/UI** | Long-form copy, table cells, form labels | The display face's medium weight, or whichever face the kit ships in a readable weight. If the editorial face only ships in Bold, it is **not** the body face. |

Rules that travel across brands:
- Pricing numerals run 2–3× the labels around them (check the kit for the brand's number).
- Set the family **explicitly** on card titles and any `<h3>`/`<h4>` inside components — bare headings inherit the global heading font and will drift.
- **Signature treatments — pick ONE per screen.** The kit will name them (marker highlight, hand-drawn underline, tilt). Implementation patterns:
  - *Marker highlight:* `::before` block of `--signal` behind the word, small rotation (~-1.5deg), `z-index` under the text.
  - *Hand-drawn underline:* inline SVG squiggle positioned under the word.
  - Never two treatments in one viewport, and a treatment counts toward the priority rule if it uses `--signal`.

---

## STEP 4: COMPONENT RECIPES

If a prior on-brand app exists for this brand, copy its working CSS instead of re-deriving. Otherwise build from these. Every recipe uses tokens only — no raw hexes in component CSS.

- **Masthead:** brand mark (kit says which — mascot vs logo, and on which surface), structural kicker with dot separators, emotional h1 with one signature-treated word, 2px `--rule` bottom border, optional illustration from `brand/illustrations/` absolutely positioned top-right.
- **Sticky tab nav:** `position:sticky; top:0`, structural all-caps links, hover `--signal-soft`, active tab solid `--signal` with ink text. **The active tab is the screen's signal moment** — nothing else on that screen gets `--signal`.
- **Cards:** `--surface` or `--surface-2` background, 1.5–2px border in `--rule`/`--rule-2` (`--ink` border for emphasized cards), radius ~10–14px, `var(--card-shadow)`. Flat offset, never blurred — unless the kit's imagery section says the brand uses soft shadows.
- **Chips/pills:** structural face, all caps, ~10px, `--support` fill with ink text. `--accent` variant for warnings/guesses. Outlined variant with `--rule-2` border.
- **Pill toggle:** segmented control of structural pills, active pill filled, `role="tablist"` semantics.
- **KPI strip:** row of stat cards, structural label + oversized numeral, optional small sub-line inside the same card (a short qualifier such as an active count) rather than a separate card.
- **Section heads:** 60px column with an oversized muted section number, emotional h2, one-line sub in `--ink-2`.
- **Collapsible dropdowns (`<details>/<summary>`) — full suppression stack, no exceptions.** Hard-won across three debugging rounds. Every `<summary>` on the page, including bare unstyled ones, needs ALL of:
  1. `list-style:none`
  2. `appearance:none` (Safari specifically)
  3. `::-webkit-details-marker{display:none}`
  4. `::marker{content:none}`
  5. `::after{content:none !important; display:none !important}` — a component library's global stylesheet may inject a masked-SVG chevron via `summary::after`
  6. then your custom `::before` chevron with `order:-1`

  Miss any layer → double chevrons.
- **Lightbox (native `<dialog>`):** explicit background (`--surface` or `--ground`) and explicit font family — unstyled dialogs render dark/serif. Close button + click-on-backdrop close (`if (e.target === dialog) dialog.close()`). Event delegation for open buttons when cards are script-rendered.
- **Inline video cards:** real `<video controls poster=...>` so creatives play in place; 9:16 media frames for vertical ad content.
- **Bar charts:** hand-built — left labeled y-axis with gridlines at 5 even intervals behind bars, dual bars per row (primary metric `--ink`, secondary `--signal`), value labels floating directly above their own bar, thumbnail true-centered under each pair via shared grid columns. No charting library at this scale. Note: if a chart uses `--signal` for a series, that is the screen's signal moment.
- **Compare tables:** sticky header row in `--surface-2` with structural all-caps headers, 1.5px `--rule` row borders.
- **Jump-chip index:** row of chip links anchoring into long docs.

---

## STEP 5: IMAGERY AND MARKS

Pull these straight from the kit's 01 and 05 sections — they are brand-specific and non-negotiable:

- **Which mark lives on which surface.** The kit names the trap (the surface where a mark disappears). Never place a mark there.
- **Mascot/character rules** if the brand has one — fixed colors, default expression at avatar size, forbidden surfaces.
- **Logo integrity:** never recolor, rotate, stretch, add effects, or rebuild the wordmark.
- **Decorative illustrations:** use the surface-matched variant (the kit ships color variants per surface for a reason).
- **Illustration vs photography lead:** follow the kit. Only use photography from `assets/images/` and only per the kit's rights note.
- **Temperature:** if the kit says warm/no clinical white/no cool tones, that applies to every gradient, placeholder and empty state too.
- **Emoji:** follow the kit's stance exactly. Most kits ban emoji in UI with at most one exception (e.g. ★ for review stars). Playfulness comes from the mascot and illustrations, never from Unicode.

---

## STEP 6: UI MICROCOPY

From the kit's 04 — Voice:

- Person and register (usually second person, warm, specific). Never the words the kit says never to call the customer ("users", "consumers").
- **Banned list** — every label, empty state, tooltip and button passes it.
- **Compliance swaps** — these are the ones with legal weight (e.g. "clinically studied", never "clinically proven"). Treat as blocking.
- Real numbers over vague claims in labels and stat lines.
- Layer the environment's copy-standards skill on top for anything longer than a label, if one is present.

---

## STEP 7: QA CHECKLIST (before handoff)

1. **No default-theme leakage.** Page background is `--ground`; no stock component-library look anywhere; no inherited scaffold styling.
2. **Fonts render as the kit's faces** (check a headline and a pill) and load from `src/fonts/`. Network tab shows no Google Fonts and no fallback families.
3. **Exactly one `--signal` moment per viewport; one signature treatment per screen.**
4. **Body text is `--ink`, not black; `--deep` used only as type/lines/inverted strip** (or as the kit allows).
5. **Every `<summary>` on the page has the full six-layer chevron suppression** — check Safari specifically.
6. **Dialogs have explicit background + font.**
7. **Marks obey the surface rules.** No mark on its disappearing surface; mascot rules honored.
8. **No emoji beyond the kit's exception. Microcopy passes the never-say list and compliance swaps.**
9. **Font licensing.** These files and this styling are for this brand's apps only — never reused for other brands' work. Confirm the kit's licensing note allows the use.
10. **Derived values listed.** Every token you derived rather than read from the kit is named in the handoff for the brand to confirm.

---

## HANDOFF

Deliver with:
- One line naming the kit version used (its `Saved:` date) and any prior app copied from
- The list of derived tokens (Step 0) and any [inferred] kit rules a design decision leaned on
- Confirmation the QA checklist passed, with the Safari check called out

If a decision in this build should become standing policy (a new font choice, a new component pattern, a fixed bug), save it back to the brain: component recipes go in this skill, brand rules go in the kit via `brand-kit`, and the app itself becomes the next "built example" in Step 0's table.
