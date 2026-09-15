# Brain Organization SOP

This is the map for where things live in the brain. Read it before saving anything. When you save something durable, put it in the right home below. If it's a skill, add it to the skills table in this file.

The brain is organized around the creative strategy flywheel (numbered folders) plus a set of support folders. One brain holds one brand.

**New brand? Start with `skills/brain-setup/SKILL.md`.** It fills `assets/` and `1. research/` from a website URL and hands off to the rest of the system.

## The flywheel folders (numbered)

Each numbered folder represents one stage of the creative strategy flywheel. Save stage-specific knowledge, source material, and skills inside the matching stage.

| Folder | What goes here |
|---|---|
| `1. research` | Anything about customer research or product research. `brand/` holds the brand's own overview, `product/` one facts-only profile per product, `customer/reviews/` and `customer/ad comments/` the voice of customer, `customer/personas/` the personas the engine reads, `competitors/<brand>/` one folder per competitor with the same `brand/`, `product/`, `customer/` shape, plus `creators/` and `articles/`. |
| `2. ideate` | Anything about generating new ad ideas and turning them into briefs. The creative strategy engine lives here with the libraries it draws on — `visual-formats/`, `messaging-angles/`, `hooks/` (each has a README saying what goes in it) — plus the concept log `ad-concepts.md`, the briefs themselves, and briefing skills/templates. |
| `3. create` | Anything about producing, checking, and shipping the actual creative. Static and video production workflows, generation skills, production reference material, QA checklists, compliance/claims checks, launch ops, naming/tagging conventions, and handoff checklists. |
| `4. analyze` | Anything about post-launch performance analysis. Reporting frameworks, teardown protocols, creative analysis skills, what-worked/what-didn't learnings. |

## Support folders (not numbered)

| Folder | What goes here |
|---|---|
| `assets` | Brand assets, flat (one brand). `fonts/`, `logos/`, `images/product/`, `images/lifestyle/`, `images/illustrations/`, and the brand kit at `assets/brand-kit-<brand>.md`. Filled by the `brand-kit` skill; read by `app-generation`. |
| `team` | One folder per person on the team. Each person stores context they need that is not relevant to the rest of the team. Example: `team/<name>/...` |
| `integrations` | One folder per integration. Store context that helps the assistant navigate that specific integration (what its data means here, where to find what, how to read it). Example: `integrations/<app>/index.md` |
| `strategy` | Business context: what matters to the business, current business objectives, and priorities right now. |

## Where skills go

There are two homes for skills. Pick by scope:

- **Stage skills** belong to one flywheel stage. Save them inside that stage's `skills` folder: `<numbered stage>/skills/<skill-name>/SKILL.md`.
- **Cross-stage skills** are used across all four stages, or build out a support folder (for example, `app-generation`, or `brand-kit`, which fills `assets/`). Save these in the top-level `skills` folder: `skills/<skill-name>/SKILL.md`.

If a skill is only ever run during one stage, it is a stage skill — even if other stages read its output.

To save a skill:
1. Decide the scope: one stage, or cross-stage / support folder.
2. Open the matching `skills` folder (inside the stage, or top-level).
3. Make a folder named after the skill.
4. Save the skill inside that folder as `SKILL.md` (SKILL in all uppercase).

## Skills in the brain today

| Skill | Path | Scope |
|---|---|---|
| `brain-setup` | `skills/brain-setup/SKILL.md` | Cross-stage — onboards a new brand; fills `assets/` and `1. research/` |
| `brand-kit` | `skills/brand-kit/SKILL.md` | Cross-stage — builds the brand kit and harvests assets into `assets/` |
| `app-generation` | `skills/app-generation/SKILL.md` | Cross-stage — builds on-brand apps, reports, dashboards from the kit |
| `product-info` | `1. research/skills/product-info/SKILL.md` | Research — facts-only profile per product (own brand or competitor) |
| `brand-overview` | `1. research/skills/brand-overview/SKILL.md` | Research — brand overview (own brand or competitor) |
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

