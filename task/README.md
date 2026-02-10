# Init Club - Onboarding Tasks (2026)

## Overview

This directory contains onboarding tasks. Each task folder describes the goal, acceptance criteria, and the artifacts reviewers expect. Implement and test solutions locally, then include only the requested artifacts in your submission.

## How this document is organized

- Task summaries and expected deliverables.
- Submission guidance so reviewers can reproduce and verify work quickly.
- Review checklist and grading expectations.

## General guide for contributors

- Place your submission under task/<your-github-username>/<task-id> and open a PR.
- Include a short README in your submission folder that explains your approach and how a reviewer can verify the work.
- Avoid committing large binaries, models, or secrets. If your task requires large artifacts, host them externally and link to them.
- Provide clear, concise verification steps and at least one piece of evidence (screenshot, diff, or link) when requested.

## Task summaries

### Task 1 - Terminal Velocity

This task focuses on reducing friction between thought and execution by improving typing speed and terminal usage.

### Task 2 - Linux Migration

To understand software systems, one must control the environment they run on. This task introduces participants to Linux by setting up a developer-friendly operating system.

### Task 3 - Algorithm Tour

Participants implement the same algorithms across multiple programming languages to observe how identical logic is expressed, constrained, and reasoned about in different execution environments.

### Task 4 - The Broken Web App

This task introduces debugging by fixing a broken frontend–backend interaction in a web application.

### Task 5 - Containerization ("It Works on My Machine")

This task introduces containerization using Docker to ensure applications run consistently across systems.

## Submission guidelines

- Create your submission directory: task/<your-github-username>/<task-id>.
- Include:
  - README.md that explains what you implemented, how a reviewer can verify it, and any assumptions.
  - Only the files requested by the task.
  - Evidence requested by the task (screenshots, diffs, external PR links).
- Keep the README concise and actionable: list the verification steps and expected results.
- Use a focused branch and a single PR per submission.

## Reviewer checklist

- Confirm all required deliverables are present.
- Follow the README verification steps and reproduce the evidence.
- Ensure submissions do not include secrets or large generated artifacts.
- Provide clear feedback or request changes when verification is incomplete.

## Notes for maintainers

- Requests for starter scaffolds should be tracked via Issues.
- If a README accidentally contains solution code or sensitive data, open an Issue and remove or redact the content.

## If you need help

Open an Issue describing your task and what kind of guidance you need. Maintainers can provide non-executable scaffolds or review README drafts, but will not provide full solution code in this repository.

Thank you for keeping the tasks documentation-first and reproducible.
