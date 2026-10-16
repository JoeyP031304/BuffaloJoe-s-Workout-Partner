# "Sync to Ironlog" — iPhone Shortcut

Pulls the last 7 days of daily step totals out of the Health app and copies them to the clipboard in the format Ironlog reads. Then, in Ironlog, tap **Paste from clipboard** (on the Steps card on Home, or under More → Health). Nothing leaves your phone.

**Install in one tap:** https://www.icloud.com/shortcuts/114435bc94dc4fe2a01be32637ac401c (this is the link behind the app's "Get the shortcut" button). Tap it on the iPhone → **Add Shortcut**.

## Why steps only

Apple's Shortcuts app has no action that reads workouts from Health — the only workout actions are Start Workout, End Workout and Log Workout, and "Workouts" is not a Health Sample type. So the shortcut syncs steps, and cardio/strength sessions are logged in Ironlog itself, which computes their calories.

## Why the clipboard

A shortcut can only open a web address in Safari, and iPhone keeps a Home Screen web app's data separate from Safari's. Copying to the clipboard works for both: run the shortcut, open Ironlog wherever you use it, tap Paste. (Ironlog also understands `?import=` + URL-encoded text on its address, which is what opens in Safari.)

## What the shortcut contains (to rebuild it by hand)

The app has an illustrated version of this under More → Health → "Prefer to build it yourself?".

1. **Find Health Samples** — Type **Steps**, filter **Start Date is in the last 7 days**, Show More → **Group By: Day**.
2. **Repeat with Each** (Health Samples). Inside the loop:
   - **Get Details of Health Samples** → **Start Date** of Repeat Item
   - **Format Date** → Custom → `yyyy-MM-dd`
   - **Get Details of Health Samples** → **Value** of Repeat Item
   - **Text**:
     ```
     date: [Formatted Date]
     steps: [Value]

     ```
     (one empty line at the end)
3. After **End Repeat**: **Combine Text** → Repeat Results with **New Lines**; **Set Variable** → `StepsText` = Combined Text.
4. **Copy to Clipboard** → StepsText.

Tip: if a new action lands below End Repeat instead of inside the loop, press-and-hold it and drag it up between Repeat and End Repeat.

Run it once: Allow **Steps** when iOS asks. Nothing shows on screen; the text is on the clipboard. Open Ironlog → Paste from clipboard → Allow Paste.

## Make it automatic

Shortcuts → **Automation** → **+** → **Time of Day** → e.g. 7:00 AM, Daily → **Run Immediately** → **Sync to Ironlog**. Each morning the fresh steps are on the clipboard; paste when you open Ironlog.

## If something's off

- **"Clipboard doesn't contain Health data from the shortcut"** → run the shortcut first, or something copied over it since. Run it again, then paste.
- **"Already up to date — nothing new"** → the same days were already imported (normal if you paste twice).
- **Step counts look tiny** → Group By in step 1 isn't set to Day, so Value is a single sample instead of a daily total.
- **Test without Health** → More → Health → Advanced → paste the example text there and tap Import.

## Share a modified shortcut

Long-press its tile → **Share** → **Copy iCloud Link**. Paste into Ironlog under More → Health ("Already have an iCloud shortcut link?") or send it to the maintainer to replace the built-in link.
