# Block Drop

An original, offline-capable falling-block puzzle game designed for touch screens. This repository contains a responsive web game that can be installed from a supported mobile browser, plus a Capacitor configuration for producing a native Android wrapper.

## Play on Android now

1. Open the hosted game URL in Chrome on Android (or serve this project over HTTPS).
2. Use Chrome's **Install app** / **Add to Home screen** action.
3. Launch Block Drop from the home screen. Core gameplay and saved scores work offline after the first successful load.

For local testing, serve the `www` directory from an HTTPS host or localhost. Service workers do not work from a `file://` URL. For a quick desktop server, run `python -m http.server 8080 --directory www` and open `http://localhost:8080`.

## Game features

- Five modes: Classic, Sprint (40 lines), Time Attack (2 minutes), Zen, and an 8-line Challenge.
- Seven-piece shuffled-bag generation, rotation with simple wall kicks, ghost landing guide, hold, five-piece preview, hard/soft drop, line clears, levels, scoring, and combos.
- Touch buttons, swipe movement/drop, tap rotation, and keyboard controls for desktop testing.
- Dark/light themes, synthesized original sound effects with mute, and locally stored best scores/statistics/settings.
- Responsive portrait layout, installable web app metadata, offline service-worker cache, and no accounts, ads, analytics, tracking, or network calls during gameplay.

## Android native wrapper (Capacitor)

This source is ready to be wrapped with Capacitor, but this repository does **not** contain a compiled APK/AAB or generated Android Studio project. Build artifacts must be created and tested on a machine with the Android SDK and Java installed.

1. Install Node.js LTS and Android Studio with the Android SDK / platform tools.
2. From the repository root, run `npm install`.
3. Generate the native Android project with `npx cap add android` (only once), then `npx cap sync android`.
4. Open it using `npx cap open android`; confirm the package ID `com.sayod0050.blockdrop` is available to you and set the current required target API in the Android Gradle configuration before release. Google Play's target API rules change regularly; verify the current requirement in the Play Console and official Android documentation at submission time.
5. Build and install a debug APK through Android Studio, then test on both a physical phone and an emulator. For store publication, configure a private release keystore, build a signed Android App Bundle (AAB), and keep the keystore and passwords out of source control.

Typical Capacitor build commands after generating the Android project:

```bash
npx cap sync android
cd android
./gradlew assembleDebug
./gradlew bundleRelease
```

On Windows use `gradlew.bat assembleDebug` and `gradlew.bat bundleRelease`. A release build is not signed for publishing until a secure signing configuration is provided. Do not commit signing keys or credentials.

## Controls

| Action | Touch | Keyboard |
| --- | --- | --- |
| Move | Left/right buttons or swipe | ← / → or A / D |
| Rotate | Tap board or rotate button | ↑ or W |
| Soft drop | Down button or short downward swipe | ↓ or S |
| Hard drop | DROP button or long downward swipe | Space |
| Hold | HOLD button | C |
| Pause | Pause button | P or Escape |

## Testing status and limitations

The game source is committed, but no Android build, device run, automated test suite, or Play submission has been performed in this environment. Verify gameplay modes, rotations, storage, lifecycle interruption/resume, responsive layouts, and offline behavior before release. The wrapper does not add native ads, analytics, permissions, or a privacy-sensitive data collection flow. Store listing artwork, screenshots, privacy-policy hosting, content-rating questionnaire, and release signing still need to be prepared for an actual Play release.
