# Track B — AI Researcher (Sentiment Analyzer)

Purpose
- Give practical experience using pre-trained NLP models to perform a focused task: sentence-level sentiment classification.
- Learn how to wire up off-the-shelf inference, design a minimal, reproducible script, and document dependencies and verification steps.
- This document intentionally contains no runnable code — it explains what to build, how to structure your submission, and how reviewers will verify it.

Goal (what to implement)
- A small, well-documented Python program (single file) that:
  - Accepts user input (interactive or via a command-line option) and classifies each sentence as one of:
    - `Positive`
    - `Negative`
    - `Neutral`
  - Is robust to short inputs and returns a single label per input.
  - Contains a brief, one-paragraph README describing design choices and how to run the script.

Design constraints and guidance (no code here)
- Use a pre-trained model or library; common options include:
  - A transformer-based sentiment pipeline (e.g., a Hugging Face model) for higher accuracy.
  - A lightweight fallback (e.g., TextBlob or another lexical-based library) when model downloads are not available.
- Implement a neutral/uncertain threshold so the classifier can output `Neutral` when the model is not confident — document your threshold choice and rationale in the README.
- Avoid committing any large model files, datasets, or secret credentials.
- Keep the program dependency list small and provide it in a `requirements.txt` or in the README (names of libraries only; do not paste installation commands here).

Inputs & outputs (behavioral spec)
- Inputs:
  - Single-sentence mode: accept a sentence passed as an argument (e.g., `--text "<sentence>"`) — describe this in your README.
  - File/batch mode (optional): accept a path to a file with one sentence per line and output one label per line in the same order.
  - Interactive mode: if no input is given, prompt the user for sentences until they exit.
- Outputs:
  - For each input sentence, print exactly one of the words: `Positive`, `Negative`, or `Neutral`.
  - Optionally provide a JSON or verbose mode (documented) that also includes confidence scores — this is optional and must be documented.

Deliverables (what to include in your submission)
Place these under: `task/<your-github-username>/5b-track-ai-researcher/`
- `README.md` — short explanation of your approach, how to run, expected behavior, and notes about model downloads or offline fallback.
- `sentiment.py` — the program source (single file). Keep it minimal and focused.
- `requirements.txt` — list of required Python packages (names and optional version hints).
- `examples.txt` — 5–10 example sentences with the expected outputs from your program (helps reviewers when models cannot be downloaded).
- (Optional) `tests/` — a few tiny unit tests exercising mapping logic (e.g., mapping label+score → final label), if you provide tests, document how reviewers run them.

Verification guidance for reviewers (conceptual)
- Reviewers will:
  - Read the README to understand how to run the program and which environment assumptions exist (e.g., internet required for model download).
  - Run the program in single-sentence mode (or interactive mode) and confirm outputs are one of the three permitted labels.
  - If the reviewer cannot download models (offline), they will use your `examples.txt` and your README to validate expected outputs conceptually.
  - If tests are provided, run the small test suite (if present) to verify mapping logic.

Recommended documentation items to include in README
- Which model/library you selected and why (accuracy, size, inference requirements).
- How you decide between `Positive`/`Negative`/`Neutral` (confidence thresholds or polarity cutoffs).
- Whether the script downloads models on first run and where they are cached (note disk usage).
- Any platform-specific notes (GPU vs CPU) and expected performance characteristics.
- How to run the script for a reviewer to quickly validate (conceptual steps, not long tutorial).

Testing recommendations (conceptual)
- Include a few deterministic examples in `examples.txt` that cover:
  - Clear positive sentiment
  - Clear negative sentiment
  - Neutral / ambiguous cases
  - Edge cases: very short inputs, sarcasm-like phrasing (document limitations)
- (Optional) Add a small unit test for your mapping function (mapping model output to Positive/Negative/Neutral) so reviewers can run logical checks without heavy model downloads.

Security, privacy, and licensing notes
- Do NOT commit any API keys, private tokens, or large model files.
- If you use models with licenses, document the license and any usage implications in the README.
- If your examples include personal or sensitive content, sanitize them before committing.

Extra-credit ideas (optional)
- Provide a lightweight CLI flag to output JSON with labels and confidence scores.
- Add a minimal HTTP wrapper (FastAPI) to expose a sentiment endpoint — only if you document how to run it and keep it optional.
- Add brief calibration notes: small statistics or a tiny calibration set that motivated your neutral threshold.

Evaluation rubric (how reviewers will grade)
- Correctness & behavior (50%): Program prints exactly one of the three labels per input and handles edge cases cleanly.
- Documentation & reproducibility (25%): README clearly explains how to run, maps thresholds, and lists dependencies.
- Design & robustness (15%): Sensible fallback behavior when models cannot be loaded; no secrets committed.
- Extras & testing (10%): Small tests, batch mode, JSON mode, or a basic HTTP wrapper (optional).

If you want help
- I can draft a short README template (conceptual instructions only, no commands) you can copy into your task folder.
- I can review your README, `requirements.txt`, and `examples.txt` and provide feedback on clarity and verification steps.
- I cannot provide the full program code in this document — the goal is for you to implement the program and document it according to the guidance above.

Good luck — focus on clarity, reproducibility, and documenting assumptions. The review is as much about clear communication and reproducibility as it is about model choice.
