# Tempo — Speed Reading Trainer

**Live app: https://tbukuai-coder.github.io/speed-reading-trainer/**

Single-file static HTML app, zero dependencies, no build step. Open `index.html` in any browser.

## What it does

Evidence-based speed-reading training with a comprehension gate: speed only counts when you can answer questions about what you read.

- **The plan** — a **tracked comfort speed** panel (seeded from your baseline test, auto-adjusted by the progression rule) with the three derived sprint speeds, plus a one-click **guided daily session** that walks you through pacer warm-up → three RSVP rounds → an alternate-day speed test with a per-step timer bar. Also the 4-week outline and an honest summary of the research (Rayner et al. 2016: realistic gains are 20–50%, not 1000 wpm).
- **Speed test** — timed natural reading of a built-in passage + 4-question quiz → measured wpm + comprehension %, auto-logged. Seeds/updates comfort speed and rejects implausibly fast reads (>1200 wpm) so a misclick can't poison your baseline. **Twelve** passages, each tiered easy/standard/dense.
- **RSVP sprints** — words flashed at a fixed point with the optimal-recognition-point letter in red (Spritz-style), 150–800 wpm, chunk size 1–3, punctuation/long-word pauses. Space = play/pause, ←/→ = speed ±25.
- **Pacer drill** — moving highlight sweeps normal text in 1–4 word chunks (regression suppression that transfers to real pages).
- **Progress** — WPM line chart + comprehension bar chart (only quizzed sessions), baseline/best/gain stats, full session table.

## Notes

- All data in `localStorage` (`tempo-log-v1`, `tempo-comfort-v1`, `tempo-theme`); nothing leaves the page.
- Twelve built-in test passages with quizzes; RSVP/pacer also accept pasted text.
- Light/dark themes via CSS tokens; follows OS preference, toggle overrides (persisted).
- See `ROADMAP.md` and the repo's Issues tab for what's planned next (streaks, PWA, quiz-any-text).

## Development

No build step. Verified end-to-end with Playwright — `scratchpad/drive.py` in the working session drives the baseline test, comfort-speed seeding, guided-session orchestration, and both themes. To re-verify after edits, run that script against the local `index.html`.
