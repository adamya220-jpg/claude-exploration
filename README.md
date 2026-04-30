# Building a Tic Tac Toe Game with Claude Code — Process Documentation

This document captures the full development process for a Tic Tac Toe web game, built using Claude Code. It is intended to support a presentation demonstrating how Claude Code assists in real software development tasks.

---

## What Was Built

A fully self-contained Tic Tac Toe game (`index.html`) with:
- Two-player turn-based gameplay (X and O)
- Win and draw detection
- Colorful, animated UI with a purple/pink gradient background
- A restart button
- Zero external dependencies — works offline in any browser

A second file, `PROCESS.md` (this file), documents the development process and key decisions for presentation purposes.

---

## How Claude Code Was Used

The session used Claude Code's **Plan Mode** — a mode where Claude researches the task and proposes a plan *before* writing any code. The user reviews and approves the plan, then Claude implements it.

### Key Claude Code Features Demonstrated

| Feature | How It Was Used |
|---|---|
| **Plan Mode** | Claude planned both files and deployment approach before writing a single line of code |
| **Worktrees** | Code was written in an isolated git worktree, keeping the main branch clean |
| **Live Preview** | The game appeared in Claude Code's preview panel immediately after `index.html` was created |
| **AskUserQuestion** | Claude surfaced structured questions mid-plan to capture preferences (see below) |

---

## Where User Input Was Required

Claude did not make all decisions autonomously. At two points during planning, Claude paused and asked the user structured questions before continuing:

### Question 1 — Documentation Format
> "What format should the process documentation be in?"

**Options offered:** Markdown file, HTML page, or inline comments  
**User chose:** Markdown file  
**Why it mattered:** This determined whether documentation would be a separate browsable file, embedded in the game, or part of the GitHub repo's visible README experience.

### Question 2 — Visual Style
> "What visual style should the Tic Tac Toe game have?"

**Options offered:** Clean & minimal, Dark mode, or Colorful & playful  
**User chose:** Colorful & playful  
**Why it mattered:** This directly shaped the CSS — gradient background, rounded cells, animated marks, and glow effects on winning cells.

---

## Key Decisions Made

### Single HTML file with inline CSS and JS
**Decision:** Everything lives in `index.html` with no external stylesheets or scripts.  
**Why:** GitHub Pages serves static files. A single file requires no build step, no bundler, and no configuration — it just works when pushed.

### Named `index.html` (not `tictactoe.html`)
**Decision:** The file is named `index.html` rather than a descriptive name.  
**Why:** GitHub Pages serves `index.html` as the root of a site. Any other name would require navigating to the full filename in the URL.

### CSS attribute selector for cell state (`data-mark`)
**Decision:** Cell state (X or O) is stored as a `data-mark` HTML attribute, and CSS targets it with `[data-mark="X"]`.  
**Why:** This keeps styling and logic separated cleanly — the JS sets the attribute, the CSS responds to it, with no JS needed to toggle class names for color/animation.

### No framework, no dependencies
**Decision:** Pure HTML, CSS, and vanilla JavaScript.  
**Why:** Keeps the project simple, portable, and immediately deployable. No `npm install`, no build tools, no breaking changes from package updates.

---

## Deployment to GitHub Pages

To deploy this game:

1. Push `index.html` (and `PROCESS.md`) to the `main` branch of a GitHub repository.
2. Go to **Settings → Pages** in the GitHub repository.
3. Under **Source**, select **Deploy from a branch**, choose `main`, and set the folder to `/ (root)`.
4. Save. GitHub will publish the site at:

```
https://<your-username>.github.io/<your-repo-name>/
```

No server, no hosting costs, no configuration files needed.

---

## File Structure

```
/
├── index.html     ← The game (serve this via GitHub Pages)
└── PROCESS.md     ← This document
```
