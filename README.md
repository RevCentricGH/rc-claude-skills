# RC Claude Skills

Claude Code skills for the RevCentric team. Drop any of these into your Claude setup and they auto-trigger when you ask for the right thing.

---

## What's in here

| Skill | What it does | Trigger phrases |
|---|---|---|
| `revcentric-cold-calling-screenplay` | Generates cold call main pitch screenplays (Short and Full versions) with delivery annotations | "screenplay for [client]", "cold call script", "main pitch", "talk track" |
| `rc-client-spot` | Generates single point of truth documents for RC clients — contacts, ICP, sequences, messaging | "create SPOT doc for [client]", "client brief for [client]", "RC client overview" |
| `rc-linkedin` | Runs the LinkedIn leg of the RC outbound pipeline via HeyReach | "LinkedIn campaign for [client]", "load leads into HeyReach" |

---

## How to install

### Option A — Claude Code (recommended)

1. Copy the skill folder into your Claude skills directory:

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

No code to run, no dependencies to install for the screenplay and SPOT skills. The LinkedIn skill requires HeyReach access.

---

## Questions

Contact Kevin — he built these.
