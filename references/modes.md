# Mode Steps and Output Templates

Follow these closely. Repeat runs the same week should be shorter — report deltas, don't re-list unchanged state.

## `ops` — COO health check

Steps:

1. Read dossier: `workstreams.yaml`, `metrics.yaml`, `advice_log.yaml`, `decisions.yaml`.
2. Pull Granola meetings involving this company since the last run — extract decisions, commitments, blockers. Write new ones to the dossier with `source` provenance.
3. Pull Gmail (last 7 days) for threads implying work owed to/from the company; Calendar for the coming week's commitments.
4. Compute: stalled workstreams (14+ days quiet), overdue advice checks, decisions past revisit, stale metrics (30+ days).

Output template:

```
## Ops — [Company], [Date]

### Health
[one line per dimension: pipeline/demand, delivery, cash (or "blind — no finance data"), people. Green/yellow/red with the reason.]

### Since last check
[decisions made, commitments landed, blockers cleared — with provenance]

### Workstreams
| # | Workstream | Status | Next step | Due | Flag |
[priority order; flag = stalled/blocked/slipping]

### Open advice past check date
[each: recommendation, age, evidence found. Skip section if none.]

### The one thing
[the single most consequential item this week and why]
```

## `advise <topic>` — consultant/coach session

Read `references/advisory.md` first. This mode is a conversation, not a report.

Steps:

1. Read the dossier; check whether this topic has prior advice or decisions attached.
2. Diagnose: identify which constraint the topic actually touches. Ask at most 2-3 sharp questions if the dossier can't answer them.
3. Pull evidence — connectors, dossier metrics, web search for outside benchmarks.
4. Deliver a position: recommendation, reasoning, expected effect, what would change your mind.
5. Log to `advice_log.yaml` with owner and check date. If the user rejects it, log that too, with their reason.

No fixed template. Rules: one recommendation at a time; name the constraint you believe is binding; give the counter-case honestly; end with the specific next step and who owns it.

## `stack` — systems & AI audit

Read `references/advisory.md` (stack section) first.

Steps:

1. Read `systems.yaml`. If empty or stale (90+ days), run the inventory interview: what tools, what cost, who owns, what talks to what.
2. Map domains: customer, money, work, docs, comms, marketing. Identify system of record per domain.
3. Web search current pricing/capabilities for anything you're about to recommend — training data on SaaS tools is reliably stale.
4. Assess fit-for-stage, integration gaps, overlap, and AI-layer opportunities ranked by hours saved.

Output template:

```
## Stack Audit — [Company], [Date]

### System-of-record map
| Domain | System | Status |
[status: healthy / no system of record / contested (2+ systems)]

### Findings
[numbered, severity-ordered: overlap, gaps, integration debt, overpayment, underuse]

### AI layer
| Opportunity | Where | Est. hours/wk saved | Effort |
[apply AI at the seams — data entry, drafting, triage, extraction, reporting — not as new silos]

### Recommendations
[max 3, sequenced. Each: change, cost delta, migration effort, expected effect. Log each to advice_log.]
```

## `program` — workstream / RAID review

Steps:

1. Read `workstreams.yaml` fully.
2. Cross-check against Granola transcripts and email since last run — detect activity the dossier missed, and dossier claims the evidence contradicts.
3. For each active workstream: is the next step still right, is the owner clear, is the blocker being worked?

Output template:

```
## Program Review — [Company], [Date]

### Alignment check
[do the top-3 priority workstreams actually serve the stated strategy in profile.yaml? Name any drift.]

### Board
| # | Workstream | Owner | Status | Next step | Blocker | Risk |

### Blockers needing escalation
[blockers older than 7 days with the suggested unblock action]

### Risks
[risks with [raised: N] counts; escalate per the dossier ladder]

### Cuts
[workstreams that should be killed or merged — be direct]
```

## `growth` — marketing & sales review

Read `references/advisory.md` (growth section) first.

Steps:

1. Read `metrics.yaml` funnel metrics; note what's blind.
2. Pull available signals: email threads with prospects, meeting cadence with leads (Calendar/Granola). If HubSpot is connected, pull real pipeline.
3. Map every current marketing/sales activity to a funnel stage and the number it should move.
4. Compute pipeline coverage and stage-stall if data allows.

Output template:

```
## Growth Review — [Company], [Date]

### Funnel snapshot
[stage → volume → conversion, marking every blind spot explicitly]

### Activity-to-outcome map
| Activity | Funnel stage | Metric it should move | Moving it? |
[activities that map to nothing get named as such]

### Pipeline
[coverage ratio vs target; deals stalled by stage; skip if blind]

### Keep / kill / fix
[each activity gets a verdict and one line of reasoning. Log material recommendations to advice_log.]
```

## `review` — monthly business review

Steps:

1. Full dossier read.
2. Metrics: month-over-month movement against targets.
3. **Advice-outcome audit**: every `done` recommendation gets outcome vs expected effect; every stale `open` gets the escalation treatment.
4. Decisions due for revisit: record outcomes.
5. Workstream throughput: shipped vs started (starting is easy; finishing is the metric).

Output template:

```
## Monthly Review — [Company], [Month]

### Scorecard
| Metric | Target | Last month | This month | Trend |

### What shipped / what didn't
[throughput, honestly]

### Advice audit
[recommendation → what happened → verdict, including your own misses]

### Decision revisits
[decision → expected → actual]

### Patterns
[recurring drags or wins across the month — the consultant's-eye view]

### Watchdog noise audit
[alerts fired vs acted on; threshold tuning proposals if acted-on rate < 50%. Skip if no alerts.]

### Next month's one thing
```

## `plan` — quarterly planning

Steps:

1. Run a compressed `review` of the quarter first — planning without retrospective is fantasy.
2. **Calibration scoring.** Across all resolved advice this quarter (all companies): acceptance rate, hit rate against expected effects, and both broken out by domain (ops / stack / growth / pricing). Compare stated confidence to actual hit rate. Report it plainly — "I ran 78% on stack advice but 40% on growth; discount my growth confidence accordingly" — and carry the adjustment into future recommendations. Append the quarter's scores to `calibration.yaml` at the workspace root so the trend is visible.
3. Pull structural risks and constraints from `profile.yaml`.
4. Facilitate, don't dictate: propose 3 candidate quarterly priorities with reasoning, then shape the user's choices into the plan.
5. Write the result: update `profile.yaml` constraints if changed, reset `workstreams.yaml` priorities, set metric targets, log the plan as a decision with a revisit date at quarter end.

Output: quarter plan with at most 3 priorities, each with an owner, a metric, and a kill criterion ("we stop if X").

## `client <name>` — switch or onboard

**Switch:** update `active_company.txt`, confirm in one line, run a 5-line context refresher from the dossier (last session, open advice, top workstream).

**Onboard (no dossier exists):** create the directory and `git init` it, then build the dossier by the cheapest reliable path:

*Document intake (preferred when documents exist).* If the user can provide a folder or files (P&L, org chart, contracts, tool invoices, proposals, prior consultant reports), read them and draft the full dossier befo