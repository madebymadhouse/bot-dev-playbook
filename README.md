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
| [AGENTIC_GIT_WORKFLOW.md](./AGENTIC_GIT_WORKFLOW.md) | Branch, PR, merge, and handoff rules for high-output human + agent work |
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
AGENTIC_GIT_WORKFLOW.md # Branch / PR / merge rules for humans and agents
HANDOFF_TEMPLATE.md    # Write this before asking an AI to implement anything
```

> [!TIP]
> Keep this repo stable and shared. Each bot repo owns its own code and state.
> Copy a pattern from here into a bot repo only when it's actually needed there.

---

## Runbooks

All runbooks are grounded in real scripts from `madebymadhouse/chopsticks-lean` and `madebymadhouse/chopsticks`.

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

All agents are in `.github/agents/`. Drop any of them into another repo and they work the same way.

| Agent | What it does |
|---|---|
| [delegator.agent.md](./.github/agents/delegator.agent.md) | Your single entry point — describe what you want in plain language, it picks the right agents and dispatches them in order |
| [orchestrator.agent.md](./.github/agents/orchestrator.agent.md) | Runs the full fleet — dispatches agents in sequence, collects outputs, delivers unified result |
| [context-keeper.agent.md](./.github/agents/context-keeper.agent.md) | Writes session logs, handoffs, and decision records so nothing gets lost between sessions |
| [librarian.agent.md](./.github/agents/librarian.agent.md) | Org-wide unification — consistent branding, badges, wording, cross-repo sync |
| [git-keeper.agent.md](./.github/agents/git-keeper.agent.md) | Version control workflow — branching, conventional commits, PR descriptions, merge strategy |
| [coder.agent.md](./.github/agents/coder.agent.md) | Production code implementation — minimal correct change, verified output |
| [debugger.agent.md](./.github/agents/debugger.agent.md) | Root cause analysis — reads the failure, hypothesizes, tests, fixes |
| [reviewer.agent.md](./.github/agents/reviewer.agent.md) | Code review before merge — correctness, security, patterns, tests |
| [auditor.agent.md](./.github/agents/auditor.agent.md) | Structured audit of any repo or docs set, scored findings |
| [security.agent.md](./.github/agents/security.agent.md) | Security audit — secrets, auth, injection, deps, infra |
| [updater.agent.md](./.github/agents/updater.agent.md) | Acts on audit findings systematically |
| [writer.agent.md](./.github/agents/writer.agent.md) | Rewrites any doc to sound like a person, not a bot |
| [beautiful-readme.agent.md](./.github/agents/beautiful-readme.agent.md) | Writes GitHub READMEs to the Mad House visual standard |
| [bot-dev-playbook.agent.md](./.github/agents/bot-dev-playbook.agent.md) | Bot development workflow, standards, handoff coordination |
| [playbook-builder.agent.md](./.github/agents/playbook-builder.agent.md) | Turns repeated chat guidance into a durable repo |
| [vps-maintenance-planner.agent.md](./.github/agents/vps-maintenance-planner.agent.md) | VPS maintenance planning and runbooks |

Canonical source for all agents: [madebymadhouse/agents](https://github.com/madebymadhouse/agents)

---

## What This Repo Is For

Shared workflow, standards, and runbooks that apply across all Mad House bots. Specifically: the process for AI-assisted development, the quality bar a bot has to hit before it's production-ready, and the handoff format that keeps agents on track.

It's not for production secrets, bot-specific config, or feature specs that only apply to one bot.

---

## Contributing

This repo is the shared contract for how Mad House builds bots. If something here is wrong, outdated, or missing — fix it.

Good contributions:
- Runbook gaps — something you had to figure out manually that should have been documented
- Standard updates — something the standard says to do that doesn't match what actually works
- New patterns — a reusable structure that came up in real bot work and belongs here
- Agent updates — keeping the `.github/agents/` copies in sync with `madebymadhouse/agents`

Open a PR with a clear description of what changed and why. The Librarian runs a unification pass on any documentation changes before merge.

---

## License

[MIT](./LICENSE)
