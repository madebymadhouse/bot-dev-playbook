# Workflow

This is the default flow for AI-assisted bot development at Mad House.

## Default Flow

1. Identify the target bot repo
2. Read the local docs in that repo
3. Decide whether the task is design, implementation, fix, or release work
4. Write or review the handoff contract
5. Make the smallest correct change
6. Verify the result with tests, manual checks, or both
7. Update docs if the change affects future work

## Task Types

### Design

Use this for planning new commands, systems, or refactors.

Rules:
- keep output concrete
- name files and boundaries early
- do not jump into code before the repo constraints are clear

### Implementation

Use this for building a known change in a known bot repo.

Rules:
- start from an explicit handoff
- keep scope narrow
- verify behavior before stopping

### Fix

Use this for bugs, regressions, or broken deploys.

Rules:
- find the root cause before patching
- avoid unrelated cleanup
- document any residual risk

### Release

Use this for command registration, migrations, deploy prep, rollout, and rollback.

Rules:
- follow the bot repo's deploy docs
- treat data changes carefully
- record what was released and how it was verified

## Anti-Drift Rules

- Do not rely on chat as the only plan
- Do not make product decisions implicitly in code
- Do not push deployment behavior into this repo if it belongs in a bot repo
- Do not let repeated tasks stay undocumented for long
