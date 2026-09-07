# Team Conventions

> Sample conventions for the Kiro Cloud demo. These are intentionally simple and
> visible so you can point at them during a live session and show Kiro applying
> them automatically — without being re-told in the prompt.

## Git & branches

- Branch names use the pattern `feature/<short-kebab-desc>` for features and
  `fix/<short-kebab-desc>` for bug fixes.
- Never commit directly to `main`. All changes land through a pull request.
- Keep commits focused: one logical change per commit.

## Commit messages

- Use the imperative mood in the subject line ("Add", "Fix", "Refactor").
- Keep the subject line under ~72 characters.
- Add a short body explaining the *why* when the change isn't obvious.

## Pull requests

- Title summarizes the change in one line.
- Body includes: what changed, why, and how to verify it.
- Target `main` as the base branch.

## Code style (this project)

- This is a zero-dependency, single-file project — keep the game self-contained
  in `index.html` (HTML + CSS + JS together). Do not introduce a build step or
  package manager unless explicitly asked.
- Use 2-space indentation.
- Prefer clear, descriptive names over abbreviations.
- Add a brief comment above any non-obvious block (e.g. the minimax logic).
- Keep game logic pure and testable where practical (e.g. `evaluate(board)`
  takes a board and returns a result, with no DOM access).

## Accessibility

- Interactive elements are real buttons with meaningful `aria-label`s.
- The board uses `role="grid"` / `role="gridcell"`.
