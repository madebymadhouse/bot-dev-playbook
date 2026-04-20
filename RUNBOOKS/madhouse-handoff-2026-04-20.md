# Mad House Handoff - 2026-04-20

## Current State

- Org: `madebymadhouse`
- All repos were audited for old `House` / `WokSpec` branding drift and cleaned.
- GitHub repo descriptions/about text were unified.
- `CONTRIBUTORS.md` was added across all Mad House repos to make maintainer ownership explicit.
- The three new toolkit repos were seeded and then strengthened:
  - `repo-bootstrap-kit`
  - `agent-updater`
  - `org-standardization-kit`
- Full Mad House agent fleet exists in canonical form at `repos/agents/agents/`.
- Toolkit repos now also contain `.github/agents/` copies plus `AGENT_OPERATIONS.md`.

## Important Clarification About Agents

- Repo-local `.agent.md` files are stored and synced correctly.
- Only the workspace-level custom agent folder at `/home/samhcharles/.github/agents` is currently exposed in the Copilot UI agent picker.
- Right now that UI-visible folder only contains `vps-maintenance-planner.agent.md`.
- If the next chat expects all 16 agents to show up in the Copilot custom-agent menu, they must be copied into `/home/samhcharles/.github/agents/` or configured through VS Code custom agent registration.

## What Was Still In Progress

The next execution sprint was intentionally ordered as:

1. `repo-bootstrap-kit`: build a real bootstrap apply engine
2. `agent-updater`: build drift-report mode plus CI
3. `org-standardization-kit`: build orchestrator plus PR helper

## Intended Deliverables

### 1. repo-bootstrap-kit

Add:

- `scripts/apply-bootstrap.sh`
- a smoke test script
- CI workflow for script validation

Behavior target:

- apply README / CONTRIBUTING / workflow templates into a target repo
- support token replacement for repo name, owner, and default branch
- support dry-run mode

### 2. agent-updater

Add:

- `scripts/drift-report.sh`
- optional config support for target directories
- CI workflow that fails on drift

Behavior target:

- report missing / outdated / extra agent files
- exit non-zero in strict mode
- keep `sync-agents.sh` as the repair path

### 3. org-standardization-kit

Add:

- `scripts/orchestrate.sh`
- `scripts/open-prs.sh`

Behavior target:

- roster fetch
- checklist generation
- optional clone / sync / bootstrap stages
- standardized PR creation helper

## Repos In Scope

- `.github`
- `agents`
- `bot-dev-playbook`
- `vps-maintenance-playbook`
- `chopsticks`
- `chopsticks-lean`
- `liquibar`
- `repo-bootstrap-kit`
- `agent-updater`
- `org-standardization-kit`

## Verified Facts

- Old `House` / `WokSpec` string audit returned zero hits across the Mad House repos after remediation.
- Remaining open PRs in `chopsticks` and `chopsticks-lean` are dependency PRs, not org-standardization drift.
- The substantive gap is now tooling depth, not branding cleanup.

## Best Next Prompt For The Next Chat

Use this exactly or with minor edits:

"Continue the Mad House no-fluff tooling sprint from `RUNBOOKS/madhouse-handoff-2026-04-20.md`. Implement in this order: 1) `repo-bootstrap-kit` apply engine, 2) `agent-updater` drift-report + CI, 3) `org-standardization-kit` orchestrator + PR helper. Work on real scripts, tests, docs, branches, commits, and PRs. Also explain the difference between repo-stored agent specs and UI-visible custom agents, and if appropriate sync the full fleet into `/home/samhcharles/.github/agents/`."
