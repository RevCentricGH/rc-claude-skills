# RC Claude Skills

Claude Code skills for the RevCentric team. Drop any of these into your Claude setup and they auto-trigger when you ask for the right thing.

---

## What's in here

| Skill | What it does | Trigger phrases |
|---|---|---|
| `revcentric-cold-calling-screenplay` | Generates cold call main pitch screenplays (Short and Full versions) with delivery annotations | "screenplay for [client]", "cold call script", "main pitch", "talk track" |
| `rc-client-spot` | Generates 8-tab single point of truth documents for RC clients — campaign status, company overview, problem/solution, ICP, competitors, objections, screenplay | "create SPOT doc for [client]", "client brief for [client]", "RC client overview" |
| `rc-linkedin` | Walks through the LinkedIn outbound pipeline for RC clients — Apollo search, ICP scoring, HeyReach campaign setup | "LinkedIn campaign for [client]", "load leads into HeyReach" |

---

## How to install

### Option A — Claude Code (recommended)

1. Copy the skill folders into your Claude skills directory:

```bash
# Mac
cp -r rc-client-spot ~/.claude/skills/
cp -r revcentric-cold-calling-screenplay ~/.claude/skills/
cp -r rc-linkedin ~/.claude/skills/
```

2. Restart Claude Code. The skills load automatically on next session.

### Option B — Claude Chat / Cowork

Each `SKILL.md` is self-contained. Open the file, copy the full contents, and paste it as a system prompt or project instruction in Claude Chat.

---

## How skills work

A skill is just a markdown file (`SKILL.md`) that tells Claude what to do when you ask for something specific. The `description` field at the top defines the trigger phrases. When you say something that matches, Claude loads the skill and follows its instructions.

No code to run, no dependencies to install. The skills generate content (screenplays, SPOT doc text, LinkedIn campaign plans) that you copy-paste into the relevant tool (Google Docs, HeyReach, etc.).

---

## For full automation — Google Docs API setup

The current `rc-client-spot` skill outputs the SPOT doc as 8 separate text blocks for you to manually paste into Google Docs tabs. To automate the full doc creation (auto-create the doc, auto-create tabs, auto-paste content), you need to connect Claude Code to the Google Docs API.

### What you need

1. **Google Cloud project** with the Docs API + Drive API enabled
2. **OAuth credentials** (or a service account) downloaded as JSON
3. **A local CLI helper** that wraps the Google Docs API (gdocs.py / gdrive.py pattern)
4. **Claude Code permissions** to call that CLI from a skill

### Why it's not in here by default

Auto-creation requires:
- Google API auth specific to your account
- A small Python script that wraps the Docs API
- Claude Code `allowed-tools` permission so the skill can shell out to it

This makes the skill non-portable — it only works on a machine where all of that is set up. The current skills stay as content-generation only so anyone on the team can use them right out of the box.

If you want to wire up full automation on your machine, ping Kevin — he's done this on his Jarvis setup and can walk you through the gdocs.py + auth flow.

---

## Questions

Contact Kevin — he built these.
