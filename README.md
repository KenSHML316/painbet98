# PAINBET '98 — offline Android app

`www/` is your game, fully offline: Tailwind CSS is compiled locally, `marked` and the three
fonts (Press Start 2P, VT323, Cinzel) are bundled. No internet is needed once installed.
Progress (your bank) is saved on the phone through the WebView's localStorage.

## Easiest way: get the APK from GitHub (no installs)
1. Create a free GitHub repo and upload everything in this folder (including `.github`).
2. Open the repo's **Actions** tab, run **Build PAINBET 98 APK** (it also runs on every push).
3. When it finishes (about 5 minutes), download the `painbet98-apk` artifact, unzip it, and you
   have `app-debug.apk`.
4. Copy it to your phone, allow "Install unknown apps", and open it. The game starts in landscape.

## Build it on your own computer
Needs Node 18+, JDK 17 and Android Studio (for the Android SDK).
```
npm install
npx cap add android
npx cap sync android
npx cap open android      # then Build > Build APK(s) in Android Studio
```
For landscape, add `android:screenOrientation="sensorLandscape"` to the `<activity>` tag in
`android/app/src/main/AndroidManifest.xml`.

## Changing the game later
Edit `www/index.html`. If you add new Tailwind classes, re-run:
`npx tailwindcss -i in.css -o www/tailwind.css --minify` (see `in.css` and `tailwind.config.js`).
Then `npx cap sync android` and rebuild.
