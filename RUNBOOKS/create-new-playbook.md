# Create New Playbook

Use this when a workflow keeps living in chat and needs to become a repo, playbook, or control-plane style doc set.

## Purpose

Turn repeated explanation into durable docs without overbuilding.

## Preconditions

- You can name the repeated problem clearly
- You know who the repo is for
- You know whether the repo is about one environment or shared development practice

## Step 1: Name The Problem

Write one plain sentence.

Examples:

- A fresh AI cannot maintain this VPS without rebuilding context from chat.
- A fresh AI cannot work across our bot repos without inventing local standards.
- We keep repeating the same deploy and rollback guidance in chat.

If you cannot name the problem simply, do not build the repo yet.

## Step 2: Pick The Right Shape

- choose a control-plane style repo for one live environment
- choose a playbook repo for shared development practice
- choose bot-local docs when the knowledge applies to one repo only

## Step 3: Start With The Minimum Files

Create only:

- `README.md`
- `START_HERE.md`
- one state or standards file
- `WORKFLOW.md`
- `HANDOFF_TEMPLATE.md`
- `RUNBOOKS/README.md`

## Step 4: Pull In Real Source Material

Before writing runbooks, inspect:

- the actual repo scripts
- current deploy docs
- current production or VPS layout
- existing bot or service health checks
- public docs only when they support what the repo already does

Do not let public docs override observed reality.

## Step 5: Add Real Runbooks First

Good first runbooks:

- local setup
- deploy and verify
- command deployment
- incident triage
- backup and restore

Prefer runbooks based on actual scripts and commands already used by the team.

## Step 6: Add An Agent Only If It Helps

A repo-level agent is worth adding when:

- it forces the right first-read order
- it keeps fresh AIs inside the repo boundaries
- it improves handoff quality

Do not add an agent just to sound advanced.

## Step 7: Keep Scope Tight

If a file does not help the next operator act safely, cut it.

## Done Means

The playbook is good enough when:

- a fresh AI can start from the repo without asking the same first questions
- repeated tasks have real runbooks
- repo-specific details stay in the repo that owns them
- the docs read like working notes, not marketing copy
