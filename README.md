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

iOS / iPhone (macOS + Xcode)

Notes: building and exporting an iOS app requires a Mac with Xcode and CocoaPods installed. Use Xcode for signing and distribution.

1) Open the Xcode workspace

```bash
cd /home/kali/miradi/phoisec-web-mobile/mobile/kazini_capacitor_mobile
npm run open:ios
```

2) (Optional CLI) Install CocoaPods and build for simulator or device

```bash
cd ios
pod install
# build for simulator
xcodebuild -workspace App/App.xcworkspace -scheme App -configuration Debug -destination 'generic/platform=iOS Simulator' build
```

3) Archive and export (for TestFlight / Ad-Hoc / App Store)

Open the workspace in Xcode and use Product → Archive, or run from the command line:

```bash
cd ios
xcodebuild -workspace App/App.xcworkspace -scheme App -configuration Release -archivePath build/App.xcarchive archive
xcodebuild -exportArchive -archivePath build/App.xcarchive -exportOptionsPlist exportOptions.plist -exportPath build
```

You can create an `exportOptions.plist` (example provided in the project) to choose `ad-hoc`, `enterprise`, or `app-store` export methods. Use Xcode Organizer to upload to App Store Connect or export an IPA for distribution.


## Important notes
- The source of truth remains the Wateja web project in `../wateja`.
- The Capacitor app loads the built static frontend, which keeps the exact app behavior consistent with the web version.
- Local developer testing can be done by running the Wateja dev server and configuring navigation in `capacitor.config.json`.
