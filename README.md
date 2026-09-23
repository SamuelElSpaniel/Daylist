# Daylist — iPhone-friendly offline PWA

Daylist is a personal task planner designed for installation from **Safari > Share > Add to Home Screen**. No Xcode or Apple Developer account needed. It is a standalone static website with no backend, analytics, accounts or subscription.

## Features
- Today screen with a week selector, Work/School/Personal tasks and completion progress.
- Recurring daily, weekday, weekly, and monthly routines. Weekly routines repeat on the weekday they are created; monthly routines repeat on that calendar date. Each occurrence has its own checkmark history.
- Unscheduled inbox for surprise tasks, plus move-to-today / choose-date / move-to-inbox actions.
- Month calendar and overdue unfinished one-time tasks on today's screen.
- On-device storage via `localStorage` and JSON backup export/import.
- Offline-ready after the first successful online load, using an installable PWA manifest and service worker.

## Publish free with GitHub Pages (no Mac required)
1. Unzip this package in the iPhone **Files** app, or on any computer. Keep all the files together, including the `icons` folder.
2. Sign in at https://github.com and create a **public repository**, for example `daylist`. (GitHub Pages on GitHub Free uses public repositories; note your site's *code* is public, but your tasks stay local on your iPhone.)
3. Select **Add file > Upload files**, upload `index.html`, `app.js`, `styles.css`, `sw.js`, `manifest.webmanifest`, the empty `.nojekyll` file, and the entire `icons` folder with its three PNG files (the `.nojekyll` file is optional if the upload interface hides it). On iPhone, GitHub's mobile upload can be awkward: use Safari **Request Desktop Website** if necessary or upload using any computer. Maintain the structure shown below. Commit the files on the default branch.
4. In the repository choose **Settings > Pages > Build and deployment**. Choose **Deploy from a branch**, `main`, and `/ (root)`; press Save.
5. When published, GitHub provides a URL similar to `https://YOUR-USERNAME.github.io/daylist/`. Open that exact HTTPS URL in **Safari** on your iPhone. (GitHub Pages publishing is usually not instantaneous.)
6. Tap **Share** (the square with the up arrow), then **Add to Home Screen**. If offered, enable **Open as Web App**. Tap **Add**.
7. Launch Daylist via its new icon while connected to the internet once. The service worker caches the app's files for future offline use. Afterwards, turn on Airplane Mode to test opening it offline.

**Do not upload the ZIP file alone to Pages:** the individual website files must exist at the published root, with the `icons/` folder preserved. GitHub Pages requires an `index.html` at that location. If the icons folder is flattened on upload, create it first and upload its files inside the folder.

Alternative: upload these same files to any HTTPS static site host such as Netlify Drop (https://app.netlify.com/drop). Use the complete unzipped `Daylist-PWA` folder, not its Swift app predecessor. The finished HTTPS URL is your install link; a ZIP by itself is not installable from Safari.

## Data and privacy
Your tasks are saved only in the browser's local storage on the specific device and app installation. They **do not** automatically sync with Apple Calendar, iCloud, Safari on other devices, or another installation of Daylist. To protect your tasks, open **More > Download backup** regularly and save the exported `.json` to iCloud Drive or Files. **More > Restore from backup** replaces the current task list. Clearing Safari website data, deleting/reinstalling the Home Screen app, or changing its website URL can cause data loss. Storage persistence can vary by iOS version and usage, so backups matter.

No native iOS notifications, Apple Calendar synchronization, automatic school assignment imports, or cloud sync are included. The Home Screen experience depends on iOS/Safari's support for PWA features. Offline use starts only after the site is visited online at least once and the service worker's install/cache succeeds. Backups can be downloaded offline on supported browsers.

## Optional local testing on a computer
Run `python3 -m http.server 8000` in this folder and browse to `http://localhost:8000`. A local server is important: opening `index.html` directly as a `file://` URL won't register a service worker. For the iPhone, publish to HTTPS first.

## File structure
```
Daylist-PWA/
  index.html
  styles.css
  app.js
  manifest.webmanifest
  sw.js
  .nojekyll
  icons/
    icon-192.png
    icon-512.png
    apple-touch-icon.png
  README.md
```
