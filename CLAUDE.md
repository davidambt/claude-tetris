# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands
The project is vanilla JS/HTML/CSS with no build process.
- Run game: Open `index.html` in a browser or use a local server:
  - `python3 -m http.server 8000`
  - `npx serve .`
- Lint/Test: No automated tests or linting configured.

## Custom Commands
- `clima [ciudad]`: Fetch current weather for the city (default Barcelona) using `WebSearch`. Always respond in Spanish.


### Structure
- `index.html`: DOM structure, game board canvas (300x600), and UI overlays (Pause/Game Over).
- `style.css`: Dark-themed arcade styling.
- `game.js`: Core game logic.

### Core Logic (`game.js`)
- **State**: Board is a 2D array (`ROWS` x `COLS`) storing color indices.
- **Game Loop**: `requestAnimationFrame` based loop managing `dropInterval` for piece descent.
- **Mechanics**:
  - **Rotations**: Matrix transposition + row reversal (`rotateCW`) with basic wall kicks (`tryRotate`).
  - **Collisions**: `collide()` checks board boundaries and fixed blocks.
  - **Scoring**: Classic scoring based on lines cleared multiplied by level.
  - **Ghost Piece**: `ghostY` calculates and renders the landing position.
  - **Progression**: Level increases every 10 lines, decreasing `dropInterval`.
