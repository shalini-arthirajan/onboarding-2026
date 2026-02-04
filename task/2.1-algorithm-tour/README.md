# Task 2.1 — Algorithm Tour

## Purpose
**Compare how the same algorithm is expressed across different language paradigms.**  
This task focuses on clarity, correctness, and idiomatic implementations of an iterative binary search in three languages.


## Problem statement (high level)
Given a sorted sequence and a target value, implement binary search to locate the target with O(log n) comparisons. Each implementation should be correct, handle edge cases, and be easy for a reviewer to build and run.


## Required languages
Implement the algorithm in **exactly three** languages:
- **A systems language**: C or C++ (focus on compilation and explicit types)
- **A scripting language**: Python (focus on readability)
- **A runtime/web language**: JavaScript (Node.js) (focus on quick iteration)


## Deliverables (what to place in your submission directory)
Create `task/<your-github-username>/2.1-algorithm-tour/` and include:
- `binary_search.c` or `binary_search.cpp` — C/C++ implementation
- `binary_search.py` — Python implementation
- `binary_search.js` — JavaScript (Node) implementation
- `README.md` — short notes describing how you ran each file and one observation per language
- (Optional) `tests.txt` or a small `tests/` folder with sample inputs and expected outputs

Do **not** commit compiled binaries or large test fixtures.


## Required behavior (specification)
Each implementation must:
- Return the 0-based index of the target if found.
- Return `-1` (or clearly document another sentinel) when the target is not present.
- Provide a minimal harness or in-file sample inputs so reviewers can exercise the implementation easily.

Edge cases to address (document in your README):
- Empty sequence
- Single-element sequence (target present / absent)
- Target at first, middle, and last positions
- Optional: notes on behavior with large arrays (how you tested, complexity observations)

Include a single-line comment in each source file with one observation about that language (e.g., typing, memory model, build/runtime workflow, or debugging ergonomics).


## How reviewers will verify
For each language:
- Build/run the implementation with the standard toolchain and confirm outputs match the expected results for the provided tests.
- Confirm the source file contains the one-line observation comment.
- Read your README for concise run instructions and a one-paragraph reflection per language.

Keep run instructions brief and conceptual (which command to run or compiler used) — avoid long shell scripts in the README.


## Suggested test cases (describe, include expected outputs)
Provide a small deterministic set of tests (place them in `tests.txt` or the README):
- Sorted list: `[1, 3, 5, 7, 9, 11, 13, 17]`
  - Targets and expected results: `7` → found, `2` → not found, `17` → found at last index, `1` → found at first index, `18` → not found
- Empty list → any target → not found
- Single-element list → target equal → found at index 0; otherwise not found

List expected outputs explicitly so reviewers can validate quickly.


## Style and tooling guidance
- Keep each implementation **idiomatic and minimal**: a single function implementing binary search plus a tiny harness.
- Avoid external dependencies.
- For C/C++: document the compiler and flags used (e.g., compiler name and minimal flags).
- For Python/Node: note the runtime version you tested with.
- Use concise, high-level comments in code; do not embed long tutorials in source files.


## Documentation checklist (what to include in your README)
For each language, include:
- One-sentence run instruction (e.g., compile command or runtime invocation).
- One-paragraph reflection on what you learned and how the language affected implementation choices.
- A short list of test cases and expected outputs.
- Any limitations or noteworthy differences across languages.


## Resources
- Official language documentation (C/C++ compiler docs, Python docs, Node.js docs)
- Algorithm references for binary search and discussion of common pitfalls (off-by-one, midpoint calculation)


## Grading rubric (high level)
- **Correctness (50%)** — returns correct indices for tests and edge cases
- **Documentation (20%)** — clear run instructions and per-language observations
- **Code quality (20%)** — concise, readable, idiomatic implementations
- **Extras (10%)** — simple tests, small harnesses, or insightful reflections


## Final notes
Implementations must be your own work. If you want feedback on a draft, add your files under `task/<your-github-username>/2.1-algorithm-tour/` and open a PR; reviewers will focus on correctness, clarity, and reproducibility.
