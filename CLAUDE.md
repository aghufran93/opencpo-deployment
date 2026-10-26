# OpenCPO Development Instructions

## Project Overview
OpenCPO is an EV charging platform using OCPP 1.6 and 2.0.1,
with a Python-based core, CPO admin dashboard, driver charge app,
compliance tester, charger simulator, PostgreSQL/TimescaleDB,
Redis, and Docker Compose.

This root repository manages deployment, installation, documentation,
and orchestration. The five application components are separate Git
repositories and must retain their own Git histories.

## Repository Structure
- opencpo-core: OCPP backend and API
- opencpo-admin: CPO administration dashboard
- opencpo-charge-app: driver-facing application
- opencpo-tester: OCPP compliance testing
- opencpo-charger-farm: virtual charger simulator
- docker-compose.yml: local service orchestration
- setup.sh, install.sh, update.sh: deployment and maintenance scripts
- docs/: installation, configuration, and troubleshooting guides

## Mandatory Safety Rules
1. Inspect the relevant code and Git status before making changes.
2. Never discard, overwrite, or revert existing user changes.
3. Never run git reset --hard, git clean, force-push, or destructive
   database commands unless explicitly approved by the user.
4. Never print, commit, or expose secrets from .env, .env.bak,
   credentials, tokens, private keys, or production configuration.
5. Keep API keys and passwords in environment variables or an approved
   secrets manager. Never place secrets in frontend code.
6. Do not restart, rebuild, stop, or redeploy running services without
   explicit approval.
7. Do not run database migrations or alter production data without
   explicit approval and a verified backup.
8. Do not change component repository remotes or delete component .git
   directories.
9. Do not commit or push automatically. Show the proposed changes and
   wait for user approval.
10. Prefer small, reversible changes and explain risks before execution.

## Git Workflow
- Use a dedicated feature branch for each task.
- Check git status before and after edits.
- Review diffs and run relevant tests before proposing a commit.
- Keep root deployment changes in this repository.
- Keep application changes inside their respective component repositories.
- Do not merge unrelated component changes into the root repository.
- Never commit .env files, backups, local logs, or generated artifacts.

## Engineering Practices
- Follow existing project conventions and supported dependency versions.
- Prefer minimal changes over broad refactoring.
- Validate Python changes with appropriate syntax checks and tests.
- Validate shell scripts with bash -n where applicable.
- Validate Docker Compose configuration before proposing deployment.
- Do not claim tests passed unless they were actually run.
- Document configuration changes and required environment variables.

## UAE Regional Configuration
- UAE local timezone default: Asia/Dubai.
- UAE currency default: AED.
- Use ISO currency code AED for APIs and financial integrations.
- Do not assume existing database amounts are converted merely because
  a display currency or default has changed.
- Preserve external OCPI/provider currency semantics unless explicitly
  instructed otherwise.

## Claude AI Integration
- Keep Anthropic API calls server-side.
- Read API credentials from environment variables or a secrets manager.
- Begin with read-only assistance for charger status, logs, tariffs,
  and documentation.
- Require explicit authorization and suitable safeguards before any
  AI-triggered operational action.
- Never expose credentials, personal data, or unrestricted control
  interfaces to the model or browser.

## Required Delivery Summary
For each task, report:
- Files changed
- Reason for each change
- Tests and validations actually performed
- Any remaining risks or manual steps
- Git status and whether a commit or push was performed
