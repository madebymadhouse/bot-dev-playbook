# Command Deployment

Use this when adding, changing, or re-registering slash commands.

This runbook is based on the deploy scripts used in `madebymadhouse/chopsticks-lean` and `madebymadhouse/chopsticks`.

## Purpose

Deploy slash commands safely with fast feedback during development and deliberate rollout for production.

## Preconditions

- `DISCORD_TOKEN` is set
- `CLIENT_ID` is set
- A target guild ID is available for development deploys
- The repo's command files load without syntax errors

## Default Rule

Use guild deploys during development. Use global deploys only when the command set is ready.

Why:

- Guild deploys are effectively immediate
- Global deploys can take time to propagate
- Fast feedback reduces needless waiting while iterating

## Lean Repo Commands

In `madebymadhouse/chopsticks-lean`:

```bash
npm run deploy:guild
npm run deploy:global
```

Docker:

```bash
docker compose exec bot npm run deploy:guild
docker compose exec bot npm run deploy:global
```

The lean deploy script requires:

- `DISCORD_TOKEN`
- `CLIENT_ID`
- `DEV_GUILD_ID` or `GUILD_ID` for guild mode
- `PROD_GUILD_ID` when targeting a production guild in repo-specific flows

## Full Stack Commands

In `madebymadhouse/chopsticks`:

```bash
DEPLOY_MODE=guild node scripts/deployCommands.js
DEPLOY_MODE=global node scripts/deployCommands.js
```

If the repo includes wrappers such as Make or control scripts, prefer those when they match the environment.

## Verification

- Deploy script reports success
- Updated command appears in the target guild
- Command opens and runs without missing option or permission issues
- If global deploy is used, allow for propagation delay before calling it broken

## Failure Handling

If deploy fails:

1. Check missing env variables first
2. Check whether the command file imports cleanly
3. Check whether the target guild ID is correct
4. Check whether the bot application in Discord matches the token and client ID in use
5. Check logs for REST errors, rate limits, or permission failures

## Common Rules Worth Keeping

- Deploy to a guild first when possible
- Do not assume global propagation is instant
- Keep command registration separate from unrelated deploy steps when debugging
- If a repo filters which commands deploy globally, respect that rule instead of forcing everything out

## What To Update Afterward

- The target bot repo if its deploy steps changed
- This playbook only if the lesson should apply across multiple bots

## References

- `madebymadhouse/chopsticks-lean/scripts/deployCommands.js`
- `madebymadhouse/chopsticks/scripts/deployCommands.js`
- `madebymadhouse/chopsticks` deploy and self-host docs
