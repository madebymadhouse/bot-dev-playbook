<div align="center">

# Mad House Bot Dev Playbook

**Shared workflow, standards, and runbooks for AI-assisted Discord bot development.**

![License](https://img.shields.io/github/license/madebymadhouse/bot-dev-playbook)
![Last Commit](https://img.shields.io/github/last-commit/madebymadhouse/bot-dev-playbook)
![Discord.js](https://img.shields.io/badge/discord.js-v14-5865F2)
![Node](https://img.shields.io/badge/node-%3E%3D22-brightgreen)

</div>

---

A fresh AI or human should be able to open this repo, understand how Mad House runs Discord bot work, and walk into the correct bot repo without rebuilding context from chat. This repo is the layer between "raw idea" and "working implementation."

> [!IMPORTANT]
> This repo is for workflow, standards, and handoffs. **It does not contain bot code.**
> Bot-specific docs, secrets, and config live inside each bot's own repo.

---

## Navigation

| Section | What it answers |
|---|---|
| [START_HERE.md](./START_HERE.md) | What to read before touching a bot repo |
| [STANDARDS.md](./STANDARDS.md) | Architecture, data, and quality standards that apply to all bots |
| [WORKFLOW.md](./WORKFLOW.md) | Task types: Design / Implement / Fix / Release |
| [HANDOFF_TEMPLATE.md](./HANDOFF_TEMPLATE.md) | Contract format for AI implementation tasks |
| [BOT_CHECKLIST.md](./BOT_CHECKLIST.md) | What a production-worthy bot must include |
| [RUNBOOKS/](./RUNBOOKS/) | Step-by-step guides for repeated or risky tasks |
| [PATTERNS/](./PATTERNS/) | Reusable structures that apply across bots |

---

## How to Use This

```
1. Read START_HERE.md
2. Read STANDARDS.md and WORKFLOW.md
3. Fill in HANDOFF_TEMPLATE.md before asking an AI to change a bot repo
4. Check BOT_CHECKLIST.md before calling a bot production-ready
5. Run a RUNBOOK before any repeated or risky task
```

> [!TIP]
> Keep this repo stable and shared. Keep each bot repo focused on its own code and state.
> Copy patterns from here into a bot repo only when the pattern is genuinely needed there.

---

## Runbooks

All runbooks are grounded in real scripts from `samhcharles/chopsticks-lean` and `madebymadhouse/chopsticks`.

| Runbook | When to use it |
|---|---|
| [local-setup.md](./RUNBOOKS/local-setup.md) | First-time setup on a new machine |
| [command-deployment.md](./RUNBOOKS/command-deployment.md) | Deploying slash commands to guild or global |
| [docker-deploy-and-verify.md](./RUNBOOKS/docker-deploy-and-verify.md) | Deploying a stack update via Docker Compose |
| [incident-triage.md](./RUNBOOKS/incident-triage.md) | Bot is down or behaving unexpectedly |

---

## Patterns

| Pattern | What it describes |
|---|---|
| [playbook-repo-shape.md](./PATTERNS/playbook-repo-shape.md) | How to structure a control-plane or playbook repo |
| [beautiful-readme.md](./PATTERNS/beautiful-readme.md) | How to write a README that communicates and looks deliberate |

---

## Agents

| Agent | Purpose |
|---|---|
| [bot-dev-playbook.agent.md](./.github/agents/bot-dev-playbook.agent.md) | Main playbook agent — workflow, standards, handoff coordination |
| [playbook-builder.agent.md](./.github/agents/playbook-builder.agent.md) | Turns repeated chat guidance into a durable repo |
| [beautiful-readme.agent.md](./.github/agents/beautiful-readme.agent.md) | Writes or rewrites READMEs to the beautiful-readme standard |

---

## Scope

**This repo is for:**
- Shared AI-assisted development workflow across Mad House bots
- Standards that apply to every bot: architecture, data boundaries, quality bar
- Handoff contracts for AI implementation tasks
- Runbooks for repeated or risky bot-development tasks
- Patterns that should stay consistent across bots

**This repo is not for:**
- Production secrets or environment values
- Bot-specific config or deploy state
- Application code that belongs in a bot repo
- Feature specs for a single bot

---

## License

[MIT](./LICENSE)
