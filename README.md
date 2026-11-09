# Study Hall

A single-file HTML study hub covering **7 UTHS classes** (2026/27) — built directly from each course's real Canvas module list, so every quiz question and flashcard traces back to an actual lesson.

Open [`valence-lab.html`](valence-lab.html) in any browser. No build step, no server required to use it — it's one self-contained file. (A `.claude/launch.json` is included for local dev, so unit-aware URL routing works under a real `http://` origin — plain `file://` works too in a normal browser, just not inside some sandboxed preview tools.)

## Classes

| Class | Questions | Flashcards | Teaching modules |
|---|---|---|---|
| Honors Chemistry | 319 | 100 | 101 |
| Honors Algebra 2 | 50 | 35 | — |
| Art Appreciation | 55 | 45 | — |
| Computer Science 1 | 55 | 40 | — |
| English 2 | 70 | 50 | — |
| Personal Financial Literacy | 45 | 35 | — |
| US History Since 1877 | 95 | 69 | — |

Chemistry is the deepest build (it also keeps its original **Learn** mode — 101 short teaching modules grouped by lesson); the other six classes get solid Quiz + Flashcard coverage across every real unit. Advisory, Student Services Supports for an IEP, and the Independent Learner/Credit-By-Exam FAQ course are intentionally excluded, since they're not classes to study.

## Modes

- **Quiz** — multiple-choice drills with instant feedback, an explanation for every answer, a live score/streak, and a round-end summary that lists exactly what you missed. Each round pulls a fresh random set of up to 12 questions from whatever units you've selected.
- **Flashcards** — flip-card review of key terms and definitions. Shuffle, step through with arrow keys, tap to flip, or hit **Sort #** to snap the deck back into unit-number order after shuffling.
- **Learn** (Chemistry only) — 101 short teaching modules grouped by lesson, covering the concept explanations behind each unit.

## Navigation

- **Homepage** (`#/`) — a card grid of all 7 classes with live question/flashcard/lesson counts; click a card to jump in.
- **URL slugs** — every class and mode has its own address, e.g. `#/chemistry`, `#/us-history/cards`, `#/algebra-2/quiz`. Back/forward and bookmarking work normally.
- **Unit chips** — numbered (`1.`, `2.`, …) and colored, one per real course unit; toggle any combination on/off. At least one must stay selected.
- **Exam segment presets** — one-tap buttons that jump straight to the units covered by each class's real 6-weeks exam (1st Six Weeks / 2nd Six Weeks / Final Exam), derived from each course's actual exam module placement — plus an "All Units" reset.

## Notes

- All state (best scores per class, per-viewer conveniences) is stored in `localStorage` — nothing leaves your browser.
- Proctorio/exam-logistics pages from the source courses were intentionally left out; this app only covers teachable concepts.
- No build tooling — edit `valence-lab.html` directly. Each class's data lives in its own set of plain JS arrays near the top of the `<script>` block (e.g. `HIST_UNITS`, `HIST_QUESTIONS`, `HIST_FLASHCARDS`), referenced from one `COURSES` array that the rest of the app (router, homepage, quiz/flashcard/learn logic) reads generically — so adding an 8th class means adding one more `COURSES` entry, not touching the app logic.
