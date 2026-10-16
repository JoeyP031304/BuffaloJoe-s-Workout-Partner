# Ironlog

A personal strength and fitness tracker that runs entirely in your browser. No account, no server, no subscription. Add it to your iPhone home screen and it behaves like an app.

## Features

- **Workout logger** – set-by-set logging with weight, reps and RPE; set types (warm-up, drop, failure); "last time" shown next to every set; supersets; notes; automatic rest timer with beep and vibration.
- **Progressive overload** – when you hit all your target reps, the next session suggests a heavier weight.
- **Muscle recovery map** – every muscle's freshness (0–100 %) based on your recent hard sets, recovering over ~72 h.
- **Workout generator** – builds a session from your freshest muscles, your equipment, your goal (strength / muscle / endurance) and how long you have.
- **Routines** – seven built-in splits (push/pull/legs, upper/lower, full body, home) plus your own; repeat any past workout.
- **Guided circuits** – timed bodyweight sessions (HIIT, Tabata, EMOM, core) with a full-screen interval timer.
- **Progress** – strength score per lift and overall, weekly volume chart, per-exercise 1RM trend, personal records, consistency calendar, body weight / body fat / measurements.
- **Calculators** – plate loading per side, warm-up ramp, 1RM.
- **Exercise library** – 60+ exercises tagged by muscle and equipment, plus custom exercises.
- **Profile** – sex, age, height, weight adjust the strength-score standards and give a daily calorie and protein estimate for your goal.
- **Weekly plan builder** – goal + days you can train + experience → a week of lifting, cardio and rest days you can tweak; Home shows today's session.
- **Cardio** – running and walking (outdoor/indoor), stair climber, treadmill, swimming; stopwatch, distance and pace, floors, laps; feeds the recovery map and a weekly minutes chart.
- **Calories burned** – MET-based estimate per session (uses your bodyweight, duration, and pace/incline for cardio); shown on the summary, in history, and as a weekly chart.
- **Apple Health / Samsung Health** – the app detects iPhone vs Android and offers the matching one. On first open it asks to connect. Yes walks you through adding the "Sync to Ironlog" shortcut (steps and Apple Watch / Fitness workouts with duration, distance, calories, heart rate); No is remembered and you can connect later from More → Apple Health, where you can also disconnect or switch provider. iPhone: via the "Sync to Ironlog" shortcut (see SHORTCUT.md). Android: via Samsung Health → Settings → Download personal data; pick the emailed zip (or a CSV from it) in the app — steps, Galaxy Watch workouts, calories and heart rate come in. Zip is unpacked in the browser; nothing is uploaded anywhere. Re-running a sync skips what's already in. Steps chart on Home and Progress.
- **Backup** – export/import JSON, export CSV. Dark mode.

## Files

| File | Purpose |
|---|---|
| `index.html` | The whole app (HTML + CSS + JS in one file) |
| `manifest.json` | Lets Android/Chrome install it as an app |
| `icon.png`, `icon-192.png` | Home-screen icons |
| `SHORTCUT.md` | How to build the iPhone Shortcut that syncs Apple Health into the app |

## Host it free on GitHub Pages

1. Sign in to github.com and click **New repository**. Name it `ironlog`, keep it **Public**, click **Create repository**.
2. On the empty-repo page click **uploading an existing file**, drag in all four files, click **Commit changes**.
3. Go to **Settings → Pages**. Under *Build and deployment*, set Source to **Deploy from a branch**, Branch to **main** and folder **/ (root)**, then **Save**.
4. Wait a minute, refresh the Pages settings page, and your site is live at `https://<your-username>.github.io/ironlog/`.

To update the app later, open `index.html` in the repo, click the pencil icon, paste the new version, commit. Pages redeploys automatically.

## Put it on your iPhone home screen

1. Open the site in **Safari** (not Chrome).
2. Tap the **Share** button (square with arrow), then **Add to Home Screen**, then **Add**.
3. It opens full-screen with the Ironlog icon, like a native app.

Your data is stored in that browser. Export a backup from **More → Backup** now and then, and import it if you change phones.
