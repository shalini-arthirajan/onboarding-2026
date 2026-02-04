# Task 4.2 — The "Good First Issue"

Purpose
- Practice contributing to open-source by finding a small, well-scoped issue, fixing it, and submitting a clear Pull Request (PR).
- Focus areas: repository discovery, evaluating scope, making a minimal fix, writing a good PR, and communicating with maintainers.

What this document
- Intentionally contains no copy-pastable patches or automated scripts.
- Follows project-specific CONTRIBUTING.md, style guides, and tests when available.

What to do (summary)
1. Find a candidate issue labeled for newcomers (e.g., "good first issue", "help wanted", "documentation").
2. Evaluate whether the issue is appropriately scoped for a small, single-commit change.
3. Fork the repository, create a focused branch, implement the change, run tests and linters, and open a PR with a clear description and verification steps.
4. Link the external PR in your onboarding submission and include a short summary in your task folder.

How to find candidate issues
- Use GitHub filters:
  - Search for `label:"good first issue" is:open` and filter by language or topics you know.
  - Search by organization if you prefer an organisation's projects.
- Use aggregators and curated lists (e.g., “good first issues” websites) to find suitable projects.
- Pick active repositories with recent maintainer activity to avoid stalled PRs.

How to evaluate an issue quickly
- Scope: Is the change small (single file or documentation fix)? Will it take a few hours?
- Reproducible: Can you reproduce the bug locally or clearly identify the doc problem?
- Tests & CI: Does the repository have tests or CI checks you can run locally? If yes, ensure your change doesn't break them.
- Maintainer activity: Recent comments or PR merges indicate the project is responsive.
- Contribution rules: Read LICENSE, CONTRIBUTING.md, and any CLA/DCO requirements.

Recommended workflow (high level)
1. Fork + clone
   - Fork the project to your GitHub account and clone locally.
2. Create a focused branch
   - Use descriptive branch names like `fix/docs/broken-link` or `fix(readme): typo`.
3. Reproduce & run tests
   - Run the repository's test and lint commands locally. Fix any unrelated failures only if you can do so cleanly and briefly.
4. Implement the change
   - Keep changes minimal and testable. Prefer docs fixes, small code fixes, or single-case bugfixes.
5. Run tests & linters again
   - Ensure your change passes existing checks.
6. Commit and push
   - Use small, clear commits. Follow repository commit message conventions if specified.
7. Open a PR
   - Use a clear title, describe the problem and the fix, include verification steps, and attach screenshots if helpful.
8. Respond to review feedback promptly and courteously.

PR quality checklist (what maintainers expect)
- Clear title and problem summary.
- Short description of the change and why it fixes the issue.
- Reproduction steps and verification checklist for reviewers.
- Tests added or updated only if necessary and minimal.
- No secrets or large files committed.
- Respect repository formatting/lint rules; run linters locally if available.
- If the project requests a DCO/CLA or specific sign-off, follow that process.

Suggested PR description template
- Title: concise, prefixed by scope (e.g., `fix(docs): correct install link`)
- Summary: 1–2 sentences about the bug or doc issue.
- Changes: bullet list of files changed and rationale.
- How to verify:
  1. Step A (what reviewer runs / opens)
  2. Step B (what reviewer should see)
- Notes: any limitations, edge cases, or follow-up tasks.
- Links: link to the original issue and any relevant discussion.

What to include in your onboarding submission
- Create: `task/<your-github-username>/4.2-good-first-issue/`
  - `README.md` — 1–2 paragraph summary of your contribution and why you picked the issue.
  - `external_pr_url.txt` — URL to the external PR (the PR you opened in the target repo).
  - Optional: `patch/` folder with a small diff or a screenshot showing the before/after if the external repo removed the change from history.
- In your onboarding PR description include the external PR link and a short summary of verification steps.

Verification guidance for reviewers (onboarding repo)
- Confirm the external PR exists and the changes are focused.
- Validate the PR description explains the problem and how to verify the fix.
- Optionally, fetch the PR branch and run repository tests locally (if small and feasible).

Best practices & etiquette
- Be polite and concise in issue comments and PR discussions.
- Ask clarifying questions if the issue description is unclear, but show what you tried first.
- Respect maintainers’ guidance and requested changes; iterate quickly on feedback.
- If a maintainer asks you to close the PR in favor of another approach, accept constructive direction and learn from it.

Common small contribution types (good first issues)
- Documentation fixes (typos, broken links, inaccurate instructions).
- Small API doc updates or README clarifications.
- Minor bug fixes that require a one-line change or a small conditional.
- Adding or fixing tests that are straightforward and clearly scoped.

What to avoid for first contributions
- Large refactors or architectural changes.
- Changes that require long-running environment setup or heavy external dependencies.
- Committing secrets, credentials, or large binaries.

Resources (where to learn more)
- GitHub Docs — for forking, branching, and PR workflow.
- The target project's `CONTRIBUTING.md` and `README.md` — always the first source of truth.
- Popular guides on writing good PRs and contributor etiquette.

If you want help
- If you find a candidate issue and want feedback before starting, open an Issue in this onboarding repo with:
  - The issue link
  - Why you think it's a good fit
  - A brief plan of how you'd fix it
- Maintainers and mentors can then advise on scope or point out pitfalls.

Scoring / rubric (how reviewers will judge your onboarding submission)
- External PR correctness: Did the PR address the stated issue? (40%)
- Communication: Clear PR description, verification steps, and onboarding README (30%)
- Scope & hygiene: Small, focused changes without unrelated modifications or secrets (20%)
- Responsiveness: Engagement with maintainers / follow-up if requested (10%)

Final note
- The goal of this task is learning how to contribute responsibly to open source: pick small, high-impact issues, follow project rules, write good PRs, and communicate clearly. This document deliberately avoids prescriptive code or scripts — use the project's own docs and tests as your guide.
