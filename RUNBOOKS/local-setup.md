# Local Setup

Use this when bringing up a Discord bot repo for the first time on a development machine.

This runbook is based on the setup flows used in `samhcharles/chopsticks-lean`, `madebymadhouse/chopsticks`, and common discord.js guidance.

## Purpose

Get a bot repo running locally with the fewest surprises.

## Preconditions

- You know which bot repo you are setting up
- You have a Discord application, bot token, and client ID
- You know whether the repo expects Docker or direct Node.js runtime
- You have PostgreSQL and Redis available if the repo uses them

## Pick The Right Path

- Use the lean path for a single bot process with simple Docker Compose or direct Node.js
- Use the full-stack path when the repo includes extra services such as agents, dashboard, monitoring, or Lavalink

## Standard First Pass

```bash
git clone <repo-url>
cd <repo-name>
cp .env.example .env
```

Fill in the required environment values before trying to boot the bot.

Minimum values usually include:

- `DISCORD_TOKEN`
- `CLIENT_ID`
- `BOT_OWNER_IDS`
- `DATABASE_URL` or `POSTGRES_URL`
- `REDIS_URL`

## Lean Bot Path

This mirrors `samhcharles/chopsticks-lean`.

```bash
npm ci
npm run migrate
npm run verify
npm run deploy:guild
npm start
```

If the repo is Docker-first:

```bash
docker compose up -d --build
docker compose exec bot npm run migrate
docker compose exec bot npm run deploy:guild
```

## Full Stack Path

This mirrors `madebymadhouse/chopsticks`.

For direct Node-first local work:

```bash
npm install
npm run migrate
node scripts/deployCommands.js
npm run bot
```

For Docker-first local work:

```bash
docker compose -f docker-compose.laptop.yml up -d
npm run migrate
DEPLOY_MODE=guild node scripts/deployCommands.js
```

If the repo provides a single control script such as `chopsticksctl.sh`, prefer that over ad hoc commands.

## Verification

- Command deployment completes without missing env errors
- The bot logs in successfully
- One test slash command appears in the dev guild
- Health or verify script passes if the repo provides one

## Failure Handling

- If env validation fails, stop and fix `.env` before trying again
- If migrations fail, inspect database connection values first
- If commands do not appear, verify you deployed to a guild and used the correct application ID
- If Docker boots but bot logic fails, check bot container logs before rebuilding everything

## What To Update Afterward

- The bot repo README if setup steps were incomplete or wrong
- This playbook only if the lesson applies across multiple bots

## References

- `samhcharles/chopsticks-lean` README and `DEPLOYMENT.md`
- `madebymadhouse/chopsticks` README, `QUICKSTART.md`, and deploy docs
- discord.js guide: keep code organized and deploy commands intentionally during development
