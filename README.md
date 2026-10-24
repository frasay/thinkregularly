# think regularly

*A quiet place for writers.*

A distraction-free writing app with the soul of a 90s electric typewriter. One plain, light-yellow page. No menus, no toolbars, no noise — except the good kind.

## Features

- **One quiet page** — a pale yellow-tinged background, a title, and your words. Nothing else.
- **Autosaves as you write** — every keystroke is saved to your browser (`localStorage`) within a third of a second. A subtle *saved* indicator sits in the corner.
- **90s electric typewriter sounds** — synthesized entirely in code with the Web Audio API. No audio files, zero load time:
  - 4 daisy-wheel key variants with random pitch/tone jitter so no two taps sound identical
  - A deeper **spacebar** thunk
  - A softer **backspace** click
  - A mechanical clunk + **carriage-return ding** on Enter
- **Clean renaming** — the title at the top of the page *is* the filename. Click it, type, done. Press Enter to drop into the body.
- **Multiple pieces** — a drafts drawer (bottom-left, or `Ctrl+K`) lists all your writing, sorted by last touched. Create, open, or delete pieces.
- **Take your words with you** — download the current piece as `.txt`, or back up everything as `.json`.

## Keyboard shortcuts

| Keys | Action |
|---|---|
| `Ctrl+S` | Force save (it autosaves anyway) |
| `Ctrl+M` | Toggle typewriter sound |
| `Ctrl+K` | Open/close the drafts drawer |
| `Esc` | Close the drawer |
| `Enter` (in title) | Jump to the page |

## Running it

It is a single `index.html` with zero dependencies. Open it in any modern browser, or serve it with GitHub Pages:

1. Repo **Settings → Pages**
2. Source: **Deploy from a branch**, branch `main`, folder `/ (root)`
3. Your app will appear at `https://frasay.github.io/thinkregularly/`

## Notes

- Writing is stored in the browser you use it in. Use **backup all** in the drafts drawer for a portable copy.
- Sound starts on your first keypress (browsers require a user gesture before audio can play).
- Built for laptop keyboards — Dell and ThinkPad approved.
