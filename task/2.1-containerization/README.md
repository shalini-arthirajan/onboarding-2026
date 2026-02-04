# Task 2.1 — Containerization

## Purpose

**Learn how to package an application and its environment so it runs reproducibly across machines.**  
This document provides the acceptance criteria. It intentionally does not include copy/paste commands or runnable code — implement the concrete files yourself and document how a reviewer can verify them.


## High-level objective

Take a small service (for example, a tiny web app) and produce the minimal artifacts needed to run it in a containerized environment along with one auxiliary service (for example: a key-value store or a small database). Demonstrate how the services are built, started, and verified locally.


## Deliverables (conceptual)

Place the required artifacts in `task/<your-github-username>/2.1-containerization/`:

- **A minimal application source** (one small program or script).
- **`Dockerfile`** — image build instructions (keep minimal and readable).
- **`docker-compose.yml`** (or equivalent) — defines the app service and one auxiliary service.
- **`README.md`** — short description, build/run steps, and verification notes.
- **One screenshot** that clearly shows running containers (image names and port bindings).

Do not include compiled images, large binaries, or pre-downloaded artifacts in the repository.


## Suggested scope & constraints

- Keep the app intentionally tiny: a single-file HTTP service or similar minimal program.
- Choose a lightweight auxiliary service (e.g., Redis or Postgres) to demonstrate service-to-service networking.
- Avoid adding heavy external systems or large datasets.
- Keep dependency surface minimal so reviewers can verify quickly.


## Design considerations

- **Image size**: prefer small base images and consider multi-stage builds for compiled languages.
- **Security**: avoid baking secrets into images and run processes as a non-root user where practical.
- **Health & readiness**: provide a simple healthcheck endpoint so the stack can signal readiness.
- **Ports & networking**: document what host ports are bound and how services discover each other (service names / env vars).
- **Persistence**: if state is required, use a volume and document its role in verification.


## How to approach the task (conceptual steps)

1. Choose a tiny app you can implement and verify locally.
2. Create a minimal `Dockerfile` to build the app image.
3. Create a `docker-compose.yml` that:
   - Builds the application service from the `Dockerfile`.
   - Defines one auxiliary service (e.g., Redis or a small DB).
   - Includes minimal port mappings and an optional healthcheck.
4. Verify locally that the stack starts, the app is reachable, and the app can communicate with the auxiliary service.
5. Capture a single screenshot showing running containers (names, images, ports).
6. Add a concise `README.md` in your submission folder that explains how a reviewer can build, run, and verify the stack.


## What to include in your submission directory (recommended layout)

- `task/<your-github-username>/2.1-containerization/`
  - `README.md` — brief build/run/verify instructions and notes.
  - `Dockerfile` — minimal and readable.
  - `docker-compose.yml` — minimal compose definition for the demo stack.
  - `app/` — small app source (single-file preferred).
  - `docker-ps-screenshot.png` — one clear screenshot for verification.
  - `usage.txt` — short conceptual verification checklist (not a long tutorial).


## Acceptance criteria (for reviewers)

A submission should satisfy the following:

- The `Dockerfile` and `docker-compose.yml` are present and minimal.
- The compose configuration starts the application and auxiliary service without manual edits.
- The application exposes at least one simple, reachable endpoint or behavior a reviewer can exercise (e.g., health endpoint or page).
- The screenshot clearly shows containers running with image names and port bindings.
- The submission `README.md` contains concise verification steps and any environment-specific notes.


## Best practices (recommendations)

- Use a `.dockerignore` to keep build contexts small.
- Pin auxiliary service image versions to avoid surprises.
- Keep environment variables and secrets out of source control; document use of an `.env` file and add it to `.gitignore`.
- Make Dockerfiles short and easy to read so reviewers can quickly understand the build.
- Document any platform-specific verification notes (macOS / Windows / Linux differences).


## What not to include

- Large images, binaries, or production artifacts.
- Private keys, API tokens, or secrets.
- Long example datasets or pre-built images.


## References

- Docker official documentation (Dockerfile and image build references).
- Docker Compose documentation (service definitions and versioning).
- Language runtime docs for best practices when containerizing specific languages.


## Extra credit (optional)

- Provide a dev variant (compose override) that mounts local source for fast iteration.
- Add a tiny Makefile with minimal shorthand targets (`make build`, `make up`, `make down`) — keep it documented and optional.
- Include a short note about how the setup could be adapted for CI (conceptual only).


## Review & help

- If you want a checklist-style `README.md` template (no commands) I can provide one to copy into your submission folder.
- If you want a review of a draft, open a PR or paste the file contents and I will provide feedback on structure and clarity (I will not provide finished solution code).
