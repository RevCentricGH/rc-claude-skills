---
name: rc-client-spot
description: Generate RC client single point of truth (SPOT) documents — multi-tab Google Docs covering campaign status, company overview, problem/solution, ICP, competitive landscape, objections, and screenplay. One-shot generation that pulls from onboarding call transcripts, meeting summaries, and web research. Use when user says "create SPOT doc for [client]", "build the client KB for [client]", "set up SPOT for [client]", "generate client brief for [client]", "onboard [client]", or pastes a client onboarding transcript / Gemini summary / Fireflies notes and asks to turn it into a SPOT. Also use when starting a new RC client engagement or refreshing campaign context before an outbound push.
---

# RC Client SPOT Skill

## Purpose

One-shot generates a complete single point of truth document for an RC client, structured as 8 separate tabs to match the actual Cekura, MeshAPI, and Workstreet SPOT docs at RevCentric.

The skill takes whatever info is in the trigger message, pulls the rest via web search, and outputs all 8 tabs in a single response. No clarifying questions, no back-and-forth. Anything not findable becomes `[TBD]`.

The output is organized tab-by-tab so the user can create each tab in Google Docs and paste the matching content block.

---

## Workflow — One-Shot Generation

This skill generates the full 8-tab SPOT doc in a single response. Do not ask the user clarifying questions before generating. Extract everything possible from inputs (trigger message, attached transcripts, meeting summaries) and web research, then output all 8 tabs.

### Input priority

Use these sources in order. Earlier sources override later ones — first-party client info beats web research every time.

1. **Onboarding meeting transcripts or recordings (highest priority)** — anything pasted, attached, or referenced from a kickoff call, discovery call, or onboarding meeting. This is direct client voice and beats anything else.
2. **Meeting summaries / call notes** — Gemini summaries, Fireflies notes, manual notes from client calls. Lower fidelity than raw transcripts but still first-party.
3. **Trigger message details** — anything Kevin/Hunter typed directly into the prompt
4. **Web research (fallback)** — only used to fill gaps left by 1–3

### Step 1 — Extract from provided client material

If the user pasted or attached a transcript, summary, or meeting notes, extract:
- Client's exact words on what they do, who they sell to, why now
- Pain points they described in their own customers' words
- Competitors they mentioned (direct and indirect)
- Objections they expect to hear or have already heard
- ICP signals: titles they want targeted, companies to avoid, geo, size
- Messaging the client wants used (or specifically does NOT want)
- Open questions or unresolved items raised on the call
- Names of contacts at the client (founders, ops, engineering)

Quote directly from the transcript when possible — these become the highest-credibility lines in the SPOT doc.

### Step 2 — Extract what else is in the trigger message

Pull anything Kevin/Hunter typed: client name, website, campaign type, anything else not in the transcript.

### Step 3 — Web research to fill remaining gaps

For everything still missing after steps 1–2, run web searches:
- "[Client name] company" → website, what they do, headquarters, founders
- "[Client name] customers" → notable logos, case studies
- "[Client name] funding" → backers, latest round, total raised
- "[Client name] competitors" → market positioning
- "[Client name] [target buyer title]" → buyer persona context

Cap research at 4–6 searches. Move on once you have enough.

### Step 4 — Generate all 8 tabs in one response

Output every tab as its own labeled code block. Mark anything still unknown as `[TBD]`. Do not pause mid-generation to confirm.

When a transcript was provided, add a line at the top of Tab 1 (Campaign Status) under Key Direction:
```
SOURCE: Onboarding call with [client contact name] on [date]
```

### Step 5 — Hand off

After all 8 tabs are output, append the hand-off instructions at the bottom.

If the trigger message gave nothing but a client name, generate anyway with web research and `[TBD]` covering the rest. The user can edit before pasting into Docs.

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
