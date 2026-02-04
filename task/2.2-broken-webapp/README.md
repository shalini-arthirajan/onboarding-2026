# Task 2.2 — The "Broken" Web App

## Purpose

**Practice diagnosing and fixing frontend↔backend integration bugs.**  
This document outlines a safe, repeatable approach to reproduce the failure, narrow root causes, and produce a minimal, well-documented fix. It deliberately contains no copy-paste patches or runnable snippets; implement changes in your working branch and reference official documentation as needed.

## Scope

- Focus on the full request flow: user interaction → frontend event handler → network request → backend endpoint → storage/response.
- Aim for a minimal, targeted fix that addresses the root cause, includes verification steps, and keeps changes small and reviewable.

## Diagnosis workflow

### 1) Reproduce the failure
- Run the application locally and open the UI. Observe and capture the failing behavior when clicking **Submit** (no-op, error, or unexpected reload).
- Collect artifacts: browser console logs, Network panel screenshots, and a short screen recording or screenshots demonstrating the failure. Sanitize any sensitive information.

### 2) Inspect the frontend
- Use Developer Tools (Console, Network, Elements, Sources).
- Confirm whether a click produces a JavaScript error or emits a network request.
  - No request: likely a client-side issue (missing handler, incorrect event binding, or default form behavior).
  - Request present but failing: inspect the request URL, HTTP method, headers, payload, and the server response (status and body).

### 3) Inspect the backend
- Ensure the backend is running and listening on the expected port.
- Verify the route and HTTP method match what the client sends.
- Check server logs for incoming requests and errors.
- Confirm the backend parses the request body format the client uses (JSON, form-encoded, multipart).

### 4) Narrow hypotheses and test iteratively
- If the client never sends a request, check handler attachment timing, event attributes, and button/form types.
- If the request fails, check URL/method mismatches, CORS, Content-Type, and auth/CSRF requirements.
- If requests succeed but data is not stored, validate backend input processing and persistence paths (DB writes, return codes).

## Common root causes

- **Missing or misbound frontend event handler.**
- **Script loading order** (handlers attached before DOM elements are available).
- **Endpoint or method mismatch** between frontend and backend.
- **Backend body parsing misconfiguration** (e.g., JSON not parsed).
- **CORS issues** blocking cross-origin requests.
- **Uncaught client-side errors** that stop execution.
- **Auth/CSRF constraints** or missing credentials/cookies.
- **Field name mismatches** between client payload and server expectations.

## Fixing principles

- Make **minimal, focused** changes that directly address the root cause. Keep PRs small.
- Add concise logging on both client and server around the fixed flow to aid future debugging.
- Return clear error responses and use appropriate HTTP status codes (4xx for client errors, 5xx for server errors).
- When changing endpoints or payload schemas, update both client and server and document the change in the PR.
- For CORS or auth fixes, prefer environment-scoped, least-permissive solutions; avoid broad relaxations in production.

## Testing & verification

Reviewers will:
- Follow the verification steps in your submission `README.md` to reproduce the original failure.
- Confirm the **Submit** action now emits a network request and the server returns a successful response.
- Verify the data is persisted or otherwise observable on the backend (DB entry, in-memory store, or response).
- Ensure there are no uncaught console errors and the network request shows an appropriate HTTP status.
- Inspect any added tests or logs that demonstrate and guard the fix.

## Submission contents

Create `task/<your-github-username>/2.2-broken-webapp/` and include the following (do not commit secrets):

- **`README.md`** — short summary of the bug, root cause, and step-by-step verification instructions for reviewers.
- **`screenshots/`** — before/after screenshots or a short GIF showing the failing behavior and the successful flow (include Network tab evidence where relevant).
- **Source changes** — a focused patch that:
  - Fixes the root cause with minimal, reviewable changes.
  - Uses concise commit messages that explain intent.
- **Tests or logs** (recommended):
  - Small unit or integration tests that validate the corrected behavior when practical.
  - Short notes describing manual test cases executed.
- **`verification.txt`** — a one-line checklist the reviewer follows (no commands required), e.g., open UI, fill fields, click Submit, verify success.

## Pull Request guidance

- **Title:** use a clear prefix and short summary, e.g., `fix(frontend): attach RSVP form submit handler after DOM ready`.
- **Description should include:**
  - One-paragraph summary of the bug and root cause.
  - Files changed and a rationale for each change.
  - Clear verification steps and expected results.
  - Links to screenshots and any added tests.
  - Notes on limitations or follow-up actions.
- Keep PRs small and focused; address reviewer feedback in follow-up commits.

## Security & privacy

- Never commit secrets, API keys, or private credentials.
- Sanitize screenshots and logs to remove PII or sensitive tokens before including them.
- For CORS/auth changes, avoid permissive production settings; prefer environment-scoped, least-privilege configurations.

## Reviewer rubric

- **Reproducibility (30%)** — The bug is reproducible before the fix and the PR provides clear verification steps.
- **Correctness (30%)** — The fix addresses the root cause without regressions and accounts for edge cases.
- **Communication (20%)** — The PR explains the problem, change, and verification clearly.
- **Safety (10%)** — No insecure shortcuts; security settings remain appropriate.
- **Tests & logs (10%)** — Targeted tests or helpful logs are present to aid future debugging.

## Getting help

If you get stuck, open an Issue in this onboarding repository and include:
- Steps to reproduce the bug.
- Relevant logs and sanitized screenshots.
- The branch name you are working on.
Provide a minimal reproducible example so maintainers and mentors can give targeted guidance.

## Final notes

This exercise emphasizes root-cause analysis, small and testable fixes, and clear communication. Keep submissions focused and well-documented so reviewers can validate the fix quickly.
