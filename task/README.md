onboarding-2026/task/README.md#L1-200
# Init Club — Onboarding Tasks (2026)

Overview

This directory contains onboarding tasks. Each task folder describes the goal, acceptance criteria, and the artifacts reviewers expect. Implement and test solutions locally, then include only the requested artifacts in your submission.

How this document is organized

- Task summaries and expected deliverables.
- Submission guidance so reviewers can reproduce and verify work quickly.
- Review checklist and grading expectations.

General guide for contributors

- Place your submission under task/<your-github-username>/<task-id> and open a PR.
- Include a short README in your submission folder that explains your approach and how a reviewer can verify the work.
- Avoid committing large binaries, models, or secrets. If your task requires large artifacts, host them externally and link to them.
- Provide clear, concise verification steps and at least one piece of evidence (screenshot, diff, or link) when requested.

Task summaries and deliverables

Task 1.1 — Linux Migration
Purpose
- Install and configure a Linux environment to understand the runtime platform.

Deliverables
- A screenshot showing a system-info tool output that clearly identifies the distribution.
- A short README that describes which installation path you chose and any notable steps or issues.

Task 1.2 — Terminal Velocity
Purpose
- Improve typing speed and shell fluency.

Deliverables
- A screenshot from your typing practice showing speed and accuracy.
- A short file listing three representative terminal commands you used to demonstrate shell fluency, and a one-line note for each explaining why it demonstrates skill.

Task 2.1 — Containerization
Purpose
- Package a small service and an auxiliary service so they run reproducibly.

Deliverables
- Minimal Dockerfile and compose configuration that build and run the app plus one auxiliary service.
- A short README describing how to build and run locally and a single screenshot showing the running containers.

Task 2.1 — Algorithm Tour
Purpose
- Implement binary search in three different languages to compare idioms and tooling.

Deliverables
- Three small source files (one per language) and a README describing how you ran them and one observation per language.
- Optional small tests or test vectors described in the README.

Task 2.2 — Broken Web App
Purpose
- Debug and fix a real frontend-backend integration bug.

Deliverables
- A PR that contains the fix and a PR description that explains root cause and verification steps.
- Optional screenshots or a short GIF demonstrating the fixed flow.

Task 4.1 — Dotfiles Showcase
Purpose
- Share a reproducible shell/editor configuration.

Deliverables
- A public dotfiles repository link and a README with a short bootstrap guide and one screenshot showing the result.

Task 4.2 — Good First Issue
Purpose
- Practice contributing to external open-source projects.

Deliverables
- Link to the external PR and a one-paragraph note in your submission explaining what you fixed and how you found it.

Task 5 — Career Tracks (pick one)

Track A — Systems Engineer
Purpose: small, safe diagnostics and scheduling.
Deliverables
- A minimal script that checks disk and memory and writes to a user-local log.
- One-line example scheduling suggestion and a README describing how to run and test the script.

Track B — AI Researcher
Purpose: minimal, reproducible sentiment classifier.
Deliverables
- Single-file program, a short requirements list, examples.txt with deterministic examples, and a README that documents model choices and expected outputs.

Track C — Software Developer
Purpose: small CLI that persists tasks to a JSON file.
Deliverables
- One small single-file implementation, an optional sample tasks.json, and a README with high-level verification steps.

Submission guidelines

- Create your submission directory: task/<your-github-username>/<task-id>.
- Include:
  - README.md that explains what you implemented, how a reviewer can verify it, and any assumptions.
  - Only the files requested by the task.
  - Evidence requested by the task (screenshots, diffs, external PR links).
- Keep the README concise and actionable: list the verification steps and expected results.
- Use a focused branch and a single PR per submission.

Reviewer checklist

- Confirm all required deliverables are present.
- Follow the README verification steps and reproduce the evidence.
- Ensure submissions do not include secrets or large generated artifacts.
- Provide clear feedback or request changes when verification is incomplete.

Notes for maintainers

- Requests for starter scaffolds should be tracked via Issues.
- If a README accidentally contains solution code or sensitive data, open an Issue and remove or redact the content.

If you need help

Open an Issue describing your task and what kind of guidance you need. Maintainers can provide non-executable scaffolds or review README drafts, but will not provide full solution code in this repository.

Thank you for keeping the tasks documentation-first and reproducible.
