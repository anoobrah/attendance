# Attendance Tracker

A class attendance tracker that installs on your phone like an app.

- Every class counts as **present** unless you mark it **Absent**.
- Missed a class for a medical reason? Mark it **Medical** and attach the report (photo or PDF). One report can cover several classes, even across courses.
- Medical absences don't count against you: attendance % = attended ÷ (classes held − medical).
- Each course shows its %, estimated attendance marks (e.g. ≈ 9.2 / 10), and how many more classes you can miss and stay above the minimum (default 75%).
- Holidays: tick "No classes this day" and that day's classes don't count. **Cancelled** does the same for a single class.

It works offline and needs no account. Everything, including report files, stays in the browser on the device where you use it.

## First-time setup (in the app)

1. **Setup → Semester**: first day of classes, and the last day if you know it (that enables "classes you can still miss this semester").
2. Set the attendance marks (default 10) and minimum % (default 75).
3. **Setup → Courses**: add each course and its weekly class times (e.g. CSE 4305: Sun 9:00, Tue 9:00).

After that, use **Today** to mark absences, **Reports** to add medical reports, and **Courses** to see where you stand.

## Files

| File | What it does |
|---|---|
| `index.html` | The whole app (layout, styles, logic) |
| `manifest.webmanifest` | Name, icon and colors used when installing |
| `sw.js` | Service worker that caches the app so it opens offline |
| `icons/` | App icons (normal, maskable for Android, Apple touch icon) |

## Put it online with GitHub Pages

1. Create a new **public** GitHub repository, e.g. `attendance`.
2. Upload everything in this folder, keeping the `icons` folder (Add file → Upload files).
3. Settings → Pages → Deploy from a branch → `main` → `/ (root)` → Save.
4. It goes live at `https://<your-username>.github.io/attendance/`.

## Install on your phone

Open the address in Chrome → ⋮ → **Install app**. On iPad/iPhone: Safari → Share → **Add to Home Screen**.

## Your data

- Stored in this browser on this device only (report files in IndexedDB).
- Uninstalling the app or clearing site data **deletes it**. Use **Setup → Back up** now and then; the backup includes the report files.
- **Restore** merges a backup into what's already there.
- **Export CSV** lists every class held with its status, for Google Sheets.

## Updating the app

Edit the files and upload them to the repo again. If you change `sw.js` or the icons, bump `CACHE = "attendance-v1"` to `v2`.
