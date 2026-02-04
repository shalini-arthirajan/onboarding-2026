onboarding-2026/task-05/README.md#L1-999
# Task 05 — Open-source contribution and career-track sampler

Objective

This task has two parts:
1. Practice a real open-source-style contribution workflow by finding a small improvement and submitting a focused Pull Request (open-source contribution).
2. Choose ONE career track (Systems Engineer, AI Researcher, or Software Developer) and complete the relevant practical assignment so you can taste that path before committing.

This document explains both the open-source contribution workflow and the three career-track tasks (Task 5 tracks A, B and C). Complete the open-source contribution portion plus exactly one track.

Context

This onboarding curriculum is maintained by the Init Club at Amrita Vishwa Vidyapeetham, Coimbatore. Use this repository to practise collaboration, then pick a track that aligns with your interests.

Prerequisites

- Completion of `task-00` (forking, branching and PR basics) recommended.
- Local development environment (`task-01`) available.
- Basic familiarity with Git and GitHub PR workflows.
- For track-specific requirements, see the track sections below.


Part 1 — Open-source style contribution (required)

Objective

Simulate contributing to a real open-source project: locate a small issue or improvement, open an issue if needed, implement the change, and submit a polished PR with discussion and iteration.

Why this matters

- Teaches issue triage, repository navigation and PR etiquette.
- Demonstrates ability to make small, high-quality contributions.
- Mirrors real-world open-source collaboration practices.

Scope and acceptable improvements

- Small documentation fixes (typos, broken links).
- Small usability improvements in README or task instructions.
- Minor bug fixes in examples or small scripts present in this repo.
- Adding a helpful example or missing screenshot.

Step-by-step instructions

1. Find or propose an issue
   - Search this repository for `good first issue` or `help wanted`.
   - If none exist, open a short issue proposing your improvement and wait for a maintainer to confirm.

2. Create a focused branch
   - Branch naming: `feat/task-05-<short-desc>` or `fix/task-05-<short-desc>`.
   - Example:
```sh
git checkout -b feat/task-05-fix-typo-readme
```

3. Implement and test your change
   - Keep changes minimal and document any behavioural changes.
   - If adding code, include tests or a verification step.

4. Commit with conventional messages
   - Format: `type(scope): short summary`
   - Example:
```sh
git add docs/README.md
git commit -m "docs(task-05): fix typo in contribution guidelines"
```

5. Open a PR
   - Target the `main` branch of this repository.
   - PR title example: `docs(task-05): fix broken link in README — <Your Name>`
   - Use the PR template below.

6. Engage with reviewers
   - Respond to comments, update the same branch and push new commits.
   - Keep the conversation professional and focused.

Required deliverables (Open-source contribution)

- A GitHub Issue (if you created one) and a focused Pull Request implementing the change.
- Clear PR description with verification steps and links to changed files.

PR description template (suggested)

- Title: `<type>(task-05): short summary`
- Body:
  - Task: `task-05` — Open-source contribution
  - Summary of changes
  - Deliverables
  - How to verify (steps a reviewer can reproduce in 5–10 minutes)
  - Assumptions

Evaluation criteria (Open-source contribution)

- Focus: PR addresses a single, well-scoped change.
- Quality: Clear explanation, concise commits and no unrelated changes.
- Verification: Reviewer can reproduce verification steps.
- Process: Branch naming and commit messages follow conventions.

Reviewer checklist (Open-source contribution)

- [ ] PR is focused and small.
- [ ] Title and description follow template.
- [ ] No sensitive data included.
- [ ] Tests or verification steps are provided when applicable.


Part 2 — Choose ONE track (A, B or C)

Instruction: pick exactly one of the following tracks. Submit the track deliverables in a single PR (from your fork) to this repository and reference `task-05` in the PR description. Name your branch `feat/task-05-track-<a|b|c>-<short-desc>`.

Track A — Systems Engineer (OS internals, scripts, automation)

Focus

Systems-level tooling, automation, and scheduling.

Task

Write a Bash script that:

1. Checks the system's available RAM and disk space.
2. If disk space used is above 80% (i.e. free below 20%), alert the user (console output and optional email if configured).
3. Schedule the script to run daily via cron (include instructions to install the crontab entry).

Requirements

- Script name: `task-05/systems/monitor.sh`
- Script must run on a typical Linux environment (Debian/Ubuntu). Document any platform-specific requirements.
- Provide a safe, read-only "dry-run" flag to show what would happen without making changes.
- Provide clear exit codes:
  - `0` — OK
  - `1` — warning (low disk)
  - `2` — error (script failure)

Deliverables (Systems Engineer)

- `task-05/systems/monitor.sh` — the script with comments and a `--help` usage output.
- `task-05/systems/README.md` — run instructions, example crontab line and a short note on how to configure email alerts (optional).
- Evidence that the script runs: sample output file `task-05/systems/sample-output.txt` or a short terminal transcript.

Example crontab entry (add via `crontab -e`):

```sh
# Run monitor.sh at 07:00 daily
0 7 * * * /path/to/onboarding-2026/task-05/systems/monitor.sh --daily >> /var/log/monitor.log 2>&1
```

Evaluation (Systems Engineer)

- Script correctness: correctly measures RAM and disk; triggers alert at the threshold.
- Usability: helpful `--help`, safe dry-run mode, clear README.
- Automation: crontab instructions are correct and non-destructive.


Track B — AI Researcher (Data, models, Python)

Focus

Practical use of pre-trained models for simple NLP tasks.

Task: Sentiment Analyzer

1. Use a pre-trained library (TextBlob, VADER, or a small Hugging Face transformer) to build a sentiment analyser.
2. Provide a Python script `task-05/ai/sentiment.py` that:
   - Accepts a single sentence as input (command-line argument or interactive prompt).
   - Outputs: `Positive`, `Negative`, or `Neutral` with a short confidence score if available.
3. Keep dependencies minimal and document them in `requirements.txt`.

Deliverables (AI Researcher)

- `task-05/ai/sentiment.py` — runnable Python script with usage examples.
- `task-05/ai/requirements.txt` — pinned minimal dependencies.
- `task-05/ai/README.md` — instructions to create a virtual environment, install dependencies, and run the script with examples and expected output.

Example usage:

```sh
python task-05/ai/sentiment.py "I enjoyed the workshop; it was very helpful."
# Output: Positive (confidence: 0.92)
```

Evaluation (AI Researcher)

- Correctness: script runs and produces sensible labels for sample texts.
- Reproducibility: clear instructions and pinned dependencies.
- Conciseness: minimal external dependencies and clear README.

Notes (AI Researcher)

- If using a transformer model, prefer a small, CPU-friendly model (e.g. distil models) and document model sizes and expected runtime.
- If online model download is required, advise reviewers about potential network/time constraints.


Track C — Software Developer (Full-stack, APIs, CLI)

Focus

User-facing tooling; command-line user experience and data persistence.

Task: To-Do List CLI

1. Build a simple command-line To-Do application in the language of your choice (Python, Node.js recommended).
2. Features:
   - Add a task: `todo add "Buy milk"`
   - List tasks: `todo list`
   - Delete a task by ID or index: `todo delete 2`
3. Persist tasks to a local JSON file (e.g. `~/.todo.json` or `task-05/todo/tasks.json` if you prefer repo-local storage).
4. Provide helpful `--help` output and handle edge cases (empty list, invalid ID).

Deliverables (Software Developer)

- `task-05/todo/` — source code, README and an example tasks file.
- `task-05/todo/README.md` — installation, usage and examples.
- (Optional) Basic tests demonstrating add/list/delete behaviours.

Example CLI usage:

```sh
# Add
todo add "Write onboarding documentation"

# List
todo list

# Delete
todo delete 1
```

Evaluation (Software Developer)

- Usability: intuitive commands and helpful help text.
- Persistence: tasks saved and loaded correctly between invocations.
- Robustness: handles edge cases and invalid input gracefully.
- Documentation: clear README with examples.


Submission and PR expectations (tracks)

- Create a single branch: `feat/task-05-track-<a|b|c>-<short-desc>` (e.g. `feat/task-05-track-a-monitor`).
- Include only files relevant to your track and the open-source contribution in the PR.
- PR description must include:
  - Which track you completed (A/B/C).
  - Links to the files added.
  - How a reviewer can run and verify your deliverables (step-by-step).
  - Any assumptions or platform constraints.
- Use conventional commit messages and tidy history.

Example PR description snippet

```md
Task: task-05 — Track A (Systems Engineer) + open-source doc fix

Summary:
- Added `task-05/systems/monitor.sh` with daily cron instructions.
- Fixed a minor typo in `CONTRIBUTING.md` (see commit 123abc).

How to verify:
1. Run `bash task-05/systems/monitor.sh --dry-run`
2. Inspect `task-05/systems/sample-output.txt`
```


Evaluation and grading notes

- Each PR will be reviewed for correctness, clarity and process adherence.
- Passing criteria for a track:
  - Deliverables are present and documented.
  - Reviewer can reproduce verification steps.
  - Branch and commit conventions are followed.
- Reviewers may request changes; update the same branch and push additional commits.

Optional extensions (bonus)

- Track A: integrate with systemd timers or add email/SMS alert examples.
- Track B: provide a small web or CLI demo that labels several sentences and shows aggregated metrics.
- Track C: add a basic REST API around the todo (Flask/Express) and a small frontend sample.

Accessibility, privacy and security

- Do not include sensitive personal data in examples.
- If your solution uses networked services or APIs, provide mock data or instructions for safe, local testing.
- Keep default configuration non-destructive and suitable for disposable environments.

Support

- If you need the club's example Hello World app or the buggy RSVP repo, open an issue and mention `@init-club-maintainers` or ask your onboarding buddy.
- For platform-specific questions, document OS/version and error messages in your PR to speed review.


Reviewer checklist (summary)

- [ ] Open-source contribution PR is small, linked to an issue (if created) and documented.
- [ ] Track branch follows naming convention and contains only related files.
- [ ] Deliverables for the chosen track are present and runnable.
- [ ] README(s) include clear verification steps.
- [ ] Commits and PR description follow conventional style and include assumptions.

Good luck — pick the track that excites you, make a focused contribution, and request review when ready. We look forward to reading your PR and helping you iterate.
