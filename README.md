# Tempo — Speed Reading Trainer

**Live app: https://tbukuai-coder.github.io/speed-reading-trainer/**

Single-file static HTML app, zero dependencies, no build step. Open `index.html` in any browser.

## What it does

Evidence-based speed-reading training with a comprehension gate: speed only counts when you can answer questions about what you read.

- **The plan** — 15-min daily session (pacer warm-up → RSVP sprints → speed test every other day), progression rule (+10% comfort speed after two tests ≥75% comprehension), 4-week outline, and an honest summary of the research (Rayner et al. 2016: realistic gains are 20–50%, not 1000 wpm).
- **Speed test** — timed natural reading of a built-in passage + 4-question quiz → measured wpm + comprehension %, auto-logged.
- **RSVP sprints** — words flashed at a fixed point with the optimal-recognition-point letter in red (Spritz-style), 150–800 wpm, chunk size 1–3, punctuation/long-word pauses. Space = play/pause, ←/→ = speed ±25.
- **Pacer drill** — moving highlight sweeps normal text in 1–4 word chunks (regression suppression that transfers to real pages).
- **Progress** — WPM line chart + comprehension bar chart (only quizzed sessions), baseline/best/gain stats, full session table.

## Notes

- All data in `localStorage` (`tempo-log-v1`, `tempo-theme`); nothing leaves the page.
- Three built-in test passages with quizzes (octopus cognition, Pony Express, container shipping); RSVP/pacer also accept pasted text.
- Light/dark themes via CSS tokens; follows OS preference, toggle overrides (persisted).
