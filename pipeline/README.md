# Pipeline

Where ads live while they move through the workflow. One folder per ad.

The numbered flywheel folders hold knowledge that applies across every ad — customer truth, the engine and its libraries, the production method, the learnings. None of them holds an instance. The pipeline is where instances live, and it reads from all four.

## The rule

**The pipeline holds documents. `assets/` holds media.**

Raw clips get repurposed. A finished ad gets cut back up. So no media file lives inside a concept folder — footage goes to `assets/footage/<shoot-or-creator>/`, finished cuts go to `assets/ads/<ad-name>/`, and the concept folder points at them by path. A later concept that wants the same clip references the same path; nothing is duplicated, and nothing has to reach into another concept's folder.

## What a concept folder holds

Copy `_template/` to start one. Create only the files that concept actually needs — a static has no script, and an empty file reads as unfinished work rather than an absent one.

| File | Written at | What it holds |
|---|---|---|
| `overview.md` | ideate | Where the idea came from, the hypothesis, the persona, the angle, the awareness stage, the format, and the current status. The rationale both the script and the brief are built on — so it lives in neither. |
| `references.md` | any | Inspiration, the ads that sparked it, and paths into `assets/` for any media this concept uses. |
| `script.md` | create | The spoken lines and the beats. Video only. |
| `brief.md` | create | Instructions to whoever produces the final asset — editor or designer. |
| `qa.md` | create | The pre-launch review, written against `script.md`, `brief.md`, and the brand's claims list. |
| `ad-name.md` | create | The launched name, or names if the concept shipped in variants. |

## Two QAs, two places

`qa.md` here is **pre-launch**, and it asks whether the delivery matches what was asked for — did they shoot the script, does it clear the claims list, is it on brand. It gates the launch.

The **post-launch** teardown asks why the ad performed the way it did, references the live ad and its performance data, and is read against other ads rather than on its own. That belongs in `4. analyze`, filed under the ad name. `overview.md` carries the status and points at it.

## Naming

`<number>-<short-slug>`, numbered in the order concepts are opened. The number is what makes a concept traceable from its ad name back to its rationale, so it should appear in the ad name too.

## Status

Tracked as a field in each `overview.md` and summarized across concepts in `roadmap.md`:

`concept` · `scripted` · `briefed` · `in production` · `in QA` · `live` · `retired`

## Relationship to the concept log

`2. ideate/ad-concepts.md` stays the index — one row per concept, pointing at its folder. Read the log to see coverage across personas, stages and angles. Open the folder to work on one ad. Do not merge them.
