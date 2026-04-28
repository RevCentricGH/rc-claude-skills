---
name: rc-client-spot
description: Generate RC client single point of truth (SPOT) documents — structured reference docs covering campaign status, company overview, ICP, competitive landscape, and objection handling. Use when user says "create SPOT doc for [client]", "build the client KB for [client]", "set up SPOT for [client]", "generate client brief for [client]", or "onboard [client]". Also use when starting a new RC client engagement or refreshing campaign context before an outbound push.
---

# RC Client SPOT Skill

## Purpose

Generates a complete single point of truth document for an RC client. Ask for the client info, fill in what's known, mark gaps as [TBD], and output a doc the user can paste directly into Google Docs (or any doc tool).

Modeled from the actual Cekura, MeshAPI, and Workstreet SPOT docs used at RevCentric.

---

## Workflow

### Step 1 — Gather inputs

Ask the user for the following. Only ask for what they haven't already provided:

- Client name and website
- What the product does (one sentence is fine)
- Target buyer (title, company type, size)
- Key contacts at the client (names, roles)
- Campaign type (cold email, cold calling, LinkedIn, or combo)
- Any known differentiators, competitors, or objections
- Anything else relevant to the campaign

If they don't have something, mark it [TBD] — don't block on it.

### Step 2 — Generate the SPOT doc

Fill out the full template below using what they provided. For unknown fields, write [TBD] so it's easy to find and fill later. Output the completed doc as a code block so it's easy to copy.

### Step 3 — Hand off

Tell the user: "Copy this into a new Google Doc titled '[Client Name] Single Point of Truth'."

---

## SPOT Doc Template

```
[Client Name] — Single Point of Truth
RevCentric Internal
Last Updated: [date]
Version: 1.0

---

CAMPAIGN STATUS

Action Items
[ ] [item]

Open Questions
[ ] [item]

Key Direction
[1-3 paragraph summary of campaign positioning and current focus]

Call Feedback Log
Date | What worked | What missed | Fix
(none yet)

Meetings Booked
(none yet)

---

COMPANY SNAPSHOT

Company Name:
Website:
HQ:
Backed By:
Campaign Contact(s):
Campaign Start Date:
Campaign Type:

---

COMPANY OVERVIEW & POSITIONING

What They Do:

One-Line Differentiator:

Tagline:

Awards & Credibility:

---

ICP & BUYER PERSONA

Geography:
Industry / Segment:
Firmographics:
  - Revenue:
  - Headcount:
  - Stage:
Target Titles (Primary):
Target Titles (Secondary):
Do-Not-Target:
Persona Priority:
  1.
  2.
  3.

---

PROBLEM / SOLUTION OVERVIEW

What's happening in their world:

Day-in-the-life pain (what the buyer feels):

Why [Client Product] is uniquely positioned:

Core Use Cases:
1.
2.
3.

Time-to-Value:

---

COMPETITIVE LANDSCAPE

Direct Competitors:
| Competitor | Their angle | Our edge |
|------------|-------------|----------|

Indirect / Build-in-house risk:

Battlecard Notes:

---

OBJECTION HANDLING

| Objection | Response |
|-----------|----------|
| "Not interested" | |
| "Send me an email" | |
| "We already have something" | |
| "No budget" | |
| "Call me back in [X]" | |

---

CAMPAIGN NOTES & OPEN ITEMS

Open Questions for Client:
[TBD]

Version History:
[date] | v1.0 | Initial SPOT generated
```
