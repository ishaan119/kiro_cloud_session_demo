# Tic-Tac-Toe — Kiro Cloud Demo Kit

A simple Tic-Tac-Toe (X and O) game that runs entirely in the browser — no build
step, no dependencies — packaged as a **turnkey demo kit for showcasing Kiro
Cloud sessions**.

## Play

**Live:** https://ishaan119.github.io/kiro_cloud_session_demo/ (once GitHub Pages is enabled — see below).

Or open `index.html` in any modern web browser locally.

## Live hosting (GitHub Pages)

This repo auto-deploys the game to **GitHub Pages** via GitHub Actions
(`.github/workflows/deploy-pages.yml`) on every push to `main`.

**One-time setup** (repo admin, in the GitHub UI):
1. Go to **Settings → Pages**.
2. Under **Build and deployment → Source**, choose **GitHub Actions**.
3. Push to `main` (or re-run the workflow from the **Actions** tab). The site
   goes live at the URL above in ~1–2 minutes.

## Game features

- **Two modes:** 2 Players (local) or **vs Computer**.
- **AI difficulty:** *Hard* uses a minimax algorithm and is **unbeatable**;
  *Easy* plays optimally most of the time but mixes in random moves so it can be
  beaten.
- **Scoreboard** tracking X wins, O wins, and draws across rounds.
- Win detection across all rows, columns, and diagonals, with the winning line
  highlighted.
- Turn indicator and a **New Round** button.

`index.html` is fully self-contained (HTML + CSS + JavaScript in one file).

## Winning & draws

Game results are reported by a pure `checkWinner(board)` function — it takes a
board and returns a result with no DOM access, consistent with the existing
`evaluate(board)` helper.

`board` is a 9-element array of `"X"`, `"O"`, or `""` (empty string for an empty
cell), laid out row-major:

```
0 1 2
3 4 5
6 7 8
```

It returns exactly one of:

- `"X"` or `"O"` — the mark that has completed a winning line (any row, column,
  or diagonal).
- `"draw"` — the board is full and no one has won.
- `null` — the game is still in progress (no winner and at least one empty cell).

```js
// Top row of X → "X"
checkWinner(["X", "X", "X",
             "O", "O", "",
             "",  "",  ""]);   // "X"

// Full board, no winning line → "draw"
checkWinner(["X", "O", "X",
             "X", "O", "O",
             "O", "X", "X"]);  // "draw"

// Still in progress → null
checkWinner(["X", "O", "",
             "",  "X", "",
             "",  "",  "O"]);  // null
```

## Using this as a Kiro Cloud demo

This repo is set up to showcase Kiro Cloud's strengths: **autonomy, real GitHub
integration, spec-driven structure, and memory.**

- **`DEMO_SCRIPT.md`** — a minute-by-minute run sheet with exact copy-paste
  prompts, talking points, and fallback lines for a live session.
- **`.kiro/steering/conventions.md`** — sample team conventions (branch naming,
  commit style, code style). During a demo you can show Kiro applying these
  automatically, without re-stating them in the prompt.
- **`backup/win-detection-bug` branch** — a version with a subtle diagonal
  win-detection bug seeded, ready for a "find and fix the bug" demo segment.

See `DEMO_SCRIPT.md` for the full run-of-show.

## Files

- `index.html` — the entire game.
- `DEMO_SCRIPT.md` — the demo run sheet.
- `.kiro/steering/conventions.md` — sample steering conventions.
