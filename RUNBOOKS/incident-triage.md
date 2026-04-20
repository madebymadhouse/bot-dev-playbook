# Incident Triage

Use this when a bot is down, commands are broken, or the deploy state looks wrong.

This runbook is based on operational patterns from the Chopsticks repos.

## Purpose

Get from "something is broken" to a verified next action without flailing.

## First Questions

1. Is the bot process down, unhealthy, or just missing commands?
2. Did a deploy or migration happen recently?
3. Is the failure local to one guild or global?
4. Is the issue runtime, data, or Discord API related?

## Fast Triage Order

### 1. Check container or process status

Docker:

```bash
docker compose ps
```

Systemd if used:

```bash
systemctl status <service-name> --no-pager
```

### 2. Check recent logs

Docker:

```bash
docker compose logs --tail=200 bot
```

Follow live logs if needed:

```bash
docker compose logs -f bot
```

### 3. Check health endpoint

If the repo exposes one, use it.

Lean example:

```bash
curl http://127.0.0.1:9100/healthz
```

### 4. Separate runtime failure from command-registration failure

Symptoms of command-registration problems:

- bot is online
- old commands still exist
- new commands do not appear
- only the interaction surface looks stale

In that case, rerun the command deploy flow instead of restarting everything first.

### 5. Check backing services

If the bot depends on PostgreSQL or Redis, verify those services are healthy before blaming application code.

## Targeted Recovery

Prefer the smallest recovery step that matches the failure.

Examples:

- restart only the bot container
- rerun migrations if schema drift caused startup failure
- redeploy commands if the bot is healthy but Discord interactions are stale
- use the repo's watchdog or doctor command if available

## Failure Handling

Escalate carefully when:

- multiple services are down
- migrations partially ran
- data integrity is unclear
- a rollback may be safer than another forward deploy

## What To Write Down

After the incident, record:

- what failed
- what you checked first
- what fixed it
- what still feels risky
- whether a dedicated runbook or bot-repo doc needs to change

## References

- `madebymadhouse/chopsticks/docs/runbooks.md`
- `madebymadhouse/chopsticks/docs/OPS.md`
- `samhcharles/chopsticks-lean` deploy and watchdog scripts
