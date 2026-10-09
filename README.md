# AttendanceManager — Website

Static landing page for **AttendanceManager**, an Android app that helps college students track attendance per subject, record Attend / Bunk / OD, and check the math before skipping a class.

This site is hosted with **GitHub Pages**. It is not the app itself. The APK is distributed through **GitHub Releases**.

## Project structure

```
.
├── index.html                 # The whole site (HTML, CSS and JS in one file)
├── assets/
│   ├── icon.png               # App icon (nav, footer, favicon)
│   └── screenshots/           # App screenshots shown on the site
│       ├── home.jpg
│       ├── subjects.jpg
│       ├── subject-details.jpg
│       ├── calculator.jpg
│       ├── digicampus.jpg
│       └── settings.jpg
├── .gitignore
└── README.md
```

## Configuration

All links are configured in one place: the `CONFIG` block near the bottom of `index.html`.

```js
const CONFIG = {
  GITHUB_REPOSITORY_URL: "https://github.com/bharathraj-b-dev/Attendance-Manager", 
  VERSION: "v1.0",
  SCREENSHOTS: [ ... ]
};
const APK_DOWNLOAD_URL   = CONFIG.GITHUB_REPOSITORY_URL + "/releases/latest/download/AttendanceManager.apk";
const GITHUB_RELEASES_URL = CONFIG.GITHUB_REPOSITORY_URL + "/releases";
const ISSUES_URL          = CONFIG.GITHUB_REPOSITORY_URL + "/issues";
```

The repository is set to `bharathraj-b-dev/Attendance-Manager`. If it ever moves, change that one value. Every Download button, the "View All Releases" button, and the bug-report link follow from that one value.

## How downloads work

The Download APK buttons link directly to:

```
https://github.com/<user>/<repo>/releases/latest/download/AttendanceManager.apk
```

so the file downloads without visiting the release page. For this to keep working, **every release must upload its APK named exactly `AttendanceManager.apk`**.

## Releasing a new app version

1. Update `versionCode` and `versionName` in the Android project.
2. Build the signed release APK (same package ID and signing key as before, so updates install over the old version).
3. Create a new GitHub Release with a tag such as `v1.1`.
4. Upload the APK named exactly `AttendanceManager.apk`.
5. Publish the release.

The website does not need to be changed. The changelog entry in `index.html` is static, so add a new entry there by hand only if you want it listed.

## Replacing screenshots

Replace the files in `assets/screenshots/` (keep the same filenames), or edit the `SCREENSHOTS` list in `CONFIG`. All phone frames use the same proportions (about 1080 × 2412), and images are cropped to fit, so screenshots with similar proportions look best. If a file is missing, a labelled placeholder is shown.

## Run locally

No build step. Open `index.html` in a browser, or serve the folder:

```bash
python3 -m http.server 5500
# then open http://127.0.0.1:5500
```

(VS Code's Live Server extension also works.)

## Deploy to GitHub Pages

1. Push these files to your repository.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select your branch and the `/ (root)` folder, then save.
4. The site will be available at `https://<user>.github.io/<repo>/`.

## Notes

- AttendanceManager is an independent project and is not affiliated with or endorsed by DigiCampus or the institution providing it.
- The site uses the Manrope font from Google Fonts; it falls back to system fonts if offline.
- Animations respect `prefers-reduced-motion`.
