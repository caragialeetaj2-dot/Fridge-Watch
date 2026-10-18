# Watch Weather – Android (Capacitor)

720p (1280×720) landscape clock + live weather station.
Clock ⇄ Pitești rotate every 20 s; Valea Mare and Arefu open only from the location buttons
(and return to the clock after 20 s without interaction).

## Buttons
- **⟳ Actualizează** (weather screen, bottom right): updates all 3 locations now.
  Shows "Actualizat" on success or "Fără conexiune" if offline (cached data stays on screen).
- **Zile următoare / Prognoză pe ore**: switches between hourly and 7-day forecast.
- **✕** (top right, both screens): tap once → "Apăsați din nou pentru ieșire", tap again within 3 s to exit.

## Weather
Open-Meteo (https://api.open-meteo.com/v1/forecast) – current, hourly, 7-day daily.
Automatic refresh every 15 min + on app resume + when the network comes back + manual button.
Offline: last successful response per location is cached with @capacitor/preferences.

## Build on GitHub (no local tools needed)
Upload all files to the repository root (including `.github/workflows/build-apk.yml`).
Actions tab → Build Android APK → wait for ✅ → Artifacts → watch-weather-apk.

## Build locally
```bash
npm install
npm run build
npx cap add android
npx cap sync android
npx cap open android
```
Android Studio: **Build > Build APK(s)**.

## Kiosk
`package.json → watchWeather.kioskLauncher: true` makes the app selectable as the Home screen
(auto-start after reboot). Note: in that mode, ✕ closes the app but Android reopens it as the Home screen.
Set it to `false` if you want ✕ to return to the normal Android home screen.
