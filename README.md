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

## How fast is fast? Reading-speed benchmarks

Reading rate is conventionally measured in **words per minute (WPM)**, not per second (nobody reads a whole page per second — that would be ~15,000 WPM). These bands classify a reader *at normal comprehension*.

> **Not an official standard.** There is no ISO or international standard for reading-speed classes. The *anchor* figures are research-based — the ~238 WPM average (non-fiction) is from Brysbaert's 2019 peer-reviewed meta-analysis, and the comprehension drop-off past ~500–600 WPM is from Rayner et al. 2016. The *band labels and exact cutoffs*, however, are a common synthesis of reading-education literature and popular sources, and different sources draw the lines at slightly different values. Treat them as a well-grounded rule of thumb, not a certification scale. (The nearest thing to a formal norm — Hasbrouck & Tindal oral-reading-fluency norms — covers K–12 *oral* reading in specific school systems, not general adult silent reading.)

| Level | Words/min | ≈ Pages/min\* | ≈ Min/page\* | What it is |
|---|---|---:|---:|---|
| Beginning / studying | 100–150 | 0.4–0.6 | 1.7–2.5 | Learning readers, or careful study of hard material |
| Below average | 150–200 | 0.6–0.8 | 1.3–1.7 | Slower adult reading |
| **Average adult** | **200–300** | **0.8–1.2** | **0.8–1.3** | Typical silent reading with full comprehension (~238 WPM for non-fiction, Brysbaert 2019) |
| Above average | 300–400 | 1.2–1.6 | 0.6–0.8 | Proficient, practiced readers |
| Fast (still *reading*) | 400–600 | 1.6–2.4 | 0.4–0.6 | Upper edge of genuine reading; comprehension starts dropping past ~500–600 (Rayner 2016) |
| Skimming / scanning | 600–1000+ | 2.4–4+ | ≤0.4 | Not full reading — extracting gist; comprehension materially reduced |
| "Speed-reading" claims | 1000–20,000 | 4–80 | — | Marketing territory; controlled tests don't support these *with* comprehension |

\* Page figures use **~250 words per page** — the standard manuscript-page convention, and a clean round anchor. Printed novels are often denser (~275–350 words/page), so on a physical book these estimates run slightly optimistic. There's no strict standard: page density varies with trim size, font, and spacing, so read the page columns as a practical "how long is a book" guide, not an exact conversion.

**The catch that makes this app what it is:** a WPM number is only meaningful *at a stated comprehension level*. "600 WPM" at 40% recall is not faster reading than "300 WPM" at 95% — it's skimming with a worse outcome. That's why every speed here is paired with a quiz, and why the honest target is to move up a band *while holding ≥75% comprehension*, not to chase the raw number. Realistic trained improvement is roughly one band (20–50%), not a leap into the "speed-reading" row.

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

## References & further reading

Read the practical books for the *drills* and the science books for the *reality check* — the popular technique guides tend to promise 1,000+ WPM with full comprehension, which the research below does not support. Tempo deliberately teaches the techniques while keeping the claims honest.

**Practical technique**

- Peter Kump — *Breakthrough Rapid Reading* (rev. ed., 1998). One of the more grounded practical courses: hand-pacing, cutting regressions, widening fixations.
- Abby Marks-Beale & The Princeton Language Institute — *10 Days to Faster Reading* (2001). Approachable drills; realistic about skimming vs. reading.
- Stanley D. Frank — *The Evelyn Wood Seven-Day Speed Reading and Learning Program* (1990). The classic "Reading Dynamics" method, source of much modern speed-reading lore.
- Tony Buzan — *The Speed Reading Book* (rev. ed., 2006). Widely read; some throughput claims are disputed, so treat the numbers with the skepticism the science section invites.
- Mortimer J. Adler & Charles Van Doren — *How to Read a Book* (rev. ed., 1972). Not about speed, but the definitive guide to reading *levels* — inspectional reading (skimming with intent) is the skill most "speed readers" are actually using.

**The science (evidence-based)**

- Keith Rayner, Elizabeth R. Schotter, Michael E. J. Masson, Mary C. Potter & Rebecca Treiman (2016). "So Much to Read, So Little Time: How Do We Read, and Can Speed Reading Help?" *Psychological Science in the Public Interest*, 17(1), 4–34. **The definitive review** — the app's core premise comes from here.
- Marc Brysbaert (2019). "How Many Words Do We Read Per Minute? A Review and Meta-analysis of Reading Rate." *Journal of Memory and Language*, 109. Source of the ~238 WPM non-fiction baseline used in the benchmark table.
- Stanislas Dehaene — *Reading in the Brain: The New Science of How We Read* (2009). Why the eyes and language system, not willpower, set the ceiling.
- Maryanne Wolf — *Proust and the Squid* (2007) and *Reader, Come Home* (2018). How the reading brain is built, and what fast/shallow reading trades away.
