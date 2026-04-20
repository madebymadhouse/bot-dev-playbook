<div align="center">

# Mad House Bot Dev Playbook

**How Mad House builds Discord bots — workflow, standards, handoffs, and runbooks.**

![License](https://img.shields.io/github/license/madebymadhouse/bot-dev-playbook)
![Last Commit](https://img.shields.io/github/last-commit/madebymadhouse/bot-dev-playbook)
![Discord.js](https://img.shields.io/badge/discord.js-v14-5865F2)
![Node](https://img.shields.io/badge/node-%3E%3D22-brightgreen)

</div>

---

AI-assisted bot work tends to drift. Context gets lost between sessions. An agent that worked great last week rewrites something that was fine. Standards that existed only in someone's head get ignored.

This repo is the fix for that. Open it before touching a bot repo and you'll know how Mad House likes the work to happen, what the standards are, and what to write in the handoff before you hand a task to an AI.

> [!IMPORTANT]
> **This repo has no bot code.** Bot-specific secrets, config, and app logic belong inside each bot's own repo — not here.

---

## Don't Feel Like Reading?

Drop this repo into any AI assistant and ask it to explain the workflow, help you fill in a handoff template, or walk you through the runbook for whatever you're trying to do. Everything it needs to guide you is in here.

---

## Navigation

| Section | What it answers |
|---|---|
| [START_HERE.md](./START_HERE.md) | What to read before touching a bot repo |
| [STANDARDS.md](./STANDARDS.md) | Architecture, data, and quality standards that apply to all bots |
| [WORKFLOW.md](./WORKFLOW.md) | Task types: Design / Implement / Fix / Release |
| [HANDOFF_TEMPLATE.md](./HANDOFF_TEMPLATE.md) | How to write a handoff contract for an AI implementation task |
| [BOT_CHECKLIST.md](./BOT_CHECKLIST.md) | What a production-ready bot needs to have |
| [RUNBOOKS/](./RUNBOOKS/) | Step-by-step guides for repeated or risky tasks |
| [PATTERNS/](./PATTERNS/) | Reusable structures that apply across bots |

---

## Before You Start

```bash
# Read in this order before doing anything else
START_HERE.md          # Pre-flight questions and stop-and-clarify rules
STANDARDS.md           # Architecture, data, and quality bar
WORKFLOW.md            # What kind of task is this?
HANDOFF_TEMPLATE.md    # Write this before asking an AI to implement anything
```

> [!TIP]
> Keep this repo stable and shared. Each bot repo owns its own code and state.
> Copy a pattern from here into a bot repo only when it's actually needed there.

---

## Runbooks

All runbooks are grounded in real scripts from `samhcharles/chopsticks-lean` and `madebymadhouse/chopsticks`.

| Runbook | When to use it |
|---|---|
| [local-setup.md](./RUNBOOKS/local-setup.md) | First-time setup on a new machine |
| [command-deployment.md](./RUNBOOKS/command-deployment.md) | Deploy slash commands to a guild or globally |
| [docker-deploy-and-verify.md](./RUNBOOKS/docker-deploy-and-verify.md) | Push a stack update, confirm all containers come up |
| [incident-triage.md](./RUNBOOKS/incident-triage.md) | Bot is down or doing something unexpected |
| [create-new-playbook.md](./RUNBOOKS/create-new-playbook.md) | Turn a repeated workflow into a real repo |

---

## Patterns

| Pattern | What it describes |
|---|---|
| [playbook-repo-shape.md](./PATTERNS/playbook-repo-shape.md) | How to structure a control-plane or playbook repo |
| [beautiful-readme.md](./PATTERNS/beautiful-readme.md) | How to write a README that actually communicates |

---

## Agents

| Agent | What it does |
|---|---|
| [librarian.agent.md](./.github/agents/librarian.agent.md) | Org-wide unification — consistent branding, badges, wording, cross-repo sync |
| [bot-dev-playbook.agent.md](./.github/agents/bot-dev-playbook.agent.md) | Playbook agent — workflow, standards, handoff coordination |
| [auditor.agent.md](./.github/agents/auditor.agent.md) | Audits any repo or docs set, produces scored findings |
| [security.agent.md](./.github/agents/security.agent.md) | Security audit — secrets, auth, injection, deps, infra |
| [updater.agent.md](./.github/agents/updater.agent.md) | Acts on audit findings systematically |
| [writer.agent.md](./.github/agents/writer.agent.md) | Rewrites any doc to sound like a person, not a bot |
| [beautiful-readme.agent.md](./.github/agents/beautiful-readme.agent.md) | Writes GitHub READMEs to the Mad House visual standard |
| [playbook-builder.agent.md](./.github/agents/playbook-builder.agent.md) | Turns repeated chat guidance into a durable repo |

---

## What This Repo Is For

Shared workflow, standards, and runbooks that apply across all Mad House bots. Specifically: the process for AI-assisted development, the quality bar a bot has to hit before it's production-ready, and the handoff format that keeps agents on track.

It's not for production secrets, bot-specific config, or feature specs that only apply to one bot.

---

## License

[MIT](./LICENSE)
