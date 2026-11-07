# Kid Games

A collection of browser games for kids, hosted with GitHub Pages from the `npyati/kid-games` repo (branch `main`, root folder). Live at https://npyati.github.io/kid-games/. The players are the user's kids (2nd and 5th graders at the start), so games should be readable and fair for that age.

## Layout

- `index.html`: the game picker. Games are listed in the `GAMES` array at the top of its script.
- `<game-name>/index.html`: one folder per game, each a single self-contained file (inline CSS and JS, no build step, no frameworks). It must also work when opened straight from disk (`file://`).
- `<game-name>/README.md`: notes for that game.
- `gobble-grid.html` at the root is only a redirect for old links.

## Adding a new game

1. Create `<game-name>/index.html`. Include a full `<!doctype html>` page, an "All games" link to `../`, and a visible way back to the menu.
2. Add the game to `GAMES` in the root `index.html`, with card art as an inline SVG (viewBox 0 0 320 180).
3. Add a row to the table in the root `README.md`.
4. Make original games. Don't recreate a specific existing game's name, characters, art or music, even if the mechanics are similar.

## Conventions

- **Saved data:** all games share one origin (npyati.github.io), so every `localStorage` key must start with the game's own prefix (Gobble Grid uses `gobblegrid`). Wrap every storage access in try/catch, and clean up bad saved values on load so they can't break the menu.
- **Sound:** start Web Audio only after a user click or keypress. Keep separate music and sound-effect toggles.
- **Fonts and look:** Gobble Grid and the picker use Lilita One (display) and Nunito (body) on a dark indigo palette. New games can have their own look, but should still feel at home on the picker.
- **Correctness:** any game that teaches facts (math answers, phonics) gets a separate checker script run over many generated questions before shipping. Wrong-answer explanations must be true too.

## Testing and shipping

- Syntax check: pull the `<script>` out of the file and run `node --check` on it.
- Browser test: serve the folder with `python3 -m http.server 8765 --bind 127.0.0.1` and drive it with Claude in Chrome. Close the tab and stop the server afterwards.
- Push to `main` only when the user asks. GitHub Pages rebuilds in about a minute. Afterwards, fetch the live page to confirm the change is there.
- Commits end with the Co-Authored-By line the session provides.
