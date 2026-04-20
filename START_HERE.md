# Start Here

Read this before doing any meaningful work in a Mad House bot repo.

Your job is to understand the task, clarify the boundaries, and make the smallest correct change without inventing project rules on the fly.

## Questions To Answer First

1. Which bot repo is in scope?
2. Is this a new feature, bug fix, refactor, migration, or deploy task?
3. What will prove success?
4. What files or subsystems are allowed to change?
5. What should be tested before the work is considered done?
6. Which docs in the bot repo need updates afterward?

## Required Reading Order

1. This file
2. `STANDARDS.md`
3. `WORKFLOW.md`
4. `BOT_CHECKLIST.md`
5. `HANDOFF_TEMPLATE.md`
6. Any matching file in `RUNBOOKS/` or `PATTERNS/`
7. The target bot repo's README and local docs

## Rules

- Prefer verified repo context over chat assumptions
- Keep bot-specific decisions inside the bot repo
- Do not invent environment values, deployment details, or database structure
- Keep changes narrow unless the task explicitly requires larger restructuring
- Leave behind notes or doc updates when the next AI would otherwise have to rediscover context

## When To Stop And Clarify

Stop and ask for clarification when:

- the target bot repo is unclear
- the requested change crosses product, infra, and bot-code boundaries at once
- the deploy process is unknown
- the change may affect payments, moderation, security, or data deletion
