# Iron Log

A private lifting tracker for Android: built-in strength programs (Starting Strength, GZCLP, 5/3/1 Boring But Big, Texas Method, Smolov Jr) that work out every set's weight and progress as you log. Plate calculator, rest timer with a lock-screen alarm, exercise swaps, and custom day layouts.

Your workouts are stored only on your phone. Nothing is sent anywhere. The only network call is the optional update check against this repo's releases.

## Install or update

1. On your phone, open **[the latest release](https://github.com/Kawana87/iron-log/releases/latest)** and download `iron-log.apk`.
2. Open the downloaded file. The first time, Android asks you to allow installs from your browser; allow it.
3. Tap **Install** (or **Update**). Updates install over the top and keep your data.

The app checks for new versions when you open it and shows an "Update ready" banner on the Today screen.

## Backups

Settings → **Save backup file** shares a `.json` file you can save to Google Drive, email or Files. Restore it from Settings → **Restore from a backup**. Uninstalling the app deletes its data, so keep a recent backup.

## How builds work

Every push to `main` runs `.github/workflows/android.yml`, which builds the app with Capacitor and Gradle, signs it, and publishes a GitHub release with `iron-log.apk`. The signing key lives only in the repository secrets `KEYSTORE_B64` (base64 of a PKCS12 keystore, alias `ironlog`) and `KEYSTORE_PASS`. Every release must be signed with the same key, or it won't install over the previous version.

- App code: `www/index.html` (a single page) plus bundled fonts in `www/fonts/`
- Native project: `android/` (Capacitor 6)
- Build logs: the `ci-logs` branch keeps the last ten
