# Bot Checklist

Use this as a baseline when building or reviewing a Discord bot.

## Core Product

- Clear command or interaction surface
- Permissions and role checks where needed
- Useful error handling for failed user actions
- Logging for important actions and failures

## Configuration

- Centralized config loading
- Startup validation for required env vars
- No secrets committed to the repo
- Clear separation between local, staging, and production behavior if relevant

## Data

- Persistent data model is named clearly
- Migrations or schema updates are documented
- Dangerous data operations are explicit
- Backup or recovery expectations are known if the bot stores important state

## Operations

- Health or readiness checks if the bot is important enough to need them
- Deploy steps written down in the bot repo
- Rollback path understood before risky releases
- Logs are easy to inspect during failures

## Development

- README explains how to run the bot locally
- Important commands or scripts are documented
- Repeated tasks have a runbook if they are easy to forget
- AI handoffs are used for non-trivial changes
