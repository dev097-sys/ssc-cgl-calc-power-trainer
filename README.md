# SSC CGL Calculation Power Trainer

An offline-first, mobile-first browser app for building **calculation speed, accuracy, and automatic recall** for SSC CGL Tier 1. Pure calculation training — not a general Quantitative Aptitude course. No account, no server, no API key, no build step.

## Open and use

### Desktop
1. Save `index.html` anywhere on your computer.
2. Double-click it — it opens in Chrome/Edge/Firefox and works fully offline.

### Android phone / tablet
1. Transfer `index.html` to your phone (USB, email to yourself, Google Drive download, or WhatsApp "document" to yourself).
2. Open it with **Chrome** (Files app → tap the file → Open with Chrome).
3. Optional: Chrome menu → **Add to Home screen** for an app-like icon that launches full-screen.
4. The on-screen keypad is built in; no keyboard needed.

No internet connection is required after the file is saved.

## What's inside

- **Topics**: Number Sense · Multiplication · Squares/Cubes/Roots · Division · Fractions & Percentages · Addition & Subtraction · Mixed Calculations — 25+ reusable question generators, each with 3 difficulty levels.
- **9 practice modes**: Learn & Drill, Rapid Fire, Fixed-Time Sprint (30 s / 1 / 3 / 5 / 10 min), Accuracy Training, Reverse Recall, Mixed Challenge, Weakness Training, Daily Benchmark (same seeded test each day, comparable over time), Error Revision.
- **Technique library**: 25+ mental-calculation techniques with when-to-use conditions, worked examples, and common mistakes.
- **Adaptive engine**: per-skill accuracy, median response time, recent form, and mastery estimate (marked "insufficient data" below 10 attempts). Weakness Training weights questions toward your weakest skills.
- **Analytics**: totals, accuracy, median time, correct/min, topic mastery bars, 14-day activity chart, benchmark history, recommendations.
- **Error notebook**: every miss/skipped question with your answer, correct answer, explanation, and timestamp; spaced-revision scheduling (0/1/2/4/7/15/30-day ladder) with a revision session mode.

## Answer formats

- Integers: exact value required.
- Fractions: type `a/b` (e.g. `3/8`); equivalent fractions (`6/16`) are accepted.
- Decimals: must match to the stated decimal places — rounded answers are rejected unless the question says `≈` (±2 % tolerance).

## Backup & restore

- Progress is stored in the browser's `localStorage` on that device/browser only.
- **Export**: Settings → Export JSON → a dated backup file downloads.
- **Import**: Settings → Import JSON → choose a previously exported file. Malformed or foreign files are rejected with an error message; your current data is only replaced after validation passes.
- Importing replaces current progress — export first if unsure.
- **Reset**: Settings → Danger zone → double confirmation.

## Privacy

Everything runs locally in your browser. No data leaves the device; there is no analytics, tracking, or network call of any kind.
