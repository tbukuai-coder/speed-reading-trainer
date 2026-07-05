# Roadmap

Ordered by training value, not feature count. The guiding principle: the app should stay **honest** (speed only counts with comprehension), **zero-dependency**, and **static-hostable** on GitHub Pages.

## v1.1 — Close the training loop  ⟵ in progress

- [ ] **Tracked comfort speed.** Store comfort speed in localStorage, seed it from the first speed test, and apply the progression rule automatically (two tests ≥75% → +10%; any test <60% → −10%). Surface it on the Plan tab and pre-set the sprint sliders to comfort +25% / +50% / +10%. Removes the mental arithmetic from the protocol.
- [ ] **Guided daily session.** A "Start today's session" flow that walks through the 15 minutes — pacer warm-up → three RSVP rounds at derived speeds → test on alternate days — with a per-step timer.
- [ ] **More passages (~12–15).** Three quizzes get exhausted in week one; a full 4-week cycle must never repeat a passage (re-reading inflates scores).

## v1.2 — Habit and honesty

- [ ] Streak counter + "last session" nudge on the Plan tab.
- [ ] Comfort-speed line + 7-session rolling average overlaid on the WPM chart, so the trend reads through the noise.
- [ ] Passage difficulty tiers (easy / standard / dense): drill on easy, test on standard.
- [ ] JSON export / import of the session log, so data survives switching browser or device.

## v1.3 — Real mobile app

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
