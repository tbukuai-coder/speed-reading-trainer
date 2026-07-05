# Tempo — Speed Reading Trainer

**Live app: https://tbukuai-coder.github.io/speed-reading-trainer/**

Single-file static HTML app, zero dependencies, no build step. Open `index.html` in any browser.

## What it does

Evidence-based speed-reading training with a comprehension gate: speed only counts when you can answer questions about what you read.

- **The plan** — a **tracked comfort speed** panel (seeded from your baseline test, auto-adjusted by the progression rule) with the three derived sprint speeds, plus a one-click **guided daily session** that walks you through pacer warm-up → three RSVP rounds → an alternate-day speed test with a per-step timer bar. Also the 4-week outline and an honest summary of the research (Rayner et al. 2016: realistic gains are 20–50%, not 1000 wpm).
- **Speed test** — timed natural reading of a built-in passage + 4-question quiz → measured wpm + comprehension %, auto-logged. Seeds/updates comfort speed and rejects implausibly fast reads (>1200 wpm) so a misclick can't poison your baseline. **Twelve** passages, each tiered easy/standard/dense.
- **RSVP sprints** — words flashed at a fixed point with the optimal-recognition-point letter in red (Spritz-style), 150–800 wpm, chunk size 1–3, punctuation/long-word pauses. Space = play/pause, ←/→ = speed ±25.
- **Pacer drill** — moving highlight sweeps normal text in 1–4 word chunks (regression suppression that transfers to real pages).
- **Progress** — WPM chart (session line + 7-session rolling average + comfort reference line, with legend) and comprehension bar chart (only quizzed sessions), baseline/best/gain stats, full session table, and **JSON export/import** of all data. The Plan tab also shows a **daily streak** with a last-session nudge.

## Passages & difficulty tiers

All 12 passages are original, ~250–280 words, each with a 4-question comprehension quiz. The tier tells you **how to use** each one — the app surfaces it in every passage selector and defaults speed tests to standard-tier material.

| Tier | Use it for | Reading demand |
|---|---|---|
| **Easy** | Drills (RSVP, pacer) — practice on words you already know | Concrete narrative, familiar vocabulary |
| **Standard** | Speed tests — your real, logged progress measure | General nonfiction, moderate density |
| **Dense** | Occasional stretch tests | Technical / abstract, higher cognitive load |

The training logic: **drill on easy, test on standard, stretch on dense.** Re-reading a passage inflates its comprehension score, so a full 4-week cycle should never repeat one — hence 12.

| # | Passage | Tier | Words |
|---|---|---|---:|
| 1 | Eighteen Months of the Pony Express | Easy | 263 |
| 2 | How Bees Vote With Their Bodies | Easy | 257 |
| 3 | The Invisible Livestock in Sourdough | Easy | 249 |
| 4 | The Keyboard That Was Never Meant to Be Fast | Easy | 251 |
| 5 | The Distributed Mind of the Octopus | Standard | 264 |
| 6 | The Box That Shrank the World | Standard | 265 |
| 7 | The Map That Lies About Size | Standard | 257 |
| 8 | Why the Brain Cleans House at Night | Standard | 252 |
| 9 | The Animal That Can Stop Being Alive | Standard | 260 |
| 10 | Why Roman Concrete Outlasts Ours | Dense | 260 |
| 11 | The Clock That Found Longitude | Dense | 280 |
| 12 | The City Built on a Forest of Trees | Dense | 251 |

**Tier mix:** 4 easy · 5 standard · 3 dense. RSVP and pacer drills also accept any pasted text (untiered).

## Notes

- All data in `localStorage` (`tempo-log-v1`, `tempo-comfort-v1`, `tempo-theme`); nothing leaves the page.
- Light/dark themes via CSS tokens; follows OS preference, toggle overrides (persisted).
- See `ROADMAP.md` and the repo's Issues tab for what's planned next (streaks, PWA, quiz-any-text).

## Development

No build step. Verified end-to-end with Playwright — `scratchpad/drive.py` in the working session drives the baseline test, comfort-speed seeding, guided-session orchestration, and both themes. To re-verify after edits, run that script against the local `index.html`.
