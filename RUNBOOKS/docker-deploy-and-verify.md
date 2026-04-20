# Docker Deploy And Verify

Use this when a Discord bot repo is deployed with Docker Compose.

This runbook is based on the actual deploy paths documented in `samhcharles/chopsticks-lean` and `madebymadhouse/chopsticks`.

## Purpose

Update a bot safely, restart the right services, and verify that the deploy actually worked.

## Preconditions

- Docker and Docker Compose are installed
- `.env` is present and up to date
- You know which compose file is correct for the target environment
- You know whether migrations are required

## Choose The Deploy Shape

Lean bot shape:

- one bot container
- PostgreSQL
- Redis
- usually one small compose file

Full stack shape:

- bot plus extra services such as agents, dashboard, monitoring, reverse proxy, or voice stack
- multiple compose files or control scripts may exist

## Generic Deploy Flow

```bash
git pull origin main
```

If the repo is lean and uses a single compose file:

```bash
docker compose up -d --build
```

If the repo has explicit production compose files, use the one documented by that repo instead of guessing.

## Migrations

Run migrations before declaring the deploy healthy.

Lean example:

```bash
docker compose exec bot npm run migrate
```

Full-stack example:

```bash
docker compose -f docker-compose.production.yml exec chopsticks-bot npm run migrate
```

## Command Deploy

If slash commands changed:

```bash
docker compose exec bot npm run deploy:guild
```

Or use the repo's full-stack command deploy flow.

## Verification

Minimum verification:

```bash
docker compose ps
docker compose logs --tail=100 bot
```

If a health endpoint exists, check it.

Lean example:

```bash
curl http://127.0.0.1:9100/healthz
```

Full-stack repos may expose a different health port or provide a doctor command.

If the repo ships a verify script, run it.

Lean example:

```bash
npm run verify
```

## Systemd And Auto-Recovery

If the repo provides systemd install scripts, use them instead of writing your own units from scratch.

Examples from the Chopsticks repos include:

- boot-time compose startup
- watchdog service
- watchdog timer for periodic health checks

## Failure Handling

- If only the bot changed, prefer restarting the bot service before tearing down the whole stack
- If health fails after deploy, inspect bot logs before rebuilding again
- If migrations fail, stop and resolve schema problems before retrying the deploy
- If command deploy fails but runtime is healthy, treat command registration as a separate step

## What To Update Afterward

- The bot repo deploy docs if the exact deploy path changed
- This playbook only if the deployment lesson applies across more than one bot

## References

- `samhcharles/chopsticks-lean/DEPLOYMENT.md`
- `samhcharles/chopsticks-lean/scripts/ops/install-systemd.sh`
- `samhcharles/chopsticks-lean/scripts/ops/chopsticks-watchdog.sh`
- `madebymadhouse/chopsticks` deploy docs, ops docs, and control scripts
