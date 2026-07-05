# Roadmap

Ordered by training value, not feature count. The guiding principle: the app should stay **honest** (speed only counts with comprehension), **zero-dependency**, and **static-hostable** on GitHub Pages.

## v1.1 — Close the training loop  ✅ shipped

- [x] **Tracked comfort speed.** Stored in localStorage, seeded from the first speed test, auto-adjusted by the progression rule (two tests ≥75% → +10%; any test <60% → −10%). Shown on the Plan tab with the three derived sprint speeds; sprint sliders pre-set from it.
- [x] **Guided daily session.** "Start today's session" walks through pacer warm-up → three RSVP rounds → alternate-day test via a fixed session bar with per-step progress.
- [x] **More passages.** Expanded 3 → 12, each tagged easy / standard / dense.
- [x] **Implausible-read guard.** Tests over 1200 wpm are rejected so a misclick can't poison the baseline.

## v1.2 — Habit and honesty  ✅ shipped

- [x] Streak counter + "last session" nudge on the Plan tab.
- [x] Comfort-speed reference line + 7-session rolling average overlaid on the WPM chart, with a legend.
- [x] Passage difficulty tiers surfaced in the selectors; tests default to standard-tier material.
- [x] JSON export / import of the session log (with validation), so data survives switching browser or device.

## v1.3 — Real mobile app  ⟵ next

- [ ] PWA manifest + service worker: installable to the home screen, works offline. Cheap given it's already static HTML, and daily-habit apps live on the phone.
- [ ] Touch controls for RSVP (tap = pause, swipe = speed).

## v1.4 — Honest metrics

The app's whole pitch is that speed only counts with comprehension. These make that tradeoff *visible* rather than just enforced.

- [ ] **Effective Reading Rate (ERR = wpm × comprehension%).** A single number that refuses to reward speed you can't recall — 450 wpm @ 50% (225) is worse than 300 @ 90% (270). Better headline stat than raw "best wpm."
- [ ] **Speed–comprehension frontier chart.** Scatter every session (wpm × comprehension) and trace your personal efficient frontier along the top edge, so the wall where speed starts costing recall is something you can see.
- [ ] **Next-day retention check.** A short delayed re-quiz on something read the day before — immediate comprehension and real retention are different things, and the gap is worth measuring.
- [ ] **Confidence calibration.** After each answer, "how sure were you?" — surfaces whether fast reading is breeding overconfidence.

## v1.5 — New drills

- [ ] **Subvocalization suppression drill.** Read while a metronome tap / distractor count occupies the inner voice — the technique the app describes but doesn't yet train.
- [ ] **Schulte tables.** Shuffled-number grid tapped in order — a classic peripheral-span / fixation-width exercise, a different muscle from RSVP.
- [ ] **Progressive column narrowing.** Squeeze the pacer's column over time so each line needs fewer fixations, training a wider span on real prose.

## v1.6 — Reach and habit

- [ ] **Streak calendar heatmap** (GitHub-style), extending the streak counter.
- [ ] **Dyslexia-friendly reading option** — bundled OpenDyslexic face (data-URI, stays zero-dependency) + adjustable letter/line spacing.
- [ ] **Configurable session length & daily reminder** (reminder ties into the v1.3 PWA push work).

## v2 — Quiz any text

- [ ] Optional "bring your own Claude API key" mode that generates four comprehension questions from any pasted text, so custom reading counts toward verified progress. Kept optional so the default build stays zero-dependency and key-free.
- [ ] **Auto-estimate tier for pasted text** (Flesch reading ease, computed locally) so custom material slots into easy / standard / dense automatically.
- [ ] **"Read your own book" mode** — paste a chapter, pace through it across sessions, track your position; turns drills into actual reading.

## Explicitly not planned

- Accounts / backend — localStorage + JSON export covers it.
- Gamification beyond a streak.
- Any vanity "900 wpm!" metric that contradicts the research the app is honest about.

---
Tracked as GitHub issues; see the repo's Issues tab.
