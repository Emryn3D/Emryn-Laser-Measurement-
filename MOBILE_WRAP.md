# Mobile Packaging (iOS + Android)

This project now behaves as a mobile-friendly web app and can be packaged as a native app shell using **Capacitor**.

## Why this matters
- Android Chrome can use Web Bluetooth in HTTPS context.
- iOS Safari does not support Web Bluetooth, so a native wrapper lets you add native Bluetooth plugins for App Store builds.

## Quick wrap steps
1. Install dependencies:
   ```bash
   npm init -y
   npm install @capacitor/core @capacitor/cli @capacitor/android @capacitor/ios
   ```
2. Initialize platforms:
   ```bash
   npx cap add android
   npx cap add ios
   ```
3. Sync web assets:
   ```bash
   npx cap sync
   ```
4. Open native IDE projects:
   ```bash
   npx cap open android
   npx cap open ios
   ```

## Bluetooth support for "any" laser
- Current app supports generic GATT discovery and URL-based service/characteristic mapping (`btService`, `btCharacteristic`, `btFormat`, `btUnits`, `btScale`).
- For unsupported models (especially on iOS), add a Capacitor native BLE plugin and feed decoded values into the same measurement pipeline used by `handleNotification`.

## Recommended next step
Create a device profile registry (JSON) per model (Leica, Bosch, Hilti, etc.) and ship it with the app so field users can select model profiles instead of entering URL params.
