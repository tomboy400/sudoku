# Sudoku

A simple Sudoku game for Android, built as a web app and wrapped with [Capacitor](https://capacitorjs.com/).

## Play

- **Easy / Medium / Hard** difficulties with generated puzzles (unique solutions)
- Number pad, erase, hints (3 per game), timer
- 3 mistakes and it's game over — win dialog when the board is complete

## Project layout

| Path | What's in it |
|---|---|
| `index.html` | The game itself — open in any browser to play |
| `app/` | Capacitor project (`com.tomboy.sudoku`) |
| `app/www/` | Web assets synced into the Android app |
| `app/android/` | Generated Android project (Capacitor) |
| `build-apk/` | Standalone APK build scripts (no Gradle needed) |

## Build the APK

The `build-apk/` scripts build a debug APK without Gradle:

```bash
cd build-apk
python3 resolve_deps.py deps   # download Maven dependencies (needs network)
python3 build_apk.py           # aapt2 → javac → d8 → zipalign → apksigner
```

Requirements: JDK 17 and the Android SDK (build-tools 34.0.0, platform 36).
The signed APK lands at `build-apk/out/sudoku-debug.apk`.

## Run in a browser

Just open `index.html` — no build step needed.
