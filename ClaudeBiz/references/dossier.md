# Dossier Management

One directory per company in the Business Agent workspace folder (path chosen at first run and recorded in Cowork auto-memory), under `companies\<slug>\`. Slug is lowercase-hyphenated ("acme-consulting"). `active_company.txt` at the workspace root holds the active slug — update it whenever context switches, and confirm the switch to the user in one line so they always know whose books are open.

Dossiers are the source of truth. Connectors provide fresh signals; the dossier records what those signals mean. When a run produces new understanding (a decision surfaced in a transcript, a blocker mentioned in email), write it back — an unwritten insight is lost by next session.

## profile.yaml

Changes rarely. Rewrite sections, don't append.

```yaml
name: "Acme Consulting"
stage: "solo | 2-10 | 11-50 | 50+"
model: "one paragraph: who pays, for what, how it's delivered"
revenue_streams:
  - name: "Advisory retainers"
    share: "~70%"
    notes: "3 clients, monthly"
org:
  - person: "Jane Doe"
    role: "Founder"
    notes: "does sales + delivery — key-person risk"
constraints:
  - "Delivery capacity caps at 4 concurrent clients"
structural_risks:
  - risk: "Customer concentration — top client is 45% of revenue"
    first_flagged: "2026-07-01"
    status: "open"
relationship: "own | advisory client | prospective"
```

`relationship` matters: for the user's own business, be a COO (drive execution). For advisory clients, be a consultant (drive clarity and recommendations — the user drives execution through the client).

## systems.yaml

```yaml
systems:
  - tool: "HubSpot Starter"
    domain: "customer"       # customer | money | work | docs | comms | marketing | other
    cost_monthly: 20
    owner: "Jane"
    system_of_record: true   # exactly one per domain should be true
    integrations: ["Gmail (native)", "QuickBooks (Zapier)"]
    ai_layer: "none | native | external | opportunity"
    notes: "deal stages not maintained"
last_audit: "2026-07-09"
```

The `domain` + `system_of_record` fields power the stack audit: every domain needs exactly one system of record. Zero means data lives in someone's head; two or more means reconciliation work and drift.

## workstreams.yaml

The program coordinator's ledger. Updated every run.

```yaml
workstreams:
  - name: "Website relaunch"
    owner: "Jane"
    priority: 1              # rank, not label — forces trade-offs
    status: "active | blocked | stalled | done"
    next_step: "Approve copy draft"
    next_step_due: "2026-07-15"
    blockers:
      - "Waiting on brand photos from vendor"
    risks:
      - "Vendor has slipped twice — [raised: 2]"
    last_activity: "2026-07-07"
    source: "granola:2026-07-07 weekly sync"
```

Rules:
- `priority` is a rank. If two workstreams claim priority 1, force the call.
- `stalled` = no activity for 14+ days with no stated reason. Detect it; don't wait to be told.
- `[raised: N]` on risks tracks how many times flagged — same escalation ladder as advice (below).
- `source` gives provenance so the user can verify where a claim came from.

## decisions.yaml

Append-only. The point is to make decision quality reviewable, which almost no small business does.

```yaml
decisions:
  - date: "2026-07-09"
    decision: "Raise advisory rate to $X/mo for new clients"
    rationale: "At capacity; demand exceeds supply"
    alternatives_considered: ["hire subcontractor", "productize tier"]
    expected_effect: "Revenue per client +25%, possible slower close rate"
    revisit: "2026-10-09"
    outcome: null            # filled at revisit
```

Surface decisions past their `revisit` date in every mode. At revisit, record the outcome honestly — including "worse than expected." A decision log that only records wins teaches nothing.

## metrics.yaml

```yaml
metrics:
  - name: "MRR"
    definition: "Sum of active retainers"
    target: 25000
    alert_below: 18000       # optional watchdog tripwire — omit unless the user sets it
    alert_above: null
    values:
      - {as_of: "2026-07-01", value: 21500, source: "manual"}
  - name: "Pipeline coverage"
    definition: "Open qualified pipeline / next-quarter revenue target"
    target: 3.0
    alert_below: 1.5
    values:
      - {as_of: "2026-07-01", value: 1.8, source: "manual"}
```

Keep history — trend beats snapshot. If a metric hasn't been updated in 30+ days, flag it as blind rather than quoting the stale number as current.

`alert_below` / `alert_above` are the watchdog's only metric tripwires. They are set by the user, not inferred — a threshold they didn't choose produces alerts they won't trust. Health-check colors in `ops` mode also key off these where defined, so scoring stays stable run to run instead of drifting with the model's mood.

## advice_log.yaml

The accountability loop. Every recommendation from `advise`, `stack`, `growth`, or `review` mode gets an entry.

```yaml
advice:
  - id: "2026-07-09-crm-hygiene"
    date: "2026-07-09"
    mode: "growth"
    domain: "growth"          # ops | stack | growth | pricing | people | finance
    recommendation: "Enforce deal-stage updates weekly; 40% of pipeline is unaged"
    expected_effect: "Forecast reliability; stall detection"
    confidence: 0.7           # your stated probability the expected effect materializes
    owner: "Jane"
    check_date: "2026-07-23"
    status: "open | accepted | rejected | done | overtaken"
    rejected_reason: null
    evidence: []             # what you observed at each check
    outcome: null            # filled when resolved: what actually happened
    hit: null                # at resolution: true | partial | false vs expected_effect
```

`confidence` and `hit` feed quarterly calibration scoring (see `modes.md`, `plan` mode). State confidence honestly at write time — calibration only works if the number was a real belief, not a hedge.

### Escalation ladder

| State | Behavior |
|-------|----------|
| Open, before check date | Leave it alone. Nagging early erodes trust. |
| Open, past check date | Check evidence (connectors, dossier). Surface in the current run's brief. |
| Open, 2+ weeks past check | Lead the next `ops` brief with it. Quantify the cost of delay if possible. |
| Open, 4+ weeks past check | Direct challenge: still a priority, or should it be logged as rejected? Either answer is fine — limbo is not. |
| Rejected | Record th