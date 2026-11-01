# Pocket Dungeon (Android)

The game lives in `www/index.html`. GitHub Actions wraps it with Capacitor and builds an APK.

## Get the APK
1. Push this folder to a GitHub repo (branch `main`).
2. Open the repo's **Actions** tab, wait for "Build Android APK" to finish (~5 min).
3. Open the run, download the `pocket-dungeon-apk` artifact, unzip it, and you have `app-debug.apk`.
   (Or push a tag like `v1.0` and the APK is attached to a GitHub Release, which is easy to download on the phone.)
4. Copy/download the APK to your phone, tap it, and allow "install unknown apps" when asked.

## Updating the game
Edit `www/index.html`, commit, push. A new APK is built automatically.

## Updating an installed app
Every build gets an automatically increasing version code (the GitHub run number, which is what Android uses to allow updates) and is signed with the key in `keystore/`.
The version name people see (e.g. 1.1.0) comes from `"version"` in `package.json`, so change it there when you release something new.
That means a new APK installs straight over the old one and keeps your save. Keep the `keystore` folder in the repo and never change it.
Note: APKs built *before* this change were signed with a throwaway key, so the first time you install a build from this version you must uninstall the old app (this erases its save). After that, updates install normally.
