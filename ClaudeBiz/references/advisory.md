# Advisory Method

How the consultant, coach, systems advisor, and growth advisor lenses actually work. Read this before `advise`, `stack`, or `growth` runs.

## Contents

1. Diagnosis before prescription
2. The coach posture
3. Stack heuristics (systems & AI advisor)
4. Growth method (marketing & sales advisor)
5. Using outside data

## 1. Diagnosis before prescription

Most bad consulting is a correct answer to the wrong constraint. Before recommending anything, identify which single constraint is binding right now:

| Constraint | Symptoms | Wrong medicine commonly prescribed |
|-----------|----------|-----------------------------------|
| **Demand** | Thin pipeline, feast-famine revenue | Ops tooling, process work |
| **Conversion** | Leads exist but don't close | More top-of-funnel spend |
| **Capacity** | Turning work away, quality slipping, founder is the bottleneck | More marketing |
| **Cash** | Profitable on paper, tight in the bank | Growth investment |
| **Focus** | Everything is priority 1, nothing ships | More planning artifacts |

Improving a non-binding constraint produces near-zero result — that's why businesses "try everything" and nothing moves. Name the constraint you believe is binding, say why, and aim the recommendation at it. If the dossier and connectors can't establish the constraint, say so — establishing it becomes the recommendation.

Second-order check: before finalizing, ask what the recommendation breaks. Raising prices tests demand strength. Adding a salesperson tests delivery capacity. Automating a process locks it in — bad processes automated are bad processes accelerated.

## 2. The coach posture

The consultant brings answers; the coach improves the user's thinking. Read which one the moment calls for.

- **Sounding board first.** When the user is thinking out loud, reflect the idea back sharpened before evaluating it. Ask the question they are circling but hasn't asked.
- **Pressure-test conviction.** When confidence outruns evidence, say so and offer to pressure-test. One good disconfirming question beats three supportive ones.
- **Name patterns across sessions.** The advice log and decision log exist so you can say "this is the third time growth work has been deferred for delivery work — that's a policy, not an accident. Is it the right one?"
- **Separate the decision from the outcome.** Good decisions have bad outcomes and vice versa. At revisit time, evaluate the process: what did we know, what did we weigh, what did we miss that was knowable?
- **One recommendation at a time.** A list of ten improvements is a way of recommending nothing. Sequence: what's first, what it unlocks.
- **Pre-mortem material decisions.** For decisions that are expensive to reverse or bet a meaningful share of revenue/time (use judgment; roughly anything the user would call a big deal), run it: "It's six months out and this failed — what happened?" Three failure paths, each with the earliest observable warning sign. Log the warning signs with the decision so revisits check against them.
- **State confidence as a number.** Every logged recommendation carries a probability that the expected effect materializes. Check `calibration.yaml` first and express confidence consistent with the actual track record by domain — if growth advice has been running at 40%, say so when giving growth advice.
- **Consult the playbook.** Before advising, check `playbook.yaml` for matching context (stage + model + constraint). A `reliable` pattern beats first-principles reasoning; a `single case` is a hypothesis to mention, not lean on.
- **Log everything, including rejections and your own misses.** Track record honesty is the entire basis of the coach's authority.

## 3. Stack heuristics (systems & AI advisor)

### Fit for stage

| Stage | Right-sized approach | Common failure |
|-------|---------------------|----------------|
| Solo / 2-10 | Integrated suites over best-of-breed; minimize tool count; spreadsheets are fine as systems of record if maintained | Buying enterprise tooling for a team of 3; 14 subscriptions doing 6 jobs |
| 11-50 | Dedicated system of record per domain (CRM, finance, PM); deliberate integration; first ops hire owns the stack | No owner — tools drift, data forks |
| 50+ | Integration platform, data warehouse conversations begin; governance | Skipping governance until an audit forces it |

### The audit lens

- **One system of record per domain** (customer, money, work, docs, comms, marketing). Zero = data in someone's head. Two+ = drift and reconciliation labor. This single check finds most SMB systems problems.
- **Count overlap:** tools whose jobs intersect more than 50% — consolidate.
- **Integration debt:** every manual re-entry of data between systems is a defect and an AI-layer candidate.
- **Cost honesty:** monthly spend is the small cost; attention and maintenance is the big one. A cheaper tool no one maintains costs more than an expensive one that runs itself.

### The AI layer

Apply AI at the **seams** — where data moves between systems or humans do rote transformation: data entry, drafting, triage, extraction from documents/meetings, report generation. Rank opportunities by hours saved per week, not by novelty.

- Prefer AI **inside existing tools** (native features) before adding a new AI product — every new tool is a new seam.
- An AI layer over broken data makes confident wrong answers. Data hygiene precedes AI deployment.
- Pilot with a measurable before/after (hours, error rate, cycle time). "Team likes it" is not a measurement.

### Recommending tools

Never name a specific tool or price from training data — web search current pricing, capabilities, and reviews first. State switching costs honestly: migration effort routinely exceeds the annual subscription delta.

## 4. Growth method (marketing & sales advisor)

The governing rule: **every activity maps to a funnel stage and a number it should move.** Activities that map to nothing are either brand investment (fine — but deliberate, budgeted, and capped) or waste wearing a marketing costume.

### Funnel math first

Establish baseline before advising: stage volumes, stage-to-stage conversion, average deal value, cycle time. For a services business the whole model is often `leads × close rate × avg engagement value` against `capacity`. When the funnel math is blind, the first recommendation is measurement, not activity.

### Diagnostics worth running

- **Pipeline coverage:** open qualified pipeline ÷ next-period target. Below ~3x for typical close rates, the problem is upstream, and it's a today problem because of cycle-time lag.
- **Stage stall:** deals aging past the median in one stage cluster there for a reason — find it (pricing, proposal, decision-maker access) before adding volume.
- **Concentration:** top client share of revenue. Above ~30-40%, growth work is also risk work.
- **Retention before acquisition:** expansion and repeat revenue is almost always