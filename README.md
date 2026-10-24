# think regularly

A single-page retro typewriter writing app. No accounts, no server, no tracking — everything lives in your browser's `localStorage`, and it works offline once installed.

**v2.1**

---

## What's new in v2.1

| Feature | Notes |
|---|---|
| **Paged writing view** | Stacked A4-proportioned sheets. Text flows down the page; a new sheet appears only once the current one is full. Page numbers sit centred at the foot of each sheet as `— 1 —`, with a `PAGE x / y` readout in the status bar. |
| **Caret-follow scrolling** | The line you are typing is always visible. As each new line starts the view eases upward (requestAnimationFrame cubic ease, or an instant jump if you have *prefers-reduced-motion* set) so the active line rests at roughly 60% of the viewport height — paper feeding through a platen. Uses the `visualViewport` API so it also works on mobile with the on-screen keyboard open. |
| **LCD one-liner mode** | A green-backlit strip showing only the line you are typing, in the spirit of a 90s Brother word processor. Toggle with the **LCD** button or **Ctrl+L**. Switching between page view and LCD never loses text — the same editor stays focused underneath. |
| **Font controls** | **A−** / **A+** across six size steps, plus a typeface picker: **VT323** (default), **Courier Prime**, **IBM Plex Mono** and **Libre Baskerville** (serif), loaded from Google Fonts. Size and typeface are saved to `localStorage` and page breaks are recalculated whenever either changes. |
| **Open saved .txt files** | **OPEN .TXT** button, **Ctrl+O**, or drag and drop a `.txt` anywhere onto the app. The file opens as a new draft named after the file. |
| **Right-click → Open with** | Installable PWA with a `file_handlers` entry for `text/plain`, a service worker for offline use and a pixel-art sun icon. |

Everything from v2.0 still works: typewriter key audio, multiple drafts, autosave, `.txt` export and JSON backup/restore.

---

## Keyboard shortcuts

| Shortcut | Action |
|---|---|
| `Ctrl` / `Cmd` + `L` | Toggle LCD one-liner mode |
| `Ctrl` / `Cmd` + `O` | Open a `.txt` file |
| `Ctrl` / `Cmd` + `S` | Export the current draft as `.txt` |
| `Ctrl` / `Cmd` + `N` | New draft |

---

## Toolbar

- **DRAFTS** — open the draft drawer (switch, rename ✎, delete ✕)
- **NEW** — start a named draft
- **OPEN .TXT** — load a text file as a new draft
- **EXPORT** — download the current draft as `.txt`
- **BACKUP** — download every draft as a single `.json` file
- **RESTORE** — load a `.json` backup (dragging the `.json` onto the window also works)
- **A− / A+**, typeface picker, **LCD**, **♪ ON/OFF** (typewriter sound)

---

## Install (and the right-click "Open with")

1. Open the site in **desktop Chrome or Edge**.
2. Click the install icon in the address bar (or ⋮ → *Install app*) and choose **Install**.
3. After installing, right-click any `.txt` file in your file manager → **Open with → think regularly**.

> **Note:** the right-click file handler is a Chromium-only capability and only becomes available **after** the app is installed on desktop Chrome/Edge. It does not work in Safari or Firefox, and it does not work from a plain browser tab. In those cases use the **OPEN .TXT** button, **Ctrl+O**, or drag and drop — those are the fallbacks and work everywhere.

Hosting notes: the service worker and manifest use relative paths (`./`), so the app works from a GitHub Pages project subpath. Service workers require HTTPS (or `localhost`).

---

## Files

| File | Purpose |
|---|---|
| `index.html` | The whole app — markup, styles, logic |
| `manifest.json` | PWA manifest, including the `file_handlers` entry for `.txt` |
| `sw.js` | Service worker, cache-first app shell for offline use |
| `icon.svg` | Pixel-art sun icon |
| `README.md` | This file |

---

## Testing checklist

- [ ] **Page 2 appears with the correct number** — type (or paste) past the bottom of sheet one; a second sheet appears, its footer reads `— 2 —`, and the status bar reads `PAGE 2 / 2`.
- [ ] **The caret stays visible while typing long text** — hold down a key or type several paragraphs; the view keeps easing up and the active line never slips below the fold. Repeat on a phone with the keyboard open.
- [ ] **The LCD toggle keeps your text** — type a sentence, press `Ctrl+L`, keep typing on the green strip, press `Ctrl+L` again; everything is intact and in the right place on the page.
- [ ] **Font settings survive a reload** — change the typeface and size, reload the page; both are restored and the page breaks are recalculated to match.
- [ ] **.txt opens via the button and via drag-and-drop** — use **OPEN .TXT** / `Ctrl+O`, then drag a `.txt` onto the window. Each opens as a new draft named after the file.
- [ ] **After installing, right-click a .txt → Open with** — install in desktop Chrome/Edge, then right-click a `.txt` and choose *Open with → think regularly*; it launches and loads the file as a draft.
- [ ] **Typewriter sounds still work** — keys clack, the spacebar is softer, Return gives a carriage bell; the **♪** button mutes and the setting persists.
- [ ] **Drafts, autosave, export and backup still work** — switch drafts, confirm the status bar shows `saved …`, export a `.txt`, back up to `.json` and restore it.

---

## Licence

Personal project by Guy Fraser. Use it, fork it, write something.
