# RC LinkedIn Outbound Skill

## What This Does

Runs the LinkedIn leg of the RC Outbound Trinity for clients (Cekura, MeshAPI, Crux).

Pipeline: Apollo company search → ICP scoring → contact discovery → HeyReach campaign build + lead load.

Also supports warm nurture via post engager extraction (primary play for Crux/Artharva).

## When to Use

- "Build a LinkedIn campaign for Cekura"
- "Run the LinkedIn pipeline for Crux"
- "Find T1 contacts for MeshAPI and load into HeyReach"
- "Set up warm nurture for Artharva's post engagers"
- "Check what LinkedIn accounts are connected in HeyReach"

## How to Run

Open a Claude Code session from this directory:
```
cd $(git rev-parse --show-toplevel)/skills/skills/rc-linkedin
```

Then tell Claude Code what to do. Examples:
- "Build a Cekura outbound campaign — find T1 companies, discover contacts, create HeyReach campaign"
- "Run Crux warm nurture — extract Artharva post engagers, score, load into HeyReach"
- "Show me what LinkedIn accounts are connected"

## Key Files

| File | Purpose |
|------|---------|
| `CLAUDE.md` | Agent instructions — full pipeline, code patterns, rules |
| `clients/cekura.md` | Cekura ICP scoring rubric + copy framework |
| `clients/meshapi.md` | MeshAPI ICP scoring rubric + copy framework |
| `clients/crux.md` | Crux ICP scoring rubric + copy framework |
| `lib/apollo_client.py` | Company search + contact discovery + enrichment |
| `lib/heyreach_client.py` | HeyReach campaign creation + lead loading |
| `lib/email_enricher.py` | Email enrichment for contacts missing emails |
| `outputs/` | All generated CSVs land here |

## Required API Keys (in $(git rev-parse --show-toplevel)/.env)

- `APOLLO_API_KEY_CEKURA` — Cekura Apollo account
- `APOLLO_API_KEY_CRUX` — Crux Apollo account
- `HEYREACH_API_KEY` — HeyReach account (Hunter's)
- `EMAIL_ENRICHMENT_API_KEY` — (optional) email enrichment fallback

## Tier Routing

| Score | Channel |
|-------|---------|
| T1 (75+) | HeyReach LinkedIn first, then cold email if no reply |
| T2 (55–74) | Cold email only (SmartLead) |
| T3 (35–54) | Hold |
| Post engager | HeyReach warm nurture DM regardless of score |
