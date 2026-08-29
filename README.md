# After School '99

A Windows 98 desktop simulator built for late-90s nostalgia — boot up the family PC, sign into MSN, fire up Winamp, and waste an afternoon clicking around.

Single self-contained HTML file. No build step. No dependencies. No backend.

## Run it

Just open the file in any modern browser:

```bash
open index.html
```

Or serve it with any static file server:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploy it

Drop the folder into any static host — it's one HTML file:

- **Netlify / Vercel:** drag-and-drop the folder
- **GitHub Pages:** push to a repo, enable Pages on the branch
- **S3 / Cloudflare Pages / Surge:** same story
- **Local sharing:** run `python3 -m http.server` and share your IP

## What's inside

The desktop opens after a short boot sequence. Every icon is clickable.

| App | What it does |
|---|---|
| **My Computer** | Browse drives — Floppy (A:), Local Disk (C:), audio CD (D:). C: has folders like "Napster Downloads" and a `password.txt` easter egg. |
| **Recycle Bin** | Old files you threw away (embarrassing haircut, group project, Barbie Girl). |
| **Internet Explorer** | Loads a full GeoCities parody page — rainbow marquee, hit counter, under-construction GIF, webring, Comic Sans everywhere. |
| **MSN Messenger** | A scripted conversation starts with `~*xX_CrAzYgUrL_99_Xx*~`. Type back and get canned replies. Hit "Send Nudge" to shake the window. |
| **Winamp** | Animated EQ bars, 9-track playlist of late-90s hits, play/pause/skip. "It really whips the llama's ass." |
| **Minesweeper** | Actually playable 9×9 board with 10 mines. Left-click to reveal, right-click to flag. |
| **Paint** | Draw with the mouse on a canvas. Full 20-color palette. |
| **My Diary.txt** | Notepad with a diary entry from March 14, 1999. |
| **Guestbook** | Sign it — persists in `localStorage` across visits, seeded with fake entries. |
| **Start menu** | Programs list plus a working "Shut Down..." that shows the classic "It's now safe to turn off your computer" screen. |

A **taskbar** with real clock and system tray sits at the bottom. Windows are draggable, minimizable, maximizable, and focus-aware (inactive title bars go gray, Win98-style). About 4 seconds after boot, an MSN notification toast pops in the corner as an initial hook.

## Sound

Uses the Web Audio API to synthesize period-appropriate beeps — a rising arpeggio on boot, a click chime when windows open, and the classic three-beep MSN nudge sound. No audio files, no assets.

## Customize it

Everything lives in one file. The interesting places to poke:

- **Add a desktop icon:** append to the `DESKTOP_ICONS` array (~line 730) and add a handler to the `APPS` object.
- **Change MSN dialogue:** the opening script and canned replies are in `APPS.msn` — search for `crazygurl`.
- **Add tracks to Winamp:** edit the `tracks` array in `APPS.winamp`.
- **Rewrite the diary:** it's the `diary` template literal in `APPS.notepad`.
- **Reskin GeoCities:** the whole HTML lives in `APPS.ie` inside the `.geo` div.

Icons are inline SVG stored in the `ICONS` object — draw or paste your own to replace them.

## Browser support

Works in any evergreen browser (Chrome, Firefox, Safari, Edge). Touch events are supported for mobile — single tap selects, double tap opens.

## Notes

- The Windows 98 look is achieved with pure CSS (4-layer beveled borders, blue gradient title bars, Tahoma system font). No image assets used for chrome.
- Guestbook entries are per-browser via `localStorage` — clearing site data resets them.
- Font is `Tahoma` fallback stack, which matches Win98's default UI font on most systems.

## License

MIT — do whatever you want with it. If you ship a fun variant, I'd love to see it.
