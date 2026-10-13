# TODO: make this repo public

This repo is the download host and update feed for the TCG Collection
Manager desktop app. It holds only build outputs; source lives in the
private `mdn1023/tcg-collection-manager` repo, whose `app release` workflow
publishes here on every merge to `main` that touches `ui/`.

Each release `vYYYY.MM.N` carries:

- `TCG-Collection-Manager_<ver>_windows-x64-setup.exe` + `.sig` (updater signature)
- `SHA256SUMS.txt`
- `latest.json`, the feed that installed apps poll

## Why it must become public

Installed apps fetch
`https://github.com/mdn1023/tcg-collection-manager-releases/releases/latest/download/latest.json`
anonymously on launch and every 6 hours. While this repo is private that
URL returns 404, so **the in-app "Update now" banner never appears**. No
error is shown to the user; the app just stays on its version. Publishing
still works, because CI writes with `RELEASES_TOKEN`.

Making it public exposes only the installers and signatures. The update
mechanism does not depend on secrecy: every installer is signed with a
private minisign key that CI holds, and each app verifies the signature
against the public key baked into it before installing anything.

## To flip it

```powershell
gh repo edit mdn1023/tcg-collection-manager-releases --visibility public --accept-visibility-change-consequences
```

Takes effect on the apps' next check. No rebuild, no reinstall.

## Also still needed (one-time)

- [ ] Fine-grained PAT, Contents: read/write on this repo only, stored as
      `RELEASES_TOKEN` in `mdn1023/tcg-collection-manager` secrets.
      Without it the `release` job fails at "Release (public releases repo)".
- [ ] Make this repo public (above).
- [ ] Delete this `.TODO/` folder once both are done.

Details: `ui/RELEASE.md` in the source repo, section "Updates".
