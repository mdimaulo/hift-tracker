84 Days — HIFT Tracker v3 (personal PWA)
========================================
Files: index.html (whole app, plan data embedded), sw.js (offline cache),
manifest.webmanifest, icon-180/192/512.png

NEW IN V3
- Extra sessions: schedule any additional training (cycling, swimming,
  running, evening strength...) on any day from Train or Today. Each shows
  an energy estimate, can be ticked done, and feeds the AI coach.
- Auto nutrition adjustment: endurance sessions raise THAT day's calorie
  and carb targets (MET x body weight x duration; ~60% of extra energy as
  carbs; +0.5 L water per hour) and generate a pre/during/post fuel plan
  in the meals card, sized to the session. Estimates - tune weight in gear.

NEW IN V2
- Planned meals: mark each item eaten (v, counts in totals) or skipped (x);
  Edit mode to remove items or add your own.
- Training: tap any exercise to report what you actually did + RPE 1-10;
  Edit mode to remove exercises or add from the library / custom.
- Library tab: all 51 movements grouped by movement pattern, with videos.
- AI Coach: "Review my week" analyzes your last 7 days (actual vs planned,
  RPE, macros) and returns concrete scaling/progression advice.

DEPLOY (GitHub Pages)
1. github.com -> New repository (e.g. "hift-tracker") -> create.
2. "Add file" -> "Upload files" -> drop ALL files -> Commit.
3. Settings -> Pages -> Deploy from a branch -> main / root -> Save.
4. App at https://<username>.github.io/hift-tracker/
   Safari -> Share -> "Add to Home Screen".

UPDATING AN EXISTING DEPLOYMENT
Replace index.html AND sw.js (cache already bumped to hift84-v3),
then reopen the app; it refreshes to the new version.

API KEY (needed for photo analysis + coach)
Never commit a key to a public repo - anyone could read and abuse it.
Option A (recommended): open the app once as
  https://<your-app-url>/#key=sk-ant-...
  The key is saved on the device and stripped from the URL. Or paste it in
  the gear settings.
Option B: the EMBEDDED_KEY constant at the top of index.html - fill it ONLY
  if your repo/hosting is private (e.g. Cloudflare Pages from a private repo).

NOTES
- All logs stay on the device (IndexedDB). Clearing Safari website data erases them.
- Works offline except photo analysis, coach review and YouTube links.

--- v4 additions ---
• Meals are now built from ITEMS. Tap any planned meal to expand it: remove items (trash), add items
  from the built-in food list (161 foods, searchable, 10 categories, quantity in 0.5 steps), or tap ✨
  on an item for 3 AI-suggested replacements matched to the meal and your remaining macros for the day.
  Calories, protein, carbs and fat recalculate instantly per meal and in the "Plan total" footer;
  if a meal was already ticked as eaten, its log entry updates too.
  Note: item sums are now the source of truth — they can differ ~5-10% from the original spreadsheet's
  rounded figures (the spreadsheet's protein numbers were low for the stated portions).
• Exercise library expanded from 51 to 500 movements with modality filter chips:
  Kettlebell 113 · Barbell 100 · Calisthenics 119 · Mobility 111 · Dumbbell 28 · Conditioning 29.
  The same filters appear when adding exercises to a session (Train → ✎ Edit → Add).
• Deploying this update: replace index.html AND sw.js in your repo (cache is now hift84-v4),
  then open the installed app, wait ~15 s, close it fully, reopen.

--- v5: rebuilt on the fasting + kettlebell workbook (25 Jul - 16 Oct 2026) ---
• Targets are now PER DAY from the plan (calories, protein, water) and appear on every screen;
  the settings sheet keeps only body weight and the API key.
• Fasting protocol built in: 36h fasts in weeks 3/6/9 and a 48h fast in week 12.
  Fasting days show a banner with the exact window and stop-criteria, zero food targets,
  a 3L+ water goal, hydration-only guidance instead of meals, and the training tab switches
  to the fasting protocol with a "training suspended" notice. Extra sessions on those days
  no longer raise calorie/carb targets (only water), and no fuel suggestions are generated.
  Refeed days follow with their own 2200 kcal break-fast meal plans.
• Full kettlebell days (weeks 2/5/8/11) render with their own sections
  (Kettlebell Work-up, Load/Skill Ramp, Integrated KB WOD...).
• Plan tab shows a type icon per day (🤸 🏋️ 🚶 🧘 ⏳ 🍽 📏), per-day kcal/protein/water.
• The AI coach knows the fasting rules and will not prescribe food or training inside a fast.
• Everything from v4 remains: item-level meals, 161-food list, ✨ AI swaps, 500-exercise library.
Deploy: replace index.html AND sw.js (cache hift84-v5), open app, wait 15 s, close fully, reopen.

--- v6: re-dated plan (10 Aug - 1 Nov 2026) ---
• Rebuilt on the "start_2026-08-10" workbook: Day 1 is Monday 10 August; the block ends Sunday 1 November.
• Fasting: 36h fasts land on days 21/42/63 (weeks 3/6/9), the 48h fast covers days 83-84 (week 12).
  Day 84 ends the 48h fast at 20:00 with a light 700 kcal break-fast dinner, shown with the fasting
  banner and no activity-based target increases. The week-12 refeed day falls after the block ends.
• Refeed days 22/43/64; full kettlebell days 13/34/55/76; new session sections (Movement Prep,
  Main Work, Kettlebell WOD, Mobility Downshift...) render automatically.
• New meal-sheet guidance rows (electrolytes, no-calorie rule, avoid-list, safety stop criteria)
  are folded into the day's hydration line. Two new break-fast meals are item-decomposed like the rest.
Deploy: replace index.html AND sw.js (cache hift84-v6), open the app, wait 15 s, close fully, reopen.

--- v7: re-dated plan (27 Oct 2026 - 18 Jan 2027) ---
• Same plan content as v6, re-anchored: Day 1 is Tuesday 27 October 2026; the block ends Monday
  18 January 2027. Weekday labels and all fasting-window dates were regenerated for the new calendar.
• Because the whole calendar shifts by one weekday, the fasting rhythm moves with it:
  36h fasts now run Sunday 20:00 -> Tuesday 08:00 (full fast day = Monday) on 15-17 Nov, 6-8 Dec
  and 27-29 Dec; the 48h fast runs Sat 16 Jan 20:00 -> Mon 18 Jan 20:00, ending with the light
  700 kcal break-fast dinner on the final plan day. Refeed days: 17 Nov, 8 Dec, 29 Dec.
  Full kettlebell days: Sundays 8 Nov, 29 Nov, 20 Dec, 10 Jan.
• Note: one 36h fast spans 27-29 December. Move or skip it freely if it collides with the holidays —
  the plan is a template, not a contract.
Deploy: replace index.html AND sw.js (cache hift84-v7), open the app, wait 15 s, close fully, reopen.
