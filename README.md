# Workout Tracker

A personal workout tracking app that lives on your iPhone home screen. Built as a single HTML file hosted on GitHub Pages, with your workout data automatically backed up to this repository.

---

## What it does

- Log workouts from scratch or from saved templates
- Track sets, reps, and weight for each exercise
- Organised exercise library with muscle groups
- Progress charts per exercise
- Consistency calendar (heatmap showing days you trained)
- Weekly workout goals and streak tracking
- Bodyweight tracking
- Planned break weeks
- Automatic data backup to GitHub after every change
- Works offline once installed

---

## First-time setup

### 1. Enable GitHub Pages

Go to this repository on GitHub → **Settings** → **Pages** → under *Source* choose **Deploy from a branch** → select `main` branch and `/ (root)` folder → click Save.

After a minute or so your app will be live at:
```
https://[your-github-username].github.io/workout-tracker
```

### 2. Create a fine-grained GitHub token

The app needs permission to write your workout data back to this repository as a backup file.

1. Go to [github.com/settings/tokens](https://github.com/settings/tokens) → **Fine-grained tokens** → **Generate new token**
2. Give it a name (e.g. *Workout Tracker*)
3. Under **Repository access**, choose *Only select repositories* and pick this repo
4. Under **Permissions → Repository permissions**, find **Contents** and set it to **Read and write**
5. Generate the token and copy it — you won't be able to see it again

### 3. Set up on iPhone

1. Open Safari on your iPhone and go to your GitHub Pages URL above
2. The app will show a short setup wizard — choose your preferred week start day and whether to load a starter exercise list
3. Tap **Connect GitHub** and enter:
   - Your GitHub username
   - Repository name (`workout-tracker`)
   - The fine-grained token you just created
4. Tap **Test and connect** — the app will verify the token works
5. If this is a fresh install, it will create the backup file automatically on first sync. If you're setting up a second device, it will detect the existing backup and offer to restore it.
6. Once connected, tap the Share button in Safari → **Add to Home Screen**

Your app is now installed. Open it from the home screen icon from now on — it runs as a standalone app with no browser chrome.

---

## Day-to-day use

- **Starting a workout** — tap the Workout tab, pick a template or start blank
- **Logging a set** — enter weight and reps, tap the tick to mark it complete
- **Finishing** — tap *Finish Workout* at the bottom; incomplete sets are discarded or kept (you choose)
- **Progress** — the Progress tab shows your consistency calendar and per-exercise charts
- **Templates** — saved workout structures you can start from repeatedly

Data saves automatically after every action and syncs to GitHub in the background whenever you have a connection.

---

## Making changes to the app

All the app code lives in `index.html`. To make a change:

1. Edit `index.html` in this repository (either locally or via GitHub's editor)
2. Commit and push to `main`
3. GitHub Pages will redeploy automatically — usually takes under a minute
4. Open the app on your phone with an internet connection and it will load the new version straight away

The app uses a service worker for offline support. Because it's set up network-first, it always fetches the latest version when online — you don't need to do anything special to get updates.

---

## Adding a second device

1. Open Safari on the new device and go to your GitHub Pages URL
2. Go through the setup wizard
3. Connect GitHub with the same username, repo, and token
4. The app will detect the existing backup and offer to restore it — choose **Restore GitHub data**
5. Add to home screen

Both devices will stay in sync via GitHub — changes on one device back up and are picked up by the other next time it's online.

---

## Data and backup

Your workout data is stored in two places:

- **On-device** — in the browser's local storage (IndexedDB), survives app restarts
- **GitHub** — `data/workout-data.json` in this repository, updated automatically after every workout

If you ever need to manually restore from a backup, go to **Settings** → **Backup** inside the app.
