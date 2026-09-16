# Brain Organization SOP

This is the map for where things live in the brain. Read it before saving anything. When you save something durable, put it in the right home below. If it's a skill, add it to the skills table in this file.

The brain is organized around the creative strategy flywheel (numbered folders) plus a set of support folders. One brain holds one brand.

**New brand? Start with `skills/brain-setup/SKILL.md`.** It fills `brand/`, `assets/` and `1. research/` from a website URL and hands off to the rest of the system.

## The flywheel folders (numbered)

Each numbered folder represents one stage of the creative strategy flywheel. Save stage-specific knowledge, source material, and skills inside the matching stage.

**A numbered folder holds knowledge that applies across every ad. It never holds one ad.** Individual ads live in `pipeline/`, which reads from all four.

| Folder | What goes here |
|---|---|
| `1. research` | What was discovered about the market — never what the brand asserts about itself, which lives in `brand/`. `customer/reviews/` holds the voice of customer, `customer/personas/` the personas the engine reads, `competitors/<slug>/` one folder per competitor with a `brand/`, `product/`, `customer/` shape, plus `creators/`. |
| `2. ideate` | Anything about generating new ad ideas and turning them into briefs. The creative strategy engine lives here with the libraries it draws on — `visual-formats/`, `messaging-angles/`, `hooks/` (with its tactic library and opener swipe file) — The concept register lives in `pipeline/concepts.md`, not here — a log with one row per concept is instance data. |
| `3. create` | The method for producing, checking and shipping creative — not the creative itself. Script-writing, briefing, QA and naming skills, plus the reference material they read: `voice/`, brief templates, QA standards, compliance/claims checks, naming conventions, handoff checklists. The ads themselves live in `pipeline/`. |
| `4. analyze` | Post-launch performance analysis. The `creative-analysis` skill, reporting frameworks, and what-worked/what-didn't learnings across ads. `teardowns/<ad-name>.md` holds one teardown per launched ad — keyed to the ad name rather than the concept, because one concept can ship many ads. |

## Support folders (not numbered)

| Folder | What goes here |
|---|---|
| `pipeline` | One folder per ad moving through the workflow — its overview, script, brief, QA and launched name. Documents only; all media lives in `assets/`. See `pipeline/README.md`. |
| `brand` | Everything the brand asserts about itself: `brand-overview.md`, `brand-kit.md`, `claims.md`, `products/<product>.md` one per product, plus the identity files themselves in `logos/`, `fonts/` and `illustrations/`. Asserted facts, as opposed to the discovered ones in `1. research/`. See `brand/README.md`. |
| `assets` | The content library, flat (one brand). `images/product/`, `images/lifestyle/`, `footage/<shoot-or-creator>/` for raw clips, `ads/<ad-name>/` for finished cuts. An open pile that grows and gets drawn on per concept — it holds nothing that belongs to a single one, which is why footage and finished ads live here rather than in `pipeline/`. Brand identity files are not here; they are in `brand/`. |
| `team` | One folder per person on the team. Each person stores context they need that is not relevant to the rest of the team. Example: `team/<name>/...` |
| `integrations` | One folder per integration. Store context that helps the assistant navigate that specific integration (what its data means here, where to find what, how to read it). Example: `integrations/<app>/index.md` |
| `focus.md` | Not a folder — a single file at the brain root. What the work is pointed at right now: the objective, why now, the constraint, what is deliberately **not** being done, and how we'll know. Read it before opening a concept; check a concept against it before briefing. Positioning and audience live in `brand/` and `1. research/` — this is narrower and more perishable. |

## Where skills go

There are two homes for skills. Pick by scope:

- **Stage skills** belong to one flywheel stage. Save them inside that stage's `skills` folder: `<numbered stage>/skills/<skill-name>/SKILL.md`.
- **Cross-stage skills** are used across all four stages, or build out a support folder (for example, `app-generation`, or `brand-kit`, which fills `brand/` and `assets/`). Save these in the top-level `skills` folder: `skills/<skill-name>/SKILL.md`.

If a skill is only ever run during one stage, it is a stage skill — even if other stages read its output.

To save a skill:
1. Decide the scope: one stage, or cross-stage / support folder.
2. Open the matching `skills` folder (inside the stage, or top-level).
3. Make a folder named after the skill.
4. Save the skill inside that folder as `SKILL.md` (SKILL in all uppercase).

## Skills in the brain today

| Skill | Path | Scope |
|---|---|---|
| `brain-setup` | `skills/brain-setup/SKILL.md` | Cross-stage — onboards a new brand; fills `brand/`, `assets/` and `1. research/` |
| `brand-kit` | `skills/brand-kit/SKILL.md` | Cross-stage — builds the brand kit and harvests identity files into `brand/`, imagery into `assets/` |
| `app-generation` | `skills/app-generation/SKILL.md` | Cross-stage — builds on-brand apps, reports, dashboards from the kit |
| `product-info` | `1. research/skills/product-info/SKILL.md` | Research — facts-only profile per product (own brand or competitor) |
| `brand-overview` | `1. research/skills/brand-overview/SKILL.md` | Research — brand overview (own brand or competitor) |
| `brand-relevant-keywords` | `1. research/skills/brand-relevant-keywords/SKILL.md` | Research — the query bank for finding organic conversation |
| `customer-psychology-research` | `1. research/skills/customer-psychology-research/SKILL.md` | Research — the state a persona is in, and the moments the pain surfaces |
| `creative-engine` | `2. ideate/skills/creative-engine/SKILL.md` | Ideate — product and customer in, ad concepts out |
| `creative-mechanics` | `2. ideate/skills/creative-mechanics/SKILL.md` | Ideate — the structural move between an angle and a format |
| `yapper-hook-writing` | `2. ideate/skills/yapper-hook-writing/SKILL.md` | Ideate — three-part hook systems for talking-head video |
| `voice-copy-standards` | `3. create/skills/voice-copy-standards/SKILL.md` | Create — how copy sounds, applied to every skill that writes words |
| `creative-analysis` | `4. analyze/skills/creative-analysis/SKILL.md` | Analyze — diagnose why an ad is or isn't working |
| `review-audit` | `1. research/skills/review-audit/SKILL.md` | Research — mines reviews for pains, desires, triggers, personas, language |
| `persona-messaging-matrix` | `1. research/skills/persona-messaging-matrix/SKILL.md` | Research — builds the branded persona & messaging matrix app from reviews (own or competitor); writes personas to `customer/personas/` |
| `creative-engine` | `2. ideate/skills/creative-engine/SKILL.md` | Ideate — the creative strategy engine: pain/desire → persona → stage → trigger moment → angle → offer → format → hook |
| `creative-analysis` | `4. analyze/skills/creative-analysis/SKILL.md` | Analyze — diagnoses why an existing ad is or isn't working |

Add a row here whenever a skill is added, moved, or renamed.

## Quick decide

- Is it a reusable how-to workflow? It is a **skill** -> `<stage>/skills/<name>/SKILL.md` if it belongs to one stage, `skills/<name>/SKILL.md` if it runs across stages or builds out a support folder.
- Is it about the customer, the product, or competitors? -> `1. research`.
- Is it about coming up with ideas or briefing them? -> `2. ideate`.
- Is it about making, checking, or launching creative? -> `3. create`.
- Is it about how creative performed after launch? -> `4. analyze`.
- Is it a brand asset (font, image, logo, guideline)? -> `assets`.
- Is it context only one teammate needs? -> `team/<name>`.
- Is it about reading a connected tool? -> `integrations/<app>`.
- Is it about business goals and priorities? -> `strategy`.

