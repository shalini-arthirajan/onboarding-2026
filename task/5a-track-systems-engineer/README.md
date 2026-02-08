# Track A — Systems Engineer

Purpose
- Learn basic systems automation and monitoring practices by creating a small, safe diagnostic that checks system resources and can be scheduled to run periodically.
- This document provides conceptual guidance only — no ready-to-run scripts or copy-paste code are included. Implementations should be your own work and follow best practices.

Objective (what to build)
- A lightweight script named `check_resources.sh` (or similar) that:
  - Determines available disk free percentage for a chosen filesystem.
  - Determines available RAM (or an equivalent metric) on the host.
  - Produces a human-readable alert when thresholds are crossed (e.g., disk free < 20%).
  - Logs each check to a user-local logfile by default.
- Schedule this script to run automatically (recommended: daily) using `cron` or a `systemd` user timer. Include an example scheduling line in your submission README (conceptual, not an executable system change).

Constraints & safety
- Do not require root privileges to run by default; use a user-local log path (for example, under `$HOME`) so reviewers can run the script without elevated permissions.
- Do not modify critical system configuration or delete files. The script should be read-only with respect to system state except for appending to its log file.
- Avoid sending notifications that require third-party services (email, Slack, etc.) unless you document how reviewers can opt in and supply their own credentials locally.

What to include in your submission
Create a directory: `task/<your-github-username>/5a-track-systems-engineer/` and include:
- `README.md` — a short file (this document) describing what you implemented, how it behaves, and how a reviewer can verify it.
- `check_resources.sh` — your implementation (executable). Keep it minimal, well-documented, and safe.
- `example-crontab.txt` — a one-line example showing how to schedule the script (conceptual example, not an instruction to edit system crontab in CI).
- Optional: `sample-log.txt` showing example log lines (sanitized) so reviewers can see expected output format.

Design guidance (non-prescriptive)
- Configuration:
  - Make thresholds configurable via environment variables or command-line options so reviewers can test alert conditions without editing the script.
  - Choose sensible defaults (e.g., disk free threshold ~20%, RAM threshold described in MB or percent).
- Detection:
  - Use standard system utilities available on most Unix-like systems (`df`, `free`/`proc`-based approaches) — but consult the system's docs before assuming specific flags/options.
  - Handle missing or unexpected output robustly: log a warning rather than crashing.
- Logging:
  - Write concise, timestamped log lines to a user-local path (e.g., `$HOME/.local/state/check_resources.log`).
  - If you mention a rotation strategy, state it in the README (do not implement complex logrotate config unless documented).
- Alerts:
  - Print alerts to stdout/stderr when run interactively.
  - Optionally support a desktop notification as an opt-in feature, documented clearly for reviewers; do not require a GUI or desktop session.
- Scheduling:
  - Provide a single-line `crontab` example in `example-crontab.txt` that uses full paths and redirects output to the logfile for auditing.
  - Optionally document a `systemd` user timer alternative (conceptual steps only), but do not require reviewers to install system units.

Verification guidance (for reviewers)
- Read the `README.md` to understand thresholds and where logs are written.
- Run the script locally (no elevated privileges) and confirm:
  - It produces a log entry in the declared log file.
  - It prints an INFO/warning line and does not alter system state.
- To test alert behavior, temporarily run the script with adjusted thresholds (documented in your README) so the alert path is exercised without changing system data.
- Inspect the `example-crontab.txt` to see the suggested scheduling approach; reviewers do not need to install it but should be able to understand how to do so.

Documentation expectations
- Your `README.md` should include:
  - One-paragraph summary of what the script does and why.
  - Where the script logs output and how the log lines are formatted (one example line is fine).
  - How to run the script manually for a smoke test and how to trigger alert conditions safely (e.g., change threshold environment variables).
  - The `crontab` example line and a note about using absolute paths and a minimal environment for cron.
  - Any known limitations or environment-specific caveats.

References (authoritative docs to consult)
- `cron`/`crontab` manual pages and scheduling guides.
- `df` and `free` (or platform-specific equivalents) documentation for reading disk and memory metrics.
- Shell scripting best practices: safe option parsing, `set -euo pipefail`, quoting, and robust logging.

Privacy & security reminders
- Do not include sensitive data in logs or screenshots.
- Do not commit private keys, passwords, or credentials.
- If you offer integrations that require tokens or credentials, document them as opt-in and require reviewers to supply their own secrets during testing.
