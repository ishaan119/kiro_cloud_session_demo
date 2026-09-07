# Tic-Tac-Toe — Kiro Cloud Demo Kit

A simple Tic-Tac-Toe (X and O) game that runs entirely in the browser — no build
step, no dependencies — packaged as a **turnkey demo kit for showcasing Kiro
Cloud sessions**.

## Play

Open `index.html` in any modern web browser.

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
