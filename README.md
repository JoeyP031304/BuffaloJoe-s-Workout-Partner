# Ironlog

A personal strength and fitness tracker that runs entirely in your browser. No account, no server, no subscription. Add it to your phone's home screen and it behaves like an app.

**Live:** https://joeyp031304.github.io/BuffaloJoe-s-Workout-Partner/

## What it does

**Training**
- Workout logger: weight, reps, RPE; set types (warm-up, drop, failure); "last time" beside every set; supersets; notes; automatic rest timer with beep and vibration (survives switching apps).
- Progressive overload: hit all your target reps and the next session suggests a heavier weight.
- Muscle recovery map: 13 muscle groups, 0–100 % fresh, based on your recent hard sets and cardio, recovering over ~72 h.
- Workout generator: builds a session from your freshest muscles, your equipment, your goal and the time you have.
- Weekly plan builder: goal + days you can train + experience → a week of lifting, cardio and rest days you can tweak. Home shows today's session.
- Routines: seven built-in splits plus your own; repeat any past workout.
- Guided circuits: timed bodyweight sessions (HIIT, Tabata, EMOM, core) with a full-screen interval timer.
- Cardio: running and walking (outdoor/indoor), stair climber, treadmill, swimming; stopwatch, distance and pace, floors, laps.

**Progress**
- Strength score per lift and overall (estimated 1RM ÷ bodyweight, adjusted for sex and age).
- Calories burned per session (MET estimate from duration, pace/incline and bodyweight).
- Weekly volume, cardio minutes, calories and steps charts; per-exercise 1RM trend; personal records; consistency calendar; bodyweight, body fat and measurements.
- Calculators: plate loading per side, warm-up ramp, 1RM.
- Exercise library of 60+ exercises tagged by muscle and equipment, plus custom exercises.

**Food & macros**
- Daily log by meal with calories, protein, carbs, fat, sugar and fiber against targets from your profile and goal (editable).
- Add food four ways: search a built-in table of 130 common foods (typical values, choose servings / grams / ounces), scan or type a barcode (Open Food Facts, free, 3 million products), search packaged foods online by name, or enter the label by hand. Your own foods are saved for next time; recents on top.
- Attach a photo to any meal (kept on the device as a small thumbnail). Automatic macros from a photo would need a paid AI service, so numbers come from the database, barcode or label.
- Today's food on Home; 7-day calories chart on Progress; food CSV export.

**Profile**
- Sex, date of birth, height, weight → strength standards, daily calorie and protein targets.

**Health app connection (18+)**
- On first open the app asks for your date of birth. The health connection is only offered to adults; it unlocks automatically on an under-18 user's 18th birthday.
- Then it asks "Connect to Health?" with a choice of **iPhone (Apple Health)** or **Android (Samsung Health)**. "Not now" is remembered; it can be turned on, switched or disconnected any time under **More → Health**.
- iPhone: tap **Get the shortcut** to install the shared "Sync to Ironlog" shortcut (one tap). Running it copies your last 7 days of daily step totals to the clipboard; **Paste from clipboard** (on Home or under More → Health) brings them in. Apple does not let shortcuts read workouts, so log cardio in Ironlog itself (it computes the calories). An illustrated 14-step guide in the app shows how to build the shortcut by hand if you'd rather. Can run automatically every morning via Shortcuts → Automation.
- Android: Samsung Health → Settings → Download personal data; pick the emailed zip (or a CSV from it) in the app. Steps, Galaxy Watch workouts, calories and heart rate come in. The zip is unpacked on the phone; nothing is uploaded anywhere.
- Re-running a sync skips anything already imported. Ironlog also accepts data appended to its address as `?import=` (URL-encoded text), which opens in Safari.

**Privacy, legal and support**
- No accounts, no server, no cookies, no analytics, no ads, no payments. All data stays on the device; **More → Your data & privacy** exports it (JSON/CSV) or deletes all of it.
- Privacy & cookie policy, terms of use & refund policy, and support & accessibility statement are inside the app (More) and as pages: `privacy.html`, `terms.html`, `support.html`.
- **More → Report a problem** prepares a report (version and device type only) to post as a GitHub issue or copy.
- A first-open notice explains where data lives. The health connection is offered to adults only (date-of-birth gate).

**Accessibility**
- Screen-reader and keyboard support: landmarks, labelled controls, list rows reachable with Tab and activated with Enter/Space, dialogs with focus management and Escape to close, charts with text descriptions, status messages announced, visible focus rings, text contrast ≥ 4.5:1 in light and dark mode, pinch-zoom allowed, reduced-motion respected. Audited with axe-core (0 violations across 36 screens).

**Everything else**
- Dark mode, lb/kg (mi/km) labels, backup export/import (JSON), CSV export.

## Files

| File | Purpose |
|---|---|
| `index.html` | The whole app (HTML + CSS + JS in one file) |
| `manifest.json` | Lets Android/Chrome install it as an app |
| `icon.png`, `icon-192.png` | Home-screen icons |
| `SHORTCUT.md` | What the iPhone shortcut does and how to rebuild it (the app has the illustrated guide) |
| `privacy.html`, `terms.html`, `support.html` | Privacy & cookie policy, terms & refund policy, support & accessibility (same text as inside the app) |
| `barlow-*.woff2`, `FONT-LICENSE.txt` | Self-hosted Barlow fonts (SIL Open Font License); no third-party font requests |

## Host your own copy on GitHub Pages (free)

1. Sign in to github.com → **New repository**, Public → **Create repository**.
2. On the empty-repo page click **uploading an existing file**, add all the files above → **Commit changes**.
3. **Settings → Pages** → Source: *Deploy from a branch*, Branch: `main`, folder `/ (root)` → **Save**.
4. After a minute the site is live at `https://<your-username>.github.io/<repo-name>/`.

To update, upload a new `index.html` the same way.

## Put it on a phone home screen

- **iPhone:** open the site in Safari → Share → **Add to Home Screen**. Note: iPhone keeps the Home Screen icon's data separate from Safari's, so pick one place to use Ironlog. The health sync works the same in both (shortcut → paste).
- **Android:** open the site in Chrome → menu → **Add to Home screen** / **Install app**.

Export a backup (More → Backup) now and then; import it on a new phone to restore.

## Versions

Each release is saved in `backups/` on the maintainer's machine. Current: **v14**.
