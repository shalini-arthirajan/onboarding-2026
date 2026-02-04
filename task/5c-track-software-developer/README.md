# Track C — Software Developer (To-Do CLI)

Purpose
- Build a minimal, robust Command Line Interface (CLI) that lets a user manage a simple to-do list.
- The exercise focuses on design, correctness, persistence (small JSON file), and clear documentation — not on fancy features.

High-level objective (what you should deliver)
- A small CLI program that supports three primary actions:
  - add — add a new task with a short description
  - list — list current tasks with an identifier and creation metadata
  - delete — remove a task by identifier (or index)
- Tasks must be persisted to a local JSON file so they survive process restarts.
- Keep the implementation minimal, portable, and dependency-light.

Where to place your work
- Create the submission directory: `task/<your-github-username>/10-track-software-developer/`
- Include the deliverables listed below as individual files in that folder.

Deliverables
- `README.md` — short explanation of choices and verification instructions (this file).
- `todo.py` (or `todo.js`, or a single-file program in another language you prefer) — the CLI implementation.
- `tasks.json` (optional) — an example persisted file showing a few tasks, or let the program create it on first run.
- `examples.txt` (optional) — a short transcript showing sample `add`, `list`, and `delete` interactions and expected outputs.

Behavioral specification (no code)
- Data model:
  - Each task is an object with at minimum: a unique id, a short text description, and a created timestamp.
  - The storage file is a JSON array of task objects. Keep the format simple and human-readable.
- Commands and behavior:
  - add: Accepts a short task description and appends a new task to the file with a generated id and timestamp. The CLI should print a short confirmation including the new task id.
  - list: Reads the JSON file and prints tasks in a readable format sorted predictably (for example: by id or creation time). Provide an option to print raw JSON for automated checks.
  - delete: Removes a task by id (preferred) or by a 1-based index; the command should indicate success or a clear error if the id is not found.
- Robustness:
  - If the tasks file is missing, the CLI should create it on first write.
  - If the tasks file is empty or malformed, the CLI should back it up (or rename it) and start a fresh file, and emit a user-visible warning.
  - File writes must be atomic to avoid corrupting state (write to a temporary file and rename).
- Configuration:
  - Allow the user to override the tasks file path via an option or environment variable; otherwise use a sensible default in the current directory.

Usability & UX expectations
- Keep output concise and human-readable; include task id, text, and created-at in listings.
- Exit codes: use standard non-zero exit codes for error conditions (file IO errors, invalid arguments).
- Provide a short help message available via a help flag; keep the help content minimal and focused on the three primary actions and the file override.

Testing and verification (for reviewers)
- A reviewer should be able to:
  1. Run the program to add a few tasks.
  2. Run the program to list tasks and see the added tasks with ids and timestamps.
  3. Delete one of the tasks by id and see the task removed from the persisted file.
  4. Inspect the `tasks.json` file to confirm tasks persist between runs.
- If you include `examples.txt`, include the exact sequence of invocations (one-liners) and their expected, trimmed outputs so reviewers can reproduce and validate quickly.

Security and safety notes
- Do not store secrets or sensitive data in tasks or example files.
- Avoid running code that requires elevated privileges. The CLI should work from a normal user account and write to a user-writable path by default.
- When backing up malformed files, only move them to a local backup with a timestamped name; do not delete data silently.

Implementation constraints and guidelines
- Keep the program as a single small file so reviewers can read it quickly.
- Prefer using the language's standard library; avoid heavy third-party dependencies unless there is a compelling reason; if you must include dependencies, document them in a short `requirements.txt` or equivalent.
- Use clear, small functions and minimal error handling that includes helpful error messages.

What to write in your task `README.md`
- One-paragraph summary: what language you used and any small design choices (id format, timestamp format).
- How to run and verify (describe the high-level steps a reviewer should take; avoid long tutorials).
- Where the tasks file is stored by default and how to override it.
- Any known limitations or platform-specific notes (e.g., Windows path differences).
- A brief example (one or two lines) of expected output for `add`, `list`, and `delete` — written in plain text, not as runnable code.

Grading rubric (how reviewers will evaluate submissions)
- Correctness (50%): `add`, `list`, and `delete` work as specified and tasks persist across runs.
- Robustness (20%): safe handling of missing/corrupt files and atomic writes.
- Documentation (15%): `README.md` explains how to verify the work and any configuration.
- Code clarity (15%): code is readable, minimal, and uses standard-library features when possible.

Good practices and optional extras (bonus)
- Implement a small test script or a few unit tests that exercise add/list/delete using a temporary file.
- Support an optional `--raw` or `--json` flag on `list` that outputs the persisted JSON for machine checks.
- Provide a short tidy-up command that can validate the tasks file and fix simple inconsistencies (documented and opt-in).
- If you implement extra features, document them clearly and keep the primary deliverables small and easy to verify.

How I will help
- I can review your README and the list of example interactions and provide feedback.
- If you post a short diff or paste relevant excerpts from your submission, I can suggest small improvements to the CLI UX and robustness checks — but I will not write the entire program for you.

Final note
- Keep the submission focused: reviewers should be able to read the program, run a couple of simple checks, and verify persistence within a few minutes. Prioritize clarity, safety, and reproducibility over bells and whistles.
