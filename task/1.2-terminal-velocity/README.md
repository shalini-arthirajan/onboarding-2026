# Task 1.2 — Terminal Velocity

## Purpose

**Goal:** Improve your touch-typing and terminal fluency so you can move from thought to keystroke with minimal friction. This README lists the expected deliverables and provides clear verification steps for reviewers.


## Objectives
- **Typing:** Set and reach a personal typing target. Example targets people often choose: **>40 WPM** and **>95% accuracy**. Choose a realistic target and document it.
- **Terminal fluency:** Confidently use shell navigation and compose small, focused pipelines to solve everyday tasks without relying on graphical tools.


## What to do (high level)

### 1) Touch-typing practice
- Pick a reputable typing course and complete a baseline test.
- Practice consistently (for example, 15–30 minutes daily) and retest after a short period to measure progress.
- Capture a **legible screenshot** showing your final typing profile (WPM and accuracy).

### 2) Terminal fundamentals practice
- Learn and practice:
  - Basic navigation and file inspection.
  - Text searching and simple transformations.
  - Composing commands using pipes and redirection.
- Solve small, concrete problems at the shell and **choose three representative one-liners** or short pipelines you rely on; explain each briefly.

### 3) Short exercises (practice & evidence)
For each exercise include:
- A one-line description of the problem.
- A short explanation of the approach (which utilities you combined and why).
- A short captured output or sanitized screenshot demonstrating the result.

Suggested exercise types (describe what to do, not how):
- Identify the largest items in a directory tree and explain your approach.
- Search a codebase for “TODO” markers and summarize files with the most occurrences.
- Preview the most recently modified file in a directory and inspect its top lines.


## Deliverables (what to include in your submission)
Create `task/<your-github-username>/2-terminal-velocity/` and include:

- `README.md` — a short reflection (1–2 paragraphs) describing:
  - What you improved.
  - Which commands or workflows you use most and why.
- `typing-screenshot.png` — a clear screenshot that shows WPM and accuracy.
- `commands.md` — contains:
  - **Three short command descriptions** (one-liners or pipelines) with a sentence each on why they are useful.
  - **Three exercise entries**: problem description, approach, and captured (sanitized) output.

In your PR description include a short verification checklist for reviewers (what to open, where to look, expected outputs).


## How reviewers will verify
- Confirm the typing screenshot clearly shows **WPM** and an **accuracy metric**.
- Open `commands.md` and confirm:
  - Three concise command descriptions are present with explanations.
  - Each practice exercise includes a problem statement, an approach, and a captured result (screenshot or sanitized output).
- Optionally run the described approaches against a small example repository to confirm reproducibility.


## Recommended resources
- Typing tutors: search for reputable platforms (many are browser-based).
- Shell basics and one-liners: consult man pages and trusted references for **bash/zsh**, **grep**, **awk**, **sed**, and common utilities.
- Learn-by-doing: use a small repository or a local sample directory so you can practice safely.


## Good habits & ergonomics
- Prioritize **accuracy and posture** before speed.
- Use aliases and small shell functions to reduce repetitive typing; describe them in words in your README instead of committing dotfiles.
- Build pipelines incrementally: verify each step’s output before composing the next pipe.
- Sanitize all public outputs and screenshots; never commit secrets or personal data.


## Privacy & safety (important)
- Do **not** commit screenshots or outputs that contain passwords, API keys, private IPs, or other sensitive data.
- If outputs include personal data, redact or sanitize them before committing.


## Need help?
If you want tailored guidance, tell us:
- Which typing tutor you plan to use.
- Which shell environment you use (bash, zsh, fish, etc.).  
We will point you to focused learning paths and provide a short checklist you can copy into your `README.md`.
