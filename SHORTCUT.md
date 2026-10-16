# "Sync to Ironlog" — iPhone Shortcut

Pulls the last 7 days of steps and workouts (Apple Watch included) out of the Health app and sends them to Ironlog. One tap, or automatic every morning. Nothing leaves your phone except the data going to your own site.

Takes about 10 minutes to build. Build it on the iPhone in the **Shortcuts** app.

## The idea

1. Ask Health for the last 7 days of **Steps** (one total per day) and the last 7 days of **Workouts**.
2. Turn each into a few lines of text in the format Ironlog reads.
3. Open `https://joeyp031304.github.io/BuffaloJoe-s-Workout-Partner/?import=` + that text.

Ironlog reads the text, saves it, and shows "Imported N workouts, N days of steps." Anything already imported is skipped, so running it twice is harmless.

## Build it

Open **Shortcuts** → **+** (top right) → tap the name at the top and call it **Sync to Ironlog**. Then add these actions in order (use the search bar at the bottom to find each one).

### Part 1 — Steps

1. **Find Health Samples**
   - Type: **Steps**
   - Add a filter: **Start Date** → **is in the last** → **7 days**
   - Tap **Show More** → set **Group By** to **Day** (so you get one total per day, not thousands of tiny samples)
2. **Repeat with Each** (it will pick up the Health Samples automatically). Inside the repeat, add:
   - **Get Details of Health Samples** → Get **Start Date** of *Repeat Item*
   - **Format Date** → Date = that Start Date, Format: **Custom**, string `yyyy-MM-dd`
   - **Get Details of Health Samples** → Get **Value** of *Repeat Item*
   - **Text** containing exactly (use the magic variables, one per line):
     ```
     date: [Formatted Date]
     steps: [Value]

     ```
     (End with one empty line.)
3. After **End Repeat**: add **Combine Text** → combine *Repeat Results* with **New Lines**. Rename this result "StepsText" (tap it → Rename) so it's easy to find later.

### Part 2 — Workouts

4. **Find Health Samples**
   - Type: **Workouts**
   - Filter: **Start Date** → **is in the last** → **7 days**
5. **Repeat with Each**. Inside:
   - **Get Details of Health Samples** → **Workout Type** of *Repeat Item*
   - **Get Details of Health Samples** → **Start Date**; then **Format Date** → Custom `yyyy-MM-dd'T'HH:mm:ss`
   - **Get Details of Health Samples** → **Duration** (comes back in minutes)
   - **Get Details of Health Samples** → **Distance** (in your Health units; Ironlog takes it as miles or km to match your Ironlog setting)
   - **Get Details of Health Samples** → **Active Energy** (calories)
   - **Get Details of Health Samples** → **Average Heart Rate** (may be empty for workouts without a watch; that's fine)
   - **Text**:
     ```
     type: [Workout Type]
     start: [Formatted Date]
     minutes: [Duration]
     distance: [Distance]
     kcal: [Active Energy]
     hr: [Average Heart Rate]

     ```
6. After **End Repeat**: **Combine Text** → *Repeat Results* with **New Lines**. Rename it "WorkoutsText".

### Part 3 — Send it

7. **Text** containing:
   ```
   [StepsText]

   [WorkoutsText]
   ```
8. **URL Encode** → Encode that Text.
9. **URL** → `https://joeyp031304.github.io/BuffaloJoe-s-Workout-Partner/?import=` followed immediately by the *URL Encoded Text* variable (no space).
10. **Open URLs** → that URL.

Tap **Done**. Run it once from the Shortcuts app: iOS will ask to allow Health access for Steps and Workouts (allow both) and may ask to allow opening the website. Ironlog opens, shows the import toast, and your Steps card appears on Home.

## Share it so the app's "Get the shortcut" button works

Once it runs correctly: open the shortcut's menu (⋯ on its tile) → **Share** → **Copy iCloud Link**. Paste that link into Ironlog under More → Apple Health (the "Save link for this device" box), or better, give it to Claude to bake into the site so every new visitor's Yes button installs it in one tap.

## Make it automatic

Shortcuts → **Automation** tab → **+** → **Time of Day** → pick e.g. 7:00 AM, Daily → **Run Immediately** → choose **Sync to Ironlog**. It'll open Ironlog each morning with yesterday's data pulled in.

## If something's off

- **"Import link had no readable Health data"** → the Text in step 7 is empty or the labels are misspelled. Labels must be exactly `date`, `steps`, `type`, `start`, `minutes`, `distance`, `kcal`, `hr`, each followed by a colon.
- **Workouts show but steps don't** → Group By in step 1 isn't set to Day, so Value is a tiny sample instead of a daily total.
- **Running shows as "Cardio"** → fine; Ironlog maps Running/Walking/Hiking/Cycling/Swimming/Rowing/Stair/Elliptical by name, anything else becomes generic cardio (or a strength session if the type says Strength/HIIT/Core).
- **Distance looks wrong** → Health reports distance in the unit set in the Health app. If Ironlog is in miles, set Health to miles too (Health → Profile → Units).
- **Want to test without Health** → More → Apple Health import → paste the example text there and tap Import.
