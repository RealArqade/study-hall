# Study Hall

A single-file HTML study hub covering **51 UTHS classes** — the 7 classes actually taken (built directly from real Canvas module lists, so every quiz question and flashcard in those traces back to an actual lesson) plus the other **44 courses from UTHS's full 2026-2027 course catalog** (built from standard TEKS/AP curriculum content for each subject).

Open [`valence-lab.html`](valence-lab.html) in any browser. No build step, no server required to use it — it's one self-contained file. (A `.claude/launch.json` is included for local dev, so unit-aware URL routing works under a real `http://` origin — plain `file://` works too in a normal browser, just not inside some sandboxed preview tools.)

`index.html` at the repo root is a thin redirect to `valence-lab.html` (preserving any URL hash/query) so GitHub Pages has a landing page at the site's root URL.

Every page has a top bar with a **Read Me** button (opens this README, rendered in-page via [marked.js](https://github.com/markedjs/marked), no need to leave the app) and a **GitHub ↗** link back to this repo.

## Classes actually taken (built from real Canvas content)

| Class | Questions | Flashcards | Teaching modules |
|---|---|---|---|
| Honors Chemistry | 319 | 100 | 101 |
| Honors Algebra 2 | 50 | 35 | — |
| Art Appreciation | 55 | 45 | — |
| Computer Science 1 | 55 | 40 | — |
| English 2 | 70 | 50 | — |
| Personal Financial Literacy | 45 | 35 | — |
| US History Since 1877 | 95 | 69 | — |

Chemistry is the deepest build (it also keeps its original **Learn** mode — 101 short teaching modules grouped by lesson); the other six classes get solid Quiz + Flashcard coverage across every real unit.

## Full course catalog (44 additional courses)

Every other course UTHS offers (2026-2027 catalog), each with 4 units, 16 quiz questions, and 12 flashcards split across a 1st/2nd six-weeks + final exam structure. Advisory (×2), "Student Services Supports for an IEP," and "Independent Learner & Credit By Exam FAQ and Resources" are intentionally excluded, since they're not classes to study.

- **Math:** Algebra I, Geometry, Algebraic Reasoning, Advanced Quantitative Reasoning, Pre-Calculus, AP Calculus AB, AP Statistics
- **English/ELA:** English I, English III, AP English Language & Composition, English IV, AP English Literature & Composition
- **Science:** Biology, Integrated Physics and Chemistry, Physics, Environmental Systems, Geoscience
- **Social Studies:** World Geography, World History, US Government, Economics
- **Business:** Principles of Business/Marketing/Finance, Foundations of Business Communication & Technologies, Business Communication & Technologies, Business Management
- **Computer Science:** Fundamentals of Computer Science, AP Computer Science Principles, Computer Science II, AP Computer Science A, Computer Science III
- **World Languages:** Spanish I, Spanish II, Spanish III
- **Literacy/Humanities electives:** Practical Writing Skills, Reading I, Literary Genres, Humanities: Western Civilization, Creative Writing
- **Life skills/electives:** Health, College Readiness and Study Skills, Psychology, Lifetime Fitness and Wellness, Professional Communications, Art I

## Modes

- **Quiz** — multiple-choice drills with instant feedback, an explanation for every answer, a live score/streak, and a round-end summary that lists exactly what you missed. Each round pulls a fresh random set of up to 12 questions from whatever units you've selected.
- **Flashcards** — flip-card review of key terms and definitions. Shuffle, step through with arrow keys, tap to flip, or hit **Sort #** to snap the deck back into unit-number order after shuffling.
- **Learn** — short teaching modules grouped by lesson, covering the concept explanations behind each unit. Chemistry has its original 101 modules (grouped by real Canvas lesson); Algebra 2 has 53 modules built from its real Canvas lessons (including two not-yet-unlocked lessons written from their real module/page titles plus standard curriculum sourcing, matching the course's style); each of the 44 catalog courses has 48 modules (12 per unit, 3 lessons/unit). The other 5 real-Canvas classes (Art Appreciation, Computer Science 1, English 2, Personal Financial Literacy, US History) don't have Learn mode yet — 46 of 51 courses have it.

## Navigation

- **Homepage** (`#/`) — a card grid of all 51 classes with live question/flashcard/lesson counts; click a card to jump in.
- **URL slugs** — every class and mode has its own address, e.g. `#/chemistry`, `#/us-history/cards`, `#/ap-calculus-ab/quiz`. Back/forward and bookmarking work normally.
- **Unit chips** — numbered (`1.`, `2.`, …) and colored, one per real course unit; toggle any combination on/off. At least one must stay selected.
- **Exam segment presets** — one-tap buttons that jump straight to the units covered by each class's 6-weeks exam (1st Six Weeks / 2nd Six Weeks / Final Exam) — plus an "All Units" reset.

## Notes

- All state (best scores per class, per-viewer conveniences) is stored in `localStorage` — nothing leaves your browser.
- Proctorio/exam-logistics pages from the source courses were intentionally left out; this app only covers teachable concepts.
- No build tooling — edit `valence-lab.html` directly. Each class's data lives in its own set of plain JS arrays near the top of the `<script>` block (e.g. `HIST_UNITS`, `HIST_QUESTIONS`, `HIST_FLASHCARDS`, `WORLD_HISTORY_UNITS`, etc.), referenced from one `COURSES` array that the rest of the app (router, homepage, quiz/flashcard/learn logic) reads generically — so adding another class means adding one more `COURSES` entry, not touching the app logic.
