# think regularly

A single-page, offline-first **retro typewriter writing app**. One HTML file, no build step, no accounts, no tracking. Your writing lives in your browser (and in the `.txt` files you export).

**Version 2.1**

---

## What's new in v2.1

| Feature | Detail |
| --- | --- |
| **Paged writing view** | Stacked paper sheets in A4 proportions with a fixed number of lines per page. Text flows downward and a new page only appears once the current one is full. Page numbers are centred at the foot of each sheet (`— 1 —`), with a `PAGE x / y` readout in the status bar. |
| **Caret-follow scrolling** | The line you are typing is always visible. As each new line begins, the view pans up with an eased `requestAnimationFrame` scroll so the active line sits at roughly 60% of the viewport height — like paper feeding through a typewriter. Works on desktop and on mobile with the on-screen keyboard open (via the `visualViewport` API). |
| **LCD one-liner mode** | A green-backlit LCD strip showing only the line you are typing, in the spirit of a 90s Brother word processor. Toggle with the **LCD** button or **Ctrl + L**. Switching between page view and LCD view never loses text. |
| **Font controls** | **A−** / **A+** across 6 size steps, plus a typeface picker: VT323 (default), Courier Prime, IBM Plex Mono and Libre Baskerville, loaded from Google Fonts. Size and typeface are saved to `localStorage`, and page breaks are recalculated whenever either changes. |
| **Open saved .txt files** | **OPEN .TXT** button, **Ctrl + O**, or drag and drop a `.txt` anywhere onto the app. The file opens as a new draft named after the file. |
| **Right-click → Open with think regularly** | A PWA file handler for `text/plain`. Install the app, then open `.txt` files straight from your desktop. |

Everything from v2.0 is unchanged and still working: typewriter key sounds and the carriage-return bell, multiple drafts, autosave, `.txt` export and full JSON backup.

---

## Files

```
index.html      the entire app (UI, editor, pagination, audio, storage)
manifest.json   PWA manifest, including the text/plain file_handlers entry
sw.js           service worker, caches the app for offline use
icon.svg        pixel-art sun app icon
README.md       this file
```

---

## Keyboard shortcuts

| Shortcut | Action |
| --- | --- |
| **Ctrl + L** (⌘ + L) | Toggle LCD one-liner mode |
| **Ctrl + O** (⌘ + O) | Open a saved `.txt` file |
| **Ctrl + S** (⌘ + S) | Force a save (autosave already runs constantly) |
| **Ctrl + Shift + N** | New draft |
| **↑ / ↓** | Move between lines, including across page breaks |

---

## Toolbar

- **☰ DRAFTS** — open the drafts panel (switch, rename, delete, restore a backup)
- **+ NEW** — start a new draft
- **OPEN .TXT** — load a text file as a new draft
- **EXPORT** — download the current draft as `.txt`
- **BACKUP** — download every draft as a single JSON file (restore it from the drafts panel)
- **LCD** — one-liner display mode
- **♪ SOUND** — typewriter key clicks and the return bell
- **A− / A+** and the typeface picker — six sizes, four fonts

---

## Install (and right-click → Open with)

1. Open the app in **desktop Chrome or Edge**.
2. Click the install icon in the address bar, or menu → **Install app**.
3. Once installed, right-click any `.txt` file in your file manager → **Open with** → **think regularly**. The file opens as a new draft.

**Note:** the right-click file handler relies on the Web App Manifest `file_handlers` API, which currently only works in **desktop Chrome / Edge after installing the app**. In Safari, Firefox and on mobile, use the **OPEN .TXT** button or drag and drop — those are the fallback and work everywhere.

The service worker caches the app shell, so once it has loaded a single time it will run offline.

---

## Running it locally

Service workers and the manifest need `http://` or `https://`, not `file://`:

```bash
python3 -m http.server 8080
# then open http://localhost:8080
```

---

## Testing checklist

- [ ] **Page 2 appears with the correct number.** Type (or paste) past the bottom of page 1. A second sheet appears, numbered `— 2 —`, and the status bar reads `PAGE 2 / 2`.
- [ ] **The caret stays visible while typing long text.** Keep typing to the bottom of the screen; the view pans up and the active line settles around 60% down. Repeat on a phone with the keyboard open.
- [ ] **The LCD toggle keeps your text.** Write a paragraph, press **Ctrl + L**, keep typing on the green strip, press **Ctrl + L** again — everything is still there, in order.
- [ ] **Font settings survive a reload.** Change the typeface and press **A+** twice, then refresh. Same font, same size, page breaks recalculated.
- [ ] **.txt opens via the button and via drag-and-drop.** Use **OPEN .TXT** (or **Ctrl + O**), then drag a `.txt` onto the window. Both create a new draft named after the file.
- [ ] **After installing, right-click a .txt → Open with → think regularly.** Desktop Chrome/Edge only; the file opens as a new draft.
- [ ] **Typewriter sounds still work.** Key clicks on letters, a softer thunk on space, the bell on Enter. The **♪ SOUND** toggle silences and restores them.
- [ ] **v2.0 regression pass.** Drafts switch cleanly, autosave shows **SAVED** in the status bar, **EXPORT** downloads a `.txt`, **BACKUP** downloads JSON and **RESTORE BACKUP** reads it back.

---

## Notes

- Pagination is measured with a canvas text metric that mirrors CSS `overflow-wrap: break-word`. The three monospace faces are exact; Libre Baskerville is measured per word, so a very long unbroken string may sit a pixel or two off.
- All drafts and settings are stored in `localStorage` under `tr_drafts`, `tr_current` and `tr_settings`. Clearing site data clears your writing — use **BACKUP** regularly.
