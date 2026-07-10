[README.md](https://github.com/user-attachments/files/29870595/README.md)
# Biz — The Business Operating Agent (Cowork skill)

A business operating agent for Claude Cowork. Five roles in one skill: fractional COO, business consultant and coach, systems & AI advisor, program coordinator, and growth advisor — for your own business and any companies you advise.

Created by **Lommatsch** · [www.lommatsch.com](https://www.lommatsch.com)

## What it does

One skill, twelve modes. Trigger by saying things like:

| Say... | Get... |
|--------|--------|
| "biz" / "how's the business" | COO health check: workstreams, blockers, metrics, the one thing that matters this week |
| "advise — should I raise prices?" | A consulting session: diagnosis, evidence, one recommendation with confidence stated |
| "stack audit" / "where should AI fit" | Systems review: tool overlap, integration gaps, AI opportunities ranked by hours saved |
| "program review" / "what's blocked" | Workstream board with blockers, risks, and cut candidates |
| "growth review" / "is marketing working" | Every activity mapped to a funnel stage and a number — keep, kill, or fix |
| "monthly review" | Scorecard, advice audit, decision revisits, patterns |
| "quarterly planning" | Retrospective-first planning with calibration scoring |
| "onboard [client]" | New company dossier from documents or a 15-minute interview |
| "prep me for the [client] call" | 30-second pre-meeting brief: last commitments, open threads, land mines |
| "build the QBR deck" | Client-ready deliverables straight from the dossier |
| "what if we lose our top client" | Three-scenario spreadsheet model with assumptions exposed |
| "log — we decided X" | Decision recorded with rationale and a revisit date |

## What makes it different from asking Claude business questions

1. **It has memory with structure.** Each company gets a dossier: business model, systems inventory, workstreams, decision log, KPIs, and an advice log. Git-backed, so every change is auditable.
2. **It tracks its own advice.** Every recommendation gets a confidence level, a check date, and an outcome. Ignored advice escalates; wrong advice gets owned. Quarterly calibration scores its hit rate by domain.
3. **It compounds across clients.** A de-identified playbook accumulates what worked, in what context — client eight benefits from clients one through seven, without leaking anyone's data.
4. **It runs a rhythm.** Daily silent watchdog, weekly ops brief, monthly review, quarterly planning — created as scheduled tasks so the cadence happens without you remembering it.

## Get it

- **[biz.skill](biz.skill)** — the installable skill file (click, then use the Download button)
- **[Install Guide.pdf](Install%20Guide.pdf)** — step-by-step setup for non-technical users
- **[User Guide.pdf](User%20Guide.pdf)** — capabilities, modes, and best practices

## Install

1. Download `biz.skill` (link above), drop it into any Cowork chat, and click **Save skill** on the file card.
2. Say "biz — set me up" to run first-time onboarding (choose a workspace folder, onboard your business, approve the scheduled check-ins).
3. From then on, just say "biz."

## Requirements

None strictly required — each connector adds a dimension:

- Google Calendar, Gmail, Google Drive — activity signals and prep material
- Granola — meeting transcripts become decisions, commitments, and blockers automatically
- QuickBooks, HubSpot — live finance and pipeline data (the skill runs "blind but honest" without them)

## Customize after install

Open `SKILL.md` in the skill and edit the `[CUSTOMIZE]` markers: user context, cos handoff path (if you run a Chief of Staff skill), and timezone in `references/data-sources.md`.

## Credits

- Created by Lommatsch — [www.lommatsch.com](https://www.lommatsch.com)
- Architecture inspired by the Chief of Staff (cos) Cowork skill, itself adapted from Annie Tsai's `/cos` Claude Code skill (MomsinTech community repo)
