# Org Standardization Pass

Use this runbook when Mad House has drifted across repos and you need to bring everything back into one standard without relying on one chat thread.

This is the repeatable playbook for:
- pulling the full org into the local workspace
- auditing repo contract drift
- updating docs, GitHub workflow files, and agent copies
- pushing branches and opening PRs per repo
- leaving behind durable docs so the next pass starts from files, not memory

---

## When to use this

Run this when:
- new repos were created or transferred into `madebymadhouse`
- README quality or repo workflow drifted across repos
- agent copies are out of sync with `madebymadhouse/agents`
- GitHub templates differ repo-to-repo without a good reason
- a long chat session produced standards or decisions that should live in docs

Do not use this for one repo's feature work. This is an org-level maintenance pass.

---

## Agents to use

Default fleet sequence:

1. `@delegator` — parse the user request and route the pass
2. `@librarian` — verify the roster and audit drift across repos
3. `@auditor` — produce concrete findings per repo if the pass is large
4. `@updater` — apply the fixes systematically
5. `@writer` — humanize docs that became stiff or generated
6. `@beautiful-readme` — rebuild READMEs that miss the Mad House structure
7. `@git-keeper` — branch, commit, push, and open PRs
8. `@context-keeper` — write the final handoff and state

If the pass reveals a repeated workflow that still only exists in chat, call `@playbook-builder` and capture it here or in a sibling playbook.

---

## Definition of standard

Every Mad House repo should have:
- a README that clearly states what the repo is, who it is for, and how work happens there
- a CONTRIBUTING guide that points at the shared Git workflow standard
- a PR template with `What / Why / Testing / Notes`
- issue templates appropriate to the repo type
- CODEOWNERS when review responsibility matters
- commit and secret quality gates in `.github/workflows/`
- `.github/agents/` with the current fleet when the repo benefits from agentic work

The shared Git workflow standard is:

[AGENTIC_GIT_WORKFLOW.md](../AGENTIC_GIT_WORKFLOW.md)

---

## Step 1: Pull the org locally

List the full org first:

```bash
gh repo list madebymadhouse --limit 200 --json name,nameWithOwner,defaultBranchRef,url
```

Clone anything missing into the workspace:

```bash
cd /home/samhcharles/repos
git clone https://github.com/madebymadhouse/<repo>.git
```

Do not assume the workspace already contains the whole org.

---

## Step 2: Audit the repo contract

For every repo in scope, check:
- README quality and current org references
- CONTRIBUTING quality and workflow links
- `.github/pull_request_template.md`
- `.github/ISSUE_TEMPLATE/`
- `.github/workflows/` quality gates
- `.github/CODEOWNERS`
- `.github/agents/` drift versus `madebymadhouse/agents`

Typical findings:
- stale org or owner references after a transfer
- old `Summary / Testing / Checklist` PR template instead of the shared one
- duplicate legacy `.md` issue templates still present beside `.yml`
- no CODEOWNERS
- commitlint pinned to Node 20 while the org standard is 22
- no durable documentation for the work that just happened in chat

---

## Step 3: Capture what should not stay in chat

If the pass itself produced new process knowledge, document it before you forget it.

Common examples:
- org-standardization process
- PR-first workflow standards
- repo transfer checklist
- agent sync procedure
- merge order guidance when multiple repos are interdependent

Rule:

If you had to explain it twice in chat, it probably belongs in a playbook.

---

## Step 4: Apply fixes by repo

Use `@updater` style discipline:
- read first
- make the smallest correct change
- verify after each change
- group commits by logical unit

Recommended commit grouping:
- docs entry-point updates
- GitHub workflow/template hardening
- agent sync
- org-meta/default-template changes

Do not bundle everything into one commit unless it is truly one concern.

---

## Step 5: Push branches and open PRs

Default branch strategy:
- docs / workflow / repo-contract work branches from `main`
- target `main` unless the repo explicitly uses `dev` as its integration branch
- for repos like Liquibar that already use `dev`, target `dev`

Example:

```bash
git checkout -b docs/mad-house-standard
git push -u origin docs/mad-house-standard
gh pr create --base main --head docs/mad-house-standard
```

The human merges. Agents prepare and report.

---

## Step 6: Report the pass

At the end of the run, report:
- repos pulled into the workspace
- repos changed
- PR URLs
- merge order if there are dependencies
- any remaining drift not fixed in this pass

Template:

```text
## Org Standardization Pass
Date: YYYY-MM-DD

Repos checked:
- ...

Repos changed:
- ...

PRs opened:
- ...

Remaining gaps:
- ...

Merge order:
1. ...
2. ...
```

---

## What this pass produced in practice

This runbook exists because a real Mad House pass produced the following durable standards:
- branch-first, PR-first workflow across repos
- full fleet sync into active repos
- README / CONTRIBUTING / CODEOWNERS / PR-template baseline
- org repo enumeration before making assumptions
- durable playbook capture instead of relying on one chat

That is the point: next time, start here instead of reconstructing it from scratch.
