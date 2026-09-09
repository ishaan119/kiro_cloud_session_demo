# Kiro Cloud Session — Demo Run Sheet

A step-by-step script for showcasing **Kiro Cloud Sessions** with this
Tic-Tac-Toe repo. The arc leads with the capabilities the docs headline:
one agent across every surface, sessions that outlive a single device, and
autonomous mode that plans, delegates to sub-agents, and opens a PR on its own.

**Goal:** show that a Kiro Cloud session is *your account's agent in the cloud* —
not a browser tab. It keeps working when you step away, and any surface
(browser, phone, terminal, IDE) can pick it up because the work lives in git.

**Total runtime:** ~15–18 minutes. Recording, so no need to rush — narrate freely.

**Live game:** https://ishaan119.github.io/kiro_cloud_session_demo/

---

## The headline capabilities (say these up front)

- **One agent, every surface.** A cloud session runs the *same* agent harness as
  the local IDE and CLI. Repos are cloned server-side; your local copy is never
  uploaded.
- **The session belongs to your account, not a device.** Start a long task in the
  browser, close your laptop, and check on it later from your phone, terminal, or
  IDE. It keeps running in the cloud while you're away.
- **Two modes.** *Vibe* (collaborative, iterate together) and *Autonomous* (asks
  clarifying questions, builds a plan, delegates to sub-agents, opens a PR
  automatically). You can switch from Vibe to Autonomous at any point.

---

## Before you start (prep — do off-camera)

- [ ] Open the repo and the live game in browser tabs.
- [ ] Have this script open to copy-paste prompts (don't type live).
- [ ] Have a second device handy (phone or terminal) for the cross-device beat.
- [ ] Have your local clone + local Kiro/IDE ready for the handoff beat.
- [ ] Keep the `backup/win-detection-bug` branch handy for the bug-hunt segment.

---

## The arc

### STEP 1 — Open cold in the browser (1 min)
**Do:** Show the repo in the browser. Open the live game, play a couple of moves
against the computer.

**Say:** *"Nothing is installed on my laptop — no Node, no editor, no clone. This
is a Kiro Cloud session running in my browser, and the game is already live on
GitHub Pages. The session is running the exact same agent I'd get in the IDE or
CLI."*

### STEP 2 — Build a feature in Vibe mode (4–5 min)
**Do:** Paste the feature prompt (below) into the Vibe session. Narrate as it works.

> Add a "match series" mode: first player to win 3 rounds wins the match. Show a
> banner announcing the match winner, and add a "New Match" button that resets
> the scoreboard. Keep the existing single-round flow working.

**Say:** *"This is Vibe mode — collaborative. It reads the existing file first,
plans the change across HTML/CSS/JS, and verifies its own logic before saying done."*

### STEP 3 — Switch to Autonomous mode for a bigger task (4–5 min) ⭐
**Do:** Switch the session from **Vibe → Autonomous** (you can do this mid-session).
Give it a larger, outcome-level goal and let it run.

> Add a full Jest test suite for the game logic (win detection, draw detection,
> and the minimax AI), set up a CI workflow to run the tests on every pull
> request, then open a pull request into main with everything.

**Say:** *"Now I'm switching to Autonomous mode. Instead of stepping through with
me, it asks any clarifying questions up front, builds a plan, delegates to
specialized sub-agents, and opens the pull request itself when it's done."*

**What to point out while it runs:**
- It plans before acting and shows the plan.
- It may run **multiple sub-agents in parallel** (e.g. one writing tests, one
  wiring CI).
- It opens the PR autonomously — no manual git from you.

### STEP 4 — Step away: cross-device pickup (2–3 min) ⭐ SIGNATURE MOMENT
**Do:** While Autonomous mode is still working, **close the laptop lid** (or switch
tabs away) and pick up your **phone** (or a terminal). Open the same session /
repo from the other device and show the task still progressing / completed.

**Say:** *"Here's the part that surprises people. This session belongs to my Kiro
account, not this laptop. I can close my laptop, walk away, and the agent keeps
working in the cloud. Let me check on it from my phone… and there it is, still
going — it opened the PR while I was away."*

> (Nothing to paste — this beat is about the device switch. Just show the same
> session/PR visible from the second device.)

### STEP 5 — Review the PR & close the loop (2 min)
**Do:** Open the PR that Autonomous mode created. Walk the diff (tests + CI +
feature). Point out the branch name and commit style.

**Say:** *"Notice the branch name and commit messages follow our team conventions —
I never said that in this session. It read them from our steering file, and
steering travels with the repo, so it applies in the cloud and locally alike."*
(Open `.kiro/steering/conventions.md` to show the source.)

**Optional — Kiro as reviewer:** run a code/security review pass on the PR and
have it post findings, then address them and push fixes to the same branch.

> Review this pull request as a code reviewer with a focus on correctness and
> security. Post your findings, then address them and push the fixes.

### STEP 6 — Web ↔ local handoff via git (2–3 min)
**Do (browser session):** paste the title-bump prompt and let it push.

> Make a small visible change — bump the page title to "Tic-Tac-Toe (Cloud+Local
> Demo)" — then commit and push it to the current branch so I can pick it up from
> another Kiro session.

**Do (local terminal):**
```
git checkout feature/tic-tac-toe
git pull
grep "<title>" index.html
```

**Say:** *"I made that change in the browser with zero local setup. Now I pull it
down and keep working in my own IDE with local Kiro. No export, no copy-paste —
it's just git, and the same agent picks up right where the cloud left off. It
works the other way too: push from local, refresh the cloud session, it's there."*

### STEP 7 — Bug hunt (optional, 3 min)
**Do:** Switch to the seeded bug branch and prompt.

> Players report the game sometimes misses a diagonal win. Investigate the
> win-detection logic, find the bug, fix it, and explain the root cause.

(The `backup/win-detection-bug` branch has a subtle diagonal bug planted for this.)

### STEP 8 — Wrap (1 min)
**Recap the arc:** cold start in the browser → build in Vibe → switch to
Autonomous for a bigger task → step away and monitor from another device → PR
opened autonomously → reviewed and merged → continued locally.

**Say:** *"From a browser with nothing installed: I built a feature, delegated a
bigger task to Autonomous mode with parallel sub-agents, walked away and watched
it finish from my phone, and moved seamlessly between cloud and local — all on my
real repo, all with my team's conventions applied automatically."*

---

## Exact prompts (copy-paste block)

**Vibe — build the feature:**
```
Add a "match series" mode: first player to win 3 rounds wins the match. Show a banner announcing the match winner, and add a "New Match" button that resets the scoreboard. Keep the existing single-round flow working.
```

**Autonomous — bigger outcome (tests + CI + PR):**
```
Add a full Jest test suite for the game logic (win detection, draw detection, and the minimax AI), set up a CI workflow to run the tests on every pull request, then open a pull request into main with everything.
```

**Kiro as reviewer (optional):**
```
Review this pull request as a code reviewer with a focus on correctness and security. Post your findings, then address them and push the fixes.
```

**Web ↔ local handoff:**
```
Make a small visible change — bump the page title to "Tic-Tac-Toe (Cloud+Local Demo)" — then commit and push it to the current branch so I can pick it up from another Kiro session.
```

**Bug hunt:**
```
Players report the game sometimes misses a diagonal win. Investigate the win-detection logic, find the bug, fix it, and explain the root cause.
```

---

## Talking points to hit

- **One agent, every surface** — the cloud session runs the same harness as the
  IDE and CLI; your local copy is never uploaded.
- **Sessions outlive the device** — start in the browser, close the laptop, check
  from your phone/terminal/IDE; it keeps running in the cloud.
- **Two modes** — Vibe (collaborative) and Autonomous (plans, delegates to
  sub-agents, opens a PR automatically); switchable mid-session.
- **Autonomous + parallel sub-agents** — delegate an outcome, not step-by-step.
- **Real git & GitHub** — branches, commits, and PRs against the actual repo.
- **Web ↔ local, no lock-in** — the handoff is just git; steering and context
  travel with the repo.
- **Memory** — steering files apply team conventions automatically, everywhere.

## Notes / references

- Kiro Cloud Sessions docs: https://kiro.dev/docs/cloud-sessions/
- Autonomous mode docs: https://kiro.dev/docs/web/autonomous-mode/
- Content about Kiro capabilities is paraphrased from the official Kiro docs.
