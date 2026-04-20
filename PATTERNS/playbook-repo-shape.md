# Playbook Repo Shape

Use this when a repeated task or context-loss problem is big enough to deserve its own shared docs repo.

## Purpose

Provide a small, repeatable repo shape for playbooks, control-plane style docs, and other AI-readable working memory.

## Start With The Real Problem

A playbook repo is justified when:

- the same context keeps getting re-explained in chat
- a fresh AI keeps asking the same setup questions
- repeated tasks are risky or easy to forget
- shared standards should apply across more than one repo or operator

Do not create a repo just because the idea sounds neat.

## Smallest Useful Shape

For most cases, start with:

- `README.md`
- `START_HERE.md`
- `CURRENT_STATE.md` or `STANDARDS.md`
- `WORKFLOW.md`
- `HANDOFF_TEMPLATE.md`
- `RUNBOOKS/README.md`

Add more only when real use forces it.

## Choose The Right Type

### Control-plane style repo

Use this when the job is to maintain one live environment or machine.

Good fit:

- VPS maintenance
- runtime topology
- incident notes
- health and recovery paths

### Playbook repo

Use this when the job is to keep development work consistent across multiple repos.

Good fit:

- shared bot-development rules
- handoff contracts
- reusable patterns
- release and deploy habits

### Bot-local docs

Use this when the knowledge matters only to one repo.

Good fit:

- env quirks
- deploy details for one bot
- local architecture
- feature-specific notes

## Tone Rules

- write for a tired human or a fresh AI
- prefer direct instructions over slogans
- avoid turning one real problem into a philosophy system
- keep examples real and bounded

## What Not To Put In Shared Docs

- secrets
- one-off deploy state
- app code that belongs in a product repo
- long aspirational writing with no operational value
