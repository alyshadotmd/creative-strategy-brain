# Concepts

The register of every ad concept. One row per concept folder in `pipeline/`.

Written by `creative-engine` at the end of every pass and updated as each concept moves. It replaces having a separate log and roadmap — those were two registers of the same rows, which drift.

Read it two ways:

- **Down the status column** for what is in flight and what is waiting on someone
- **Across persona, stage and angle** for coverage gaps — which personas have no upper-funnel concepts, which stages have only one trigger moment, which angles have never been tested

| # | Opened | Pain / desire | Persona | Stage | Trigger moment | Angle | Offer | Format | Hook | Status | Waiting on | Result |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
|   |   |   |   |   |   |   |   |   |   |   |   |   |

A row with a blank column is not a finished concept. Every row is a full walk of the map.

**Column notes**

- *#* — the concept folder in `pipeline/`. The same number appears in the ad name, so performance data traces back here.
- *Persona* — the file in `1. research/customer/personas/`
- *Stage* — the awareness stage the persona is in when the ad finds them
- *Trigger moment* — one line, named by circumstance; the stage transition it drives is implied by *Stage*
- *Angle* — the file in `2. ideate/messaging-angles/`
- *Offer* — the one- or two-sentence offer statement
- *Format* — the format in `2. ideate/visual-formats/`
- *Hook* — the opening line, or a reference into `2. ideate/hooks/`
- *Status* — `concept` · `scripted` · `briefed` · `in production` · `in QA` · `live` · `retired`
- *Waiting on* — the person or step blocking it. A concept with no status change and nothing here is stalled, not in progress.
- *Result* — the teardown in `4. analyze/teardowns/`
