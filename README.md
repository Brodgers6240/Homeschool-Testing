# Homeschool Standardized Practice Test

A self-contained, Stanford 10-style practice test for homeschoolers in grades 5–12. Runs entirely in any modern web browser. No accounts, no servers, no tracking.

## What's in the box

- **`index.html`** — the entire app. Double-click to open in Chrome, Safari, Firefox, or Edge.
- **`README.md`** — this guide.

## Features

- **Grade selector home screen** (5–12). Grades 5 and 6 ship with full question banks (105 questions per grade across 7 subjects). Grades 7–12 show "Coming soon" — the framework is wired up, you just need to add questions.
- **Seven subjects per grade**: Reading Comprehension, Vocabulary, Language/Grammar, Math, Science, Social Studies, Spelling.
- **Single subject mode** or **Full Battery** (all subjects back-to-back, each timed separately).
- **Stanford 10-style timing**: each section has its own countdown. The timer turns yellow at 3 minutes left and red at 1 minute. The section auto-submits at zero.
- **Question navigation**: Previous / Next, jump to any question, flag for review, see at-a-glance which questions you've answered.
- **Results page** with overall score, per-subject breakdown, item-by-item review (your answer vs. correct answer + explanation), time per question, and skill tags.
- **Exports**: CSV (questions, choices, correct answer, student answer, status, time, explanation), JSON (raw data), and Print/Save-as-PDF.
- **Exit any time**: 🏠 Home button (with confirmation) on every screen; red Exit Test button during a section.

## Two ways to run it

### Option A — Just open it on your computer (easiest)

1. Find `index.html` in your folder.
2. Double-click it. It opens in your default browser.
3. Done. Works offline. You can copy the file to either child's laptop and run it independently.

### Option B — Host it on GitHub Pages (so anyone with a link can use it)

This puts the test online for free, with a URL like `https://yourusername.github.io/homeschool-tests/`. Anyone you share the link with can take the test.

**One-time setup (about 10 minutes):**

1. **Create a free GitHub account** at https://github.com/signup if you don't already have one.
2. From github.com, click the green **New** button (or **+** → **New repository**) in the top-right.
3. Name the repo something like `homeschool-tests`.
   - Set it to **Public** (required for free GitHub Pages).
   - Check **Add a README file**.
   - Click **Create repository**.
4. On the new repo's page, click **Add file** → **Upload files**.
5. Drag your `index.html` (and optionally this `README.md`) into the upload area.
6. Scroll down and click **Commit changes**.
7. Click the **Settings** tab (top-right of the repo).
8. In the left sidebar, click **Pages**.
9. Under **Build and deployment** → **Source**, select **Deploy from a branch**.
10. Under **Branch**, select **main** and **/ (root)**, then click **Save**.
11. Wait 1–2 minutes. Refresh the Pages settings page. You'll see: *"Your site is live at https://yourusername.github.io/homeschool-tests/"*. That's your URL.

**To update the test later** (add questions, fix things): just edit `index.html` in the repo (pencil icon on the file → make changes → Commit). GitHub Pages will redeploy automatically within a minute.

## Adding questions or new grades

All questions live inside `index.html` near the top of the `<script>` block. Each subject is added with one call:

```js
addSection(GRADE, "subject_key", "Display Name", TIME_LIMIT_SECONDS, [
  {
    id: "g7m1",                           // unique within the file
    text: "Question text here?",
    choices: ["A...", "B...", "C...", "D..."],
    correct: 2,                           // 0-based index of the right answer
    explanation: "Why the right answer is right.",
    skill: "Optional skill tag"           // shown in review + CSV
  },
  // ...more questions
]);
```

For Reading Comprehension passages, add `passage:` and `passageTitle:` to each question that should display the passage above it. Questions sharing the same passage just repeat the same `passage` text.

To turn on a grade (e.g., 7th), find the `/* --- GRADE 6 --- */` block, copy the `addSection` calls, change `6` to `7`, change the question IDs (e.g., `g6m1` → `g7m1`), and rewrite the questions.

## A few notes

- **Not a substitute for an official test.** This is high-quality practice modeled on Stanford 10 style and difficulty. For Louisiana homeschool portfolio requirements, an official nationally-normed test administered by a qualified tester is usually what counts. Use this for practice, identifying gaps, and getting comfortable with the format.
- **Honor system.** There's nothing stopping a student from refreshing the page or hunting for answers. Sit nearby for a real attempt; let them retake casually for skill practice.
- **Privacy.** Everything runs in the browser. No data is sent anywhere. Closing the tab discards the session unless you exported a CSV/JSON first.
- **Want more questions?** I can write additional banks (different passages, more math variants, grades 7–12) anytime — just ask.

## Subject time limits (per section)

| Subject | Time |
|---|---|
| Reading Comprehension | 30 min |
| Vocabulary | 15 min |
| Language / Grammar | 20 min |
| Math | 35 min |
| Science | 20 min |
| Social Studies | 20 min |
| Spelling | 12 min |
| **Full battery total** | **~2h 30min** |

These mirror Stanford 10 per-question time ratios scaled to 15-question sections.
