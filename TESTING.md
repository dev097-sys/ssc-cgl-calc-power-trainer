# Testing Report — SSC CGL Calculation Power Trainer v1.0

Test date: 2026-10-10 · Environment: Node 20 (math engine) + headless Chromium via Playwright (UI), viewport 390×844 (Android phone) and 820×1180 (tablet).

## A. Mathematical correctness (automated, Node)

- **23,700 questions generated** across all 25+ skills × 3 difficulties × 200 iterations (plus reverse-recall variants). For every question, the formatted answer key was re-checked through the same `checkAnswer` validator used by the app: **100% self-consistent, 0 failures**.
- Brute-force independent verification: HCF/LCM vs Euclidean algorithm (300 cases each), near-base multiplication vs direct product (500 cases), square-ending-in-5 structure (50 cases).
- Determinism: same seed → identical questions (daily benchmark reproducibility). ✅
- Answer-validation unit tests: **20/20 passed** — exact int match; decimal answers rejected when rounded beyond allowed dp; ±2 % tolerance only where `≈`; equivalent fractions accepted (`6/9` = `2/3`); zero denominator, blank input, and garbage input rejected.
- No `NaN`/`Infinity`/`undefined` in any generated question or explanation text.
- Division by zero: excluded by construction (divisors drawn from fixed non-zero pools); no zero divisor observed in 23,700 generations.

## B. Functional UI tests (real browser, Playwright): 39/39 passed

| Area | Checks | Result |
|---|---|---|
| Load | No console/page errors on load | ✅ |
| Layout | No horizontal overflow at 390 px and 820 px | ✅ |
| Home | 9 mode cards, 7 topic cards, recommendations render | ✅ |
| Session flow | start → question → feedback → explanation → auto-advance → results | ✅ |
| Input | Blank rejected, keypad types/clears, input locked after submit | ✅ |
| Duplicate submission | Rapid double-click counted exactly once | ✅ |
| Skip | Records attempt, advances, enters error notebook | ✅ |
| Pause/resume | Question hidden, input blocked, timer excluded | ✅ |
| Sprint | Deadline set, visible countdown, timer expiry ends session | ✅ |
| Benchmark | Same questions on repeated same-day runs (deterministic seed) | ✅ |
| Persistence | Stats identical after full page reload (localStorage) | ✅ |
| Error notebook | Errors listed; revision session starts from due items | ✅ |
| Analytics | Topic mastery table, activity chart, benchmark history render | ✅ |
| Theme | Dark/light switching applies immediately | ✅ |
| Export | Valid JSON download, schema v1 | ✅ |
| Import | Malformed JSON rejected with error message | ✅ |
| Navigation | All bottom-nav tabs and buttons exercised | ✅ |

## C. Fixed during development

1. **`renderDots()` missing** — progress-dot renderer was called but undefined, which broke auto-advance after the first answer. Found by browser test, fixed, retested green.
2. Sprint timer-bar visibility check initially raced the 200 ms tick; verified the bar renders and counts down correctly (`0:59` on a 60 s sprint).

## D. Unverified / manual checks remaining

- Physical-device touch ergonomics (tested only with emulated 390 px viewport and mouse events).
- Long-session performance (sprint queues are capped at 400 pre-generated unique questions, well above what a 10-minute sprint can consume).
- `prefers-reduced-motion` is not explicitly handled (only a short fade animation exists).
- Screen-reader walkthrough not performed; ARIA labels exist on key controls but a full audit was not done.

No known critical defects remain.
