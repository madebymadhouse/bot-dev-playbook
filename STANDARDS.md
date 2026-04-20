# Standards

These are the default standards for Mad House bot work unless a specific bot repo says otherwise.

## General

- Prefer small, reviewable changes
- Keep code readable before trying to make it clever
- Add tests when behavior is important and test coverage exists nearby
- Keep logs useful and concise
- Write code so another AI or human can follow it quickly

## Bot Architecture

- Keep Discord command handling thin
- Move reusable behavior into services or helpers
- Keep config loading centralized
- Separate transport logic from business logic when possible
- Avoid tightly coupling commands, storage, and side effects in one file

## Data And State

- Do not hardcode secrets or tokens
- Validate required config at startup
- Prefer explicit schemas or structured validation for persistent data
- Treat migrations as first-class changes, not side notes
- Make destructive data changes obvious in code review and handoffs

## AI Handoffs

- Every implementation task should name the repo, files in scope, constraints, and success criteria
- If a task needs multi-step repo changes, write the handoff before asking an AI to code
- If a task is mostly planning, keep it in docs and avoid speculative code edits

## Quality Bar

Before a change is done, the operator should be able to answer:

1. What changed?
2. Why did it change?
3. How was it verified?
4. What could still be risky?
5. What should the next operator know?
