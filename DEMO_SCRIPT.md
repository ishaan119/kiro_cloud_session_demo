# Kiro Cloud Session — Demo Run Sheet

A minute-by-minute script for showcasing Kiro Cloud with this Tic-Tac-Toe repo.
The goal is to demonstrate **autonomy, real GitHub integration, spec-driven
structure, and memory** — not just code generation.

**Total runtime:** ~15–17 minutes (trim segments to fit).

---

## Before you start (prep — do this off-camera)

- [ ] Confirm the repo opens in a fresh Kiro Cloud session with no local setup.
- [ ] Confirm `index.html` runs (open it, play one round vs Computer on Hard).
- [ ] Have the exact prompts below ready to **paste** — do not type live.
- [ ] Keep the `backup/win-detection-bug` branch handy for the bug-hunt segment.
- [ ] Have a finished-result branch ready as a fallback if live generation stalls.
- [ ] Close noisy tabs/notifications; zoom the browser so text is readable.

---

## The arc

### 0:00 — Open cold (1 min)
Show the repo in the browser. Say: **"I have nothing installed locally — no
Node, no editor, no clone. This is all running in a cloud sandbox."**
Open `index.html`, play a couple of moves against the computer to prove it works.

### 1:00 — Prompt a real feature (4–5 min)
Paste this prompt and narrate what Kiro does as it plans and edits:

> Add a "match series" mode: first player to win 3 rounds wins the match. Show
> a banner announcing the match winner, and add a "New Match" button that resets
> the scoreboard. Keep the existing single-round flow working.

**What to point out while it runs:**
- It reads the existing file before editing (grounded changes).
- It plans the change across HTML, CSS, and JS.
- It verifies its own logic before declaring done.

### 5:00 — Show self-correction (optional, 2 min)
If a command or check fails, **let the audience see the recovery** — that
resilience is the point. If nothing fails naturally, skip this segment.

### 6:00 — Land a PR (2 min)
Ask Kiro to open a pull request. Then open the PR on GitHub and walk the diff.

> Commit this on a new branch and open a pull request into main with a clear
> description of what changed.

Point out: **branch name and commit message follow our team conventions** (see
`.kiro/steering/conventions.md`) — "I never told it that in this session."

### 8:00 — Close the review loop (2 min)
Paste a review-style comment and have Kiro address it:

> Reviewer feedback: the match-winner banner should be dismissible, and the
> "New Match" button should be visually distinct from "New Round". Please update.

### 10:00 — Bug hunt (optional, 3 min)
Switch to the seeded bug branch and prompt:

> Players report the game sometimes misses a diagonal win. Investigate the
> win-detection logic, find the bug, fix it, and explain the root cause.

(The `backup/win-detection-bug` branch has a subtle diagonal bug planted for this.)

### 13:00 — Web ↔ local handoff (3 min) ⭐
The showstopper: **the same repo, picked up seamlessly across environments.**
Kiro Cloud isn't a walled garden — the work lives in git, so any Kiro (web or
local) can continue where another left off.

**Setup:** have Kiro in the *browser* make a small change and push it, then
switch to *local* Kiro (in your IDE) on the same repo to continue — or go the
other direction. The narrative beat is "no export, no copy-paste, no lock-in."

**Web → local:**
1. In the browser session, prompt Kiro to make a change and push it (see prompt below).
2. Switch to your local machine. Pull the branch:
   ```
   git pull
   ```
3. Open local Kiro and prompt it to keep going — it has the full history and
   context from git.

**Local → web:**
1. Make/commit a change locally and `git push`.
2. Back in the browser, start (or refresh) a Kiro Cloud session on the repo — it
   sees the pushed commits immediately and can continue.

**What to point out:**
- The handoff is just **git** — branches, commits, push/pull. Nothing proprietary.
- Steering (`.kiro/steering/`) travels *with the repo*, so conventions apply in
  both environments automatically.
- You can start something ambitious in the cloud (no local setup) and finish it
  locally with your own tools — or vice versa.

> Make a small visible change — bump the page title to "Tic-Tac-Toe (Cloud+Local Demo)" — then commit and push it to the current branch so I can pick it up from another Kiro session.

### 16:00 — Reveal memory & wrap (1 min)
Recap the arc: cold start → feature → PR → review loop → bug fix → web/local
handoff, all autonomous and in the browser (and continued locally). Emphasize the
steering conventions were applied without re-explaining them, in *both*
environments.

---

## Exact prompts (copy-paste block)

```
Add a "match series" mode: first player to win 3 rounds wins the match. Show a banner announcing the match winner, and add a "New Match" button that resets the scoreboard. Keep the existing single-round flow working.
```

```
Commit this on a new branch and open a pull request into main with a clear description of what changed.
```

```
Reviewer feedback: the match-winner banner should be dismissible, and the "New Match" button should be visually distinct from "New Round". Please update.
```

```
Players report the game sometimes misses a diagonal win. Investigate the win-detection logic, find the bug, fix it, and explain the root cause.
```

```
Make a small visible change — bump the page title to "Tic-Tac-Toe (Cloud+Local Demo)" — then commit and push it to the current branch so I can pick it up from another Kiro session.
```

---

## Talking points to hit

- **No local setup** — everything runs in the cloud sandbox from a browser.
- **Autonomous multi-step execution** — plans, edits multiple files, self-verifies.
- **Real git & GitHub** — branches, commits, and PRs against the actual repo.
- **Web ↔ local, no lock-in** — start in the cloud with zero setup, continue
  locally in your IDE (or vice versa). The handoff is just git; steering and
  context travel with the repo.
- **Spec-driven option** — mention specs (requirements → design → tasks) for
  audiences who want rigor, not just "vibes."
- **Memory** — steering files and learnings apply team conventions automatically.

## Fallback lines (if something is slow)

- "While that runs — here's what it's doing under the hood…" (explain the plan).
- "Networks at conferences, right?" then switch to the pre-built fallback branch.
- "Let me show you the finished result and we'll circle back to the live run."
