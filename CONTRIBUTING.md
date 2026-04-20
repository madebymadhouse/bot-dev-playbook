# Contributing to the Mad House Bot Dev Playbook

This repo is the shared contract for how Mad House builds and maintains Discord bots. If something here is wrong, outdated, or missing — fix it. That's the contribution.

---

## What belongs here

- **Runbook gaps** — something you had to figure out manually that should have been documented
- **Standard corrections** — something the standard says to do that doesn't match what actually works
- **New patterns** — a reusable structure that came out of real bot work and belongs as a shared reference
- **Agent updates** — keeping `.github/agents/` copies in sync with [madebymadhouse/agents](https://github.com/madebymadhouse/agents)

If you're adding new content, ask: does this apply to all Mad House bots, or just one? If it's specific to one bot, it belongs in that bot's repo.

---

## How to contribute

1. Fork the repo
2. Create a branch: `docs/short-description` or `fix/short-description`
3. Make your change
4. Open a PR using the PR template — fill in the What / Why / Testing sections
5. The Librarian runs a unification pass on documentation changes before merge

Default workflow for Mad House repos:

https://github.com/madebymadhouse/bot-dev-playbook/blob/main/AGENTIC_GIT_WORKFLOW.md

---

## Commit format

All commits must follow [Conventional Commits](https://www.conventionalcommits.org/):

```
docs(runbooks): add missing step to docker-deploy runbook
fix(standards): correct postgres version reference to 16
feat(patterns): add migration rollback pattern
ci: add pr-check workflow
```

The `commitlint` check in the PR workflow will reject non-conforming commits.

---

## What gets rejected

- Bot-specific content that belongs inside a bot repo
- Speculative guidance that hasn't been grounded in real bot work
- Changes that touch runbook content and agent files in the same commit
- PRs without a clear description of what changed and why
