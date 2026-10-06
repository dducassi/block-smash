# Block Smash

A block breaker game inspired by Breakout. Vanilla JavaScript, no build
step, no dependencies — one HTML file you can open in a browser.

**Play it: [dducassi.github.io/block-smash](https://dducassi.github.io/block-smash/)**

## What it is

A browser game based on the MDN Web Docs tutorial *2D breakout game using
pure JavaScript*. The tutorial ends at a basic working Breakout; this
extends it with a few things the tutorial doesn't cover.

## Beyond the tutorial

- **Delta-time movement.** Ball and paddle speeds are expressed in pixels
  per second and multiplied by the frame delta, so the game plays the
  same on a 60Hz monitor and a 144Hz monitor. The tutorial uses
  fixed per-frame increments, which makes the game run faster on
  high-refresh displays.
- **Collision side detection.** When the ball hits a brick, the code
  compares its current position to the previous frame's position to
  determine which face of the brick was hit. Naive implementations just
  flip the Y velocity, which produces wrong bounces when the ball clips
  a brick corner.
- **Level progression.** Clearing all bricks increases the level, doubles
  the points per brick, speeds up the ball and paddle, and resets the
  brick field.
- **Multi-input support.** Keyboard, mouse, and touch all move the
  paddle. Touch is handled via `touchmove` so it works on mobile without
  a virtual button overlay.
- **Arcade-styled UI.** The title, HUD, and start button use the Press
  Start 2P font with a glowing red-on-black aesthetic.

## Controls

- **Left / Right arrow keys** — move the paddle
- **Mouse** — paddle follows the cursor horizontally
- **Touch** — paddle follows your finger horizontally
- **Start button** — begin a game; also restarts after game over
- **Space** — restart after game over

## Running locally

No install, no build:

    git clone https://github.com/dducassi/block-smash.git
    cd block-smash
    open index.html

Or just double-click `index.html`. The whole game is one file.

## How it works

The game is a single `index.html` with inline CSS and JavaScript.

- **Rendering** is on a 2D `<canvas>` at 720×480, using
  `requestAnimationFrame`.
- **State** lives in module-level variables (`ballSpeedX`, `bricks`,
  `score`, `lives`, etc.) since there's only one game instance and one
  file. This is the tutorial's structure and there was no reason to
  change it.
- **Bricks** are stored as a 2D array `bricks[column][row]`, each with a
  `status` flag. A brick with `status === 0` is skipped during both
  rendering and collision checks.
- **The game loop** runs continuously; a `titleScreen` flag and a
  `gameRunning` flag gate what gets drawn and updated.

## Credits

**Tutorial base:** [2D breakout game using pure JavaScript](https://developer.mozilla.org/en-US/docs/Games/Tutorials/2D_Breakout_game_pure_JavaScript),
MDN Web Docs.

**Extensions:** Daniel Ducassi.

**Font:** [Press Start 2P](https://fonts.google.com/specimen/Press+Start+2P)
by CodeMan38, SIL Open Font License 1.1, served via Google Fonts.

## License

Copyright © 2026 Daniel Ducassi. All rights reserved.
