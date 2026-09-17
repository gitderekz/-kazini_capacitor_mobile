# Wateja Capacitor Mobile App

This project wraps the existing Wateja React web app as a native Android/iOS shell using Capacitor.

## What this app does
- Builds the actual Wateja frontend from `../wateja`
- Copies the production build into the Capacitor `www` folder
- Packages it into native Android and iOS projects
- Keeps the app behavior aligned with the existing Wateja UI rather than rebuilding the interface from scratch

## Commands

```bash
cd /home/kali/miradi/phoisec-web-mobile/mobile/wateja_capacitor_mobile
npm install
npm run build:web
npm run sync
npm run open:android
```

For Android build validation:

```bash
cd android
./gradlew assembleDebug
```

For a release build:

```bash
cd android
./gradlew assembleRelease
```

## Important notes
- The source of truth remains the Wateja web project in `../wateja`.
- The Capacitor app loads the built static frontend, which keeps the exact app behavior consistent with the web version.
- Local developer testing can be done by running the Wateja dev server and configuring navigation in `capacitor.config.json`.
