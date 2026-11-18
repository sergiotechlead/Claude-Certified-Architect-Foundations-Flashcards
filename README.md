# Claude Certified Architect (Foundations) - Flashcards

**Practice for the Claude Certified Architect (Foundations) exam with
flashcards, multiple-choice drills, and a timed 60-question exam
simulation, all in one self-contained HTML page, in English and Spanish.**

<p>
  <img alt="HTML5" src="https://img.shields.io/badge/HTML5-single%20file-E34F26?logo=html5&logoColor=white" height="20">
  <img alt="JavaScript" src="https://img.shields.io/badge/JavaScript-vanilla-F7DF1E?logo=javascript&logoColor=black" height="20">
  <img alt="Dependencies" src="https://img.shields.io/badge/dependencies-none-2ea44f" height="20">
  <img alt="Languages" src="https://img.shields.io/badge/i18n-EN%20%7C%20ES-6daaf5" height="20">
  <img alt="Claude" src="https://img.shields.io/badge/Claude-Artifact%20ready-D97757?logo=anthropic&logoColor=white" height="20">
</p>


![Claude Certified Architect (Foundations)](assets/desktop.png)

There's nothing to install or build. Open `docs/index.html` in a browser
and start studying.

> **Unofficial study aid.** This project isn't affiliated with or endorsed
> by Anthropic. Every question was written for this page from the public
> exam guide, and none is a real exam item. The estimated exam score is a
> guide, not a prediction.

## Contents

- [Features](#features)
- [Getting started](#getting-started)
- [How it works](#how-it-works)
- [Question bank](#question-bank)
- [Study modes](#study-modes)
- [Exam simulation](#exam-simulation)
- [Study timer](#study-timer)
- [Progress and storage](#progress-and-storage)
- [Keyboard shortcuts](#keyboard-shortcuts)
- [Editing the question bank](#editing-the-question-bank)
- [Study advice](#study-advice)
- [Credits](#credits)

## Features

| Feature | What it does |
|---|---|
| Flashcards | Answer in your head, turn the card, then grade yourself **Again** or **Got it** |
| Multiple choice | Pick an option and get an explanation for the right answer and every wrong one |
| Exam simulation | 60 questions, 120 minutes, grouped by scenario, no feedback until you submit, estimated score out of 1,000 |
| Scenarios | Every question is set in one of the 6 exam scenarios, shown before the question as on the exam |
| Mastery tracking | Every card moves through New → Learning → Familiar → Mastered |
| Decks | One deck per task statement (30), grouped under the 5 exam domains |
| Diagrams | 60 inline SVG diagrams explain the answers, and you can enlarge them |
| Study timer | Plan a session (120 minutes by default) with optional Pomodoro breaks and an estimate of how many cards fit |
| Languages | English, Spanish, or both side by side (`EN + ES`) |
| Themes | Auto (follows the system), Light, or Dark |
| Sync | Saves to the browser, or to your Claude account when the page runs as a Claude Artifact |

## Getting started

```bash
git clone https://github.com/sergiotechlead/Claude-Certified-Architect-Foundations-Flashcards.git
cd Claude-Certified-Architect-Foundations-Flashcards
start "" "docs/index.html"     # Windows
open "docs/index.html"         # macOS
xdg-open "docs/index.html"     # Linux
```

You can also double-click the file. It works offline, apart from the
Google Fonts stylesheet. Without it, the page falls back to system fonts.

### Optional local server

If you'd rather serve the page over HTTP, there's an optional Node.js
setup:

```bash
npm install
npm start          # serves docs/ at http://localhost:3000
```

Because the page lives in `docs/`, you can also publish it with GitHub
Pages (**Settings → Pages → Deploy from a branch → `main` / `docs`**).

## How it works

```text
docs/index.html
 ├── <style>                          layout, light/dark tokens, reduced-motion rules
 ├── markup                           header, study area, decks panel, dialogs
 ├── <script type="application/json" id="bank">   the question bank (data only)
 └── <script>                         app logic: decks, grading, exam, timer, storage, i18n
```

- **One file, no build step.** All CSS, JavaScript, data, and diagrams are
  inline. The only external request is for fonts.
- **Data and code are separate.** The question bank is a JSON block that
  the script parses at load time, so you can edit questions without
  touching the logic.
- **Every string is bilingual.** Interface text lives in the `T.en` and
  `T.es` tables. Bank entries store text as `["English", "Español"]` pairs.

## Question bank

The bank holds **60 questions**, the length of the real exam. The exam
guide (version 1.0) weights the 5 domains and lists 30 task statements
without weights, so each domain's count is rounded from its weight, with
at least one question per task statement.

| # | Domain | Weight | Task statements | Questions |
|---|---|---|---|---|
| 1 | Agentic Architecture & Orchestration | 27% | 7 | 16 |
| 2 | Tool Design & MCP Integration | 18% | 5 | 11 |
| 3 | Claude Code Configuration & Workflows | 20% | 6 | 12 |
| 4 | Prompt Engineering & Structured Output | 20% | 6 | 12 |
| 5 | Context Management & Reliability | 15% | 6 | 9 |
| | **Total** | **100%** | **30** | **60** |

Each question is set in one of the six exam scenarios. The real exam
presents four of them.

| Scenario | Questions |
|---|---|
| Customer support agent | 11 |
| Code generation with Claude Code | 10 |
| Multi-agent research | 12 |
| Developer productivity | 10 |
| Claude Code in CI | 9 |
| Structured data extraction | 8 |

Five questions ask for two answers, as the exam's multiple-response items
do.

## Study modes

- **Flashcard.** Read the question, answer in your head, and turn the card.
  Grade yourself **Got it** to move the card up one level, or **Again** to
  send it back to *Learning*. A missed card comes back within the next few
  cards.
- **Multiple choice** (the default). Choose an option (or two, when the
  card says so) and press **Check**. The card explains why the right
  answer is right and why each other option falls short.

In the **Decks and progress** panel you can choose domains and task
statements, show only cards you haven't mastered, and turn shuffle on or
off. When you finish a deck, you can restudy only the cards you missed.

## Exam simulation

**Take the exam** opens a timed run that's as close to the real exam as the
page can make it:

1. **All 60 questions, grouped by scenario.** The scenarios come in a
   random order, and the questions inside each one are shuffled. Each
   question shows its scenario first, as the exam does.
2. **120 minutes in one block, with no breaks.** The clock starts when you
   confirm, and it can't be paused. You can hide the clock, but it keeps
   running.
3. **Multiple choice only, with no feedback while you answer.** You can go
   back, change answers, flag questions to review, and strike out options
   you've ruled out.
4. **Decks, flashcards, and the timer are locked** until you submit. The
   exam doesn't change your study progress.
5. **When the time runs out, the exam is submitted for you.** Unanswered
   questions count as wrong.

The result shows how many you got right, a breakdown by domain, the
questions you missed, and an estimated score:

```text
estimated score = 100 + 900 × (correct ÷ 60)        pass mark: 720
```

The official exam reports a scaled score, and its conversion isn't
published. Treat the estimate as a guide only. Past attempts are listed in
the decks panel, and you can clear them without losing study progress.

## Study timer

**Plan your study time** sets a session of 30 min, 1 h, 2 h, or any length
from 5 to 600 minutes. It defaults to 120 minutes, the length of the exam.

- **Pomodoro breaks** are off by default. Turn them on for 25 minutes of
  focus, then a 5-minute break, with an optional chime.
- **Card estimate.** The page assumes about one minute per card at first,
  then adjusts to your own pace (idle time is ignored).
- **Breaks** open a full-screen rest prompt with a breathing guide. You
  can skip the break or end the timer.

## Progress and storage

| Key (`localStorage`) | Holds |
|---|---|
| `ccarf:progress:v1` | Each card's level and when you last graded it |
| `ccarf:settings:v1` | Theme, language, mode, filters, and your measured pace |
| `ccarf:timer:v1` | The running study timer, so it survives a reload |
| `ccarf:exam:v1` | An exam in progress, so it survives a reload |
| `ccarf:attempts:v1` | Your past exam attempts and their scores |

When the page is published as a **Claude Artifact**, it also saves progress
to your Claude account through `window.claude` and merges it with the
browser's copy, keeping the newest grade for each card. If the account
isn't available, the page keeps working from the browser's copy.

**Reset progress** erases the levels for every card, both locally and in
the account.

## Keyboard shortcuts

| Context | Key | Action |
|---|---|---|
| Study | `Space` | Turn the card |
| Study | `1` | Again |
| Study | `2` | Got it |
| Study / Exam | `A`, `B`, `C`… | Pick an option |
| Exam | `Shift` + `A`, `B`, `C`… | Strike out an option |
| Exam | `←` `→` | Previous / next question |
| Exam | `F` | Flag the question |
| Dialogs | `Esc` | Close |

## Editing the question bank

The bank is the `<script type="application/json" id="bank">` block in
`docs/index.html`. Its top-level keys:

| Key | Contents |
|---|---|
| `domains` | `d`, `name` `[en, es]`, `w` (exam weight) |
| `objectives` | Task statements: `k`, `n` (number such as `1.1`), `d` (domain), `name` `[en, es]` |
| `scenarios` | `k`, `name` `[en, es]`, `desc` `[en, es]` (the setting shown before each question) |
| `cards` | `id`, `n`, `d`, `ob` (task statement), `sc` (scenario), `q` `[en, es]`, `o` (options as `[en, es]` pairs), `a` (correct option indexes), `x` and `w` (explanations), `fixed` (keep option order), `dia` (diagram), `src` |
| `dias` | Inline SVG diagrams, keyed by the id that a card's `dia` names |
| `exam` | `minutes`, `pass`, and `tips` |
| `defaults` | The starting study mode and timer settings |
| `params`, `code` | API-parameter and code walk-through cards (empty in this build) |

After an edit:

- **The exam uses every card.** Adding or removing cards changes the exam
  length and the score's denominator.
- **Give each card a scenario.** The exam groups questions by `sc`, and
  the card shows the scenario above the question.
- **Write both languages.** Every text field needs an English and a
  Spanish entry.
- **Use `a` with two indexes for "choose two" questions.** The card and
  the exam rules pick this up on their own.
- **Check the JSON.** A syntax error stops the whole page from loading, so
  open it in a browser and watch the console.

## Study advice

From a candidate who passed: start with the official Anthropic courses
and their hands-on exercises with the Claude API, then practice the
question format with mock exams. The real scenarios are longer than the
ones here and take more reading.

## Credits

Created by **Sergio Beleño**. An unofficial study aid for the Claude
Certified Architect (Foundations) exam.
