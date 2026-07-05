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

## v2 — Quiz any text

- [ ] Optional "bring your own Claude API key" mode that generates four comprehension questions from any pasted text, so custom reading counts toward verified progress. Kept optional so the default build stays zero-dependency and key-free.

## Explicitly not planned

- Accounts / backend — localStorage + JSON export covers it.
- Gamification beyond a streak.
- Any vanity "900 wpm!" metric that contradicts the research the app is honest about.

---
Tracked as GitHub issues; see the repo's Issues tab.
