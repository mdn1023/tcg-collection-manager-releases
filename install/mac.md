# Install on a Mac

**Status: ready.** One app for both Apple-chip and Intel Macs (macOS 12 or
newer).

There is no paid Apple Developer account behind this app, so macOS can't
verify who made it and blocks it the first time. You allow it once, and
after that it opens normally.

## Install

1. Open the [latest release](../../../releases/latest) and download
   `TCG-Collection-Manager_<version>_macos-universal.dmg`.
2. Open the `.dmg` and drag **TCG Collection Manager** into **Applications**.
3. Open the app from Applications. macOS says it **"could not verify"**
   the app. Click **Done** (not Move to Trash).
4. Open **System Settings → Privacy & Security**, scroll down to the
   message about TCG Collection Manager, and click **Open Anyway**.
   Enter your Mac password.
5. The app opens. Sign in.

You only do steps 3–4 once.

## If macOS says the app "is damaged"

That message means macOS blocked an unverified download, not that the file
is broken. In **Terminal**, run:

```sh
xattr -dr com.apple.quarantine "/Applications/TCG Collection Manager.app"
```

Then open the app again.

## Updates

Nothing to do. When a new version is out the app shows **Update now**;
click it and the app restarts on the new version.

## Remove

Drag **TCG Collection Manager** from Applications to the Trash.
