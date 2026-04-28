---
name: rc-client-spot
description: Generate RC client single point of truth (SPOT) documents — multi-tab Google Docs covering campaign status, company overview, problem/solution, ICP, competitive landscape, objections, and screenplay. Use when user says "create SPOT doc for [client]", "build the client KB for [client]", "set up SPOT for [client]", "generate client brief for [client]", or "onboard [client]". Also use when starting a new RC client engagement or refreshing campaign context before an outbound push.
---

# RC Client SPOT Skill

## Purpose

Generates a complete single point of truth document for an RC client, structured as 8 separate tabs to match the actual Cekura, MeshAPI, and Workstreet SPOT docs at RevCentric.

The output is organized tab-by-tab so the user can create each tab in Google Docs and paste the matching content block. No automation — pure content generation.

---

## Workflow

### Step 1 — Gather inputs

Ask only for what's not already known:

- Client name and website
- What the product does (one sentence)
- Target buyer (title, company type, size)
- Key contacts at the client (names, roles)
- Campaign type (cold email, cold calling, LinkedIn, or combo)
- Known differentiators, competitors, objections
- Anything else relevant to the campaign

Mark unknowns as `[TBD]` — don't block on them.

### Step 2 — Generate all 8 tabs

Output each tab as its own clearly labeled code block. Use the tab structure and content templates below.

### Step 3 — Hand off

Tell the user:

```
Create a new Google Doc titled "[Client Name] Single Point of Truth"
Add 8 tabs (Insert → Tabs in Google Docs)
Paste the matching content into each tab
```

---

## Tab Structure (8 tabs)

| # | Tab Name | Purpose |
|---|----------|---------|
| 1 | Campaign Status | Living tab — action items, open questions, call feedback, meetings booked |
| 2 | Campaign Brief | Executive summary — snapshot + contents + version history |
| 3 | Company Overview | Positioning, differentiator, awards, customers |
| 4 | Problem / Solution Overview | Market context, day-in-the-life pain, why uniquely positioned, use cases |
| 5 | ICP & Buyer Persona | Geography, industry, firmographics, target titles, persona priority |
| 6 | Competitor Overview & Battlecards | Direct competitors, indirect risks, build-in-house, battlecard responses |
| 7 | Objection Handling | Objection → response table |
| 8 | Screenplay | Cold call main pitch (use the revcentric-cold-calling-screenplay skill to generate) |

---

## Tab Content Templates

### TAB 1 — Campaign Status

```
[Client Name] Campaign Status
Last Updated: [date]
[Client Website URL]

ACTION ITEMS

[ ] [item]
[ ] [item]

OPEN QUESTIONS

[ ] [item]
[ ] [item]

KEY DIRECTION

[1-3 paragraph summary of campaign positioning, target segment, current focus, and any pivots]

CALL FEEDBACK LOG

Date | What worked | What missed | Fix
(none yet)

MEETINGS BOOKED

(none yet)
```

---

### TAB 2 — Campaign Brief

```
[Client Name]
Client Knowledge Base

RevCentric Internal — Single Source of Truth
Generated: [date]
Version 1.0 — Campaign Launch

CONTENTS

1. Company Snapshot
2. Company Overview & Positioning
3. Problem / Solution Overview
4. ICP & Buyer Persona
5. Competitive Landscape
6. Objection Handling
7. Screenplay

COMPANY SNAPSHOT
Quick-reference header. Everything an SDR needs at a glance before the first dial.

Company Name:
Parent Company:
Website:
Headquarters:
Backed By:
Key Customers:
Campaign Contact(s):
Campaign Start Date:
Campaign Type:

CAMPAIGN NOTES & OPEN ITEMS

Open Questions for Client:
[TBD]

Version History:
[date] | v1.0 | Initial SPOT generated
```

---

### TAB 3 — Company Overview

```
[Client Website URL]
COMPANY OVERVIEW & POSITIONING
The elevator pitch — what does this company do and why should anyone care?

What They Do
[2-3 sentences in plain language]

One-Line Differentiator
[Single punchy sentence that names the structural difference vs commoditized alternatives]

Tagline
[Their actual tagline if known]

Awards & Credibility
[Notable credentials, recognitions]

Notable Customers & Case Studies
- [Customer 1]
- [Customer 2]
- [Customer 3]
- [Case study link or summary if available]

Funding & Backers
[Investors, total raised, latest round]
```

---

### TAB 4 — Problem / Solution Overview

```
PROBLEM / SOLUTION OVERVIEW

4.1 What's happening in their world
[Market context — what's changing that creates urgency for this buyer right now]

4.2 Day-in-the-life pain (what the buyer feels)
[Specific, visceral pain points the buyer experiences day-to-day. Not abstract — describe what their week actually looks like]

4.3 Why [Client Product] is uniquely positioned
[The structural reason competitors can't replicate this. Tech moat, data moat, distribution moat, or insight moat]

CORE USE CASES

7.1 Core Use Cases
1. [Use case]
2. [Use case]
3. [Use case]

7.2 Implementation / Support Model
[How fast can a customer go live? What does onboarding look like?]

7.3 Time-to-Value
[How fast do they see ROI? Specific timeframe and metric]
```

---

### TAB 5 — ICP & Buyer Persona

```
ICP & BUYER PERSONA OVERVIEW

3.1 Geography
[Countries, regions, exclusions]

3.2 Industry / Segment
[Industries to target, vertical focus, segment definitions]

3.3 Firmographics (Hard Filters)
- Revenue: [range]
- Headcount: [range]
- Funding stage: [range]
- Tech stack signals: [if applicable]

3.4 Target Titles (Primary)
- [Title 1]
- [Title 2]
- [Title 3]

3.5 Do-Not-Target (Functions / Roles)
- [Role/function to exclude]
- [Role/function to exclude]

3.6 Persona Priority Order
1. [Top persona — name, title, why they're priority]
2. [Second persona]
3. [Third persona]

PERSONA PROFILES

[Primary persona name]
- Day-to-day responsibilities:
- Top KPIs they're measured on:
- What keeps them up at night:
- Where they hang out (online, offline):
- How they make purchase decisions:
```

---

### TAB 6 — Competitor Overview & Battlecards

```
COMPETITIVE LANDSCAPE

9.1 General / Adjacent (not direct competitors)
[Tools that solve a related problem but not the same problem. SDR may hear these names — be ready]

9.2 Direct Competitors

| Competitor | Their angle | Our edge |
|------------|-------------|----------|
| [Name] | [How they position] | [Why we win] |
| [Name] | [How they position] | [Why we win] |

9.3 Build-in-House Risk
[Companies that might build their own version internally instead of buying. How to disarm this]

BATTLECARDS

"We already use [Competitor X]"
[Response: 2-3 sentences that acknowledge, then differentiate without bashing]

"We're building it ourselves"
[Response: cost of internal build, time, opportunity cost, ongoing maintenance]

"We're evaluating [Competitor Y]"
[Response: ask what they're solving for, redirect to your specific edge on that dimension]
```

---

### TAB 7 — Objection Handling

```
OBJECTION HANDLING

| Objection | Response |
|-----------|----------|
| "Not interested" | [Response] |
| "Send me an email" | [Response] |
| "We already have something" | [Response] |
| "No budget" | [Response] |
| "Call me back in [X]" | [Response] |
| "How did you get my number?" | [Response] |
| "We're not the right fit" | [Response] |
| "Just send me info" | [Response] |
| "I need to talk to my team" | [Response] |
| "We tried something like this before and it didn't work" | [Response] |

KEY DISARMS

Pattern interrupt (use within first 10 seconds if needed):
[1-line script]

Permission-based opener (when prospect sounds rushed):
[1-line script]

Reframe (when prospect says they're handling it internally):
[1-line script]
```

---

### TAB 8 — Screenplay

```
COLD CALL MAIN PITCH SCREENPLAY

[Use the revcentric-cold-calling-screenplay skill to generate this section]

Trigger phrases:
- "screenplay for [Client]"
- "cold call script for [Client]"
- "main pitch for [Client]"

Generate both versions:
- Short Version (status thumbnail + big idea paragraph)
- Full Version (status thumbnail → change in world → big question → UVP)

Paste both versions into this tab once generated.

---

DELIVERY NOTES

Tone: Low and slow. Status through calm control, not excitement.
Pace: Slightly above monotone. Slow down for the Change in the World section.
Annotations: All inflection markers (↓)(↑)(>) and pause cues should remain in the script — they're for the SDR's delivery.
```

---

## Hand-off Instructions

After generating all 8 tabs, tell the user:

```
1. Open Google Docs and create a new doc titled "[Client Name] Single Point of Truth"
2. Click Insert → Tabs to enable tabs (or right-click in the left sidebar)
3. Create 8 tabs with these names:
   - Campaign Status
   - Campaign Brief
   - Company Overview
   - Problem / Solution Overview
   - ICP & Buyer Persona
   - Competitor Overview & Battlecards
   - Objection Handling
   - Screenplay
4. Paste the matching content block into each tab
5. For the Screenplay tab, run the revcentric-cold-calling-screenplay skill and paste the output

Save the doc in your RC client folder.
```
