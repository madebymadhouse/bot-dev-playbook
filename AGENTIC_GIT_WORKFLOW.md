# Agentic Git Workflow

This is the default Mad House workflow for high-output development where humans and agents are both changing things constantly.

The short version:

1. Agents and humans work on branches
2. Agents commit in small logical units
3. Agents push branches and open PRs
4. Humans review and merge
5. `main` stays readable, reviewable, and deployable

If a repo is missing one of the pieces below, fix the repo before scaling the work.

---

## Default flow

```text
main
  -> branch from main (or dev if the repo actually uses dev)
  -> make one scoped change
  -> commit with conventional commits
  -> push branch
  -> open PR
  -> review
  -> squash merge
  -> delete branch
```

This is the default for docs, code, CI, infra, and agent updates.

### What agents do

- Read the current state first
- Create the right branch for the work
- Make the change
- Split commits by logical unit
- Push the branch
- Open the PR with a real title and body
- Report the PR URL back to the human

### What humans do

- Review the PR
- Request changes if the scope is muddy or the testing is weak
- Merge when the branch is clean
- Handle release decisions and production-risk judgment

---

## Branch naming

```text
feat/short-description
fix/short-description
docs/short-description
chore/short-description
security/short-description
refactor/short-description
release/vX.Y.Z
```

Lowercase only. Hyphens only. Keep it short.

---

## Commit rules

One logical change per commit.

Good:

```text
docs(readme): add delegator and git-keeper to agent table
ci: add pr-check workflow and PR template
fix(topology): point live bot repo to madebymadhouse org
```

Bad:

```text
update stuff
misc fixes
final changes
```

If a commit message would embarrass you in six months, rewrite it now.

---

## PR rules

Every PR should answer four things:

1. What changed
2. Why it changed
3. How it was tested
4. Anything the reviewer should watch for

If the PR title needs the word "and", split it.

### PR title format

Use conventional commit format for PR titles too:

```text
docs(readme): add org-wide agentic workflow standard
fix(commands): prevent /warn crash when DMs are disabled
ci: harden PR template and commitlint workflow
```

### Merge mode

Default: squash merge.

Why: `main` should read like a changelog, not a terminal transcript.

---

## Required repo files

Every Mad House repo should have these:

- `.github/pull_request_template.md`
- `.github/ISSUE_TEMPLATE/`
- `.github/workflows/` checks for secrets and commit quality
- `CONTRIBUTING.md`
- `.github/CODEOWNERS`

If any of those are missing, the repo is not ready for sustained agentic work.

---

## When direct pushes are allowed

Direct pushes to `main` are the exception.

Allowed cases:

- Approved production hotfix
- Security incident where waiting on review is riskier than merging
- Small docs/admin change where the human explicitly asked for direct push

Even then:

- write a real commit message
- describe exactly what changed
- open a follow-up issue or PR if cleanup is needed

---

## Agent handoff rule

When an agent finishes work, it should not just say "done".

It should report:

- branch name
- commits created
- PR URL
- what still needs human review

Example:

```text
Branch: docs/agentic-git-workflow
Commits:
- docs(workflow): add org-wide agentic git workflow
- docs(contrib): link repos to shared workflow
PR: https://github.com/madebymadhouse/bot-dev-playbook/pull/123
Needs review: confirm the hotfix exceptions are strict enough
```

---

## Repo roles

- `@delegator` decides the route
- `@git-keeper` owns branch / commit / PR hygiene
- `@reviewer` checks the change before PR or merge
- `@context-keeper` writes the handoff and current state
- `@librarian` checks cross-repo consistency

This is how Mad House keeps high-output work from turning into a mess.
