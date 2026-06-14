# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Running the game

Open `tic-tac-toe.html` directly in a browser — no build step or server required:

```powershell
Start-Process "tic-tac-toe.html"
```

## GitHub workflow

The remote is `https://github.com/iamPK5/tic-tac-toe`. After every change, commit and push:

```powershell
git add tic-tac-toe.html
git commit -m "<concise description of what changed>"
$env:PATH += ";C:\Program Files\GitHub CLI"; git push
```

`gh` lives at `C:\Program Files\GitHub CLI\gh.exe` and is not on the system PATH by default — prepend it when needed.

## Architecture

Everything lives in a single file (`tic-tac-toe.html`) with no external dependencies. The three sections are:

- **CSS** (lines 7–117): Dark navy theme. X is red (`#e94560`), O is teal (`#a8dadc`). `.win` triggers a pulse animation on winning cells; `.taken` blocks re-clicks.
- **HTML** (lines 119–149): Score display (`#score-x`, `#score-d`, `#score-o`), turn indicator (`#status`), 3×3 grid of `.cell` divs each with a `data-i` index (0–8), and a reset button.
- **JS** (lines 151–210): `WINS` is the hardcoded list of 8 winning index triples. `board[]` is the source of truth (9-element array). `init()` resets all state. `checkWin()` iterates `WINS` on every move. Scores persist across rounds in the `scores` object and reset only on page reload.
