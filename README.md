# TCG Collection Manager — releases

Downloads and the update feed for the TCG Collection Manager app. This repo
holds no source code; it only receives finished builds.

**To install the app, see [`install/`](install/):**
[Windows](install/windows.md) · [Mac](install/mac.md) · [iPhone](install/iphone.md)

> **Before you install:** the app talks to its server over Tailscale, so it
> only works on devices signed in to the store owner's Tailscale network.
> Public access comes later.

## What lives here

Every [release](../../releases) (`vYYYY.MM.N`, e.g. `v2026.10.19`) carries:

| File | What it is |
|---|---|
| `…_windows-x64-setup.exe` | Windows installer |
| `…_macos-universal.dmg` | Mac installer (Apple chip and Intel) |
| `…_macos-universal.app.tar.gz` | The Mac app, packed for the in-app updater |
| `….sig` | Signature the app checks before installing an update |
| `SHA256SUMS.txt` | Checksums, to verify a download |
| `latest.json` | The update feed installed apps read |

The Mac files are added a few minutes after the Windows ones, once the Mac
that builds them is awake.

iPhone builds are not published here: Apple doesn't allow installing them
from a download. See [install/iphone.md](install/iphone.md).

## How updates work

1. A change to the app is merged into the private source repo.
2. Builds run automatically and publish a new release here.
3. Installed apps on Windows and Mac read `latest.json` when they start and
   every 6 hours. When it lists a newer version, the app shows
   **Update now**.

The repo is public so apps can read the feed without logging in. That is
safe: every update is signed with a private key only the build machines
have, and the app refuses any update whose signature doesn't match.

Don't add or edit files here by hand; releases are created by the build.
