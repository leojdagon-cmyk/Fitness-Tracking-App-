# Lift Week

A dead-simple weekly workout checklist that installs on your iPhone home screen like a native app.

Four rows, one tap each:

| Row | Turns green | Turns red |
| --- | --- | --- |
| Sunday Cardio | when you tap it | Monday, if still unchecked |
| Tuesday Lift | when you tap it | Wednesday, if still unchecked |
| Thursday Lift | when you tap it | Friday, if still unchecked |
| Friday Lift | when you tap it | Saturday, if still unchecked |

- **Gray** = not done yet, day hasn't passed.
- **Green** = done.
- **Red** = the day came and went unchecked.
- The whole week **auto-resets every Sunday at midnight** (a week runs Sunday → Saturday). No button to press.
- Everything is stored on the phone itself (`localStorage`). No account, no server, works with no signal.

You can still tap a red row to turn it green if you got the workout in late, and "Clear week" wipes the current week's checkmarks if you want a do-over.

## Notes for each day

Tap the **checkbox** to check a day off. Tap **anywhere else on the row** to open that day and jot down the exercises to do — one per line works well:

```
Bench 3x5
Incline DB press 3x8
Rows 3x8
Curls 3x12
```

Notes save as you type, and the first line shows under the day's name back on the list. They are your standing plan for that day, so unlike the checkmarks they are **not** wiped by the Sunday reset or by "Clear week" — edit them whenever the routine changes, or clear the text to remove them.

## Put it on your iPhone

The app is plain static files, so it just needs a URL you can open once in Safari.

1. **Publish it** — in this repo on GitHub: *Settings → Pages → Source: Deploy from a branch*, pick the branch holding these files and folder `/ (root)`, then Save. After a minute the app is live at `https://<your-username>.github.io/<repo-name>/`.
2. **Open that URL in Safari on your iPhone** (it has to be Safari, not Chrome).
3. Tap the **Share** button → **Add to Home Screen** → **Add**.

It now opens full screen with its own icon, no address bar, and works offline.

## Changing the schedule

Everything lives in one list at the top of the script in `index.html`:

```js
var PLAN = [
  { key: 'sun', day: 0, name: 'Sunday Cardio' },
  { key: 'tue', day: 2, name: 'Tuesday Lift' },
  { key: 'thu', day: 4, name: 'Thursday Lift' },
  { key: 'fri', day: 5, name: 'Friday Lift' }
];
```

`day` is 0 = Sunday through 6 = Saturday. Add, remove, or rename rows there and give each a unique `key`.

## Files

- `index.html` — the entire app (markup, styles, logic, notes sheet).
- `manifest.webmanifest` — name, icon, and standalone display for the home-screen app.
- `sw.js` — service worker that caches the app so it opens offline.
- `icons/` — home-screen icons.
