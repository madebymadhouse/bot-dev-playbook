# Mad House Bot Dev Playbook

This repo is the shared guide for AI-assisted Discord bot development at Mad House.

Its job is simple: a fresh AI or human should be able to open this repo, understand how Mad House likes bot work to happen, and then move into the correct bot repo without rebuilding context from chat.

This repo is for workflow, standards, handoffs, and repeatable development practices.

This repo is not for shipping bot code.

## Start Here

1. Read `START_HERE.md`
2. Read `STANDARDS.md`
3. Read `WORKFLOW.md`
4. Read `BOT_CHECKLIST.md`
5. Use `HANDOFF_TEMPLATE.md` before asking an AI to change a bot repo
6. Read a matching runbook in `RUNBOOKS/` if the task is repeated or risky

## What Belongs Here

- how Mad House wants AI-assisted bot work to happen
- coding and repo standards that apply across bots
- handoff contracts for sending an AI into a bot repo
- checklists for what a production-worthy Discord bot should include
- repeatable runbooks for common bot-development tasks
- reusable patterns that should stay consistent across bots

## What Does Not Belong Here

- production secrets
- bot-specific environment values
- live deploy state for a specific bot
- large feature specs that belong inside one bot repo
- application code that should live with the bot itself

## Suggested Use

- Keep this repo stable and shared
- Keep each bot repo focused on code and bot-specific docs
- Copy patterns from here into bot repos only when they are actually needed
- Update this repo when a repeated lesson should apply across multiple bots
